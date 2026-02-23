---
tags:
  - cloud
  - AWS
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
#### **What is AWS VPC?**

Amazon **Virtual Private Cloud (VPC)** is a logically isolated network within the AWS cloud that allows you to define,  isolate, and control sections your **networking environment** within the  AWS Cloud infrastructure. It enables you to create a secure, scalable, and customizable network infrastructure for running AWS resources like EC2 instances, RDS databases, and other services. By default, resources within a VPC cannot communicate with the internet or other VPCs unless specifically configured to do so.  

With VPC, you have full control over:

- **IP address ranges** (IPv4 and IPv6)
- **Subnet creation** (public and private subnets)
- **Route tables and network gateways**
- **Security settings** (security groups and network ACLs)
- **Connectivity** (internet access, VPNs, AWS Direct Connect)

##### **What Problem Does AWS VPC Solve?**
Before VPC, AWS resources were deployed in a **shared networking environment**, which had limited customization and security options. AWS VPC solves several critical problems:


##### **1. Network Isolation and Security**
- AWS VPC creates a **private network** where your resources are isolated from other AWS customers.
- It allows you to **segment resources** using **subnets** (e.g., public vs. private subnets).
- Security Groups and Network ACLs provide **firewall-level security** at both the instance and subnet levels.


**Problem Solved:** Protects your infrastructure from unauthorized access and external threats.


##### **2. Customizable IP Addressing and Network Configuration**
- With VPC, you define your own **IP address range** using **CIDR blocks**.
- You can configure **multiple subnets** across different availability zones.
- You control how traffic flows using **route tables** and **internet gateways**.

**Problem Solved:** Gives complete control over network architecture, allowing for customized configurations.


#### **3. Private and Secure Communication Between  Services**
- AWS VPC allows secure **private communication** between EC2 instances, RDS databases, Lambda functions, and other AWS services.
- Services like **VPC Peering, AWS PrivateLink, and AWS Transit Gateway** enable private communication across different VPCs or AWS accounts.

**Problem Solved:** Eliminates the need for exposing internal services to the public internet.


#### **4. Scalable and Flexible Connectivity**
- VPC can **scale** with your infrastructure as you grow.
- You can **connect your on-premises data center** to AWS using **VPNs or AWS Direct Connect**.
- Load balancers, NAT gateways, and Elastic IPs ensure **high availability** and **efficient traffic distribution**.

**Problem Solved:** Provides seamless hybrid cloud integration and scalable network management.

#### **5. Granular Access Control for Compliance**
- AWS VPC enables **fine-grained security controls** using **IAM roles, security groups, and NACLs**.
- VPC Flow Logs allow **monitoring network traffic** for compliance and troubleshooting.
- Helps organizations **meet regulatory requirements** by keeping sensitive workloads private.

**Problem Solved:** Ensures data privacy, compliance, and monitoring capabilities.

### **Conclusion**
AWS VPC **solves the challenge of secure, customizable, and scalable networking** in the cloud. It enables businesses to **isolate workloads, secure communication, control IP addressing, and integrate with on-premises environments** without relying on public networks. By using VPC, organizations can build **highly available, resilient, and efficient cloud architectures** that meet their specific networking needs.

**Key Takeaways:**
- **Each AWS region has a limit of 5 VPCs by default** (can be increased upon request).
- **VPCs are region-locked** and do not span multiple regions.
- **VPC Peering and AWS Transit Gateway** allow communication between VPCs across different regions and accounts.

#### **What is AWS IGW?**
An Internet Gateway(IGW) is a horizontally scaled, redundant, and highly available VPC component that allows communication between instances in your VPC and the internet. It serves as a target for routing traffic destined for the internet from your VPC's subnets.  
  
The relationship between a VPC and an Internet Gateway is as follows:  
  
1. **Connection:** An Internet Gateway serves as the entry and exit point for traffic between your VPC and the internet. It enables communication between resources within your VPC and resources outside of it, such as users accessing web applications hosted in your VPC or your VPC-based resources accessing services on the internet.  
  
