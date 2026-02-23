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
# Running AWS Services Asynchronously vs. Synchronously in Serverless Architectures

When designing serverless applications on AWS, asynchronous and synchronous architectures play a key role in how services communicate and process workloads. Understanding their differences is crucial for building scalable, efficient applications.

---

## Synchronous Execution

Synchronous processing means a service waits for a response before moving forward. The caller blocks execution until it gets a result.

### Example of Synchronous Execution

Imagine a user submits a request to generate a PDF report via an API Gateway that triggers an AWS Lambda function.

1. The API Gateway invokes the Lambda function.
2. The Lambda function processes the request and returns the PDF in the response.
3. The user waits for the request to complete before moving on.

### Services Commonly Used in Synchronous Workflows

- **API Gateway → Lambda** (Immediate response to client)
- **AWS Step Functions (synchronous mode)** (Orchestrating multiple AWS services that must return results sequentially)
- **DynamoDB Queries** (Reading data in real time)
- **Amazon RDS (Relational Databases)** (Fetching and processing structured data in real time)

### Limitations of Synchronous Execution

- **Higher Latency** – The system must wait for a response before proceeding.
- **Limited Scalability** – If the processing takes too long, API Gateway or the client may time out.
- **Error Handling is Immediate** – If one step fails, the entire request may fail.

---

## Asynchronous Execution

Asynchronous processing means the caller does not wait for a response. Instead, the request is placed in a queue or event system, and the process completes in the background.

### Example of Asynchronous Execution

Consider an image-processing system where users upload images to S3, and an AWS Lambda function resizes them asynchronously.

4. The user uploads an image to an S3 bucket.
5. S3 triggers a Lambda function via S3 Event Notifications.
6. Lambda processes the image and saves the resized version back to S3.
7. The user doesn't wait for the process to complete; they get notified later (e.g., via an SNS notification or a database update).

### Services Commonly Used in Asynchronous Workflows

- **S3 Event Triggers → Lambda** (File processing, logging)
- **Amazon SNS & SQS** (Message-based decoupling)
- **EventBridge** (Event-driven workflows)
- **Step Functions (asynchronous mode)** (Long-running workflows, complex state management)
- **DynamoDB Streams** (Triggering processing from database updates)

### Advantages of Asynchronous Execution

- **Better Scalability** – The system can handle many requests simultaneously.
- **Reduced Latency for Users** – The user doesn't have to wait for processing to finish.
- **Resilient to Failures** – If an event fails, it can be retried or handled separately.

### Limitations of Asynchronous Execution

- **No Immediate Feedback** – If a user needs confirmation, they must check the status later.
- **Complex Error Handling** – Since tasks run in the background, failures must be logged and retried explicitly.
- **Potential for Out-of-Order Processing** – Events may not be processed in the order they were sent unless explicitly handled (e.g., FIFO SQS).

---

## Choosing the Right Approach

- **Use synchronous execution** when users need an immediate response (e.g., real-time API calls).
- **Use asynchronous execution** for background tasks that don’t require immediate feedback (e.g., event processing, batch jobs).
- **Combine both when needed.** Example: A synchronous API call triggers an asynchronous background process and then provides a status update later.

### Hybrid Example: Synchronous + Asynchronous

A web app that generates video transcripts:

8. The user uploads a video (**API Gateway → Lambda → S3**).
9. The system starts an asynchronous transcription job (**Lambda → S3 → Transcribe → SNS**).
10. Once completed, an SNS notification is sent, and the user is notified via email or an updated API call.

This balances user experience (fast response) with scalability (asynchronous processing).

