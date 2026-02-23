---
tags:
  - 12FactorApp
  - microservices
author:
  - jacgit18
  - chatgpt
Comments: Maybe expand and create a mindmap.
Purpose: This documentation discusses microservices in the context of 12 factor app briefly.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish: false
---
## **Codebase**  
- Single codebase per microservice  
- Maintainable, version-controlled code 

## **Dependencies**  
- Isolate dependencies within each microservice  
- Explicitly declare and manage dependencies  

## **Config**  
- Store configuration in environment variables  
- Centralized and dynamic configuration management 

## **Backing Services**  
- Treat databases, queues, etc., as attached resources  
- Isolate communication with backing services  

##  **Build, Release, Run**  
- Separation of building, releasing, and running  
- Immutable and versioned deployments  

## **Processes**  
- Execute the application as stateless processes  
- Scalable and resilient microservices  

## **Port Binding**  
- Export services via a port  
- Stateless services, easily load-balanced  

## **Concurrency**  
- Scale out via the process model  
- Handle concurrency within microservices  

## **Disposability**  
- Fast startup and graceful shutdown  
- Robust microservices that can be restarted or scaled  

## **Dev/Prod Parity**  
- Keep development and production environments similar  
- Minimize inconsistencies between environments  

## **Logs**  
- Treat logs as event streams  
- Centralized logging and monitoring  

## **Admin Processes**  
- Run admin/management tasks as one-off processes  
- Simplify maintenance and tasks like database migrations