2. **Routing:** To enable communication between resources in a VPC and the internet, you must configure route tables in your VPC to route internet-bound traffic to the Internet Gateway. Each subnet within the VPC must be associated with a route table that includes a route to the Internet Gateway.  
  
3. **Access Control:** Access to and from the internet is controlled through network access control lists (NACLs) and security groups. NACLs act as a firewall at the subnet level, while security groups act as a firewall at the instance level. You can configure these to allow or deny traffic based on specific rules.  
  
In summary, an Internet Gateway enables communication between resources in your VPC and the internet by serving as a gateway for internet-bound traffic, while a VPC provides the network isolation and configuration framework within which your AWS resources operate.


## Extra

---
### **Why You Should Not Delete the Default VPC in AWS**

The **default VPC** in AWS is automatically created in each AWS region when you create an AWS account. It provides a fully functional, ready-to-use network environment that allows you to launch instances without manually configuring networking components. While AWS gives you the ability to create custom VPCs, it's generally advised **not to delete the default VPC**. Here's why:

### **1. Convenience for Quick Deployments**

- The default VPC is pre-configured with essential networking components such as subnets, route tables, an internet gateway, and security groups.
    
- If you need to quickly launch EC2 instances or other services that require networking, the default VPC allows you to do so **without additional setup**.
    
- AWS Marketplace and various third-party tools often assume the presence of a default VPC, making deployment smoother.

### **2. Avoiding Service Dependencies and Errors**

- Some AWS services and features **expect** a default VPC to exist and may not function properly if it’s deleted.
    
- For example, services like **AWS Lambda, Elastic Beanstalk, and RDS** often default to using the default VPC unless explicitly configured otherwise.
    
- Deleting the default VPC can lead to unexpected errors and require **manual intervention** to restore functionality.
 
 
### **3. Default VPC is Free and Easily Reusable**

- The default VPC itself is **not an additional cost**—it’s provided as a convenience by AWS.
    
- Instead of deleting it, you can **repurpose** the default VPC for non-production workloads, testing, or as a backup network environment.
    
- If you don’t want to use it, simply **ignore it** rather than removing it permanently.

### **4. Restoring a Default VPC is Not Always Simple**

- Once deleted, the default VPC **cannot be restored automatically**—you must manually recreate all components.
    
- This involves setting up:
    
    - A new **VPC**
    - Public and private **subnets**
    - An **internet gateway**
    - Correct **route tables** and **security groups**
        
- If you are unfamiliar with networking configurations, this process can be time-consuming and prone to misconfigurations.
    
### **5. Some AWS Services Automatically Use the Default VPC**

- If you delete the default VPC and later try to launch an AWS service that assumes its presence, you may encounter failures.
    
- Examples of AWS services that often use the default VPC by default:
    
    - **Amazon EC2 instances**
        
    - **Amazon RDS (Relational Database Service)**
        
    - **AWS Lambda (when using VPC-based networking)**
        
    - **Elastic Load Balancers (ELB)**
        
    - **AWS Elastic Beanstalk**
        

### **6. Helps Avoid Accidental Networking Misconfigurations**

- If you delete the default VPC without creating a properly configured replacement, your AWS resources might **lose connectivity** or experience disruptions.
    
- AWS instances need a VPC, subnets, and a correctly configured route table to function properly.
    
- Keeping the default VPC ensures there’s **always a working networking environment** available.
 
### **What to Do Instead of Deleting the Default VPC**

- **If you don’t need it, just leave it unused**—there is no harm in keeping it.
    
- **Restrict access using security groups** and **network ACLs** rather than deleting it.
    
- **Use it for development and testing** instead of production workloads.
    
- **If you want a more secure VPC**, create a custom VPC while still keeping the default one as a fallback.
    

### **Conclusion**

The default VPC is a useful, pre-configured environment that allows you to deploy AWS resources without extra networking setup. Deleting it can create unnecessary complications, especially if AWS services or third-party tools rely on it. Instead of removing it, it’s better to **keep it as a backup** or use it selectively for non-critical workloads. If security is a concern, simply restrict access rather than deleting it.