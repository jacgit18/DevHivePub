---
tags:
  - microservices
  - data
  - databases
  - schema
  - scalability
  - security
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses decentralized data management architecture.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: "[[Microservices VS Monolithic Architecture |Microservices]]"
Peer Reviewed: 0
dg-publish: true
---
![[Decentralized Data.png]]
As per Decentralized Data Management principle, each Microservice should manage its own data, without relying on other Microservice, to ensure scalability and reliability. For example, each Microservice could have its own database that it uses to store data.

Sharing Database with other Microservices violate this principle and should be avoided as it will make it difficult to troubleshoot and can result in data inconsistency.

This design principle will help you better manage your database its also a basis of Database per Microservice design pattern, an essential Microservice Design Principle.

If you are thinking about how could then another Microservice get access to the same data as its very much possible that another service do need it? Well, you should always create APIs for that as we going to see in next Microservice design principle.

You can see this in following Microservice architecture we have different database for `UserService`, `MessageService` and `FriendService`.


## Security 
- [Data security](https://www.integrate.io/the-complete-guide-to-data-security/) starts with a good database schema design. Use encryption for sensitive data such as personally identifiable information (PII) and passwords. Don’t give administrator roles to each user; instead, request user authentication for database access.  
