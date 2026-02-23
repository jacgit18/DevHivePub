---
tags:
  - databases
  - cloud
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses cloud databases.
Status: Done
Started: 
EditDate: 2024-03-30
Relates: 
Peer Reviewed: 0
dg-publish:
---
When navigating the realm of databases in AWS, there exist various approaches.


# AWS Database Services

| Database Type | AWS Service                                                    |
| ------------- | -------------------------------------------------------------- |
| Relational    | Amazon Aurora, Amazon RDS, Amazon Redshift                     |
| Key-value     | Amazon DynamoDB                                                |
| In-memory     | Amazon ElastiCache for Memcached, Amazon ElastiCache for Redis |
| Document      | Amazon DocumentDB                                              |
| Wide column   | Amazon Keyspaces                                               |
| Graph         | Amazon Neptune                                                 |
| Time series   | Amazon Timestream                                              |
| Ledger        | Amazon Quantum Ledger Database (Amazon QLDB)                   |


# Purpose-Built Databases in AWS

| Database Type          | Use Case                                                                 | AWS Service                     |
|------------------------|--------------------------------------------------------------------------|---------------------------------|
| Relational             | Traditional apps, CRM, eCommerce                                         | Amazon RDS, Aurora, Redshift    |
| Non-Relational (NoSQL) | High-traffic web apps, eCommerce, Gaming                                 | Amazon DynamoDB                 |
| In-memory              | Caching, session management                                              | Amazon ElastiCache              |
| Graph                  | Fraud detection, social networking, recommendation engines               | Amazon Neptune                  |


Cloud databases are categorized into different service models within cloud computing:

1. **[[Cloud Service Model#SAAS|SAAS]] (Software as a Service):** Cloud databases under SaaS typically provide storage and data analytical tools. Users access these services through a web interface, and the provider manages infrastructure, maintenance, and updates.

2. **[[Cloud Service Model#IAAS|IAAS]] (Infrastructure as a Service):** In the IaaS model, cloud databases offer storage without integrated data analytical tools. Users have more control over the infrastructure but are responsible for managing aspects like security and updates.

3. **[[Cloud Service Model#PAAS|PAAS]] (Platform as a Service):** Cloud databases under PaaS fall in between, providing storage along with additional functionality. The platform takes care of infrastructure management, and users focus more on application development.

The benefits of cloud databases include performance at scale, security, high availability, and full management by the cloud provider. Additionally, they grant access to other cloud services, such as AWS CloudTrail, which aids in governance, compliance, and auditing of AWS account activities, ensuring operational transparency and risk management.

When opting for the Infrastructure as a Service (IaaS) approach, you have the flexibility to utilize an EC2 instance and deploy your preferred database directly onto it. This grants you greater control over configuration and customization aspects.
![[DB premises.png]]

Alternatively, you can adopt more of a Software as a Service (SaaS) approach, where your focus shifts towards optimizing and configuring your application, rather than managing the underlying infrastructure. This can be achieved by leveraging managed services such as `RDS` which launches with AWS VPC by default or `DynamoDB` which is good for serverless architecture and can be used without a lot of setup, allowing you to offload the operational overhead of database management to AWS.
![[Benefits of Managed DB.png]]

