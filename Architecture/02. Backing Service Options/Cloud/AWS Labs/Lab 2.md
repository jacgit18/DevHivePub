# Lab 2: Building Your Amazon VPC Infrastructure

## Lab Overview  

As an **AWS Solutions Architect**, it is important that you understand the overall functionality and capabilities of **Amazon Web Services (AWS)** and the relationship between AWS networking components.  

In this lab, you will create:  

- An **Amazon Virtual Private Cloud (Amazon VPC)**  
- A **public and private subnet** in a single Availability Zone  
- **Public and private routes**  
- A **NAT gateway**  
- An **Internet gateway**  

These services form the foundation of **networking architecture** inside AWS. This architecture design covers concepts of **infrastructure, design, routing, and security**.  

The following image shows the final architecture for this lab environment:  

![[2025-03-15 14.39.09 online.vitalsource.com 6cf82326d082.png]]

Objectives 
After completing this lab, you should know how to do the following:

•
 Create an Amazon VPC. 
•
 Create public and private subnets. 
•
 Create an internet gateway. 
•
 Configure a route table and associate it to a subnet. 
•
 Create an Amazon Elastic Compute Cloud (Amazon EC2) instance and make the instance publicly accessible. 
•
 Isolate an Amazon EC2 instance in a private subnet. 
•
 Create and assign security groups to Amazon EC2 instances. 
•
 Connect to Amazon EC2 instances using Session Manager, a capability of AWS Systems Manager. 

Task 1: Create an Amazon VPC in a Region 
In this task, you create a new Amazon VPC in the AWS Cloud. 




3.
 At the top of the AWS Management Console, in the search bar, search for and choose VPC. 
! Caution: Verify that the Region displayed in the top-right corner of the console is the same as the Region value on the left side of this lab page. 
 
4.
 In the left navigation pane, choose Your VPCs. 
The console displays a list of your currently available VPCs. A default VPC is provided so that you can launch resources as soon as you start using AWS. 
5.
 Choose Create VPC and configure the following: 
•
 Resources to create: Choose  VPC only. 
•
 Name tag - optional: Enter Lab VPC 
•
 IPv4 CIDR: Enter 10.0.0.0/16 
6.
 Choose Create VPC. 

A  You successfully created vpc-xxxxxxxxxx / Lab VPC message is displayed on top of the screen. 
The VPC Details page is displayed. 
7.
 Verify the state of the Lab VPC. 
 Expected output: It should display the following: 
•
 State:  Available 
ⓘ The lab VPC has a Classless Inter-Domain Routing (CIDR) range of 10.0.0.0/16, which includes all IP addresses that start with 10.0.x.x. This range contains over 65,000 addresses. You later divide the addresses into separate subnets. 
8.
 From the same page, choose Actions ▼ and choose Edit VPC settings. 
The Edit VPC settings page is displayed. 
9.
 From the DNS settings section, select ☑ Enable DNS hostnames. 
This option assigns a friendly Domain Name System (DNS) name to Amazon EC2 instances in the VPC, such as the following: 
ec2-52-42-133-255.us-west-2.compute.amazonaws.com 
10.
 Choose Save. 
A  You have successfully modified the settings for vpc-xxxxxxxxxx / Lab VPC. message is displayed on top of the screen. 
Any Amazon EC2 instances launched into this Amazon VPC now automatically receive a DNS hostname. You can also create a more meaningful DNS name (for example, app.company.com) using records in Amazon Route 53. 



Task 2: Create public subnets and private subnets 
In this task, you create a public subnet and a private subnet in the lab VPC. To add a new subnet to your VPC, you must specify an IPv4 CIDR block for the subnet from the range of your VPC. You can specify the Availability Zone in which you want the subnet to reside. You can have multiple subnets in the same Availability Zone. 
 

Task 2.1: Create your public subnet 
The public subnet is for internet-facing resources. 
11.
 In the left navigation pane, choose Subnets. 
12.
 Choose Create subnet and configure the following: 
•
 VPC ID: Select Lab VPC from the dropdown menu. 
•
 Subnet name: Enter Public Subnet. 
•
 Availability Zone: Select the first Availability Zone in the list. (Do not choose No Preference.) 
