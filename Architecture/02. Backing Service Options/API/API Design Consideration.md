---
tags:
  - API
  - SoftwareDesign
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses potential design choice for an API.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[1716391309164.gif]]


#todo/Low/Dev 
- [ ] https://medium.com/api-center/api-design-practice-7fce69e6336c

### **Get-and-Set**
*A fundamental approach in API design, comprising two operations:*
- **Get:** Equivalent to CRUD's Read, returns the most recent resource value, null if non-existent.
- **Set:** The omnibus create/update/delete, also known as last-write-wins. Set the resource to the provided value. If the provided value is null, delete it. If two differing set operations arrive concurrently, pick a “latest” to win. Optionally, also return its previous value. 

Most file-service APIs natively follow this pattern. For example, indexing workflows, such as indexing database objects into ElasticSearch, follow this model. 

### **Get-and-Patch**
For resources that are divisible into multiple fields that can be updated separately, get-and-set can be easily expanded into a slightly different pattern. Get-and-Patch consists of two operations: 
- **Get:** Same as Get from Get-and-Set.
- **Patch:** Enables updating specific resource fields, with missing fields retaining existing values.
 This pattern is used extensively for our configuration service APIs. JSON Patches are an example of this as well. 


### **Timestamp-Checked**
For applications that follow the three-step read-compute-update pattern or otherwise require transactions or protection from concurrent edits, use logical clocks to allow for optimistic concurrency. 

In addition to each resource’s current value, store a timestamp of the most recent write to that resource. Then expose two operations: 

- **Read-Return-Timestamp:** Similar to Get but returns the timestamp of the most recent write.
- **Write-Check-Timestamp:**  Similar to Set, but in addition to providing the new value, also provide the timestamp that the client first read the resource. If the resource’s service-side timestamp matches the provided timestamp, execute the write and return the new timestamp. If the timestamps are different, reject the write and return the service’s value so that the client may rerun its computation and resubmit an updated value. 

- Considered a variant of Check-and-Set (CAS), used in Firebase's Firestore API.

Like most optimistic concurrency patterns, this approach has limitations; if expected concurrency is too high or if clients have expensive computations, this could result in too much lost work in retries. In these cases, it may be best to pick a different pattern and add transactional APIs around it. 

### **Append-Only-Log**

- Ideal for applications with defined edits or limited direct client interaction:
    - **Read-Return-Timestamp:** Retrieves the current value and timestamp.
    - **Append-Return-Updated:** Defines edit operations; clients apply one, and the updated value is returned.
    - **Load-Since-Timestamp:** Optionally retrieves edit operations since a specified timestamp.

- Applied in advanced scenarios like Operational Transforms and CRDT-based applications.

**Considerations**

- Noteworthy points about the patterns:
    - Search and re-ACL/hard-delete operations are common and not pattern-specific.
    - Patterns are not mutually exclusive; an API can combine operations from different patterns.

- CRUD has its place, particularly when the creation/destruction of a resource is significant or when extensive validation is required.

[Source](https://techbeacon.com/security/critical-api-security-risks-10-best-practices#:~:text=The%20most%20critical%20API%20security,and%20insufficient%20logging%20and%20monitoring).