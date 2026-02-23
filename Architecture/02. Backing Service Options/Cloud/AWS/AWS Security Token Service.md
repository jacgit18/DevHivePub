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
### What is `sts:AssumeRole`?

`sts:AssumeRole` is an **AWS Security Token Service (STS)** action that lets a trusted **entity** (user, service, or application) **temporarily assume an IAM role**. When successful, it returns **temporary security credentials** (access key, secret key, session token) to act as the role and access resources based on the role's **permissions policy**.

---

### Why is `sts:AssumeRole` Important?

- Provides **temporary permissions** for AWS services (e.g., Lambda, EC2, cross-account access).
- Supports **temporary, limited-privilege credentials**, which are more secure than long-lived credentials.
- Enables **cross-account access** by allowing one account to assume a role in another.

---

### Example Scenario

A **Lambda function** in **Account A** needs to read objects from an **S3 bucket in Account B**. Account B creates a role with S3 read permissions and a **trust policy** that allows Account A’s Lambda to assume the role. The Lambda calls:

```bash
aws sts assume-role --role-arn "arn:aws:iam::account-b-id:role/S3ReadOnlyRole" --role-session-name "LambdaSession"

```

Response:
```json
{ 
  "Credentials": {
        "AccessKeyId": "ASIA...",
        "SecretAccessKey": "secret...",
        "SessionToken": "token..."
    }
}
```

The Lambda can now **use these temporary credentials** to access the S3 bucket.

---

### Key Point

`sts:AssumeRole` requires:

1. The **trust policy** allowing the calling entity to assume the role.
2. The calling entity must have **permission** to invoke `sts:AssumeRole` on the role.


