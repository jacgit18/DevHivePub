---
tags:
  - techDebt
  - frontend
  - backend
  - API
  - business
  - HTTP
author: 
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 2024-03-27
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
The difference between client-side and server-side rate limiting lies in where the rate limiting enforcement occurs and which entity (client or server) is responsible for managing the rate limits.  

[[System Design Interview An Insider’s Guide Volume 1.pdf#page=52&selection=6,0,57,6|System Design Interview An Insider’s Guide, page 52]]
  
1. **Client-Side Rate Limiter**:  
- **Enforcement**: Rate limiting is enforced on the client side, typically within the client application or client library.  
- **Responsibility**: The client is responsible for tracking and managing its own rate limits, usually based on the responses received from the server.  
- **Purpose**: Client-side rate limiting helps prevent the client application from overwhelming the server with excessive requests. It ensures that the client operates within the allowed rate limits specified by the server.  
  
2. **Server-Side Rate Limiter**:  
- **Enforcement**: Rate limiting is enforced on the server side, usually within the server infrastructure or API gateway.  
- **Responsibility**: The server or API gateway is responsible for monitoring incoming requests and applying rate limits based on various criteria, such as client identity, IP address, or API endpoint.  
- **Purpose**: Server-side rate limiting protects the server or API from being overloaded by excessive requests from multiple clients. It helps maintain service availability, prevent abuse, and ensure fair resource allocation among clients.  
  
3. **Server-Side API Rate Limiter**:  
- **Specificity**: This refers to rate limiting specifically applied to API endpoints on the server side.  
- **Purpose**: Server-side API rate limiting focuses on controlling the rate of API requests made to server endpoints. It allows API providers to manage API usage, prevent abuse, and maintain quality of service for all API consumers.  
- **Granularity**: API rate limiting can be applied at different levels of granularity, such as global rate limits for all endpoints, per-user rate limits, or per-endpoint rate limits.  


  
In summary, client-side rate limiting is implemented and managed by the client application, while server-side rate limiting is implemented and enforced by the server or API gateway to manage incoming requests. Server-side API rate limiting specifically targets API endpoints to control API usage and ensure optimal performance and reliability.