---
tags:
  - databases
  - scalability
  - query
  - sharding
  - data
  - distributedSystem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Database Sharding.
Status: Refinement
Started: 
EditDate: 2024-03-28
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Database Sharding.jpeg]]

Database sharding is a technique used in database management to improve scalability and performance by horizontally partitioning data across multiple databases or servers. The term "sharding" comes from the concept of dividing a larger object into smaller, manageable pieces or shards. This approach is particularly useful in handling large datasets and high transaction volumes.

Database sharding is typically used when a single database becomes a bottleneck due to increased data volume or high transaction loads. It helps distribute data across multiple servers, improving performance and scalability. Use sharding when you need to handle large datasets, high traffic, or when horizontal scaling is necessary for your application.

![[Database Sharding.gif]]

Here's an explanation of key aspects of database sharding:

1. **Horizontal Partitioning:**
   - Sharding involves splitting a large database into smaller, more manageable parts. Each shard contains a subset of the data, and collectively, the shards hold the entire dataset.
   - The division is typically based on a specific criterion, such as ranges of values, specific regions, or other logical criteria depending on the application's requirements.

2. **Distribution Across Servers:**
   - Each shard is placed on a separate server or node. This distribution across multiple servers allows the system to distribute the workload and queries, preventing a single server from becoming a bottleneck.
   - Servers can be added or removed dynamically as the database grows or shrinks, providing flexibility in managing resources.

3. **Improved Performance:**
   - Sharding enhances read and write performance by distributing the data and query load across multiple servers. This helps in parallel processing of queries and reduces contention for resources.
   - With sharding, each shard can handle a subset of the overall query workload, leading to improved response times.

4. **Scalability:**
   - Sharding is a key strategy for horizontal scalability. As data volume increases, additional shards and servers can be added to the system to handle the growing load.
   - Horizontal scalability is particularly advantageous in cloud environments, where resources can be dynamically provisioned based on demand.

5. **Consistent Hashing:**
   - To ensure an even distribution of data across shards and prevent hotspots, consistent hashing algorithms are often employed. These algorithms provide a deterministic way of mapping data to specific shards, ensuring a balanced distribution.
   - Consistent hashing helps maintain a relatively even distribution of data even when the number of shards changes.

6. **Challenges:**
   - While sharding offers significant benefits, it also introduces challenges. Data distribution needs to be carefully planned, and considerations must be made for maintaining consistency, handling joins across shards, and ensuring proper data migration when scaling.

7. **Use Cases:**
   - Sharding is commonly employed in scenarios where traditional vertical scaling (adding more resources to a single server) becomes impractical due to data growth and performance demands. Web applications with massive user bases, e-commerce platforms, and large-scale analytics systems often adopt sharding for improved scalability.

In summary, database sharding is a technique that distributes a large database across multiple servers or nodes to improve scalability and performance. It's a powerful strategy for handling large datasets and high transaction volumes, commonly employed in modern, high-demand applications. However, it requires careful planning and consideration of data distribution, consistency, and scalability requirements.

Data sharding differs from traditional partitioning in that it involves splitting data based on rows rather than columns. Each shard operates independently, handling its subset of data and processing queries in parallel with other shards.

### Horizontal Partitioning Strategies

There are different types of partitioning methods, including:  
  
1. **Range Partitioning:** Data is partitioned based on a range of values, such as date ranges or numeric ranges.  
2. **List Partitioning:** Data is partitioned based on a predefined list of values, such as categories or regions.  
3. **Hash Partitioning:** Data is partitioned based on a hash function applied to a specific column, distributing rows evenly across partitions.  
4. **Composite Partitioning:** Data is partitioned using a combination of multiple partitioning methods.


> Sharding can refer to both horizontal and vertical partitioning of a database, and the distinction lies in how the data is divided.


1. **Horizontal Sharding (Sharding by Rows):**
   - This is the more common understanding of sharding. In horizontal sharding, the dataset is divided based on rows of data. Each shard contains a subset of the entire dataset, and the division is typically done based on a specific criterion like ranges of values, geographic regions, or other logical criteria.
   - The goal is to distribute the workload and queries across multiple servers or nodes, improving parallel processing and scalability.

2. **Vertical Sharding (Sharding by Columns):**
   - In vertical sharding, the dataset is divided based on columns of data rather than rows. Each shard contains a subset of columns, representing a specific aspect of the data.
   - This division is often used when certain columns are accessed more frequently than others, and it allows for more efficient storage and retrieval of data based on the access patterns.
   - Vertical sharding is less common than horizontal sharding but can be a useful strategy in certain scenarios.

**Comparison:**

- **Horizontal Sharding:**
  - **Focus:** Divides data across servers based on rows.
  - **Use Case:** Often used for distributing large datasets, improving parallel processing, and handling high transaction volumes.
  - **Example:** Sharding a user database based on geographical regions.

- **Vertical Sharding:**
  - **Focus:** Divides data across servers based on columns.
  - **Use Case:** Used when certain columns are accessed more frequently than others, optimizing for specific access patterns.
  - **Example:** Storing frequently accessed columns (e.g., user profiles) on one server and less frequently accessed columns on another.

Both horizontal and vertical sharding can be employed independently or in combination, depending on the specific needs and characteristics of the application. The choice between them depends on factors such as the data distribution patterns, access patterns, and scalability requirements of the system.