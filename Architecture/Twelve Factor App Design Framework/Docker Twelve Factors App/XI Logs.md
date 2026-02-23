---
tags:
  - methodology
  - Docker
  - 12FactorApp
  - monitoring
  - performance
author:
  - jacgit18
  - chatgpt
Purpose: This documentation Twelve Factor App, factor eleven in the context of Docker.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 1
dg-publish:
---
Logs: The app should generate logs as event streams for monitoring and troubleshooting, providing insight into its behavior. The app should only log to STDOUT or STDERR streams so standard container tools can forward them into a centralized logging system, which is required to monitor and troubleshoot your app.

### Relationship between Disposability and Logging:
The relationship between the disposability factor and the logging factor lies in their combined effect on managing and understanding application behavior:

- **Graceful Shutdown and Recovery:** When an application is designed to be disposable (i.e., it can be stopped and started quickly without adverse effects), proper logging becomes crucial. During shutdown and startup processes, detailed logging helps track the state of the application, identify potential issues, and ensure that it recovers properly after restarting.
    
- **Diagnosing Disposability Issues:** In a disposable architecture, the ability to quickly diagnose issues during startup or shutdown is important. Detailed and structured logs provide insights into why a component might be failing to start or shut down gracefully. This can include information about dependencies, resource availability, and configuration issues.
    
- **Monitoring and Scalability:** Both disposability and logging are important for managing scalability. A stateless, disposable architecture is better suited for horizontal scaling, where new instances can be quickly spun up. Proper logging helps monitor the behavior of these instances, enabling operators to assess performance, identify bottlenecks, and make informed decisions about scaling.
    
- **Debugging and Troubleshooting:** In a disposable environment, applications can be brought up, tested, and taken down frequently. This increases the importance of effective logging for debugging and troubleshooting. Detailed logs provide insights into application behavior, allowing developers to understand issues and identify potential improvements.

![[Twelve Factor App Logs]]