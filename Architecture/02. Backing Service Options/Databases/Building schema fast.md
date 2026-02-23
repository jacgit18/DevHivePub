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
1. **Table Naming and Structure:**  
- Begin by naming the main table.  
- Optionally, start with one large table while also identifying what columns make sense to index and then decompose it into smaller tables for better organization.  
  
2. **High-Level Relationships:**  
- Define key relationships, such as suppliers selling to or buying from customers, and customers using products. Identify one-to-one relationships.  
  
3. **Table IDs and Associations:**  
- Assign unique identifiers (IDs) to tables.  
- Establish associations with other relevant IDs.  
- Create additional tables as needed to support these associations.  
  
4. **Dimension and Fact Tables:**  
- Consider the distinction between dimension and fact tables.  
- Factor in table dependencies and how they relate to one another.  
  
5. **Schema Selection:**  
- Choose between a snowflake schema for large data or a star schema for small, simple data.  
  
6. **Fact Tables and Descriptive Dimension Tables:**  
- Begin with fact tables to capture statistical data, providing an overarching view.  
- Surround these fact tables with descriptive dimension tables to provide context and detail.  
  
This structured approach ensures a systematic and comprehensive development of the database schema, addressing key considerations such as relationships, table structure, and schema design.