•
 IPv4 subnet CIDR block: Enter 10.0.0.0/24. 
13.
 Choose Create subnet. 
A  You have successfully created 1 subnet: subnet-xxxxxx message is displayed on top of the screen. 
14.
 Verify the state. 

Expected output: It should display the following: 
•
 State:  Available 
 
15.
 Select ☑ Public Subnet. 
16.
 Choose Actions ▼ and choose Edit subnet settings. 
The Edit subnet settings page is displayed. 
17.
 From the Auto-assign IP settings section, select ☑ Enable auto-assign public IPv4 address. 
18.
 Choose Save. 
A  You have successfully changed subnet settings: Enable auto-assign public IPv4 address message is displayed on top of the screen. 

Task 2.2: Create your private subnet 
The private subnet is for resources that are to remain isolated from the internet. 
19.
 Choose Create subnet, and then configure the following: 
•
 VPC ID: Select Lab VPC from the dropdown menu. 
•
 Subnet name: Enter Private Subnet. 
•
 Availability Zone: Select the first Availability Zone in the list. (Do not choose No Preference.) 
•
 IPv4 subnet CIDR block: Enter 10.0.2.0/23. 
20.
 Choose Create subnet. 
A  You have successfully created 1 subnet: subnet-xxxxxx message is displayed on top of the screen. 
21.
 Verify the state. 

 Expected output: It should display the following: 
•
 State:  Available 
 Note: The CIDR block of 10.0.2.0/23 includes all IP addresses that start with 10.0.2.x and 10.0.3.x. This is twice as large as the public subnet because most resources should be kept private, unless they specifically need to be accessible from the internet. 
Your VPC now has two subnets. However, these subnets are isolated and cannot communicate with resources outside the VPC. Next, you configure the public subnet to connect to the internet through an internet gateway. 
 Congratulations! You have successfully created a public subnet and a private subnet in the lab VPC. 

Task 3: Create an internet gateway 
In this task, you create an internet gateway so that internet traffic can access the public subnet. To grant access to or from the internet for instances in a subnet in a VPC, you create an internet gateway and attach it to your VPC. Then you add a route to your subnet&apos;s route table that directs internet-bound traffic to the internet gateway. 

22.
 In the left navigation pane, choose Internet gateways. 
23.
 Choose Create internet gateway and configure the following: 
•
 Name tag: Enter Lab IGW. 
24.
 Choose Create internet gateway. 
A  The following internet gateway was created: igw-xxxxxx - Lab IGW. You can now attach to a VPC to enable the VPC to communicate with the internet. message is displayed on top of the screen. 
You can now attach the internet gateway to your Lab VPC. 
25.
 From the same page, choose Actions ▼ and choose Attach to VPC. 
26.
 For Available VPCs, select Lab VPC from the dropdown menu. 
27.
 Choose Attach internet gateway. 
A  Internet gateway igw-xxxxx successfully attached to vpc-xxxxx message is displayed on top of the screen. 
28.
 Verify the state. 
 Expected output: It should display the following: 
•
 State:  Attached 
The internet gateway is now attached to your Lab VPC. Even though you have created an internet gateway and attached it to your VPC, you must also configure the route table of the public subnet to use the internet gateway. 
 Congratulations! You have successfully created an internet gateway so that internet traffic can access the public subnet


Task 4: Route internet traffic in the public subnet to the internet gateway 
In this task, you create a route table and add a route to the route table to direct internet-bound traffic to your internet gateway and associate your public subnets with your route table. Each subnet in your VPC must be associated with a route table; the table controls the routing for the subnet. A subnet can only be associated with one route table at a time, but you can associate multiple subnets with the same route table. 

29.
 In the left navigation pane, choose Route tables. 
There is currently one default route table associated with the VPC, Lab VPC. This routes traffic locally. You now create an additional route table to route public traffic to your internet gateway. 
30.
 Choose Create route table, and then configure the following: 
•
 Name - optional: Enter Public Route Table. 
•
 VPC: Select Lab VPC from the dropdown menu. 
31.
 Choose Create route table. 
