---
tags:
  - cloud
  - CapitalOne
  - bestPractices
  - RTIC
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status:
Started: 2025-02-25
EditDate:
Relates: "[[PTP Config Workflow]]"
Peer Reviewed: 0
dg-publish:
---
LocalStack is a cloud service emulator that enables developers to run AWS applications locally, eliminating the need for a cloud connection. By encapsulating AWS services within a single container, LocalStack streamlines the testing and development process, providing a fast, reliable, and cost-effective environment for local development.

This document provides a step-by-step guide to setting up **AWS Lambda, IAM (Identity and Access Management), and Step Functions** using **LocalStack**, which is a local AWS cloud emulator. The setup is meant for running and testing AWS services locally without needing an actual AWS account.

> [!note] Side Note
> When creating an IAM role in LocalStack, you can ignore the **path** parameter because LocalStack does not enforce IAM role path constraints as AWS does. In AWS, the **path** is an optional parameter used to organize IAM roles within a hierarchical namespace (e.g., `/service-role/` or `/application/`). However, LocalStack simplifies IAM role management and does not require or validate the **path**, making it unnecessary for local development and testing.

This allows for a more streamlined approach when defining IAM roles in LocalStack, reducing complexity and potential errors during local testing. 

#todo/CapitalOne 
- [ ] Post about Localstack and serverless development in AWS
- [ ] [How to Setup AWS Locally Using LocalStack Without Spending a Buck \| by Ben Meehan \| Medium](https://medium.com/@ben.meehan_27368/how-to-setup-aws-locally-using-localstack-without-spending-a-buck-1c6e20bce8)
- [ ] [A guide to using LocalStack — Running AWS Locally \| by Deepika Juneja \| Medium](https://deepikajuneja.medium.com/a-guide-to-using-localstack-running-aws-locally-cd68744e2c94)

Follow [[Managing IAM]] structure when defining json files along with [[Cloud Security Best Practices]]

## 1. Create a Lambda Function  
- Packages a Python script (`lambda-function.py`) into a ZIP file.
- Uses the AWS CLI (configured to connect to LocalStack) to create a Lambda function named `VerifyCustomer`.
- The function is assigned a role (`lambda-role`), which is required for execution permissions.

```sh
zip -r function.zip lambda-function.py // code should have logic to zip itself

aws --endpoint-url=http://localhost:4566 lambda create-function \
    --function-name VerifyCustomer \
    --runtime python3.12 \
    --handler lambda_function.lambda_handler \
    --zip-file fileb://function.zip \
    --role arn:aws:iam::000000000000:role/lambda-role
    --region us-east-1
```

## 2. Create IAM Role
- Creates an IAM role (`lambda-role`) with a trust policy (`trust-policy.json`) to allow Lambda execution.

```sh
aws --endpoint-url=http://localhost:4566 iam create-role \
    --role-name lambda-role \
    --assume-role-policy-document file://trust-policy.json
```

## 3. Attach Policy to IAM Role
- Attaches a policy (`policy.json`) to the IAM role.
- Ensures that Lambda has the necessary permissions.
- **Inline policies** (via `put-role-policy`) are used **less frequently**, usually for **one-off role-specific permissions**.
- **In real-world scenarios**, managed policies (via `attach-role-policy`) are more common because they allow **better scalability and maintainability**.
```sh
aws --endpoint-url=http://localhost:4566 iam put-role-policy \
    --role-name lambda-role \
    --policy-name lambda-policy \
    --policy-document file://policy.json
```

```sh
aws --endpoint-url=http://localhost:4566 iam attach-role-policy \
    --role-name lambda-role \
    --policy-arn arn:aws:iam::000000000000:policy/lambda-policy
```

## 4. Verify Policy Attached to IAM Role
- Lists attached policies for the `lambda-role` to confirm that permissions are set correctly.

```sh
aws --endpoint-url=http://localhost:4566 iam list-attached-role-policies \
    --role-name lambda-role
```

## 5. Create a DynamoDB Table
- Sets up a local DynamoDB table (`Offers`) with `OfferId` as the primary key.
```sh
aws --endpoint-url=http://localhost:4566 dynamodb create-table \
    --table-name Offers \
    --attribute-definitions AttributeName=OfferId,AttributeType=S \
    --key-schema AttributeName=OfferId,KeyType=HASH \
    --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5
```

## 6. Create and Update Data Lambda Function
- Packages and updates a second Lambda function (`DataLambda`) responsible for processing data.
```sh
cd /Users/cal141/rtjg/LocalStack/lambdas/DataLambda
zip -r DataLambda.zip data_lambda.py

aws --endpoint-url=http://localhost:4566 lambda update-function-code \
    --function-name DataLambda \
    --zip-file fileb://DataLambda.zip
```


## 7. Define Your State Machine

Create a **state machine definition file** (e.g., `collections-process-offers-enrollment.asl.json`). This file defines the **workflow logic**, such as which Lambda functions are invoked, whether you have conditions, retries, or parallel states. Example structure (simplified):

```json
{
    "Comment": "Enrollment State Machine",
    "StartAt": "VerifyCustomer",
    "States": {
        "VerifyCustomer": {
            "Type": "Task",
            "Resource": "arn:aws:lambda:us-east-1:000000000000:function:VerifyCustomer",
            "Next": "ProcessData"
        },
        "ProcessData": {
            "Type": "Task",
            "Resource": "arn:aws:lambda:us-east-1:000000000000:function:DataLambda",
            "End": true
        }
    }
}
```
### Step 1: Deploy the Step Function to LocalStack

Run the following command to **update or create the state machine using LocalStack**.

```bash
aws --endpoint-url=http://localhost:4566 stepfunctions update-state-machine \
    --state-machine-arn arn:aws:states:us-east-1:000000000000:stateMachine:EnrollmentStateMachine \
    --definition file://collections-process-offers-enrollment.asl.json
	--logging-configuration '{"level": "ALL", "includeExecutionData": true,
	"destinations": [{"cloudWatchLogsLogGroup": {"logGroupArn":  
	"arn:aws:logs:us-east-1:000000000000:log-group:/aws/states/  
	collections-process-rtic-offers-enrollment"}}]}'
```

- This assumes you already have a state machine called `EnrollmentStateMachine`.
- If you're **creating it for the first time**, you'd run:

```bash
aws --endpoint-url=http://localhost:4566 stepfunctions create-state-machine \
    --name EnrollmentStateMachine \
    --definition file://collections-process-offers-enrollment.asl.json \
    --role-arn arn:aws:iam:: 000000000000:role/state-machine-execution-role  
	--logging-configuration '{"level": "ALL", "includeExecutionData": true,
	"destinations": [{"cloudWatchLogsLogGroup": {"logGroupArn":  
	"arn:aws:logs:us-east-1:000000000000:log-group:/aws/states/  
	collections-process-rtic-offers-enrollment"}}]}'
```

The `role-arn` must match your LocalStack IAM role.



### Step 2: Test the Step Function

Once the state machine is updated/created, you can **trigger it with an input file** (like `input.json`).

```bash
aws --endpoint-url=http://localhost:4566 stepfunctions start-execution \
    --state-machine-arn arn:aws:states:us-east-1:000000000000:stateMachine:EnrollmentStateMachine \
    --input file://input.json
```



### Step 3: Monitor Execution

To check the execution status, you can list and describe executions.

```bash
aws --endpoint-url=http://localhost:4566 stepfunctions list-executions \
    --state-machine-arn arn:aws:states:us-east-1:000000000000:stateMachine:EnrollmentStateMachine
```

```bash
aws --endpoint-url=http://localhost:4566 stepfunctions describe-execution \
    --execution-arn <execution-arn>
```

---

### Summary of Components

|Component|Example|
|---|---|
|**Lambda Function 1**|`VerifyCustomer`|
|**Lambda Function 2**|`DataLambda`|
|**DynamoDB Table**|`Offers`|
|**IAM Role**|`lambda-role`|
|**Step Function**|`EnrollmentStateMachine`|
|**State Machine Definition**|`collections-process-offers-enrollment.json`|
|**Execution Input**|`input.json`|

---

### Overall Flow

1. `EnrollmentStateMachine` starts.
2. It invokes `VerifyCustomer`.
3. If successful, it invokes `DataLambda`.
4. `DataLambda` processes data, maybe interacts with DynamoDB (`Offers` table).
5. Execution completes.


## 8. Update Step Functions State Machine
- Updates an AWS Step Functions state machine (`EnrollmentStateMachine`) using a definition file (`collections-process-offers-enrollment.json`).

```sh
aws --endpoint-url=http://localhost:4566 stepfunctions update-state-machine \
    --state-machine-arn arn:aws:states:us-east-1:000000000000:stateMachine:EnrollmentStateMachine \
    --definition file://collections-process-offers-enrollment.json
```


## 9. Test Step Function Execution
- Starts an execution of the `EnrollmentStateMachine` with an input file (`input.json`). 

```sh
aws --endpoint-url=http://localhost:4566 stepfunctions start-execution \
    --state-machine-arn arn:aws:states:us-east-1:000000000000:stateMachine:EnrollmentStateMachine \
    --input file://input.json
```

## **10. List IAM Roles**

```sh
aws iam list-roles --endpoint-url=http://localhost:4566
```


## **11. Delete IAM Roles**

```sh
aws iam delete-policy --policy-arn arn:aws:iam::aws:policy/MyCustomPolicy --endpoint-url=http://localhost:4566
```


## **12. Debug IAM Roles**

```sh
aws iam get-role --role-name LambdaExecutionRole --endpoint-url=http://localhost:4566
```



### **Purpose of This Setup**

This setup is used to locally develop and test an AWS-based workflow involving:

- Lambda functions (for processing customer data).
- IAM roles and policies (for managing permissions).
- DynamoDB (as a database for storing offers).
- Step Functions (for orchestrating multi-step processes).

By using **LocalStack**, developers can simulate AWS services without incurring costs or requiring internet access.

