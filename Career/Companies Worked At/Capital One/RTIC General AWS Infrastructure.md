---
tags:
  - career
  - employment
  - CapitalOne
  - favorite
  - RTIC
  - cloud
  - AWS
author:
  - jacgit18
Purpose: This documentation discusses work done at current company.
Status: Perpetual
Started: 2023-12-14
EditDate:
Relates: "[[PTP Config Workflow]]"
dg-publish:
---
Your understanding of how AWS Lambda works is on the right track, but there’s more to it when integrating with other AWS services and handling workflows like the one you’ve described. Let me break it down:

---

### **Basic AWS Lambda Workflow**

1. **Code Repository**:
    - You store your Lambda code in a GitHub repository (or similar source control).
    - The code can be written in supported languages like Python, Node.js, Java, etc.

2. **Deployment**:
    - Code is deployed to AWS Lambda using tools like the AWS CLI, AWS Management Console, or automation pipelines (e.g., GitHub Actions, AWS CodePipeline, Terraform, or Serverless Framework).
    - During deployment, you package the code and its dependencies (if any) into a ZIP file or container image and upload it to Lambda.

3. **Configuration**:
    - You configure the Lambda function to specify:
        - **Runtime environment** (e.g., Python 3.9, Node.js 18).
        - **Handler function** (entry point for your code).
        - **Triggers** (e.g., EventBridge, SQS, API Gateway).
        - **IAM roles** (permissions to access AWS services).
        - **Environment variables** (to pass configuration values).

4. **Triggering Lambda**:
    - Once deployed, Lambda is triggered by events such as:
        - API Gateway (HTTP requests).
        - S3 events (file uploads).
        - SQS or SNS messages.
        - EventBridge rules.
        - Custom application invocations.

5. **Execution**:
    - Lambda processes the event and performs the required task (e.g., publishing an event, analyzing data, updating a database).
    - If the Lambda function fails, the event can be sent to a **dead-letter queue (DLQ)** for debugging or retry logic.

---

### **Specific Workflow Based on Your Project**

Your project has a more complex setup involving multiple services, publishers, queues, and event processing. Here's an overview:

#### 1. **Publisher Lambda**:

- This Lambda function **publishes events** to **OneStream**.
- **OneStream** then forwards these events to:
    - **QSinkLambda** (likely for further processing).
    - **BSE SQS** (a Simple Queue Service for asynchronous message queuing).

#### 2. **EventBridge Rules**:

- **EventBridge** evaluates incoming events against its configured rules.
- If rules match, it processes the events and forwards them to:
    - **DLQ Drainer Lambda** if there’s an issue (e.g., failed processing).
- **DLQ Drainer Lambda** then:
    - Sends a start message.
    - Moves tasks back to the **BSE SQS** for retry.

#### 3. **BSE SQS**:

- Acts as a buffer for event messages.
- Messages are **retried, reprocessed**, or forwarded to other systems.

#### 4. **Event Analyzer Lambda**:

- This Lambda consumes events from **BSE SQS**.
- It **analyzes and publishes data** as needed for downstream systems.

---

### **Steps to Set Up and Manage This Workflow**

1. **Infrastructure as Code (IaC)**:
    
    - Use tools like **AWS CloudFormation**, **Terraform**, or **Serverless Framework** to define and deploy your AWS resources (Lambdas, SQS queues, EventBridge rules, IAM roles).
2. **Monitoring and Logging**:
    
    - Use **AWS CloudWatch** for logs, metrics, and alarms.
    - Set up **X-Ray** for distributed tracing (helpful for debugging workflows).
3. **CI/CD Pipeline**:
    
    - Automate deployments using pipelines (e.g., GitHub Actions or AWS CodePipeline).
    - Validate code changes, package Lambdas, and deploy them to AWS environments (dev, staging, prod).
4. **Error Handling**:
    
    - Configure **dead-letter queues** (DLQs) for Lambdas to capture failed events.
    - Use **Retry policies** (e.g., EventBridge, SQS, or Lambda retries).
5. **Testing**:
    
    - Test locally using tools like AWS SAM CLI, Docker, or mocking libraries.
    - Write unit and integration tests to validate function behavior and service integrations.
6. **Permission Management**:
    
    - Use **IAM roles** to grant the least privilege required for Lambda functions to interact with SQS, EventBridge, or other services.

---

### **Summary of Lambda Lifecycle in Your Workflow**

1. Code is developed, versioned, and deployed to Lambda.
2. Lambda functions act as publishers, analyzers, or processors for events.
3. Events flow between services like OneStream, EventBridge, SQS, and downstream Lambdas.
4. Error handling mechanisms like DLQs ensure failed events are retried or logged.
5. Monitoring and automation ensure scalability and reliability.

