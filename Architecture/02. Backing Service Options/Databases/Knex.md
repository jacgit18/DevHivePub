---
tags:
  - databases
  - library
  - QueryBuilder
  - javascript
  - questions
author:
  - jacgit18
Purpose: This documentation discusses Knex.js library.
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
When you run a migration using Knex.js, the library typically checks the current state of the database against the migration files to determine whether any changes need to be applied.  

[https://openbase.com/categories/js/best-javascript-query-builders-libraries](https://openbase.com/categories/js/best-javascript-query-builders-libraries)
  
Here's a simplified process:  
  
1. **Tracking Migrations:** Knex maintains a record of which migrations have been executed in the database. This information is usually stored in a special table (e.g., "knex_migrations").  
  
2. **Comparing Database State:** When you run a migration, Knex compares the migrations that have been applied to the database against the migration files you have in your project. It checks the migration records to see which migrations have already been executed.  
  
3. **Applying Pending Migrations:** Knex then identifies any pending migrations (those not recorded in the database) and applies them in sequence to update the database schema.  
  
This process ensures that your database schema stays in sync with your migration files, allowing you to easily version and manage changes to the database structure over time.  
  
If you attempt to run a migration and there are no new migrations to apply (meaning the database is already up-to-date), Knex will typically indicate that there are no pending migrations. This helps prevent unnecessary or redundant schema modifications.

Be aware of circular references when building data models/schemas and migration files also the order of how you create and insert tables because of table relationship dependencies  

| # | Tablename | Foreign Keys |  |  |  |  |  |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 1 | role |  |  |  |  |  |  |
| 1 | markup | ?? |  |  |  |  |  |
| 1 | action |  |  |  |  |  |  |
| 2 | user | file |  |  |  |  |  |
| 2 | file | ?? | user? |  |  |  |  |
| 3 | company | file | user? |  |  |  |  |
| 3 | payment | ?? | file | user? |  |  |  |
| 4 | company_user | company | user | role |  |  |  |
| 4 | client | company | user? |  |  |  |  |
| 4 | material_type | company | user? |  |  |  |  |


## General Questions
- The ID field in the table always named ID instead of` [tablename]_id`
- Table names as singular?
- To double check -- the db schema represents the current state in MySQL? has it been updated at all since this spreadsheet was created?
- How do we deprecate junction table entries?
- What is our IT budget? Are we planning to be hurting for storage?
- I lean towards adding indexes to almost all frequently used FKs / junction tables if storage isnt an issue
- (enum issue above)
- Performance is better with unspecified text sizes. Are there specific fields where number of chars is critical? If so, I would opt to move checking into API rather than wait for DB error
- Store addresses with more detail?
- What is the "files" table?
- How is "parent_id" being used throughout?
- What is "projects_subcontractors" table? Is this table for subcontractors? What are subcontractors? Are they a type of user?
- For clarity, i usually name FKs as the `[fk table name]_[fk field name]` (e.g. to replace parent_id, type_id, etc...)
- What is the "history" table for?
- Mind if I add some performance monitoring? Doesnt incur much of a cost, and the performance stats are super useful for optimization
- Revisions and Breakdowns both appear to share an ID across types? or is that the ID of that item?
- Wont revisions inherit most of its current FKs from the relevant parent object? Probably dont need to store it
- The tables at the bottom (dcrs, logs, report issues, rates, etc...), do they already exist? Should they be added?