A  Route table rtb-xxxxxxx | Public Route Table was created successfully. message is displayed on top of the screen. 
32.
 Choose the Routes tab in the lower half of the page. 
 Note: There is one route in your route table that allows traffic within the 10.0.0.0/16 network to flow within the network, but it does not route traffic outside of the network. 
You now add a new route to permit public traffic. 
33.
 Choose Edit routes. 
34.
 Choose Add route, and then configure the following: 
•
 Destination: Enter 0.0.0.0/0. 
•
 Target: Choose Internet Gateway in the dropdown menu, and then choose the displayed internet gateway ID. 
35.
 Choose Save


A  Updated routes for rtb-xxxxxxx / Public Route Table successfully message is displayed on top of the screen. 
36.
 Choose the Subnet associations tab. 
37.
 Choose Edit subnet associations. 
38.
 Select ☑ Public Subnet 
39.
 Choose Save associations. 
A  You have successfully updated subnet associations for rtb-xxxxxxx / Public Route Table. message is displayed on top of the screen. 
 


Task 5: Create a public security group 
In this task, you create a security group so that users can access your Amazon EC2 instance. Security groups in a VPC specify which traffic is allowed to or from an Amazon EC2 instance. 

 Security: It is recommended to use HTTPS protocol to improve web traffic security. However, to simplify this lab, only HTTP protocol is used. 
40.
 In the left navigation pane, choose Security groups. 
41.
 Choose Create security group, and then configure the following: 
•
 Security group name: Enter Public SG. 
•
 Description: Enter Allows incoming traffic to public instance. 
•
 VPC: Select Lab VPC from the dropdown menu. 
42.
 In the Inbound rules section, choose Add rule and configure the following: 
•
 Type: Select HTTP from the dropdown menu. 
•
 Source: Select Anywhere-IPv4 from the dropdown menu. 
43.
 In the Tags - optional section, choose Add new tag and configure the following: 
•
 Key: Enter Name. 
•
 Value: Enter Public SG. 
44.
 Choose Create security group. 
A  Security group (sg-xxxxxxx | Public SG) was created successfully message is displayed on top of the screen. 
 Congratulations! You have successfully created a security group that allows HTTP traffic. You need this in the next task when you launch an Amazon EC2 instance in the public subnet. 


Task 6: Launch an Amazon EC2 instance into a public subnet 
In this task, you launch an Amazon EC2 instance into a public subnet. To activate communication over the internet for IPv4, your instance must have a public IPv4 address that&apos;s associated with a private IPv4 address on your instance. By default, your instance is only aware of the private (internal) IP address space defined within the VPC and subnet. 
 

45.
 At the top of the AWS Management Console, in the search bar, search for and choose EC2. 
The Amazon EC2 Management Console is displayed. 
Task 6.1: Begin the instance configuration 
46.
 From the console navigation menu on the left, choose EC2 Dashboard. 
47.
 From the Launch instances section, choose Launch instances. 
The Launch an instance page is displayed. 
Task 6.2: Add tags to the instance 
You can use tags to categorize your AWS resources in different ways, such as by purpose, owner, or environment. You can apply tags to most AWS Cloud resources. Each tag consists of a key and a value, both of which you define. One use of tags is for when you must manage many resources of the same type. You can quickly search for and identify a specific resource by the tag you have applied to


In this task, you add a tag to the Amazon EC2 instance. 
48.
 Locate the Name and tags section. 
49.
 In the Name field, enter Public Instance. 

Task 6.3: Select an AMI 
In this task, you choose an Amazon Machine Image (AMI). The AMI contains a copy of the disk volume used to launch the instance. 
50.
 Locate the Application and OS Images (Amazon Machine Image) section. 
51.
 Ensure that Amazon Linux is selected as the OS. 
52.
 Ensure that Amazon Linux 2023 AMI is selected in the dropdown menu. 
Task 6.4: Choose the Amazon EC2 instance type 
Each instance type allocates a specific combination of virtual CPUs (vCPUs), memory, disk storage, and network performance. 
For this lab, use a t3.micro instance type. This instance type has 2 vCPUs and 1 GiB of memory. 
53.
 Locate the Instance type section. 
54.
 From the Instance type dropdown menu, choose t3.micro. 
Task 6.5: Configure key pair for login 
55.
 Locate the Key pair (login) section. 
