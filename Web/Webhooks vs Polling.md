---
tags:
  - comparison
  - web
  - HTTP
  - protocol
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Webhooks vs Polling.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish: true
---
![[Polling vs Webhooks.png]]

### Polling vs. Webhooks: Models of Communication

**1. **Polling: Pull Model of Communication:**

   - **Definition:** Polling is a communication model where a system actively retrieves information by periodically making requests to another system.

   - **How It Works:**
     - A client initiates requests at regular intervals, asking the server if there is new information available.
     - The client constantly checks for updates, regardless of whether there are changes or not.

   - **Characteristics:**
     - **Client-Initiated:** The client is responsible for making requests to the server.
     - **Regular Intervals:** Requests are made at predetermined intervals, often leading to potential delays in receiving real-time information.
     - **Resource Intensive:** Frequent requests may result in increased server and network load.

**2. Webhooks: Push Model of Communication:**

   - **Definition:** Webhooks represent a communication model where information is pushed from a source application to a destination application in real-time.

   - **How It Works:**
     - The destination application registers a URL with the source application to receive notifications.
     - When an event occurs, the source application sends a direct HTTP POST request to the registered URL with relevant information.

   - **Characteristics:**
     - **Server-Initiated:** The server actively sends updates when events occur, eliminating the need for constant client requests.
     - **Real-Time:** Information is delivered instantly when changes happen, leading to faster responsiveness.
     - **Efficient Resource Usage:** Webhooks are generally more resource-efficient as they only transmit data when there are updates.

**Key Differences:**

1. **Initiator of Requests:**
   - **Polling:** Requests are initiated by the client.
   - **Webhooks:** Requests are initiated by the server.

2. **Timing of Information Retrieval:**
   - **Polling:** Information retrieval occurs at scheduled intervals, leading to potential delays.
   - **Webhooks:** Information is delivered in real-time when events occur.

3. **Resource Usage:**
   - **Polling:** May be resource-intensive due to frequent client requests.
   - **Webhooks:** Typically more resource-efficient as updates are only sent when necessary.

**Conclusion:**

   - The choice between polling and webhooks depends on factors such as real-time requirements, system efficiency, and the nature of the application. Polling suits scenarios where periodic updates are sufficient, while webhooks excel in situations demanding instant, event-driven communication, reducing latency and resource usage.