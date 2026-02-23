---
tags:
  - schema
  - databases
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: Draft
Started: 
EditDate: 2024-03-11
Relates: 
Peer Reviewed: 0
---



| *Users* |               |           | FK  | FK table name | Primary | Length | Allow Null | Default             |
| ------- | ------------- | --------- | --- | ------------- | ------- | ------ | ---------- | ------------------- |
|         | user_id       | UUID      | 0   |               | 1       |        | N          | AUTO                |
|         | is_archive    | BOOLEAN   | 0   |               | 0       |        | Y          | FALSE               |
|         | email         | TEXT      | 0   |               | 0       | 100    | N          | None                |
|         | first_name    | TEXT      | 0   |               | 0       | 50     | N          | None                |
|         | last_name     | TEXT      | 0   |               | 0       | 50     | N          | None                |
|         | phone         | TEXT      | 0   |               | 0       | 20     | Y          | None                |
|         | file_id       | UUID      | 1   | file          | 0       |        | N          | None                |
|         | password      | TEXT      | 0   |               | 0       | 100    | N          | None                |
|         | date_created  | TIMESTAMP | 0   |               | 0       |        | N          | 0000-00-00 00:00:00 |
|         | date_modified | TIMESTAMP | 0   |               | 0       |        | N          | 0000-00-00 00:00:00 |





| *Company* |  |  | FK | FK table name | Primary | Length | Allow Null | Default |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
|  |  |  |  |  |  |  |  |  |
|  | company_id | UUID | 0 |  | 1 |  | N | AUTO |
|  | address | TEXT | 0 |  | 0 |  | Y | None |
|  | is_archive | BOOLEAN | 0 |  | 0 |  | Y | FALSE |
|  | file_id | UUID | 1 | file | 0 |  | N | None |
|  | name | TEXT | 0 |  | 0 | 150 | N | None |
|  | phone | TEXT | 0 |  | 0 | 20 | Y | None |
|  | type | ENUM | 0 |  | 0 |  | N | None |
|  | created_by | UUID | 1 | user? | 0 |  | N | None |
|  | date_created | TIMESTAMP | 0 |  | 0 |  | N | 0000-00-00 00:00:00 |
|  |  |  |  |  |  |  |  |  |




