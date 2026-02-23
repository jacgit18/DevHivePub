---
tags:
  - cloud
  - services
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses types of cloud infrastructure.
Status: Done
Started: 
EditDate: 2024-02-04
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[Service Types.jpg]]

Cloud offers a range of services that fall under the categories of Infrastructure as a Service (IaaS), Platform as a Service (PaaS), and Software as a Service (SaaS). EC2 (Elastic Compute Cloud) is indeed an IaaS offering, providing virtual servers in the cloud, while Elastic Beanstalk is a higher-level service that abstracts away the infrastructure management and is classified as a PaaS. Other AWS services, such as S3 (Simple Storage Service), RDS (Relational Database Service), and Lambda, also fall into different categories within the spectrum of cloud service models.

## IAAS
IaaS, or Infrastructure as a Service, leverages virtualization to provide cloud infrastructure encompassing servers, network, storage, and operating systems. Recognized for its flexibility, users have complete control through dashboards and APIs. Unlike other models, IaaS necessitates user management of applications, data, runtimes, middleware, and OS, while the provider handles servers, storage, networking, and visualization layers.

**IaaS Characteristics:**
- *Flexibility:* Enables options for addressing future challenges.
- *Highly Scalable Services:* Mitigates resource issues through clean abstraction and tooling.
- *Consumption-dependent Costs:* Pay-as-you-go model shifts budget focus to innovation.
- *User Control:* Identity, access management, and security remain with the end-user.
- *Resources as a Service:* Provides basic computing blocks within a geographic perimeter.

**IaaS Advantages:**
- *No Infrastructure Investment:* Resources are provided by the vendor.
- *High Scalability:* Easily scales resources based on business needs.
- *Pay-as-you-go Model:* Simplifies resource purchasing and scaling.

**IaaS Disadvantages:**
- *Security Concerns:* Multiple clients using shared hardware may pose security threats.
- *Unpredictable Costs:* Scalability can lead to issues if instances are not monitored and managed properly.
- *Training Requirements:* Managing IaaS requires distinct skills; staff may need additional training.

**Infrastructure as a Service:**
- *Versatility:* Suited for startups and SMEs.
- *Control:* Offers high control levels, beneficial for large enterprises.
- *Customization:* Excellent for creating highly customizable apps.
- *Scalability:* Advantages for organizations experiencing hyper-growth.

## PAAS
PaaS, or Platform as a Service, sits between autonomy and control, providing developers a platform for rapid development, deployment, and running applications. It aims to eliminate the complexities of configuring, deploying, and managing infrastructure.

**PaaS Characteristics:**
- *Shared Responsibility Model:* Follows the shared responsibility model.
- *Infrastructure Provisioning:* Provides servers, network, and storage.
- *Server Management:* Boots and deploys servers, configures OS, runtime, and security patches.
- *Middleware Services:* Offers middleware services like databases, messaging, and cache storage.

**PaaS Advantages:**
- *Abstraction for Developers:* Provides the right level of abstraction for developers.
- *Pay-as-you-go Service:* Operates on a pay-as-you-go model.
- *Shared Good Practices:* Built on shared good practices.

**PaaS Disadvantages:**
- *One Size Does Not Fit All:* Limited scope may not cover diverse projects.
- *Vendor Lock-in:* Choosing a vendor requires caution to avoid migration costs.
- *Financial Viability:* Lack of full visibility over resource usage.

**Platform as a Service:**
- *Fast Development and Deployment:* Ideal for quick development and deployment with multiple developers.
- *Cost-Effective:* Budget-friendly compared to hiring a DevOps team.
- *Customization:* Offers a satisfying level of customization, balancing between IaaS and SaaS.


## FAAS
FaaS, or Function as a Service, represents a cloud computing model that focuses on executing individual functions or pieces of code without the need for managing underlying infrastructure. This model has gained popularity due to its event-driven architecture, where functions are triggered by specific events or requests.

