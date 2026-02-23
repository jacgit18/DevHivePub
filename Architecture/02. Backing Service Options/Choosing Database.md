---
tags:
  - databases
  - systemDesign
  - systemComponent
  - data
  - dataEngineering
author:
  - jacgit18
  - chatgpt
Purpose: Guide to selecting a database.
Status: Refinement
Started: 
EditDate: 2024-01-02
Relates: "[[Choosing Schema]]"
Peer Reviewed: 0
dg-publish:
---
![[Structured vs Unstructured Data.webp]]

Information can exist in both structured and unstructured forms. Refined information often refers to structured data, which is organized and formatted for specific purposes. Unrefined or unstructured data lacks a predefined format and organization or less of a predefined format that doesn't fit the standards of structured data.

Then you have Semi-structured data which is data that does not fit neatly into the traditional structured model (like relational databases with fixed schemas) but has some level of structure. It may contain elements of both structured and unstructured data.

![[Pasted image 20240429084212.png]]

Examples of semi-structured data include JSON (JavaScript Object Notation), XML (eXtensible Markup Language), and key-value pairs. These data formats allow for flexibility in representing information, and the structure can vary between different records. Databases that handle semi-structured data effectively are NoSQL databases. 

[[5 V's of Data]]

When selecting a database or determining the number of databases for your architecture, it's crucial to first identify the nature of your data—whether it's [[Industry Structured & Unstructured Data |structured or unstructured]]. Once this is clarified, you can narrow down your choices between SQL and NoSQL databases. For instance, if you anticipate dealing with a substantial amount of email data, opting for a NoSQL database becomes more likely.

Furthermore, leveraging the CAP theorem can help refine your database selection further. The CAP theorem addresses the trade-offs between Consistency, Availability, and Partition Tolerance, aiding in making informed decisions based on your specific application requirements and priorities. Another consideration could be using [[Cloud Databases]].



![[CAP.png]]
### **CAP Theorem and Fundamental Differences:**
The CAP Theorem, representing Consistency, Availability, and Partition Tolerance, asserts that in database systems, achieving all three elements simultaneously is not possible. These components are pivotal in shaping a database's performance characteristics, and the selection of an appropriate combination is crucial based on specific requirements. Here's a breakdown of these elements:

1. **Consistency:**
   - In the context of the CAP Theorem, consistency ensures uniformity of data throughout the system. This is especially critical in scenarios where precision, such as in banking or high-stakes transactions, is paramount.

2. **Availability:**
   - Availability concerns users' ability to read and write data, even when faced with network failures. It underscores uninterrupted access to the system, regardless of network issues.

3. **Partition Tolerance:**
   - Partition tolerance indicates the system's ability to function seamlessly, even if segments of the network are offline. It ensures the system remains operational despite potential disruptions.

The CAP Theorem aids in making informed decisions when selecting a database system, necessitating a careful consideration of trade-offs among these three factors. Relational databases, while providing consistency, often lack partition tolerance and high availability, leading to potential downtime during updates.

Side note this relates to [[System Design Interview An Insider’s Guide Volume 1.pdf#page=97&selection=0,36,27,10|Inconsistency resolution: versioning]]

#### When Choosing between CAP this what you should consider:

- **AP Systems (Partition Tolerance + Availability):** Examples include CouchDB, Cassandra, and DynamoDB. These prioritize partition tolerance and availability, accepting eventual consistency as data replicates across machines.

- **CA Systems (Consistency + Availability):** Examples include traditional relational databases like MySQL, PostgreSQL, and Oracle Database. Suited for scenarios where maintaining data consistency is critical, coupled with a high level of availability, commonly used in applications such as financial systems.

- **CP Systems (Partition Tolerance + Consistency):** Examples include MongoDB, HBase, and Redis. These focus on partition tolerance and consistency, ensuring accuracy at the expense of immediate availability.

## ACID(SQL) Principles vs BASE(NOSQL) Principles
### SQL
 SQL, a domain-specific language for relational databases, ensures robustness through ACID principles:

1. **Atomicity:** Transactions are indivisible, committing all changes or none to maintain transaction integrity.

2. **Consistency:** Guarantees that transactions transition the database between valid states, upholding integrity constraints.

3. **Isolation:** Allows concurrent transactions, ensuring each appears executed in isolation to prevent interference.

4. **Durability:** Committed transactions persist permanently, surviving failures, providing reliability even in adverse conditions.

![[ACID.gif]]
### NoSQL
NoSQL, diverse in data models, embraces BASE principles, offering flexibility and scalability:

1. **Basically Available:**
    - The system remains operational, prioritizing basic availability even during failures, ensuring continued read and write operations.
    - This may temporarily sacrifice consistency under specific conditions.

2. **Soft State:**
    - Allows mutable or "soft" state, permitting the system's adaptable and scalable state to change over time, even inconsistently across nodes.

3. **Eventually Consistent:**
    - Guarantees that, given time and no further updates, all data replicas converge to a consistent state.
    - Accepts temporary inconsistencies, resolving them gradually for adaptability in distributed environments.


![[DB Popularity.png]]

The term NoSQL encompasses various non-relational databases, with four main types: key-value, document, wide-column, and graph databases.

- **Key-Value Stores:** In key-value databases like Redis and DynamoDB, data is stored in pairs comprising a unique identifier and a corresponding data value. The inherent flexibility allows values to accommodate varying amounts of unstructured data. Tailored for rapid retrieval of unstructured information, these databases find application in caching, user preference storage, and situations where simplicity is prioritized. They prove particularly effective for session management, user preferences, and personalized product recommendations.

- **In-memory Key-Value Stores:** Distinguished by storing data predominantly in memory rather than on disk, these databases, exemplified by Redis, Memcached, and Amazon Elasticache, prioritize rapid access times by eliminating disk-related delays. However, the in-memory nature poses a potential data loss risk during process or server failures. To mitigate this, in-memory databases adopt strategies like storing operations in logs or taking snapshots, allowing for data persistence on disks while maintaining the advantages of swift memory-based retrieval.

- **Document Databases:** Document databases, exemplified by MongoDB and CouchDB, share a structure akin to key-value databases. However, in this context, keys and values are encapsulated within documents formatted in markup languages like JSON, XML, or YAML. This approach proves invaluable for agile development and diverse data types, making it well-suited for applications such as user profiles, product catalogs, and content management where flexible data storage is paramount.

- **Wide-Column Stores:** Wide-column databases, such as Cassandra and HBase, depart from strict column formats, allowing flexibility in data representation. Rows aren't obligated to have values in every column, enabling amalgamation of diverse data formats within rows and columns. This architecture proves beneficial for scenarios involving telemetry, analytics, messaging, and time-series data with known queries and substantial data volumes, ensuring swift retrieval of specific data segments.

- **Graph Databases:** Designed for illustrating multidimensional relationships, suitable for social networks, fraud detection, and recommendation engines (e.g., Neo4j, JanusGraph, Amazon Neptune, Cosmos DB through Azure Gremlin).

- **Multimodal Databases:** Often referred to as `NewSQL`, multimodal databases seamlessly integrate various data models within a single system, enabling the storage and retrieval of diverse data types like text, images, and graphs. Unlike traditional databases specializing in a single data model, exemplars like ArangoDB and OrientDB offer a unified platform adept at handling the complexity of modern data structures. This adaptability proves invaluable for applications requiring a comprehensive approach to data, where diverse information needs to be interconnected and analyzed collectively. Platforms like Azure Cosmos DB further exemplify this concept, supporting multiple models, including document data and graph databases, allowing users to choose the most suitable model for their specific application needs within a unified database service.
#### Unique Use Case Databases

- **Time Series Databases:** Specialized in organizing data chronologically, time series databases arrange information in time-ordered streams based on collection or ingestion timestamps. Unlike conventional sorting by value or ID, these databases prioritize temporal sequencing. Widely applied in industrial telemetry, DevOps, and Internet of Things (IoT) scenarios, they facilitate efficient analysis of time-sensitive data. Notable examples encompass Graphite, Prometheus, and Amazon Timestream, each tailored for managing and querying time-based datasets.

- **Ledger Databases:** Operating on log-based principles, ledger databases, such as Amazon Quantum Ledger Database (QLDB), meticulously record events associated with data values. These databases serve the crucial function of storing data changes, ensuring the integrity and immutability of the recorded information. Widely applied in domains like banking systems, registrations, supply chains, and systems of record, ledger databases provide a transparent and auditable trail of data modifications, reinforcing the reliability of the stored information.

- **Spatial Databases:** Spatial databases, such as PostGIS and Oracle Spatial, specialize in storing and querying spatial or geographical data. They extend traditional databases to handle location-based information, offering spatial indexing and geometric operations. Designed for applications like GIS (Geographic Information Systems) and location-based services, spatial databases excel in managing geographical data such as maps, points of interest, and spatial relationships. Their capabilities empower users to perform spatial queries, analyze proximity, and support a wide range of geospatial applications, from mapping to urban planning.

- **Vector Databases:** Vector databases, like Tile38 and Google's Bigtable, organize data as vectors or geometric shapes. Leveraging the power of vector representation, these databases excel in handling geospatial data with precision and efficiency. They are particularly suited for applications requiring real-time tracking, navigation systems, and dynamic mapping. By storing and processing vector data, these databases enable seamless manipulation of spatial information, making them essential for scenarios where accurate location-based insights and quick updates are crucial, such as logistics optimization and geospatial analytics.

![[Database Types.gif]]
##### **Final Determination: Project Evaluation - Time, Money, Tech**

When deciding between NoSQL and SQL databases, assess the team's expertise, project complexity, and economic factors. Consider the following:

##### **1. Time Considerations:**
- **Team Expertise:** Leverage Agile developers for quicker NoSQL development; opt for mature SQL for complex queries.
  
##### **2. Economic Considerations:**
- **Cost of Training:** Evaluate training costs, factoring in the learning curve.
- **Server Scaling:** Consider [[Vertical vs Horizontal Scaling |scalability]] costs, especially when integrating NoSQL into an existing system.
- **Overall System Complexity:** Assess the overall complexity and associated costs.

##### **3. Tech Considerations:**
- **Transactional Integrity:** Prioritize relational databases for critical transactional integrity.
- **Project Complexity:** Evaluate tools needed and project complexity.
- **Talent Availability:** Weigh the availability of talent and associated hiring/training costs.

### **Final Determination: Choosing Between NoSQL and SQL**
![[Database Selection Process.webp]]

![[Database requirement.png]]
#### **NoSQL Databases:**
- **Scalability:** Ideal for horizontal scalability, cost-effective for growing datasets.
- **Flexibility:** Suited for rapid development, handling semi/unstructured data.
- **High Performance:** Superior in certain use cases with high-volume read/write operations.

#### **SQL Databases:**
- **Structured Data:** Well-suited for predefined structured data, ensuring integrity.
- **ACID Compliance:** Adheres to ACID properties, crucial for strict data consistency.
- **Mature Ecosystem:** Well-established with a wide range of tools and expertise.
- **Catalogs:** SQL Database have a catalogs which refers to a schema or system that stores metadata about the database itself. It contains information about tables, views, indexes, and other database objects. The catalog serves as a data dictionary, providing details about the structure, relationships, and properties of the database elements. This metadata is crucial for query optimization, data integrity, and overall management of the database system. Not all databases have catalogs in the traditional sense such as NoSQL databases.

#### **Decision Factors:**
- **Project Requirements:** Consider scalability, flexibility, and performance (NoSQL) or data consistency and a mature ecosystem (SQL).
- **Data Structure:** For well-structured, relational data, opt for SQL; choose NoSQL for flexible models.
- **Workload Analysis:** Heavy read/write operations may favor NoSQL's performance advantages. Evaluate the performance characteristics of the database. Understand read and write patterns, latency requirements, and query complexities. Test the database's performance under realistic conditions.
- **Security and Compliance:** Prioritize security features, encryption options, and compliance with data protection regulations relevant to your industry (e.g., GDPR, HIPAA).
- **Future Roadmap and Vendor Lock-In:** Consider the future development roadmap of the database and whether it aligns with your application's long-term needs. Be cautious of potential vendor lock-in and evaluate the portability of your data.

>[!node]
>Side note if you use other databases like an H2 in embedded mode it can help in terms of running a database in a restricted environment like TD bank but it restricts the access of the database to external services that you may want to connect to

#### Conclusion:
The choice hinges on your project's unique needs. Factors like scalability, data structure, and workload should guide the decision-making process.

