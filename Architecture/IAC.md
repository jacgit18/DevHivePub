---
tags:
  - cloud
  - methodology
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: Done
Started: 2024-03-23
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
# **Infrastructure as Code:**  
- IaC is a methodology within [[Cloud Service Model]] to manage and provisioning infrastructure resources using machine-readable configuration files or scripts, rather than manually configuring infrastructure components through graphical user interfaces (GUIs) or command-line interfaces (CLIs).  
- With IaC, infrastructure configurations are defined in code (e.g., YAML, JSON, or programming languages like Terraform, CloudFormation, or Ansible). These configuration files or scripts describe the desired state of the infrastructure, including servers, networks, storage, security policies, and dependencies.  
- IaC enables infrastructure to be treated as code, allowing for version control, code review, and automated testing of infrastructure changes. It also facilitates the automation of infrastructure provisioning and management, ensuring consistency, repeatability, and scalability.  
- By adopting IaC practices, organizations can achieve infrastructure agility, improve collaboration between development and operations teams (DevOps), and accelerate the deployment of applications and services in a cloud environment.  

**Infrastructure as Code (IaC)** is fundamentally about automation, but where it falls within the **IaaS vs. PaaS** spectrum depends on how it's used and the specific service involved.

- **IaC as IaaS**:
    - When using IaC to provision raw infrastructure (e.g., EC2 instances, VPCs, security groups, databases), it aligns with **Infrastructure as a Service (IaaS)**.
    - Example: AWS **CloudFormation**, Terraform, and Ansible, when used to manage VMs, networking, and storage.

- **IaC as PaaS** (Overlap):
    - If IaC is used to manage higher-level **platform services** (e.g., AWS Lambda, AppRunner, ECS Fargate), it starts to **bleed into PaaS** territory.
    - Example: Using CloudFormation or Terraform to **deploy serverless applications** on AWS Lambda or AWS Elastic Beanstalk.


### **Why Does It Overlap?**

The distinction between **IaaS** and **PaaS** isn’t always rigid. Many IaC tools can provision both raw infrastructure (IaaS) and managed services (PaaS). The boundary depends on **what is being automated**:

- **Provisioning virtual machines & networking → IaaS**
- **Deploying applications to a fully managed service → PaaS**

So, while **CloudFormation, Terraform, and similar IaC tools generally fall under IaaS**, they **can extend into PaaS when managing higher-level AWS services**.
  
In summary, while IaaS provides virtualized infrastructure resources as a service, IaC is a practice for managing and provisioning infrastructure resources using code-based configuration files or scripts. IaaS is a service model offered by cloud providers, while IaC is a methodology for automating and managing infrastructure deployments in a cloud-native or hybrid environment.




## A _real_ IaC example (AWS CDK, Python)

**What this stack includes:**

- VPC
    
- Security groups
    
- S3 bucket
    
- DynamoDB table
    
- Two Lambdas (API + worker)
    
- API Gateway
    
- IAM roles (least-privilege)
    
- Environment config
    
- CloudWatch logs
    

This is no longer a “toy Lambda.”

---

## Project structure

```
infra/
├── app.py
├── stacks/
│   ├── app_stack.py
│   └── network_stack.py
├── lambda/
│   ├── api_handler.py
│   └── worker.py
├── config.py
└── requirements.txt
```

---

## `config.py` — environment-aware config

```python
from dataclasses import dataclass

@dataclass
class EnvConfig:
    name: str
    memory: int
    timeout: int

DEV = EnvConfig(
    name="dev",
    memory=256,
    timeout=10,
)

PROD = EnvConfig(
    name="prod",
    memory=1024,
    timeout=30,
)
```

---

## `network_stack.py` — VPC + security

```python
from aws_cdk import Stack, aws_ec2 as ec2
from constructs import Construct

class NetworkStack(Stack):
    def __init__(self, scope: Construct, id: str, **kwargs):
        super().__init__(scope, id, **kwargs)

        self.vpc = ec2.Vpc(
            self,
            "AppVpc",
            max_azs=2,
            nat_gateways=1,
        )
```

---

## `app_stack.py` — the _actual system_

```python
from aws_cdk import (
    Stack,
    Duration,
    aws_lambda as lambda_,
    aws_apigateway as apigw,
    aws_dynamodb as dynamodb,
    aws_s3 as s3,
    aws_iam as iam,
)
from constructs import Construct

class AppStack(Stack):
    def __init__(self, scope: Construct, id: str, vpc, config, **kwargs):
        super().__init__(scope, id, **kwargs)

        bucket = s3.Bucket(self, "UploadsBucket")

        table = dynamodb.Table(
            self,
            "ItemsTable",
            partition_key=dynamodb.Attribute(
                name="pk",
                type=dynamodb.AttributeType.STRING,
            ),
        )

        lambda_role = iam.Role(
            self,
            "LambdaRole",
            assumed_by=iam.ServicePrincipal("lambda.amazonaws.com"),
        )

        lambda_role.add_managed_policy(
            iam.ManagedPolicy.from_aws_managed_policy_name(
                "service-role/AWSLambdaBasicExecutionRole"
            )
        )

        bucket.grant_read_write(lambda_role)
        table.grant_read_write_data(lambda_role)

        api_lambda = lambda_.Function(
            self,
            "ApiLambda",
            runtime=lambda_.Runtime.PYTHON_3_11,
            handler="api_handler.main",
            code=lambda_.Code.from_asset("lambda"),
            role=lambda_role,
            memory_size=config.memory,
            timeout=Duration.seconds(config.timeout),
            environment={
                "BUCKET_NAME": bucket.bucket_name,
                "TABLE_NAME": table.table_name,
            },
            vpc=vpc,
        )

        worker_lambda = lambda_.Function(
            self,
            "WorkerLambda",
            runtime=lambda_.Runtime.PYTHON_3_11,
            handler="worker.main",
            code=lambda_.Code.from_asset("lambda"),
            role=lambda_role,
            timeout=Duration.seconds(30),
            vpc=vpc,
        )

        api = apigw.LambdaRestApi(
            self,
            "HttpApi",
            handler=api_lambda,
            proxy=True,
        )
```

---

## `app.py` — composition (this is the IaC _architecture_)

```python
import aws_cdk as cdk
from stacks.network_stack import NetworkStack
from stacks.app_stack import AppStack
from config import DEV

app = cdk.App()

network = NetworkStack(app, "NetworkStack")
AppStack(
    app,
    "AppStack",
    vpc=network.vpc,
    config=DEV,
)

app.synth()
```

---

## Why this is “big” in the only way that matters

This example demonstrates:

- **Composition** (stacks depending on stacks)
    
- **Explicit boundaries** (network vs app)
    
- **Shared IAM roles** (intentional coupling)
    
- **Environment control**
    
- **Diffable infrastructure**
    
- **Clear blast radius**
    

This is the level where IaC starts paying off.

---

## Now the critique (because this matters)

If your reaction is:

> “This feels verbose”

Good. That means you’re noticing **explicitness**, not inefficiency.

If your reaction is:

> “I could do this faster with boto3”

Also true — and you’d lose:

- Change previews
    
- Rollbacks
    
- Reproducibility
    
- Team sanity
    

Speed without reversibility is not engineering — it’s gambling.

---

## The real question you should answer next

Before going further, be honest:

**Are you trying to**

1. Learn IaC concepts?
    
2. Build something deployable for work?
    
3. Understand how large systems are _mentally structured_?
    
4. Replace Terraform?
    
5. Automate a personal project quickly?
    