56.
 From the Key pair name - required dropdown menu, choose Proceed without a key pair (Not recommended) ▼. 
Task 6.6: Configure instance networking 
57.
 Locate the Network settings section. 
58.
 Choose Edit. 
59.
 Configure the following settings from the dropdown menus: 
•
 VPC - required: Select Lab VPC. 
•
 Subnet: Select Public Subnet. 

•
 Auto-assign public IP: Select Enable. 
Task 6.7: Configure instance security groups 
You can use security groups to define both the allowed/denied and the inbound/outbound traffic for the elastic network interface. The network interface is attached to an Amazon EC2 instance. Port 80 is the default port for HTTP traffic, and it is necessary for the web server you launch in this lab to work correctly. 
60.
 For Firewall (security groups), choose  Select existing security group. 
61.
 From the Common security groups dropdown menu, choose the security group that has a name like Public SG. 
Task 6.8: Add storage 
You can use the Configure storage section to specify or modify the storage options for the instance and add additional Amazon Elastic Block Store (Amazon EBS) disk volumes attached to the instance. The EBS volumes can be configured in both their size and performance. 
In this lab, the default storage settings are all that is needed. No changes are required. 
Task 6.9: Configure user data 
62.
 Locate and expand the ▶ Advanced details section. 
63.
 From the IAM instance profile dropdown menu, select the role that has a name like EC2InstProfile. 
 Note: To install and configure the new instance as a web server, you provide a user data script that automatically runs when the instance launches. 
64.
 In the User data - optional section, copy and paste the following: 
#!/bin/bash # To connect to your EC2 instance and install the Apache web server with PHP yum update -y yum install -y httpd php8.1 systemctl enable httpd.service systemctl start httpd cd /var/www/html wget  https://us-west-2-tcprod.s3.amazonaws.com/courses/ILT-TF-200-ARCHIT/v7.9.8.prod-1c01ca56/lab-2-VPC/scripts/instanceData.zip unzip instanceData.zip  
The remaining settings on the page can be left at their default values. 


Task 6.10: Review the instance launch 
Take a moment to review that the configuration for the Amazon EC2 instance you are about to launch is correct. 
65.
 Locate the Summary section. 
66.
 Choose Launch instance. 
The Launch an instance page is displayed. 
Your Amazon EC2 instance is now launched and configured as you specified. 
67.
 Choose View all instances. 
The Amazon EC2 console is displayed. 
68.
 Occasionally choose the console refresh button  and wait for Public Instance to display the Instance state as  Running and wait for Status check to pass  3/3 checks passed. 
 


Task 7: Connect to a public instance through HTTP 
In this task, you connect to the public instance and launch the basic Apache web server page. The inbound rules added earlier that allow HTTP access (port 80) allow you to connect to the web server running Apache. 
69.
 In the left navigation pane, choose Instances. 
70.
 Select ☑ Public Instance. 
71.
 Choose the Networking tab in the lower pane. 
 Note: If you need to make any section of the console larger, you can resize the horizontal edges of the containers displayed on the console. 
72.
 Locate the Public IPv4 DNS value. 
73.
 Copy  the public DNS value. Do not choose the open address  option, because HTTPS is not set up for this lab environment. 
74.
 Open a new browser tab and paste the public DNS value for Public Instance in the URL address bar. 
The web page hosted on the Amazon EC2 instance is displayed. The page displays the instance ID and the AWS Availability Zone where the Amazon EC2 instance is located. 
75.
 Close the browser tab and return to the console. 
 Congratulations! You have successfully launched an Apache web server in the public subnet and tested the HTTP connection. You can safely close the tab and return to the console. 


Task 8: Connect to the Amazon EC2 instance in the public subnet through Session Manager 
In this task, you connect to your Amazon EC2 instance in the public subnet using Session Manager. 

76.
 At the top of the AWS Management Console, in the search bar, search for and choose EC2. 
77.
 In the left navigation pane, choose Instances. 
78.
 Select ☑ Public Instance and choose Connect. 
The Connect to instance page is displayed. 
79.
 Choose the Session Manager tab. 

. 
80.
 Choose Connect. 