### FaaS Characteristics:
- **Serverless Execution:** Users are relieved from managing servers; functions are executed in a serverless environment.
- **Event-driven:** Functions are triggered by specific events, allowing for efficient, on-demand execution.
- **Automatic Scaling:** Scales automatically in response to the number of incoming events, ensuring optimal resource utilization.
- **Short-lived Execution:** Functions typically have short lifetimes, executing quickly and independently.

### FaaS Advantages:
- **Cost Efficiency:** Users only pay for the actual execution time of functions, minimizing costs.
- **Scalability:** Automatic scaling ensures efficient handling of varying workloads.
- **Reduced Complexity:** Developers focus on writing code without concerns about infrastructure management.
- **Quick Deployment:** Rapid deployment of individual functions, facilitating agile development.

### FaaS Disadvantages:
- **Cold Start Latency:** Initial invocation may have latency (cold start) as the environment sets up.
- **Limited Execution Time:** Functions usually have time limitations, which may impact long-running processes.
- **Vendor Lock-in:** Choosing a specific FaaS provider may result in vendor lock-in.

### Function as a Service:
- **Event-triggered Execution:** Best suited for scenarios where functions need to respond to specific events or requests.
- **Cost-Effective Microservices:** Ideal for microservices architecture, offering a cost-effective and scalable solution.
- **Rapid Development:** Enables quick development and deployment of specific functions, promoting agility.

FaaS provides a serverless and event-driven approach to executing functions, offering advantages in terms of cost efficiency, scalability, and reduced development complexity. It is a valuable model for scenarios requiring rapid and event-triggered execution of functions.

## SAAS
SaaS, or Software as a Service, stands out as the most popular cloud computing model, delivering applications over the internet for easy access and management.

**SaaS Characteristics:**
- *No Infrastructure Management:* Users are not responsible for hardware and software management.
- *Internet Access:* Accessible over the internet through web browsers.
- *Remote Hosting:* Hosted on remote servers.
- *Third-party Management:* Managed by third-party vendors.

**SaaS Advantages:**
- *Any Device Accessibility:* Software accessible on any device over the internet.
- *Cost and Time Efficiency:* Eliminates concerns about installing, managing, or updating software.

**SaaS Disadvantages:**
- *No Infrastructure Control:* Lack of control over the infrastructure can lead to outages.
- *Compatibility Issues:* May not be compatible with existing tools, causing integration problems.
- *Vendor Lock-in:* Choosing the wrong vendor can result in significant costs.
- *Limited Customization:* Offers limited customization options compared to PaaS and IaaS.
- *Security Concerns:* Users have no control over the vendor's security measures, posing potential risks in case of an attack.

**Software as a Service:**
- *Quick Wins:* Ideal for scenarios requiring quick launches without concerns about server or software issues.

![[Service Types overlap.png]]

## **Key Attributes of Cloud Computing:**
- _Elasticity:_ Adapts dynamically to changes in workload.
- _Scalability:_ Allows adding resources for long-term, static workloads.
- _High Availability:_ Continues functioning even if some components fail.
- _Reliability:_ Ensures consistent and correct functioning.
- _Agility:_ Enables quick development, testing, and launching of apps.
- _Global Reach:_ Reaches users worldwide.
- _Pay-as-you-go Pricing:_ Offers economic scale and cost efficiency.


## **Cost Optimization Strategies:**
![[Cloud Cost reduce.gif]]
- _Right Sizing:_ Operate with the right amount of resources needed.
- _Automation:_ Automate behaviors to reduce costs.
- _Compliance Scope:_ Address actions dealing with data and legal requirements.
- _Managed Services:_ Use managed services instead of building up services.

## **Cloud Architecture Design Principles:**
- _Design for failure_
- _Decouple components_
- _Implement elasticity_
- _Think parallel_

## **Cloud Management Solutions:**
- **Brainboard:** Collaborative solution for visual cloud infrastructure management.
- **Pulumi:** Modern infrastructure as code platform using familiar programming languages.
- **Terraform Cloud:** Remote state management and team collaboration for cloud infrastructure. (Free for teams up to 5 users)