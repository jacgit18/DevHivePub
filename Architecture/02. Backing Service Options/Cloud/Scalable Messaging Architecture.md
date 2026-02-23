---
tags:
  - eventDriven
  - cloud
  - distributedSystem
  - systemDesign
  - components
  - scalability
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: Refinement
Started: 2024-03-30
EditDate: 
Relates: "[[Messaging systems]]"
Peer Reviewed: 0
dg-publish:
---
Amazon Simple Notification Service (SNS) is a messaging service that follows a publish/subscribe (pub/sub) model, allowing you to send notifications to a large number of subscribers simultaneously. It seamlessly integrates with multiple AWS services and supports end-user notifications across SMS, email, and push notifications.

By connecting actions to SNS topics, you can trigger a series of events and workflows. For example, when a user signs up, you can publish a message to an SNS topic, which then routes the message to various subscribers, such as analytics and fulfillment services.

Amazon Simple Queue Service (SQS) complements SNS by providing a reliable messaging queue service. Messages sent to SQS queues can be processed asynchronously, allowing for decoupling of components and fault tolerance.

### Example Use Case:
Consider a user order service that utilizes both SNS and SQS:

1. **User Order Service**: When a user places an order, the user order service publishes a message to an SNS topic.

2. **SNS Topic**: The SNS topic routes the message to multiple subscribers, including:
   - **Analytics Queue**: Receives messages for further analytics processing.
   - **Fulfillment Queue**: Receives messages for order fulfillment processing.

3. **SQS Queues**:
   - **Analytics Queue**: Processes messages for analytics ingestion. If an analytics ingestion service (e.g., Lambda function) goes down, messages are stored in the queue, ensuring fault tolerance and data durability.
   - **Fulfillment Queue**: Processes messages for order fulfillment. Messages are processed asynchronously, allowing for scalability and decoupling of components.

By utilizing SNS and SQS in combination, you can design fault-tolerant and scalable messaging architectures. SNS provides the capability to publish messages to multiple subscribers, while SQS ensures reliable message processing and decoupling of components, ultimately enhancing the resilience and efficiency of your system.