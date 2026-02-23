---
tags:
  - loadBalancer
  - distributedSystem
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: Refinement
Started: 2024-03-28
EditDate: 
Relates: "[[Load Balancer]]"
Peer Reviewed: 0
dg-publish:
---
Consistent hashing is a technique used in distributed computing and storage systems to efficiently distribute data across multiple nodes while minimizing the need for data redistribution when nodes are added or removed from the system. It's particularly useful in scenarios where the number of nodes in the system can change dynamically, such as in large-scale web services or distributed databases.

Here's how consistent hashing works:

1. **Hashing Data and Nodes**: Each data item and each node in the system is mapped to a point on a fixed-size hash ring using a hash function. The hash function converts input values into numerical values, typically within a predetermined range.

2. **Data Placement**: When storing or retrieving data, the same hash function is applied to the data's key to determine its position on the hash ring. Similarly, each node is also hashed to a position on the ring.

3. **Locating Nodes**: To find which node is responsible for storing or handling a particular data item, the system traverses the hash ring in a clockwise direction starting from the position of the data item until it encounters the first node. That node is considered responsible for the data item.

4. **Adding or Removing Nodes**: When a node/server is added or removed from the system, only a portion of the data needs to be remapped. Since each node's position on the hash ring determines its responsibility for a range of hash values, adding or removing a node affects only the data items that fall within the ranges assigned to that node and its immediate neighbors on the ring. The majority of the data remains unaffected, minimizing the need for data movement and redistribution.

5. **Load Balancing**: Consistent hashing tends to distribute data evenly across nodes, resulting in a balanced load distribution and preventing hotspots where certain nodes become overwhelmed with requests while others remain underutilized.

By using consistent hashing, distributed systems can achieve efficient data distribution and scalable performance, even in dynamic environments where nodes may join or leave the system frequently. This makes consistent hashing a fundamental technique in building robust and scalable distributed systems.


This relates to [[System Design Interview An Insider’s Guide Volume 1.pdf#page=71&selection=0,36,4,51|System Design Interview An Insider’s Guide Chapter 5]] 

> Consistent hashing is widely used in real-world systems, including some notable ones:
> • Partitioning component of Amazon’s Dynamo database [3] 
> • Data partitioning across the cluster in Apache Cassandra [4] 
> • Discord chat application [5] 
> • Akamai content delivery network [6] 
> • Maglev network load balancer [7]

[[System Design Interview An Insider’s Guide Volume 1.pdf#page=85&selection=10,0,15,34|System Design Interview An Insider’s Guide, page 85]]