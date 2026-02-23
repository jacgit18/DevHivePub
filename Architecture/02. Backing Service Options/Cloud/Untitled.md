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
Here are examples of **hard failures** and **soft failures** in **AWS Step Functions**, along with how to handle them:

  

---

  

### **1. Hard Failures (Terminal Errors)**

Hard failures are **unrecoverable** errors that cause the execution to stop immediately. AWS Step Functions marks these as `Failed` with an error like `States.Runtime`, `States.Timeout`, or `States.TaskFailed`.

  

#### **Example: Hard Failure (Lambda Timeout)**

```json

{

  "Comment": "A Step Function with a hard failure (Lambda timeout)",

  "StartAt": "ProcessData",

  "States": {

    "ProcessData": {

      "Type": "Task",

      "Resource": "arn:aws:lambda:us-east-1:123456789012:function:ProcessData",

      "TimeoutSeconds": 3,  // Lambda times out after 3 seconds

      "End": true

    }

  }

}

```

**What happens?**  

- If the Lambda function runs longer than `TimeoutSeconds`, Step Functions throws a `States.Timeout` error.  

- Execution **fails terminally** (no automatic retries).  

  

**How to handle?**  

- Use `Catch` to route failures (e.g., to a cleanup task).  

- Example `Catch` block:

  ```json

  "Catch": [{

    "ErrorEquals": ["States.Timeout"],

    "Next": "HandleTimeout"

  }]

  ```

  

---

  

### **2. Soft Failures (Retryable Errors)**

Soft failures are **transient** errors (e.g., throttling, temporary downtime) that can be retried. Step Functions uses the `Retry` field to automatically retry the task.

  

#### **Example: Soft Failure (DynamoDB Throttling)**

```json

{

  "Comment": "A Step Function with soft failure handling (retries)",

  "StartAt": "WriteToDynamoDB",

  "States": {

    "WriteToDynamoDB": {

      "Type": "Task",

      "Resource": "arn:aws:states:::dynamodb:putItem",

      "Parameters": {

        "TableName": "MyTable",

        "Item": {"ID": {"S": "123"}}

      },

      "Retry": [{

        "ErrorEquals": ["DynamoDB.ThrottlingException"],

        "IntervalSeconds": 1,

        "MaxAttempts": 3,

        "BackoffRate": 2

      }],

      "End": true

    }

  }

}

```

**What happens?**  

- If DynamoDB throttles the request (`DynamoDB.ThrottlingException`), Step Functions retries **3 times** with exponential backoff.  

- Only fails permanently if all retries are exhausted.  

  

**Common Retryable Errors:**  

- `Lambda.ServiceException` (AWS Lambda issues)  

- `States.ALL` (Retry any error)  

  

---

  

### **Key Differences**

| Feature          | Hard Failure                     | Soft Failure                     |

|------------------|----------------------------------|----------------------------------|

| **Outcome**      | Execution stops immediately      | Retries automatically            |

| **Error Types**  | `States.Timeout`, `States.TaskFailed` | `DynamoDB.ThrottlingException`, `Lambda.ServiceException` |

| **Handling**     | Requires `Catch`                 | Uses `Retry`                     |

  

---

  

### **Best Practices**

1. **For Hard Failures**: Always `Catch` critical errors to log or trigger fallback workflows.  

2. **For Soft Failures**: Configure `Retry` with `BackoffRate` to avoid overwhelming systems.  

3. **Monitor**: Use CloudWatch to track `ExecutionsFailed` metrics.  

  

Would you like a real-world use case (e.g., order processing with failure handling)?