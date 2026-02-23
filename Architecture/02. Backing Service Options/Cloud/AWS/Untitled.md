# **Common Serverless Services & Their Permissions**

## Key Principles

- **Least Privilege**: Only grant the permissions necessary for a specific function.
    
- **Service Roles**: Each Lambda (or other service) should have its **own role**.
    
- **Policy Attachment**: Permissions are attached via **IAM Policies** which are linked to IAM **Roles**.
    

## **Lambda Permissions**

When Lambda interacts with other services, it needs permissions. Common examples:

|Service|Example Actions|
|---|---|
|**DynamoDB**|`dynamodb:GetItem`, `dynamodb:PutItem`, `dynamodb:Query`, `dynamodb:UpdateItem`, `dynamodb:Scan`|
|**S3**|`s3:GetObject`, `s3:PutObject`, `s3:DeleteObject`, `s3:ListBucket`|
|**CloudWatch Logs**|`logs:CreateLogGroup`, `logs:CreateLogStream`, `logs:PutLogEvents`|
|**SQS**|`sqs:SendMessage`, `sqs:ReceiveMessage`, `sqs:DeleteMessage`|
|**Step Functions**|`states:StartExecution`, `states:DescribeExecution`|
|**EventBridge (CloudWatch Events)**|`events:PutEvents`|

### **Example Inline Policy for Lambda (Basic CRUD on DynamoDB + Logs)**

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "dynamodb:GetItem",
                "dynamodb:PutItem",
                "dynamodb:UpdateItem",
                "dynamodb:DeleteItem",
                "dynamodb:Scan"
            ],
            "Resource": "arn:aws:dynamodb:us-east-1:123456789012:table/MyTable"
        },
        {
            "Effect": "Allow",
            "Action": [
                "logs:CreateLogGroup",
                "logs:CreateLogStream",
                "logs:PutLogEvents"
            ],
            "Resource": "arn:aws:logs:us-east-1:123456789012:log-group:/aws/lambda/*:*"
        }
    ]
}
```

### Lambda Execution Role (Serverless)

Permissions for a **Lambda function** to work with other services.

**Common Actions:**

```json
"Action": [
    "logs:CreateLogGroup",
    "logs:CreateLogStream",
    "logs:PutLogEvents",
    "s3:GetObject",
    "s3:PutObject",
    "dynamodb:PutItem",
    "dynamodb:GetItem"
]
```

**Common Resources:**

- `arn:aws:logs:*:*:*`
    
- `arn:aws:s3:::my-bucket/*`
    
- `arn:aws:dynamodb:region:account-id:table/MyTable`
    

---

## **API Gateway Permissions**

API Gateway itself doesn’t need permissions unless you're using **IAM-based authorization** for endpoints. However, if you want to allow API Gateway to trigger a Lambda, ensure:

- Lambda has a **resource-based policy** allowing API Gateway to invoke it.
    

### Example Lambda Resource Policy (Allow API Gateway to Invoke)

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "apigateway.amazonaws.com"
            },
            "Action": "lambda:InvokeFunction",
            "Resource": "arn:aws:lambda:us-east-1:123456789012:function:MyFunction"
        }
    ]
}
```

### API Gateway Execution (Serverless)

If Lambda needs to be invoked by API Gateway.

**Common Actions:**

```json
"Action": [
    "apigateway:Invoke",
    "lambda:InvokeFunction"
]
```

**Common Resources:**

- `arn:aws:apigateway:*::/restapis/*/stages/*`
    
- `arn:aws:lambda:region:account-id:function:*`
    

---

## **DynamoDB Permissions**

When Lambda interacts with DynamoDB, typical permissions include:

- `dynamodb:GetItem`
    
- `dynamodb:PutItem`
    
- `dynamodb:Query`
    
- `dynamodb:UpdateItem`
    
- `dynamodb:Scan`
    
- `dynamodb:DeleteItem`
    

### Example Policy for DynamoDB Full Access to Table

```json
{
    "Effect": "Allow",
    "Action": "dynamodb:*",
    "Resource": "arn:aws:dynamodb:us-east-1:123456789012:table/MyTable"
}
```

**Common Resources:**

- `arn:aws:dynamodb:region:account-id:table/MyTable`
    

---

## **S3 Permissions**

For serverless apps handling file uploads/downloads:

- `s3:GetObject`
    
- `s3:PutObject`
    
- `s3:DeleteObject`
    
- `s3:ListBucket`
    

### Example S3 Bucket Access Policy

```json
{
    "Effect": "Allow",
    "Action": [
        "s3:GetObject",
        "s3:PutObject",
        "s3:DeleteObject"
    ],
    "Resource": "arn:aws:s3:::my-bucket-name/*"
},
{
    "Effect": "Allow",
    "Action": "s3:ListBucket",
    "Resource": "arn:aws:s3:::my-bucket-name"
}
```

**Common Resources:**

- `arn:aws:s3:::my-bucket`
    
- `arn:aws:s3:::my-bucket/*`
    

---

## **Step Functions Permissions**

If Lambda triggers or interacts with Step Functions:

- `states:StartExecution`
    
- `states:DescribeExecution`
    

### Example Step Functions Policy

```json
{
    "Effect": "Allow",
    "Action": [
        "states:StartExecution",
        "states:DescribeExecution"
    ],
    "Resource": "arn:aws:states:us-east-1:123456789012:stateMachine:MyStateMachine"
}
```

**Common Resources:**

- `arn:aws:states:region:account-id:stateMachine:MyStateMachine`
    

---

## **EventBridge (CloudWatch Events) Permissions**

For Lambda to publish custom events:

- `events:PutEvents`
    

### Example EventBridge Policy

```json
{
    "Effect": "Allow",
    "Action": "events:PutEvents",
    "Resource": "arn:aws:events:us-east-1:123456789012:event-bus/default"
}
```

**Common Resources:**

- `arn:aws:events:region:account-id:rule/MyRule`
    

---

## **Logging Permissions**

### Example CloudWatch Logs Policy

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
    }
  ]
}
```


All Lambda functions need permissions to write logs.

**Common Actions:**

```json
"Action": [
    "logs:CreateLogGroup",
    "logs:CreateLogStream",
    "logs:PutLogEvents"
]
```

**Common Resources:**

- `arn:aws:logs:*:*:*`


