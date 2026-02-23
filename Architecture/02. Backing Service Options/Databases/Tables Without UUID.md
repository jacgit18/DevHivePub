---
tags:
  - databases
  - tables
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses database tables without UUID.
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
Tables where you might not need a UUID as a primary key are typically those with straightforward structures and clear natural keys. Natural keys are columns that already exist in the real-world data and can uniquely identify each record without the need for an artificially generated identifier like a UUID. Here are a few examples:

1. **Lookup Tables:**
   - If you have a simple lookup table with a small, fixed set of values, such as a table for country codes, where the country code itself can serve as a natural key.

   ```sql
   CREATE TABLE Country (
       country_code CHAR(2) PRIMARY KEY,
       country_name VARCHAR(255)
   );
   ```

2. **Configuration Tables:**
   - Tables that store configuration settings might not need a UUID if the configuration key itself is unique.

   ```sql
   CREATE TABLE Configuration (
       config_key VARCHAR(255) PRIMARY KEY,
       config_value VARCHAR(255)
   );
   ```

3. **Logging Tables:**
   - In some logging tables, especially those recording events with a timestamp, the combination of timestamp and other contextual information might be sufficient for uniqueness.

   ```sql
   CREATE TABLE Log (
       log_timestamp TIMESTAMP PRIMARY KEY,
       log_message VARCHAR(255)
   );
   ```

4. **Audit Tables:**
   - Tables that capture audit trails might not need a UUID if the combination of the user ID and the timestamp guarantees uniqueness.

   ```sql
   CREATE TABLE AuditTrail (
       user_id INT,
       action VARCHAR(255),
       timestamp TIMESTAMP,
       PRIMARY KEY (user_id, timestamp)
   );
   ```

Remember, the decision to use or not use a UUID depends on the specific requirements of your application, the nature of the data, and the database design principles you follow.