A new browser tab or window opens with a connection to the Public Instance. 
 Note: The Session Manager service is not updated in real time. If you experience errors with Session Manager connecting to an Amazon EC2 instance you just launched, ensure that you have given the instance a few minutes to launch, pass health checks, and communicate with the Session Manager service before trying to open a session connection again. 
81.
  Command: Enter the following command to change to the home directory (/home/ssm-user/) and test web connectivity using the cURL command: 
cd ~ curl -I https://aws.amazon.com/training/  

Task 9: Create a NAT gateway and configuring routing in the private subnet 
In this task, you create a NAT gateway and then create a route table to route non-local traffic to the NAT gateway. You then attach the route table to the private subnet. You can use a NAT gateway to allow instances in a private subnet to connect to the internet or other AWS services, but prevent the internet from initiating a connection with those instances. 
 
82.
 Return to the AWS Management Console browser tab. 
83.
 At the top of the AWS Management Console, in the search box, search for and choose VPC. 
84.
 In the left navigation pane, choose NAT gateways. 
85.
 Choose Create NAT gateway and configure the following: 
•
 Name - optional: Enter Lab NGW. 
•
 Subnet: Select Public Subnet from the dropdown menu. 
•
 For Elastic IP allocation ID, choose Allocate Elastic IP. 
86.
 Choose Create NAT gateway. 
A  NAT gateway nat-xxxxxxx | Lab NGW was created successfully. message is displayed on top of the screen. 
In the next step, you create a new route table for a private subnet that redirects non-local traffic to the NAT gateway. 
87.
 In the left navigation pane, choose Route tables. 
88.
 Choose  Create route table and configure the following: 
•
 Name - optional: Enter Private Route Table. 
•
 VPC: Select Lab VPC from the dropdown menu. 
89.
 Choose Create route table. 
A  Route table rtb-xxxxxxx | Private Route Table was created successfully. message is displayed on top of the screen. 
The private route table is created and the details page for the private route table is displayed.

90.
 Choose the Routes tab. 
There is currently one route that directs all traffic locally. 
You now add a route to send internet-bound traffic through the NAT gateway. 
91.
 Choose Edit routes. 
92.
 Choose Add route and then configure the following: 
•
 Destination: Enter 0.0.0.0/0. 
•
 Target: Choose NAT Gateway in the dropdown menu, and then choose the displayed NAT Gateway ID. 
93.
 Choose Save changes. 
A  Updated routes for rtb-xxxxxxx / Private Route Table successfully message is displayed on top of the screen. 
94.
 Choose the Subnet associations tab. 
95.
 Choose Edit subnet associations. 
96.
 Select ☑ Private Subnet. 
97.
 Choose Save associations. 
A  You have successfully updated subnet associations for rtb-xxxxxxx / Private Route Table. message is displayed on top of the screen. 
This route sends internet-bound traffic from the private subnet to the NAT gateway that is in the same Availability Zone. 



Task 10: Create a security group for private resources 
In this task, you create a security group that allows incoming HTTP traffic from resources assigned to the public security group. In a multi-tiered architecture, resources in a private subnet are should not directly accessible from the internet, however their is a common use case to route web traffic from publicly accessible resources to private resources. 

98.
 In the left navigation pane, choose Security groups. 
99.
 Choose Create security group, and then configure the following: 
•
 Security group name: Enter Private SG. 
•
 Description: Enter Allows incoming traffic to private instance from public security group. 
•
 VPC: Select Lab VPC from the dropdown menu. 
100.
 In the Inbound rules section, choose Add rule and configure the following: 
•
 Type: Select HTTP. 
•
 Source: Select Custom. 
o
 In the box to the right of Custom, type sg. 
o
 Choose Public SG from the list. 
101.
 In the Tags - optional section, choose Add new tag and configure the following: 
•
 Key: Enter Name. 
•
 Value: Enter Private SG. 
102.
 Choose Create security group. 
A  Security group (sg-xxxxxxx | Private SG) was created successfully message is displayed on top of the screen. 


Task 11: Launch an Amazon EC2 instance into a private subnet 
In this task, you launch an Amazon EC2 instance into a private subnet. 

103.
 At the top of the AWS Management Console, in the search bar, search for and choose EC2. 
