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
Ah, thank you for the clarification! In that case, your original assumption is largely correct.

  

When calling non-AWS APIs (like an email API, weather API, payment gateway, or any external HTTP endpoint), you typically do need to use a Lambda function with Step Functions.

  

Why Lambda is Usually Required for External APIs

  

Step Functions' built-in service integrations are designed specifically for AWS APIs, not generic HTTP endpoints. Here's the breakdown:

  

Direct Options (Limited & Rarely Used)

  

There are two theoretical ways to call external APIs without Lambda, but they're generally not practical:

  

1. API Gateway Proxy Integration

   · You could set up an API Gateway endpoint that proxies to your external API

   · Then use Step Functions' apigateway:invoke integration

   · But this adds complexity - you're just moving the HTTP call to API Gateway instead of Lambda

2. AWS SDK HTTP Client (Very new/advanced)

   · AWS recently added support for generic HTTP requests via arn:aws:states:::aws-sdk:httpclient

   · However, this has major limitations:

     · Limited authentication methods (mainly AWS SigV4 for APIs that support it)

     · No OAuth, API keys, or complex authentication flows

     · Limited error handling compared to Lambda

  

The Practical Solution: Lambda Function

  

For calling an email API (SendGrid, Mailgun, etc.), a Lambda function is the standard and recommended approach:

  

Step Function Definition:

  

```json

{

  "Comment": "Send email via external API",

  "StartAt": "SendEmail",

  "States": {

    "SendEmail": {

      "Type": "Task",

      "Resource": "arn:aws:lambda:us-east-1:123456789012:function:sendEmail",

      "Parameters": {

        "to": "[user@example.com](mailto:user@example.com)",

        "subject": "Your order confirmation",

        "body": "Thank you for your purchase!"

      },

      "Next": "WaitForDelivery",

      "Retry": [

        {

          "ErrorEquals": ["RateLimitExceeded", "ServiceUnavailable"],

          "IntervalSeconds": 5,

          "MaxAttempts": 3,

          "BackoffRate": 2

        }

      ],

      "Catch": [

        {

          "ErrorEquals": ["States.ALL"],

          "Next": "HandleEmailError"

        }

      ]

    }

  }

}

```

  

Lambda Function (Python example):

  

```python

import json

import requests

  

def lambda_handler(event, context):

    # External email API configuration

    api_key = "your-email-api-key"

    email_service_url = "[https://api.emailservice.com/send](https://api.emailservice.com/send)"

    # Prepare the request

    headers = {

        "Authorization": f"Bearer {api_key}",

        "Content-Type": "application/json"

    }

    payload = {

        "to": event['to'],

        "subject": event['subject'],

        "body": event['body']

    }

    try:

        # Call the external API

        response = [requests.post](http://requests.post/)(email_service_url, json=payload, headers=headers)

        response.raise_for_status()  # Raises exception for 4xx/5xx status codes

        return {

            "statusCode": 200,

            "messageId": response.json()['id'],

            "success": True

        }

    except requests.exceptions.RequestException as e:

        # Handle different types of errors appropriately

        if response.status_code == 429:

            raise Exception("RateLimitExceeded")

        elif response.status_code >= 500:

            raise Exception("ServiceUnavailable")

        else:

            raise Exception(f"EmailError: {str(e)}")

```

  

Benefits of Using Lambda for External APIs

  

· Flexible Authentication: Handle API keys, OAuth, JWT tokens, etc.

· Complex Error Handling: Parse API responses and convert to meaningful errors

· Request/Response Transformation: Modify data formats between systems

· Retry Logic: Implement custom retry strategies

· Secrets Management: Use AWS Secrets Manager for API keys securely

  

Summary

  

For external/non-AWS APIs:

  

· ✅ Use Lambda - This is the standard, flexible approach

· ❌ Avoid direct integration - Not practical for most real-world scenarios

  

So your initial assumption was correct for the specific case of external APIs! The confusion often arises because people don't distinguish between AWS service APIs and external HTTP APIs.