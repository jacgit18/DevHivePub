---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 2024-03-30
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
AWS Shield is a managed Distributed Denial of Service (DDoS) protection service provided by Amazon Web Services (AWS). It is designed to help protect AWS customers' web applications and infrastructure from DDoS attacks, which are attempts to disrupt the availability of online services by overwhelming them with a flood of malicious traffic.

![[GetImage (13).png]]


AWS Shield is included in several AWS services to provide protection against DDoS attacks and ensure the security of applications and infrastructure. The main AWS services that include AWS Shield are:

1. **Amazon CloudFront**: AWS Shield Standard is automatically enabled for all Amazon CloudFront distributions at no extra cost. CloudFront also supports AWS Shield Advanced for additional protection against larger and more sophisticated DDoS attacks. Also includes `AWS WAF (Web Application Firewall)`.  

2. **Elastic Load Balancing (ELB)**: AWS Shield Standard is also automatically enabled for Elastic Load Balancing (ELB) services, including Application Load Balancer (ALB), Network Load Balancer (NLB), and Classic Load Balancer.

3. **Amazon Route 53**: AWS Shield Standard is included with Amazon Route 53, AWS's scalable Domain Name System (DNS) web service. It helps protect DNS infrastructure and ensures the availability of domain names during DDoS attacks.

4. **AWS Global Accelerator**: AWS Shield Advanced is included with AWS Global Accelerator, a service that improves the availability and performance of applications running in multiple regions. Also includes `AWS WAF (Web Application Firewall)`.

5. **Amazon API Gateway**: AWS Shield Standard is automatically included with Amazon API Gateway, a fully managed service for creating, publishing, maintaining, monitoring, and securing APIs. Also includes `AWS WAF (Web Application Firewall)`.

These services automatically benefit from the DDoS protection provided by AWS Shield Standard, which helps protect against common, most frequently occurring DDoS attacks. For additional protection and advanced features, such as 24/7 access to the AWS DDoS Response Team (DRT), customers can opt for AWS Shield Advanced, which is available for an additional fee.