---
tags:
  - web
  - HTTP
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Post request.
Status: Done
Started: 
EditDate: 2024-01-29
Relates: 
Peer Reviewed: 0
dg-publish: false
---
## **POST Method: Creating Resources**

The POST method is used to send data to the server. The Content-Type header indicates the body type. Requests are not cached and won't be in browser history. No data length restriction.

- **Create (Add)**: Ensures creation unless exists; fails if the resource already exists. If conflicting create operations occur simultaneously, at least one must fail.

- **When to Use POST**:
  - Create a new resource.
  - Modify resources via a controller resource.
  - Run queries with large inputs.
  - Perform unsafe or [[Idempotent#^43c387 |nonidempotent]] operations when other HTTP methods are not suitable.
  - POST is generally unsafe and not idempotent.

## How to Implement Asynchronous Tasks with POST

HTTP, being synchronous and stateless, doesn't mandate immediate processing of client requests. For tasks that can be processed asynchronously, such as a banking application's account transfer, utilize the following method:

1. **Handling POST Requests:**
   Upon receiving a POST request, create a new resource and respond with a status code 202 (Accepted), providing a representation of the new resource. This resource allows clients to track the status of the asynchronous task, including relevant information like time estimates.

2. **GET Request to Task Resource:**
   - If the task is still processing, return response code 200 (OK) with the current status.
   - On successful completion, respond with code 303 (See Other) and a Location header containing the URI of a resource showing the outcome.
   - In case of task failure, return code 200 (OK) along with a representation of the task resource indicating failure. Clients must read the body for failure reasons.

3. **Example - Image Processing Web Service:**
   Consider an image-processing web service for tasks like file conversions, OCR, and image cleanup. Clients upload images, and processing time varies. After completion, clients can view/download processed images.

4. **POST Method for Controller Resources:**
   - Clients use the POST method to invoke function-oriented controller resources, providing headers and a body as inputs.
   - POST is semantically open-ended, ideal for pairing with unrestricted controller resources.
   - Reserved for operations not intuitively mapped to core HTTP methods.

5. **POST Method Characteristics:**
   - Unsafe and non-idempotent, implying unpredictable outcomes and non-guaranteed repeatability without undesirable side effects.
   - POST should not be used for getting, storing, or deleting resources; specific HTTP methods exist for these functions.
   - Controller resources prioritize flexibility over transparency and robustness.

6. **Example POST Request:**
   - `POST /alerts/245743/resend`: Illustrates triggering a controller operation, akin to a runtime system's "PostMessage" mechanism, invoking functions across boundaries.


