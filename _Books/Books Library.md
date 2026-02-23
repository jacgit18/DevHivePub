---
tags:
  - 📚Books
author:
  - jacgit18
Purpose: This documentation is a early stage book tracker using dataview.js
Status: Refinement
Started: 
EditDate: 2024-03-07
Relates: 
Peer Reviewed: 0
---
## To Read
```dataview
Table without id  pdf as Name, author as Author, ("![|30](" + cover + ")") as Cover, pages, category as genre, rating, Priority, Read From "_Pdf/Books Tracker" Where contains(Read, null)
```

## Completed

```dataview
Table without id  pdf as Name, author as Author, ("![|30](" + cover + ")") as Cover, pages, category as genre, rating, Priority, Read From "_Pdf/Books Tracker" Where contains(Read, true)
```


```dataview
Table without id Title From "_Pdf/Books/Architecture/Building Microservices Designing Fine Grained Systems" Where has(Title)
```




```dataview
Table
from [[Your New Filename.pdf]]
where contains(Published)

```






```dataview
Table tester from outgoing([[Book Dir]])
```