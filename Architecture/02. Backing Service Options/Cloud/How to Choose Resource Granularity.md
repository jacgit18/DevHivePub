---
tags:
  - cloud
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses choosing Resource Granularity.
Status: Refinement
Started: 
EditDate: 2024-03-07
Relates: 
Peer Reviewed: 0
dg-publish: false
---
**Unlocking Cost Explorer's Capabilities:**
- Resource granularity in AWS Cost Explorer provides insight into EC2 instances, enabling identification of specific cost-incurred resources.
- Leverage time selection, filtering, and grouping features to focus on cost and usage details of specific workloads efficiently.

**Understanding Amazon EC2 Instances:**
- An Amazon EC2 instance is a virtual server within Amazon's Elastic Compute Cloud (EC2), designed for running applications on AWS infrastructure.

**Mapping Domain Entities to Resources:**
- Directly mapping domain entities to resources may lead to inefficient and inconvenient resources.
- Consider criteria such as network efficiency, representation size, and client convenience to determine appropriate granularity for resources.

**Guidelines for Resource Granularity:**
- Utilize network efficiency, representation size, and client convenience as guiding factors for resource granularity decisions.
- Evaluate scenarios in your application to identify nouns of different granularity, assessing factors like user data, activity streams, friends, and followers.

**Client-Centric Approach:**
- Design resources based on what a typical client for your web service does.
- Consider whether coarse-grained resources encapsulating all data or less coarse-grained resources for specific data elements are more suitable based on client needs.

**Example Scenarios:**
- For a social network application, decide resource granularity based on client behaviors and preferences.
- In cases like a user with an address, consider factors like proxy HTTP cache efficiency and client/server interaction chattiness to determine resource granularity.

**Considerations Beyond Database Tables:**
- Mapping database tables or object models directly to resources may not always yield optimal results.
- Design resources to align with clients' usage patterns, focusing on HTTP's uniform interface for network-based interactions.

**Factors Influencing Resource Granularity:**
- Evaluate factors like cacheability, frequency of change, and mutability to refine resource granularity.
- Separating cacheable, less frequently changing, or immutable data from other types can enhance efficiency for both clients and servers.

**Client and Network Perspectives:**
- Determine candidate resources and their granularity by considering client perspectives and network requirements.
- Look at factors such as cacheability, frequency of change, and mutability to ensure an optimal balance between client convenience and network efficiency.