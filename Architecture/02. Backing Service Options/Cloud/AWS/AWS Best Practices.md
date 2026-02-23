---
tags:
  - cloud
  - bestPractices
  - AWS
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 2024-03-21
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
You can utilize Amazon Inspector, an automated security assessment service tailored for `EC2` instances, to enhance your security posture and ensure compliance with security best practices.

use Virtual Private Cloud and Virtual Private Cloud together 


Configure network settings to permit inbound HTTP traffic from the internet, enabling web access to your resources. Additionally, allow SSH traffic exclusively from your specified IP address, ensuring secure remote access to your instances while restricting unauthorized connections. This setup enhances network security by implementing precise access controls tailored to your requirements.


#todo/Med/Dev 
- [ ] [Serverless is a Scam. - DEV Community](https://dev.to/code42cate/serverless-is-a-scam-5fc0)


### Use Services like 

![[AWS Services.png]]

AWS Trusted Advisor service offers comprehensive insights into your AWS infrastructure, allowing you to assess and refine your setup against industry best practices. It enables evaluation across various facets including cost optimization, performance, security, fault tolerance, and adherence to service limits.


Instead of using the AWS Management Console user interface, consider leveraging the AWS Command Line Interface (CLI) or Software Development Kits (SDKs) for automation purposes. This approach allows for scripting and programmatic interaction with AWS services, streamlining repetitive tasks and enabling more efficient management of resources. Additionally, consider implementing automation workflows to further streamline processes, such as automatically executing tasks upon logging into the AWS account, reducing manual intervention and increasing productivity.

### AWS Account Setup & Budgeting
- Create a `root` account to gain administrative access to AWS resources.
- Establish a comprehensive budget within the `AWS Billing and Cost Management` console.
- Set predefined spending thresholds to mitigate the risk of overspending.
- Configure billing alerts for real-time notifications to ensure timely intervention.

### AWS Cost Management Tools
- **AWS Cost Explorer**: Monitor and limit expenses by providing insights into usage patterns and cost trends.
- **AWS Budgets**: Better financial planning and budget allocation with integration into Cost Explorer.
- **AWS Pricing Calculator**: Estimate costs before deployment.
- **AWS Migration Hub**: Plan and execute migrations with valuable business recommendations.

### AWS Resource Management
- **AWS Resource Tagging**: Assign metadata to AWS resources for organization and efficient spending analysis.
- **AWS Organizations**: Consolidate billing and management across multiple AWS accounts for streamlined governance.
- **Amazon Config:** is a service used to assess, audit, and evaluate the configurations of AWS resources. Amazon Config provides detailed histories of resource configs and helps Enterprise stay true to the compliance provided in their internal guidelines.

### AWS Infrastructure & Edge Locations
- **AWS Regions and Availability Zones**: Specific geolocations with clusters of data centers. Currently, 30 launch regions and 96 availability zones globally.
- **Local Zones**: Extend AWS infrastructure to different geographic locations for low-latency access to compute resources.
- **Wavelength Zones**: Specialized zones connecting to 5G networks for mobile and edge computing applications.
- **Edge Locations**: Endpoints for CDNs like Amazon CloudFront and DNS services like Amazon Route 53 to improve performance and scalability of web applications.

For users with limited container experience, AWS App Runner offers a straightforward solution for deploying and managing containerized applications with ease.

However, for more complex container management needs, Amazon ECS provides a robust container orchestration service suitable for handling multiple containers efficiently. Additionally, Amazon EKS, based on Kubernetes, offers advanced orchestration capabilities for orchestrating containerized workloads at scale.

When utilizing these services, selecting a compute engine is essential. You can opt for Amazon EC2 for manual instance management or AWS Fargate, a serverless compute engine seamlessly integrated with container orchestration services. With Fargate, you eliminate the need for manual scaling and instance management, simplifying the deployment and operation of containerized applications.


![[Cloud Services.gif]]

![[Cloud Monitoring Services.jpeg]]








