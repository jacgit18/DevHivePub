---
cssclasses:
  - cards
---

 `BUTTON[daily-note]` 🪷  `BUTTON[weekly-note]`


- ### Annual Goals #mcl/list-card 
	```dataviewjs
	
	let goals = dv.pages('"_Review/Goals"'); 
	
	dv.table(["Goal", "Target", "Progress", "Deadline"], 
	
		goals.map(goal => [
			
			 `<div style="position: relative; overflow: hidden; width: 100%; height: 200px;"> <img src="${goal.banner}" alt="Banner" style="object-fit: cover; object-position: center; width: 100%; height: 100%;"> <div style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></div> 
			 
			 </div>`, `<span style="font-size: 1.1em;">${goal.file.link}</span>`, 
			 
			 goal.deadline, 
			 
			 `<progress value="${goal.progress}" max="${goal.target}"></progress><br>${Math.round((goal.progress / goal.target) * 100)}% completed` ]) ); 
			 
			 dv.container.classList.add("cards-align-top");
	```
---

---

```meta-bind-button
style: primary
label: Open Daily Note
hidden: true
id: daily-note
action:
  type: command
  command: daily-notes
```

```meta-bind-button
style: primary
hidden: true
label: Open Weekly Note
id: weekly-note
action:
  type: command
  command: periodic-notes:open-weekly-note
```