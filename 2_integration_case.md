This document will walk you through the main steps to integrate the "Adaptive Learning Solution" into your platform.

# What do you need?
In order to proceed, you have to make sure that you have the following requirements:

*	A working e-learning or LMS platform
*	Credentials to connect to Domoscio's adaptive learning engine API
*	An HTTP requester to try out your request before implementing them
*	Basic knowledge of how to construct a HTTP request and what are 

Before starting, you can check if a SDK already exists to connect to the API for your programming language. 
For instance, if you are lucky enough that you're platform is coded with Ruby, we can use the [SDK](https://github.com/Celumproject/domoscio_rails) that we developped to connect the API to our White Label solution. Otherwise you can always refer to this library to get inspired!

## Get your credentials anc connect to the API

Request your API credentiels and you will receive:

1. An instance_id
2. An api_key

With these two elements you can start communicating with the API and requesting some information. The way to do this is to get your favorite HTTP requester and to ping a URL that we will build the following way:

![URL Creation](https://raw.githubusercontent.com/Celumproject/domoscio-docs/master/uploads/creation_url.png)

# Integrating the API into your platform

Let us start actually work on the integration of the API into your platform. In order to fully describe the process we will highlight two parts: information that you will need to provide to the API and information that you might be receiving from the API.


## Information you need to send to the API

In this part, we focus on what your application should declare to the API in order to be able to make its computation and deliver its adaptive learning functionnalities. For the main part of this section, the method that you will be using is:

	HTTP Method: POST 

If everything goes well with your request, you shall receive a:

	OK RESPONSE 200

or simply a json object describing the newly created object:

	{name: "Mathematics", uid: "mat0036grde", created_at: [Now]}

Amongst all the types of information you should send to the API, the following three are mandatory. In some cases, the "Contents structure and meta-data" can be imported directly into the API. If that is your case or if you are willing to do so, please contact us directly.
### Contents structure and meta-data 
All user activity related to content is mastered by KnowledgeNodeStudent. They operate also as a permission controller between a Student and a Content. Their existence mean that a Student is entitled to access this piece of Content.

![User Enrollment](https://raw.githubusercontent.com/Celumproject/domoscio-docs/master/uploads/user_enrollment_.png)

*	Unique : Can be considered as a student subscription to a notion
*	Smart: Carry all user data : results, analysis, computations…
*	Simple: Use this object to record all student results

### Users, and subscriptions

### Events and users interactions with your platform

## What you can receive from the API
### Recommendations engine
### Reviews engine
### Api engine

