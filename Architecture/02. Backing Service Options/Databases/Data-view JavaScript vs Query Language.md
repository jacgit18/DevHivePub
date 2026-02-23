---
tags:
  - databases
  - query
  - javascript
  - obsidian
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses obsidian data view.
Status: Refinement
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
DataView.js is a JavaScript library that allows you to work with data efficiently. In DataView.js, query types refer to different methods of retrieving and manipulating data. The two main query types are:

1. **DataView Query Language (DVQL):**
   - DVQL is a domain-specific query language designed for interacting with DataView.js.
   - It provides a structured way to express queries on the underlying data.
   - Queries in DVQL are typically written as strings, following a specific syntax tailored for working with DataView.js.
## Example of DVQL
   
   ``` dataview
   table
   from [[Your Data Note]]
   sort some_column
   ```


2. **DataView JavaScript API:**
   - The DataView JavaScript API involves using JavaScript code to interact with DataView.js.
   - Instead of writing queries in a separate language like DVQL, you use JavaScript functions and methods provided by DataView.js to perform operations on the data.
## Example of Dataview JS

```dataviewjs
dv.span("**🏋️ Exercise 🏋️**")

const calendarData = {
    colors: {
        red: ["#ff9e82","#ff7b55","#ff4d1a","#e73400","#bd2a00",]
    },
    entries: []
}

for(let page of dv.pages('"System Design Thought Process Flow"').where(p=>p.EditDate)){
    calendarData.entries.push({
        date: page.file.name,
        intensity: page.EditDate,
        content: await dv.span(`[](${page.file.name})`), //for hover preview
    })
       
}

renderHeatmapCalendar(this.container, calendarData)
```

**Difference:**
- **Expressiveness:** DVQL is a dedicated query language designed for working with data, offering a specialized syntax for expressing queries. JavaScript, on the other hand, is a general-purpose programming language, providing more flexibility but may require more code for certain operations.

- **Ease of Use:** DVQL is tailored specifically for data queries, making it more concise for certain tasks. JavaScript, being a general-purpose language, might be more verbose for the same operations.

- **Integration:** JavaScript API allows seamless integration with other JavaScript code and libraries. DVQL, being a specific query language, may have limitations in terms of integration with non-DataView.js code.

   ``` dataviewEXAMPLE
   TASK/ LIST field1 /TABLE field1, field2, fieldn
   FROM // Source ""/#
   WHERE // if condition
   FLATTEN field AS F // Metadata manipulation
   WHERE // if condition the flattened array
   GROUP BY // Grouping
   SORT // Sorting
   ```

In summary, DataView Query Language (DVQL) provides a specialized syntax for data queries within DataView.js, while the DataView JavaScript API allows you to interact with DataView.js using JavaScript code, offering more flexibility but potentially requiring more verbosity.