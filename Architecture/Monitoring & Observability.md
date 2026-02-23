---
tags:
  - monitoring
  - traceability
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses Monitoring & Observability
Status: Done
Started: 
EditDate: 2024-03-07
Relates: "[[Distributed Tracking & Monitoring]]"
Peer Reviewed: 0
dg-publish:
---
![[logging metrics.gif]]

## Monitoring
  - **Purpose:** Monitoring focuses on tracking the health and performance of a system, utilizing metrics, logs, and alerts to identify issues proactively.
  - **Components:** Monitoring tools generate alerts based on predefined thresholds, using metrics and logs to assess the system's overall health.

## Observability
  - **Purpose:** Observability goes beyond monitoring by providing deep insights into the internal states and behaviors of a system also tends to be used along with [[Chaos Engineering]] in order to identify weakness in the overall system by injecting controlled failures and disrupption into a system.
  - **Components:** Observability relies on instrumentation, including logging and tracing, to gather detailed insights. Metrics contribute numerical data for a comprehensive understanding of system behavior.


## Logging
  - **Definition:** Logging involves recording information about the application's runtime behavior. Logs are typically used for debugging, monitoring, and auditing, providing insights into errors, warnings, and informational messages.
  - **Role in Monitoring and Observability:** Logs play a crucial role in both monitoring and observability by capturing events and messages that help developers and operators understand the state and behavior of a system.

## Tracing
  - **Definition:** Tracing involves tracking the flow of requests as they move through a system. It helps identify performance bottlenecks and understand the interactions between different components, especially in distributed systems.
  - **Role in Monitoring and Observability:** Tracing complements monitoring and observability efforts by providing a detailed view of request journeys across multiple services, aiding in the diagnosis of issues and optimization of system performance.

## Metrics
  - **Definition:** Metrics involve quantifiable measurements of system behavior, providing a numerical representation of specific aspects like response times, error rates, or resource usage. this info is pulled from Logging and Tracing.
  - **Role in Monitoring and Observability:** Metrics are fundamental to both monitoring and observability, offering numerical data for performance analysis. They contribute to tracking the health of a system over time and help in identifying trends and anomalies.


## In summary
- Logging captures events and messages for debugging and monitoring.
- Tracing follows the flow of requests, aiding in performance optimization, especially in distributed systems.
- Metrics provide quantifiable measurements crucial for monitoring and observability, offering a numerical representation of system behavior over time. Together, these elements contribute to building a robust and well-understood software system.