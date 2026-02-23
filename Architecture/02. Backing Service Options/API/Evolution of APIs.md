---
tags:
  - API
  - REST
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses different types of APIs.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: 
Peer Reviewed: 0
dg-publish: true
---
APIs are a set of protocols that define how system components interact with each other. As architectural styles evolve, APIs have gained prominence in recent years. The diagram below shows how the rise of microservices and cloud-native applications brings further granularity to services. In-process calls in monolithic applications transition to inter-process calls in microservice and serverless applications. Additionally, each process might reside on a different physical server, and service calls can fail due to various network issues.

Increased service complexity emphasizes the need for more disciplined API designs.
![[mono to Servless .png]]

## Type of APIs
1. **Data APIs (RESTful APIs):**  
	- These APIs primarily deal with data retrieval or manipulation. They are designed to expose data, often in a structured format such as JSON or XML.  
	- Examples include APIs that retrieve information from a database, weather data, user profiles, or any other form of data that can be queried or manipulated.  
  
2. **Service APIs (Functional APIs):**  
	- These APIs provide specific functions or services that can be utilized by applications or systems.  
	- Examples include APIs that facilitate sending emails (e.g., SendGrid for email services), processing payments, translating text, image recognition, or any other service-oriented functionality.  
  
3. **RESTful APIs:**  
	- RESTful APIs (Representational State Transfer) are a common type of data API that follows principles such as statelessness, client-server architecture, and resource-based endpoints.  
	- RESTful APIs are often used for data-related operations, providing a standard approach for accessing and manipulating resources.  
  
4. **RPC APIs (Remote Procedure Call):**  
	- RPC APIs are a form of service API where the focus is on invoking procedures or functions remotely.  
	- Examples include APIs that expose specific functionalities or services for remote invocation, allowing developers to call functions on a remote server.  
  
In the case of SendGrid, it falls into the category of a service API. SendGrid provides a set of functions or services related to email, allowing developers to integrate email sending functionality into their applications.  
  
It's worth noting that these distinctions can sometimes blur, as APIs may offer both data-related operations and specific functions or services. The choice of terminology often depends on the primary purpose or focus of the API.

## API First
Over the past decade, “API First” has emerged as a popular software development model. It prioritizes API design before system design. Various functional teams and systems use APIs as a shared communication language. For example, frontend developers, backend developers, and QA teams work together to design APIs based on system requirements. These APIs serve as specifications for business requirements and system designs. Each team then works independently, and they reconvene during the dev testing phase. 

The diagram below compares the “Code First” and “API First” approaches. In the “Code First” model, APIs are byproducts of system designs, often referred to as “documentation”. The "API First" model begins with API specifications and concludes with API-driven tests, making APIs the driving force behind the entire software development cycle.

![[Api first.png]]
"API First" offers several advantages:

1. Improved system integration. “API First” encourages developers to carefully consider system interactions from the project’s outset, reducing the need for ongoing modifications during development.

2. Enhanced collaboration and quality. APIs serve as a shared specification within the organization, allowing developers, testers, and DevOps to work independently. Agreeing on APIs at the project’s beginning helps eliminate uncertainties and boost software quality. 

3. Increased scalability. With defined interfaces for each service, scaling becomes more manageable by spinning up new instances and adjusting load balancer settings.


In addition to efficiency and transparency, the API-first design also fosters network effects. 