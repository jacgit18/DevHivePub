---
tags:
  - cloud
  - distributedSystem
  - AWS
  - eventDriven
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 2024-04-05
EditDate: 
Relates: "[[Designing YouTube Recommendation Engine]]"
Peer Reviewed: 0
dg-publish:
---
Both Amazon Kinesis Data Streams and Amazon Kinesis Data Firehose offer real-time data processing capabilities, but they serve slightly different use cases and have different pricing models. Also [[Apache Kafka]] is a alternative to these service. In the context of a youtube recommendation engine you can process data like video views, likes, dislikes, comments, and subscriptions.   

Here's a comparison:

1. **Amazon Kinesis Data Streams**:
   - Pricing: With Amazon Kinesis Data Streams, you pay for the shard hours you use and for the data volume ingested, stored, and processed by the stream. Additionally, there are charges for data retrieval and data transfer out.
   - Use Case: Kinesis Data Streams is ideal for scenarios where you need fine-grained control over data processing and want to build custom data processing applications or analytics pipelines. It offers flexibility and scalability for processing large volumes of streaming data with low latency.

2. **Amazon Kinesis Data Firehose**:
   - Pricing: With Amazon Kinesis Data Firehose, you pay for the data volume ingested and delivered to destinations such as Amazon S3, Amazon Redshift, or Amazon Elasticsearch Service. There are no charges for managing infrastructure or scaling resources.
   - Use Case: Kinesis Data Firehose is suited for scenarios where you want to stream data into data lakes, data warehouses, or analytics services without the need for managing infrastructure or writing custom code. It simplifies the process of ingesting, buffering, and delivering streaming data to destinations for further processing or analysis.

For a YouTube-like platform, both services can be relevant depending on your specific requirements:
- If you need to perform custom real-time data processing or analytics on the streaming data before storing it, Amazon Kinesis Data Streams might be a better fit.
- If you primarily want to ingest streaming data and deliver it to storage or analytics services without additional processing, Amazon Kinesis Data Firehose could be more cost-effective and simpler to manage.

In some cases, it may make sense to use both services in conjunction. For example, you could use Kinesis Data Streams to process and analyze raw user interaction data in real-time and then use Kinesis Data Firehose to deliver the processed data to a data warehouse or analytics service for further analysis or reporting. This approach allows you to leverage the strengths of each service in different stages of your data processing pipeline.