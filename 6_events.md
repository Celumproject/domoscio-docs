# Events
Once all the management layers and knowledge’s structure are declared, you can start registering all your student’s data and retrieve their statistics on our API. Hence, you can declare Event objects and manage them. For instance, if you need to store results, you can declare an Event object with a EventResult type. <br/><br/>
The only constraint for the consolidation feature is that you must register your Event as EventResult type and the payload should be either “0” or “100”. For the adaptive learning functionality, the more types we have and the more precise is the payload, the more accurate we are doing recommendations. <br/><br/>
<img src="https://raw.githubusercontent.com/Celumproject/domoscio-docs/master/uploads/events_example.jpg"/>

## Parameters

| Param | Type | Description |
|---|---|---|
| student_id | Integer | Student indentifier |
| content_id (or content_uid) | Integer (or string) | The content identifier related to the event |
| type | String | The format the payload is stored. Ex: "xAPI" (Optional) |
| payload | String | Element associated to the event, a result for instance. xApi format is recommended |
| return_recommendation | Boolean | If true, API compute new user recommendations. |

## Create Event (POST)

    Method: POST
    URL: HOST_URL/instances/{instance_id}/events
  
Here are the required parameters :

    {
        "student_id": 1, 
        "content_id": 2,
        "type": "EventResult",
        "standard": "score",
        "payload": "100",
        "return_recommendation": true
    }
  
In this case, you are posting a event involving student n° 1, having a result to an assessment on content n° 2, with a simple result at 100, and you are waiting for the API to compute some recommendations after event save.
