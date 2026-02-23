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
Amazon **SQS (Simple Queue Service)** is designed for **temporary, transient data** rather than permanent storage. It is primarily used for **decoupling services** in distributed systems, allowing components to communicate asynchronously.

#todo/High/Dev 
- [ ] [Guide to Sending Messages to an SQS Queue With Lambda. \| by Kim siangchin \| Code Like A Girl](https://code.likeagirl.io/guide-to-sending-messages-to-an-sqs-queue-with-lambda-758cf782cb83)


### **What Type of Data is Processed by SQS?**

1. **Event-Driven Data** – Messages that trigger processing in another system (e.g., order placed, user signup, email notifications).
2. **Task Queues** – Jobs that need to be processed by background workers (e.g., image processing, batch data processing).
3. **Temporary Data** – Messages meant to be consumed quickly and not stored long-term (e.g., logs, status updates).
4. **Retry Mechanism** – Failed tasks that need reattempting before being discarded (Dead Letter Queues).

### **Best Practices for Data Sent Through SQS**

✅ **Send Lightweight, Stateless Messages** – Keep messages small (<256 KB) and avoid storing entire datasets in the queue.  
✅ **Use it for Work Distribution** – Spread workload across multiple consumers (e.g., workers processing user-generated content).  
✅ **Idempotency Handling** – Ensure messages can be reprocessed safely (SQS does **not guarantee exactly-once delivery**).  
✅ **Short-Lived Data** – Don't treat SQS as a database; messages expire after their retention period (max 14 days).  
✅ **Metadata Instead of Full Data** – Store only references (e.g., IDs, paths) instead of large payloads.

### **When NOT to Use SQS**

❌ **Permanent Storage** – Use a database like DynamoDB, RDS, or S3 for persistent data.  
❌ **Real-Time Streaming** – Use **Amazon Kinesis** if you need low-latency, high-throughput data streaming.  
❌ **Large File Transfers** – Use **S3** and send file URLs via SQS instead of pushing entire files into the queue.

