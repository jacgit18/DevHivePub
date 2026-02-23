---
tags:
  - cloud
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
# **Services That Generate or Start Other Services**

#todo/Med/Dev 
- [ ] Update with Google & Azure S

This is a categorized breakdown of AWS services that **provision, automate, or manage** infrastructure and applications within an **IaaS (Infrastructure as a Service)** context.

---

## **1. Infrastructure as Code ([[IAC|IAC]]) & Automation**

Services that define, provision, and manage AWS resources through templates or automation.

- **AWS CloudFormation** → Deploys entire infrastructures (**EC2, RDS, VPCs, etc.**) using templates.
- **AWS OpsWorks** → Automates configuration management using **Chef/Puppet**.
- **AWS Service Catalog** → Creates and manages **pre-approved CloudFormation stacks**.
- **AWS Proton** → Automates infrastructure templates for **containerized and serverless applications**.
- **AWS CodePipline** → is the primary service that orchestrates the flow between CodeCommit, CodeBuild, and CodeDeploy in a CI/CD workflow.

---

## **2. Application & Compute Orchestration**

Services that launch and manage compute resources dynamically.

- **AWS Elastic Beanstalk** → Deploys and manages **EC2, RDS, and ALB** for web applications.
- **AWS Auto Scaling** → Automatically scales **EC2 instances, ECS tasks, and Aurora databases**.
- **AWS Batch** → Provisions **EC2 or Fargate instances** for batch jobs.
- **AWS Step Functions** → Orchestrates workflows by triggering **Lambda, ECS, or other AWS services**.

---

## **3. Multi-Account & Governance Automation**

Services that create and manage AWS accounts and security policies at scale.

- **AWS Control Tower** → Automates **multi-account setup** with governance policies.
- **AWS Organizations** → Manages multiple AWS accounts, **creating them as needed**.

---

## **4. Systems Management & Maintenance**

Services that automate operational tasks like patching, provisioning, and monitoring.

- **AWS Systems Manager (SSM) Automation** → Starts and configures **EC2 instances, runs patches, and manages state**.
- **AWS Backup** → Automates backups for **EC2, RDS, DynamoDB, and more**.

---

Would you like an example of how these services work together in a **real-world deployment**?