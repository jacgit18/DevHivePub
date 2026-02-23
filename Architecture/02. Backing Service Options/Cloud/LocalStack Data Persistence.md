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
Relates: 
Peer Reviewed: 0
dg-publish:
---
In **LocalStack**, you should avoid setting **persistence to 0** for any service where you need data to persist between restarts. Here are some key services where persistence matters:

### **1. DynamoDB**
- **Avoid setting persistence to 0** if you're testing locally and want to keep your database records across LocalStack restarts.
- **Fix:** Enable persistence by using:
    
    ```bash
    export DATA_DIR=/tmp/localstack/data
    ```

### **2. S3**
- If persistence is disabled, uploaded files will be lost when LocalStack restarts.
- **Fix:** Use the `DATA_DIR` setting or mount a volume in Docker.

### **3. Step Functions**
- Without persistence, execution history and state machine definitions will be lost after restart.
- **Fix:** Set a **data directory** for LocalStack to store state machine data.

### **4. SQS & SNS**
- Messages in queues or topics will be wiped out if persistence is off.
- **Fix:** Store messages by enabling persistence.

### **How to Enable Persistence in LocalStack**
To keep data even after a restart, start LocalStack with:

```bash
export DATA_DIR=/tmp/localstack/data
```

or in **Docker Compose**:

```yaml
services:
  localstack:
    image: localstack/localstack
    environment:
      - DATA_DIR=/var/lib/localstack
    volumes:
      - "./localstack_data:/var/lib/localstack"
```

### **When Is It OK to Disable Persistence?**
- If you **only need ephemeral testing** (e.g., running tests in CI/CD).
- If data persistence isn't needed (e.g., temporary S3 file uploads).
- If you want to reset state easily between test runs.





 