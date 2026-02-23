---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
relates aws

### **Choosing between RESTful APIs and WebSocket APIs**

Using API Gateway, you can build and deploy both RESTful APIs and WebSocket APIs. Now that you have an introduction to these API types, this table compares a few features of each to help you choose the right API type.

|                                                                                                 |                                                                                   |                                                                                                                                       |
| ----------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **REST API**                                                                                    | **HTTP API**                                                                      | **WebSocket API**                                                                                                                     |
| All-inclusive set of features needed to build, manage, and publish APIs at a single price point | Building modern APIs that are equipped with native OIDC and OAuth 2 authorization | Bidirectional communication that lets clients and services independently send messages to each other                                  |
| Building APIs that use certificates for backend authentication, AWS WAF, or resource policies   | Building proxy APIs for Lambda or any HTTP endpoint                               | Richer client-to-service interactions because services can push data to clients without requiring clients to make an explicit request |
| Workloads that need an edge-optimized or private API type                                       | APIs for latency-sensitive workloads                                              | APIs for real-time communication                                                                                                      |



WebSocket APIs offer APIs that the client can access through the WebSocket protocol. Unlike REST and HTTP APIs, WebSocket APIs allow bidirectional communications. WebSocket APIs are often used in real-time applications such as chat applications, collaboration platforms, multiplayer games, and financial trading platforms.

  

WebSocket APIs maintain a persistent connection between connected clients to facilitate real-time message communication. With WebSocket APIs in API Gateway, you can define backend integrations with Lambda functions, Amazon Kinesis, or any HTTP endpoint to be invoked when messages are received from the connected clients.

![WebSocket API Gateway architecture showing how API Gateway can be used with Amazon Elastic Container Service using WebSocket APIs.](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1738958400/MmlZiMpAQnh0b8bS7TQZYg/tincan/914789_1645026071_p1fs1j2ru4ua0g4910qldke14j14_zip/assets/websocket-api-integration-with-ecs.png)


### **Benefits and use cases of WebSocket APIs**

API Gateway WebSocket APIs are designed for bidirectional communication between your client and backend architecture. You can do this by using any WebSockets client such as a mobile app, chat app, AWS IOT device, or application dashboard. 

When you connect the client to API Gateway, API Gateway will manage the persistence and state needed to connect it to your clients. Unlike a REST API, which receives and responds to requests, a WebSocket API supports two-way communication between your client applications and your backend.

WebSocket APIs are often used in real-time application use cases such as:

- Chat applications
    
- Streaming dashboards
    
- Real-time alerts and notifications
    
- Collaboration platforms

-  Multiplayer games
    
- Financial trading platforms
    

By using WebSockets with API Gateway, your clients can send messages to a service and the services can independently send messages back to the clients. This bidirectional behavior creates more valuable interactions between your clients and services because the services can push data to clients without requiring clients to make an explicit request.


## **Developing a WebSocket API in API Gateway**

As you're developing your WebSocket API in API Gateway, there are a number of characteristics you need to choose for your API. These characteristics depend on your API's use case.

For example, you might want to only allow certain clients to call your API, or you might want it to be available to everyone. In addition, you might want an API call to invoke a Lambda function, make a database query, or call an application. All of these options will change the characteristics of the API as you design and deploy it.


## **API Gateway optional cache**

You can turn on API caching in API Gateway to cache your endpoint's responses. With caching, you can reduce the number of calls made to your endpoint and also improve the latency of requests to your API.

This is an optional configuration only available for REST APIs, but definitely an option that you want to consider based on your use cases. To learn about API Gateway caching, expand each of the following three categories.


## Why use API Gateway caching

When caching is turned on, API Gateway caches responses from your endpoint for a specified Time-to-Live (TTL) period. API Gateway then responds to a request by looking up the endpoint response from the cache instead of making a request to your endpoint. There are two big benefits of using the cache:

1. It reduces overall latency for serving requests.
2. It minimizes the number of requests that need to be made to your backend.

This becomes even more valuable as you scale and want to reduce the amount of calls to your backend resources.


## **API stages**

When you are ready to make your API callable for your users, you need to deploy your API to a stage.

- A stage is a snapshot of the API and represents a unique identifier for a version of a deployed API.
    
      
    
    With stages, you can have multiple versions and roll back versions. Anytime you update anything about the API, you need to redeploy it to an existing stage or to a new stage that you create as part of the deploy action.
    
    ![The API Gateway URL with the word stage in the URL highlighted.](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1738958400/MmlZiMpAQnh0b8bS7TQZYg/tincan/914789_1645026071_p1fs1j2ru4ua0g4910qldke14j14_zip/assets/Deployed%20to%20Stage_1.png)