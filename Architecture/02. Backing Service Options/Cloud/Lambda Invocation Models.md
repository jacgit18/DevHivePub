---
tags:
  - cloud
  - security
  - bestPractices
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
AWS Lambda supports different **Invocation Models** for running functions, depending on how the function is triggered and how it handles responses. The three main invocation models are:

---

### **1. Synchronous Invocation**

The caller **waits** for the function to complete and receives the response.

- **Use Case:** API requests, interactive applications, or real-time processing.
- **Examples:**
    - Amazon API Gateway invoking a Lambda function to return HTTP responses.
    - AWS SDK calling Lambda and waiting for a result.
- **Error Handling:** Errors are returned directly to the caller. The caller decides whether to retry.

The following AWS services invoke Lambda synchronously:

- Amazon API Gateway
- Amazon Cognito
- AWS CloudFormation
- Amazon Alexa
- Amazon Lex
- Amazon CloudFront


**Execution Flow:**

1. Caller triggers Lambda.
2. Lambda executes the function.
3. The function returns a response to the caller.

---

### **2. Asynchronous Invocation**

The caller **does not wait** for the function to complete. The request is queued, and Lambda executes it **later**.

- **Use Case:** Event-driven processing where an immediate response isn't needed.
- **Examples:**
    - S3 triggering Lambda when an object is uploaded.
    - EventBridge triggering Lambda on a scheduled event.
- **Error Handling:** Lambda automatically retries the function twice (total of three attempts). Unsuccessful executions can be sent to a **dead-letter queue (DLQ)** or **failure destination** for debugging.

The following AWS services invoke Lambda asynchronously: 

- Amazon SNS 
- Amazon S3
- Amazon EventBridge

**Execution Flow:**

4. Caller triggers Lambda.
5. Lambda **queues** the event.
6. Lambda processes the event **asynchronously**.

---

### **3. Event Source Mapping (Poll-Based Invocation)**

Lambda **polls a data stream or queue** and processes events automatically.

- **Use Case:** Continuous event processing from queues or streams.
- **Examples:**
    - Lambda reading messages from an **SQS queue**.
    - Lambda processing records from **Kinesis** or **DynamoDB Streams**.
- **Error Handling:**
    - For SQS, messages are returned to the queue after retry attempts.
    - For Kinesis/DynamoDB, errors cause retries for up to 24 hours before skipping records.

The configuration of services as event triggers is known as event source mapping. This process occurs when you configure event sources to launch your Lambda functions and then grant theses sources IAM permissions to access the Lambda function. 

  

Lambda reads events from the following services:

- Amazon DynamoDB
- Amazon Kinesis
- Amazon MQ
- Amazon Managed Streaming for Apache Kafka (MSK)
- self-managed Apache Kafka
- Amazon SQS


**Execution Flow:**

7. Lambda automatically polls the source.
8. Lambda retrieves and batches events.
9. The function processes each batch.

---

### **Comparison Summary**

|Invocation Model|Caller Waits?|Retried Automatically?|Example Use Case|
|---|---|---|---|
|**Synchronous**|Yes|No|API responses, interactive apps|
|**Asynchronous**|No|Yes (2 retries)|S3 events, SNS triggers|
|**Event Source Mapping**|No (Auto-Triggered)|Depends on source|SQS, Kinesis, DynamoDB|


