This document will walk you through the main steps to integrate the "Consolidation Solution" into your platform.

# What do you need to start?
In order to proceed, you have to make sure that you have the following requirements:

*	A working e-learning or LMS platform
*	Credentials to connect to Domoscio's adaptive learning engine API
*	An HTTP requester to try out your request before implementing them
*	Basic knowledge of how to construct a HTTP request and how to interact with an API

Before starting, you can check if a SDK already exists to connect to the API for your programming language. 
For instance, if you are lucky your platform is coded with Ruby, we can use the [SDK](https://github.com/Celumproject/domoscio_rails) that we developped to connect the API to our White Label solution. Otherwise you can always refer to this library to get inspired!

## Get your credentials and connect to the API

Request your API credentiels and you will receive:

1. An instance_id
2. An api_key

With these two elements you can start communicating with the API and requesting some information. The way to do this is to get your favorite HTTP requester and to ping a URL that we will build the following way:

![URL Creation](https://raw.githubusercontent.com/Celumproject/domoscio-docs/master/uploads/creation_url.png)

# Integrating the API into your platform

Let us start actually work on the integration of the API into your platform. In order to fully describe the process we will highlight two parts: information that you will need to provide to the API and information that you might be receiving from the API.


## Information you need to send to the API

In this part, we focus on what your application should declare to the API in order to be able to make its computation and deliver its consolidation functionnalities. For the main part of this section, the method that you will be using is:

	HTTP Method: POST 

If everything goes well with your request, you shall receive a:

	OK RESPONSE 200

or simply a json object describing the newly created object:

	{name: "Mathematics", uid: "mat0036grde", created_at: [Now]}

Amongst all the types of information you should send to the API, the following three are mandatory:

*	Contents structure and meta-data
*	Students and subscriptions
*	Events and users interactions with your platform

### Contents structure and meta-data 

In some cases, the "Contents structure and meta-data" can be imported directly into the API. If that is your case or if you are willing to do so, please contact us directly.

Your learning objects (such as text or videos) are registered as **Contents**. Those Contents deal with one or several concept(s), which are called **Knowledge Nodes** by the API. To express that relationship, **KnowledgeNodeContents** are created.

To do so, we will use the POST method.
First, we will declare a content:

	Method: POST
	URL: HOST_URL/instances/{instance_id}/contents

And you will receive the following message depending on what you actually sent to the API:

	{
		"id": 2,
		"uid": "my_first_content"
	}
	
That content deals with the solar system for instance. This is a concept you will want to declare:

	Method: POST
	URL: HOST_URL/instances/{instance_id}/knowledge_nodes

And you will receive the following message depending on what you actually sent to the API:

	{
		"id": 5,
		"uid": "my_first_concept",
	}
	
The last step is to create a bridge between the content and the knowledge node:

	Method: POST
	URL: HOST_URL/instances/{instance_id}/knowledge_node_contents

And you will receive the following message depending on what you actually sent to the API:

	{
		"id": 3,
		"knowledge_node_id": "5"
		"content_id": "2"
		"importance_degree": "1" (Optional)
	}


### Students and subscriptions
#### Students
A Student is the object on Domoscio's API that represents a user who is learning something on your platform. This object is obviously central and necessary for the application to do the proper computations. 
Creating a Student is as simple as requesting a POST method on the Student Index URL:

	Method: POST
	URL: HOST_URL/instances/{instance_id}/students

You should be receiving the following answer depending on what you actually sent to the API:

	{
		"id": 48,
		"uid": "my_first_student",
		"civil_profile_attributes": {
			"name": "John Doe",  (Optional)
			"sexe": "male",  (Optional)
			"day_of_birth": "1970/01/01"  (Optional)
		},
		"student_group_id": "1" (Optional)
	}
	
Once you created your first user, you can start focusing on creating an KnowledgeNodeStudent!

#### Links between a User and a piece of knowledge (KnowledgeNode)
All user activity related to a KnowledgeNode is mastered by the KnowledgeNodeStudent.

![User Enrollment](https://raw.githubusercontent.com/Celumproject/domoscio-docs/master/uploads/user_enrollment.jpg)

*	Unique: Can be considered as a student subscription to a piece of Knowledge
*	Smart: Carry all user data : results, analysis, computations…

Creating a KnowledgeNodeStudent is, as usual, done through this example of request:

	 Method: POST
	 URL: HOST_URL/instances/{instance_id}/knowledge_node_students

The response you will be receiving will look like:

	{
		"id": 547,
		"knowledge_node_id": 45,
		"student_id": 12,
		"uid": "kns1" (Optional)
	}

Once you created your first KnowledgeNodeStudent object, you are ready to start declaring an Event and going further.

### Events and users interactions with your platform

Every user activity can trigger the creation of an Event object. The most basic one is an Event generated by the correct or wrong answer to a question. To specify what kind of Event you want to declare, the API uses a "type" attribute. In the Reviewing case, the type would be **EventReview**. Sending such an Event will trigger the API to store and process it in order to deliver its consolidation functionalities.

![User Event](https://raw.githubusercontent.com/Celumproject/domoscio-docs/master/uploads/user_event.jpg)

Events are linked to a Content object. Hence, to declare a new Event to the API you might just want to do:

	 Method: POST
	 URL: HOST_URL/instances/{instance_id}/events

	 {
	 	"content": 65,
	 	"type": "EventReview",
		"standard": nil, (Can be "xAPI")
	 	"payload": "100" (100 meaning success, and 0 failure)
	 }


Here are the easiest steps to interact, declare and create objects in Domoscio's API. Next, we will go through what you can expect and receive from this API.


## Reviews engine
In order to provide to your user an automated, personnalized and optimized revision plan you can request from Domoscio's API, all the reviews for a specific student. To do this you need to use the "Utils" class.

For instance:

	 Method: GET
	 URL: HOST_URL/instances/{instance_id}/review_utils/fetch_reviews/?student_id={student_id}&pending=true

The response is an array of all the KnowledgeNodes that are scheduled to be reviewed today (and the days before if the reviewing has not been done). Each entry of this array contains:

*	the IDs and UIDs of the corresponding KnowledgeNodeStudent
*	the next due dates for the revisions
*	the IDs and UIDs of the corresponding KnowledgeNode

The number of elements in the json Array is equivalent to the number of questions that your current user has to answer to proceed with the reviewing process.

_Note:_ You can request all the forecasted revisions by not sending the **pending** parameter.

