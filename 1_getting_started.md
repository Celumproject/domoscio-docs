# Use our REST Api

We designed the Domoscio API in a **Restful way**, so that your user experience is simple and straightforward. You are able to :

*	Submit data requires an **HTTP POST** request
*	Retrieve data requires an **HTTP GET** request
*	Change data requires an **HTTP PUT** request


Requests must be sent using content-type "application/json". The request and response body encoding is UTF-8.
<br/><br/>

# Create a Sanbox account

To get your credentials, you can either refer to the document explaining **How to create a sandbox account** on Domoscio's API or ask us to create them.

Now that you've got your authentication keys, let us see how to properly authenticate your application to our API.
<br/><br/>

# Authenticate your app

We provide two ways to authenticate and communicate with the service

*	**Basic Access Authentication**
*	**LTI/OAuth protocol**

## With URL parameters

You can pass your authentication key as a token in the URL to authenticate your appliance:

	http://adaptive-engine.domoscio.com/v2/instances/{your instance id}/users?token={you key}

## With authorization header

For your applications developed with Ruby On Rails, we provide a gem which highly ease authentication process. In this case we use standard basic access authentication.
The header is constructed as follows:

	'Authorization' => "Token token=#{DomoscioRails.configuration.client_passphrase}"

