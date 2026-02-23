---
tags:
  - schema
  - systemDesign
  - databases
  - data
  - dataTables
  - dataEngineering
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses fact tables.
Status: Refinement
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
As a data engineer, understanding business requirements and data sources is paramount in choosing the appropriate type of fact table. Here are guidelines to aid in this decision:

##### General Guidelines for Fact Table Design

![[Association Relationship.png]]


1. **Identify the Grain:**
   - Determine the level of detail (grain) needed in the fact table, such as transaction, daily, or monthly data, based on business requirements.

2. **Type of Measurement:**
   - Differentiate between `additive` and `semi-additive` measures. Additive measures can be summed across dimensions, while semi-additive measures may vary in aggregation across dimensions.

3. **Number of Dimensions:**
   - Consider the number of dimensions in the fact table. A few dimensions may suit a simple fact table, while many dimensions may necessitate a more complex design like a snowflake schema.

4. **Frequency of Updates:**
   - Evaluate the frequency of updates to the fact table. Frequent updates may favor a simpler design, while infrequent updates might benefit from a more complex structure.

5. **Level of Aggregation:**
   - Assess the required level of aggregation. Summary fact tables may be suitable for high-level data, while transactional fact tables offer more detailed analysis.

### Fact Table Types and Use Cases:

![[Aggregation and Composition.png]]

1. **Transact Fact Table:**
   - Ideal for detailed, transaction-level data.
   - Well-suited for additive measures like sales revenue.
   - Larger in size, with no frequent updates.

2. **Periodic Snapshot Fact Table:**
   - Suited for tracking non-aggregated data over time, e.g., hospital bed status.
   - Smaller than transact tables, with no updates.

3. **Accumulating Snapshot Fact Table:**
   - Appropriate for tracking processes at scale, like shipping phases in large-scale operations.
   - Smallest in size, with updates after specific milestones.

### Advantages of Fact Table Integration:

1. **Eliminating Redundancy:**
   - Minimize data redundancy by efficiently linking surrogate keys in fact tables to related attributes in dimension tables.

2. **Improved Accessibility:**
   - Leverage the fact table as a central integration point for enhanced accessibility to diverse data across dimension tables.

### Role-Playing Dimensions:

- **Definition:**
   - Role-playing dimensions represent different views of the same underlying data, based on the context of analysis.

- **Benefits:**
   - Simplifies the data model by avoiding redundant tables.
   - Enhances query flexibility by providing different perspectives on the same data.

- **Suitability:**
   - Suitable for dimension tables with hierarchical structures or context-specific attributes.

In summary, fact table selection depends on specific business needs, considering factors like granularity, measurement type, dimension count, update frequency, and aggregation requirements. By carefully evaluating these aspects, data engineers can make informed decisions for effective data warehousing.


### Navigating Multiple Fact Tables in a Schema

**Possibility of Multiple Fact Tables:**
- Indeed, a schema can host multiple fact tables in a data warehouse, each containing distinct measures such as sales, revenue, or customer interactions.
- Example: A retail company may have separate fact tables for sales and inventory data, connected through common dimensions like product, store, and time.

**Benefits and Considerations:**
- Multiple fact tables enhance data analysis complexity, facilitating in-depth insights and report creation.
- Design precision is crucial to ensure well-defined relationships and efficient query execution within the schema.

**Fact Tables vs. Dimensional Tables Ratio:**
- While less common, having more fact tables than dimensional tables is feasible based on the nature and complexity of the analyzed data.
- Example: In a customer relationship management system, various fact tables for different interactions may share a common dimensional table for customer data.

**Schema Design Principles:**
- Emphasizes designing a schema that mirrors data relationships and hierarchy while optimizing query efficiency.