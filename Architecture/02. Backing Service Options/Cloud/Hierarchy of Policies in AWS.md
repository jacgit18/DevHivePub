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
#### 1. **[[Managing IAM#**Example Least Privilege IAM Policy(Permissions Policy) **|Identity-Based Policies]] (IAM Policies)**

- These policies are **attached to IAM users, groups, or roles**. They define what actions a principal (user, group, or role) can perform on specific resources (e.g., S3, EC2).
    
- **Order of Evaluation**: These policies are evaluated when a principal (like a user or service) attempts to perform an action. AWS checks whether the action is allowed or denied based on the policies attached to the principal.
    
- **Example**: An IAM policy attached to a user that allows access to an S3 bucket.
    

#### 2. **Resource-Based Policies**

- These policies are attached **directly to AWS resources** like S3 buckets, Lambda functions, or SNS topics. They specify who (users, roles, or services) can access the resource and under what conditions.
    
- **Example**: An S3 bucket policy that grants specific IAM users or roles permission to access the bucket.
    

##### Example: S3 Bucket Policy (Resource-Based Policy)

This policy allows the IAM role `arn:aws:iam::123456789012:role/MyIAMRole` to perform the `s3:GetObject` action on all objects in the bucket `my-secure-bucket`.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::123456789012:role/MyIAMRole"
      },
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-secure-bucket/*"
    }
  ]
}
```

##### Explanation:

- **`Principal`**: Specifies the IAM role (`arn:aws:iam::123456789012:role/MyIAMRole`) that is allowed to access the resource.
- **`Action`**: The allowed action, in this case, `s3:GetObject`, which allows reading objects from the bucket.
- **`Resource`**: Specifies the S3 bucket and its contents (`arn:aws:s3:::my-secure-bucket/*`), meaning all objects in the `my-secure-bucket` are covered by the policy.

#### 3. **Trust Policies**

- These policies are attached to **IAM roles**. They define **who can assume the role** (e.g., an AWS service like Lambda or a user from another AWS account).
    
- **Example**: A trust policy for a Lambda function to assume an IAM role.


In **AWS**, a **trust policy** is a JSON document attached to an **IAM role** that defines **who (which entities) is allowed to assume the role**.

These entities can be:

- AWS accounts
- Specific IAM users
- Other AWS services (like EC2, Lambda, etc.)
- Federated users from an external identity provider

##### Example

A trust policy might look like this:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "ec2.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```

##### Key Points

- Trust policies are attached to **roles**, not users or groups.
    
- They define **who can assume the role**, not what actions the role can perform (that’s the job of the permissions policy).
    
- Without a valid trust policy, no one can assume the role.





#### 4. **Permissions Boundaries**

- These are **advanced policies** used to limit the maximum permissions that a role or user can have. They don’t grant permissions directly but restrict what can be granted by IAM policies.
    
- **Example**: A permissions boundary that limits the actions a user or role can perform, regardless of the IAM policies attached.



#### Example: Permissions Boundary for an IAM Role

Let’s create a permissions boundary that limits the actions a role can perform within a specific EC2 instance type (e.g., `t2.micro`).

**Permissions Boundary Policy**:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:RunInstances",
        "ec2:DescribeInstances"
      ],
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "ec2:InstanceType": "t2.micro"
        }
      }
    }
  ]
}
```

This boundary allows users to launch EC2 instances (`ec2:RunInstances`) or describe EC2 instances (`ec2:DescribeInstances`), but only if the instance type is `t2.micro`.

To apply the permissions boundary to an IAM role:
- When creating the role, you can specify the Permissions Boundary.
- This ensures that the role's permissions are constrained by the boundary, regardless of the permissions granted in the role's identity-based policies.
    

- **Permissions Boundaries**:    
    - Applied to IAM roles or users.
    - Restrict the **maximum** permissions a user or role can have.
    - Do not grant permissions themselves, but limit the scope of permissions granted by identity-based policies.

#### 5. **Service Control Policies (SCPs)**

- These policies are used in **AWS Organizations** to control what actions can be performed across AWS accounts. SCPs are applied at the organizational level and apply to all accounts within the organization.
    
- **Example**: An SCP that prevents the creation of EC2 instances in all accounts within an AWS Organization.


**Service Control Policies (SCPs)** are part of AWS Organizations and allow you to set permission guardrails across your entire AWS Organization. SCPs define what actions can or cannot be performed across AWS accounts within your organization.

SCPs don’t grant permissions directly but set the maximum permissions that can be granted by account-level IAM policies.

#### Example: Deny All `ec2:TerminateInstances` Action

This SCP prevents any account in the organization from terminating EC2 instances, regardless of the permissions assigned to users or roles.

**Service Control Policy (SCP)** to deny EC2 instance termination:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Deny",
      "Action": "ec2:TerminateInstances",
      "Resource": "*"
    }
  ]
}
```

This SCP would be applied at the **organizational unit (OU)** or account level within AWS Organizations to restrict the `ec2:TerminateInstances` action across all accounts in the scope of the policy.

- **Service Control Policies (SCPs)**:
    
    - Applied at the **organization or account** level.
    - Set **global permission boundaries** for accounts within an AWS Organization.
    - Can deny specific actions across multiple accounts or organizational units.

---

### Policy Evaluation:

When a principal (e.g., a user or service) attempts to perform an action, AWS evaluates policies in the following order:

1. **Explicit Deny** (overrides any Allow)
    
2. **Identity-Based Policies** (attached to the user, role, or group)
    
3. **Resource-Based Policies** (attached to the resource, like an S3 bucket)
    
4. **Trust Policies** (if assuming an IAM role)
    
5. **Permissions Boundaries** (if applied)
    
6. **Service Control Policies (SCPs)** (if using AWS Organizations)
    

If any policy explicitly denies the action, it will override any allow. If no deny is found, the allow rules from IAM policies, resource-based policies, and trust policies will be considered to determine if access is granted.

---

### Summary:

- **IAM Policy**: Defines what actions a user, group, or role can perform on AWS resources (permissions).
    
- **Trust Policy**: Defines who can assume an IAM role (assume role permission).
    
- **Hierarchy**: The hierarchy starts with explicit denies and includes IAM policies, resource-based policies, trust policies, and permissions boundaries.



## Here’s a **combined policy for a Lambda function** that:

- Logs to CloudWatch
- Reads from S3
- Writes to DynamoDB

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "logs:CreateLogGroup",
        "logs:CreateLogStream",
        "logs:PutLogEvents"
      ],
      "Resource": "arn:aws:logs:*:*:*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::my-bucket/*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "dynamodb:PutItem",
        "dynamodb:GetItem"
      ],
      "Resource": "arn:aws:dynamodb:us-east-1:123456789012:table/MyTable"
    }
  ]
}
```

