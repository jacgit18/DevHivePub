---
tags: 
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[API Architectural Styles.gif]]

#todo/High/Dev 
- [ ] find notes related and condense and remove repetitiveness in vault  
- [ ] look into OpenAPI (Swagger) - API specification
- [ ] Review [#systemdesign #coding #interviewtips \| Alex Xu \| 82 comments](https://www.linkedin.com/posts/alexxubyte_systemdesign-coding-interviewtips-activity-7308876372804796416-2g8g/?utm_source=share&utm_medium=member_android&rcm=ACoAAB5RM-sBDcWQxGls-I2ibiN5J52xIwkopmg)
### Advanced communication technologies 
  
1. **gRPC:** gRPC is a high-performance, open-source RPC (Remote Procedure Call) framework developed by Google. It uses HTTP/2 for transport and Protocol Buffers (protobuf) for serialization, providing features such as bidirectional streaming, strong typing, and efficient binary serialization.  
  
2. **SOAP (Simple Object Access Protocol):** SOAP is a protocol for exchanging structured information in the implementation of web services. It typically uses XML for message formatting and can be transported over various protocols such as HTTP, SMTP, or TCP.  
  
3. **REST (Representational State Transfer):** REST is an architectural style for designing networked applications, often used in the context of web services. It relies on standard HTTP methods (GET, POST, PUT, DELETE) for communication and operates over HTTP or HTTPS. 

4. **Webhooks:** Webhooks are a mechanism for automatically sending real-time notifications or events from one application to another. They utilize HTTP(S) to deliver event payloads to predefined URLs, enabling integrations between different systems.  
  
5. **GraphQL:** GraphQL is a query language and runtime for APIs, developed by Facebook. It provides a more efficient and flexible alternative to RESTful APIs by allowing clients to specify exactly what data they need from the server. GraphQL typically operates over HTTP or HTTPS.  


## Communication Protocol
1. **WebSocket:** WebSocket is a protocol that provides full-duplex communication channels over a single TCP connection, allowing for real-time, bidirectional communication between client and server. It's commonly used for applications requiring low-latency communication, such as chat applications or online gaming.  


While all these technologies can leverage web protocols like HTTP, HTTPS, TCP, and UDP, they offer different communication paradigms, data formats, and capabilities to suit various application requirements. Understanding the strengths and use cases of each technology can help developers choose the most appropriate solution for their projects.