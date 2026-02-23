---
tags: 
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
### IAM Role Example: Lambda Role to Access S3

1. **Trust Policy**: Defines who can assume the IAM role. In this case, the Lambda service is allowed to assume this role.
    

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "sts:AssumeRole",
      "Principal": {
        "Service": "lambda.amazonaws.com"
      }
    }
  ]
}
```

- **Explanation**: The **trust policy** allows the **AWS Lambda service** to assume this role using the `sts:AssumeRole` action. This is necessary for Lambda to execute and access resources.
    

2. **Permissions Policy**: Defines the actions the role is allowed to perform once assumed. In this case, it allows Lambda to read from an S3 bucket.
    

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-secure-bucket/*"
    }
  ]
}
```

- **Explanation**: The **permissions policy** grants the role the ability to perform the `s3:GetObject` action on objects within the S3 bucket `my-secure-bucket`. This is required if the Lambda function needs to read files from the bucket.
    

### IAM Role Creation Example in AWS CLI:

To create this IAM role via the AWS CLI, you can use the following commands:

1. **Create Trust Policy JSON** (saved as `trust-policy.json`):
    

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "sts:AssumeRole",
      "Principal": {
        "Service": "lambda.amazonaws.com"
      }
    }
  ]
}
```

2. **Create Permissions Policy JSON** (saved as `permissions-policy.json`):
    

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-secure-bucket/*"
    }
  ]
}
```

3. **Create IAM Role with AWS CLI**:
    

```bash
aws iam create-role --role-name LambdaS3AccessRole \
  --assume-role-policy-document file://trust-policy.json
```

4. **Attach Permissions Policy to IAM Role**:
    

```bash
aws iam put-role-policy --role-name LambdaS3AccessRole \
  --policy-name LambdaS3ReadPolicy \
  --policy-document file://permissions-policy.json
```

### Role Usage:

Once the IAM role is created, you can associate it with an AWS Lambda function. The Lambda function will then have the necessary permissions to access the S3 bucket as defined in the permissions policy.

