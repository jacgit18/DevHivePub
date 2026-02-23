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
# **Serverless IAM Role Best Practices**

## **Separate Roles per Function**

Don’t reuse roles across different Lambdas unless they have **identical permission needs**.

## **Use Wildcards Sparingly**

Only allow `*` in development or if truly necessary.

## **Monitor with CloudTrail**

Log who/what changed roles/policies.

## **Review Periodically**

Use tools like **AWS IAM Access Analyzer** to detect over-privileged roles.

## **Use Conditions**

Restrict by source IP, VPC, or even request tags when possible.

---

# **AWS CLI Example - Attach Policy to Role**

```sh
aws iam attach-role-policy \  
    --role-name MyLambdaRole \  
    --policy-arn arn:aws:iam::aws:policy/AWSLambdaBasicExecutionRole
```

# **AWS CLI Example - Inline Policy (Full Example)**

```sh
aws iam put-role-policy \  
    --role-name MyLambdaRole \  
    --policy-name MyInlinePolicy \  
    --policy-document file://policy.json
```

Where `policy.json` is the JSON document (like the examples above).

---

# **Summary Table - Common AWS Managed Policies for Serverless**

|Policy Name|Description|
|---|---|
|**AWSLambdaBasicExecutionRole**|CloudWatch Logs permissions for Lambda|
|**AWSLambdaDynamoDBExecutionRole**|Basic Lambda + DynamoDB permissions|
|**AmazonS3ReadOnlyAccess**|Read-only S3 access|
|**AWSLambdaVPCAccessExecutionRole**|Lambda VPC network permissions|
|**CloudWatchFullAccess**|Full access to CloudWatch (logs, metrics, etc.)|
|**AmazonEventBridgeFullAccess**|Full EventBridge permissions|

---

# **Understanding ARN Structure**

In an **AWS IAM policy's `Resource` ARN**, the part **after the region** usually represents the **account ID** followed by the **specific resource type and name**.

## **General ARN Format**

```sh
arn:aws:<service>:<region>:<account-id>:<resource-type>/<resource-name>
```

---

## **Example Breakdown - DynamoDB Table**

```sh
arn:aws:dynamodb:us-east-1:123456789012:table/MyTable
```

|Section|Example|Description|
|---|---|---|
|**Service**|`dynamodb`|Service (DynamoDB)|
|**Region**|`us-east-1`|Region|
|**Account ID**|`123456789012`|AWS Account ID|
|**Resource Type**|`table`|Resource type (table in this case)|
|**Resource Name**|`MyTable`|Name of the specific resource|

---

## **Examples by Service**

|Service|Example ARN|Explanation|
|---|---|---|
|**Lambda Function**|`arn:aws:lambda:us-east-1:123456789012:function:MyFunction`|`function` type with name `MyFunction`|
|**S3 Bucket**|`arn:aws:s3:::my-bucket-name`|Buckets only use the bucket name (no account ID)|
|**S3 Object**|`arn:aws:s3:::my-bucket-name/my-folder/my-object.txt`|Objects append the key (path)|
|**DynamoDB Table**|`arn:aws:dynamodb:us-east-1:123456789012:table/MyTable`|Table named `MyTable`|
|**Step Function**|`arn:aws:states:us-east-1:123456789012:stateMachine:MyStateMachine`|State Machine|
|**EventBridge Rule**|`arn:aws:events:us-east-1:123456789012:rule/MyRuleName`|Rule named `MyRuleName`|
|**SQS Queue**|`arn:aws:sqs:us-east-1:123456789012:MyQueue`|Queue named `MyQueue`|

---

## **In Short**

✅ **Immediately after the region is the AWS Account ID.**  
✅ **Then comes the resource type (table, function, bucket, etc.).**  
✅ **Finally, the resource name (MyTable, MyFunction, MyBucket, etc.).**

---

## **How to Find the Right ARN**

You can find the full ARN in:

- **AWS Console** (each service usually shows the ARN somewhere in the UI)
    
- **AWS CLI** with describe commands (e.g., `aws lambda get-function`)
    
- **CloudFormation Outputs** (if you deploy resources via IaC)