The Amazon EC2 console is displayed. 
Task 11.1: Begin the instance configuration 
104.
 Choose EC2 Dashboard from the console navigation menu on the left. 
105.
 Choose Launch instance from the Launch instance section. 
The Launch an instance page is displayed. In this task, you add a tag to the Amazon EC2 instance. 
106.
 Locate the Name and tags section. 
107.
 Enter Private Instance in the Name field. 

Task 11.3: Select an AMI 
In this task, you choose an AMI. The AMI contains a copy of the disk volume used to launch the instance. 
108.
 Locate the Application and OS Images (Amazon Machine Image) section. 
109.
 Ensure that Amazon Linux is selected as the OS. 
110.
 Ensure that Amazon Linux 2023 AMI is selected in the dropdown menu. 
Task 11.4: Choose the Amazon EC2 instance type 
Each instance type allocates a specific combination of vCPUs, memory, disk storage, and network performance. 

For this lab, use a t3.micro instance type. This instance type has 2 vCPUs and 1 GiB of memory. 
111.
 Locate the Instance type section. 
112.
 Choose t3.micro from the Instance type dropdown menu. 
Task 11.5: Configure key pair for login 
113.
 Locate the Key pair (login) section. 
114.
 Choose  Proceed without a key pair (Not recommended) ▼ from the Key pair name - required dropdown menu. 
Task 11.6: Configure instance networking 
115.
 Locate the Network settings section. 
116.
 Choose Edit and configure the following settings from the dropdown menus: 
•
 VPC - required: Select Lab VPC. 
•
 Subnet: Select Private Subnet. 
•
 Auto-assign public IP: Select Disable. 
Task 11.7: Configure instance security groups 
117.
 For Firewall (security groups), choose  Select existing security group 
118.
 Choose the security group that has a name like Private SG from the Common security groups dropdown menu. 
Task 11.8: Add storage 
You can use the Configure storage section to specify or modify the storage options for the instance and add additional Amazon Elastic Block Store (Amazon EBS) disk volumes attached to the instance. The EBS volumes can be configured in both their size and performance. 
In this lab, the default storage settings are all that is needed. No changes are required. 
Task 11.9: Configure the IAM instance profile 
119.
 Locate and expand the ▶ Advanced details section. 
120.
 From the IAM instance profile dropdown menu, select the role that has a name like EC2InstProfile. 


The remaining settings on the page can be left at their default values. 
Task 11.10: Configure user data 
121.
 Locate and expand the ▶ Advanced details section. 

122.
 In the User data - optional section, copy and paste the following: 
#!/bin/bash # To connect to your EC2 instance and install the Apache web server with PHP yum update -y yum install -y httpd php8.1 systemctl enable httpd.service systemctl start httpd cd /var/www/html wget  https://us-west-2-tcprod.s3.amazonaws.com/courses/ILT-TF-200-ARCHIT/v7.9.8.prod-1c01ca56/lab-2-VPC/scripts/instanceData.zip unzip instanceData.zip  
The remaining settings on the page can be left at their default values. 
Task 11.11: Review the instance launch 
Take a moment to review that the configuration for the Amazon EC2 instance you are about to launch is correct. 
123.
 Locate the Summary section. 
124.
 Choose Launch instance. 
The Launch an instance page is displayed. 
Your Amazon EC2 instance is now launched and configured as you specified. 
125.
 Choose View all instances. 
The Amazon EC2 console is displayed. 
126.
 Occasionally choose the console refresh button  and wait for Private Instance to display the Instance state as  Running and wait for Status check to pass  3/3 checks passed. 



Task 12: Connect to the Amazon EC2 instance in the private subnet 
In this task, you connect to the Amazon EC2 instance in the private subnet using Session Manager. 
127.
 In the left navigation pane, choose Instances. 
128.
 Select ☑ Private Instance and choose Connect. 
The Connect to instance page is displayed. 
129.
 Choose the Session Manager tab. 
130.
 Choose Connect. 
A new browser tab or window opens with a connection to the Private Instance. 

131.
  Command: Enter the following command to change to the home directory (/home/ssm-user/) and test web connectivity using the cURL command: 
cd ~ curl -I https://aws.amazon.com/training/   


