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
# Why Catch Blocks Can't Be Used in Choice States in AWS Step Functions  
  
In AWS Step Functions, you cannot use `Catch` blocks in `Choice` states because of fundamental differences in how these state types operate:  
  
## Key Reasons:  
  
1. **Non-Retryable Nature**: Choice states are purely decision-making constructs that don't perform actions that could fail in a way that would require error handling.  
  
2. **Deterministic Evaluation**: Choice states evaluate conditions to route workflow execution - they don't execute external services or code that might throw exceptions.  
  
3. **State Type Limitations**: AWS Step Functions explicitly defines which state types can have `Catch` blocks (Task, Parallel, Map) - Choice isn't one of them.  
  
## Workaround Options:  
  
If you need error handling around choices:  
1. **Use a Task State before the Choice** to perform any operations that might fail  
2. **Structure your workflow** so the Choice follows a Task that can handle errors  
3. **Use input processing** to validate data before it reaches the Choice state  
  
## Example of Proper Structure:  
  
```json  
"States": {  
"ValidateInput": {  
"Type": "Task",  
"Resource": "arn:aws:lambda:...",  
"Catch": [{  
"ErrorEquals": ["States.ALL"],  
"Next": "HandleError"  
}],  
"Next": "MakeChoice"  
},  
"MakeChoice": {  
"Type": "Choice",  
"Choices": [  
{  
"Variable": "$.status",  
"StringEquals": "success",  
"Next": "SuccessState"  
}  
],  
"Default": "DefaultState"  
}  
}  
```  
  
This design separates the error-prone operation (in the Task state) from the purely logical Choice state.