---
tags:
  - query
  - obsidian
author:
  - jacgit18
  - chatgpt
Purpose: This documentation highlights the most common views of data view.
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
DataView in Obsidian supports various types of views that allow you to visualize and manipulate structured data within your notes. The primary views include:

1. **Table View:**
   - The table view is the most common and versatile DataView view. It displays data in a table format, allowing you to sort, filter, and organize information effectively.


   ``` dataview
   table
   from [[Your Data Note]]
   sort some_column
   ```

2. **List View:**
   - The list view is useful for creating lists of items based on your structured data.


   ``` dataview
   list
   from [[Your Data Note]]
   ```


3. **Task View:**
	- a task view that allows you to work with tasks and to-do items within your notes.

``` dataview
task
from [[Your Tasks Note]]

```


4. **Calendar View:**
   - The calendar view displays your data in a calendar format, allowing you to visualize events over time.


   ``` dataview
   calendar
   from [[Your Data Note]]
   ```
