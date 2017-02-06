This document will walk you through the main steps to integrate the "Adaptive Learning Solution" into your platform.

# What do you need?
In order to proceed, you have to make sure that you have the following requirements:
*	A working e-learning or LMS platform
*	Credentials to connect to Domoscio's adaptive learning engine API
*	An HTTP requester to try out your request before implementing them

Before starting, you can check if a SDK already exists to connect to the API for your programming language. 
For instance, if you are lucky enough that you're platform is coded with Ruby, we can use the [SDK](https://github.com/Celumproject/domoscio_rails) that we developped to connect the API to our White Label solution. Otherwise you can always refer to this library to get inspired!

## Get your credentials anc connect to the API

Request your API credentiels and you will receive:
1. An instance_id
2. An api_key

With these two elements you can start communicating with the API and requesting some information. The way to do this is to get your favorite HTTP requester and to ping a URL that we will build the following way:

![URL Creation](https://raw.githubusercontent.com/Celumproject/domoscio-docs/master/uploads/creation_url.png)

# Integrating the API into your platform

## What you need to send to the API
### Contents structure and meta-data 
### Users, and subscriptions
### Events and users interactions with your platform

## What you can receive from the API
### Recommendations engine
### Reviews engine
### Api engine

