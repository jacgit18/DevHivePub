---
cssclasses:
  - dashboard
banner: "![[Hive Banner.gif]]"
banner_y: 0.494
banner_x: 0.5
dg-home: true
dg-publish: true
---
<div class="title" style="color:#FFC300"; text-shadow: 0 0 10px rgba(255, 195, 0, 0.8);>Hive Mind Dashboard</div>

`BUTTON[daily-note]` 🪴 `BUTTON[weekly-note]` 🪴 `BUTTON[light-mode, dark-mode]` 🪴 `BUTTON[tasks]`
> [!multi-column]
> 
> ```dataviewjs
> let goals = dv.pages('"Review/Goals"');
> dv.table(["Goal", "Deadline", "Progress"],
>     goals.map(goal => [
>         `<span style="font-size: 1.2em;">${goal.file.link}</span>`,
>         goal.Deadline,
>         `<progress value="${goal.progress}" max="${goal.target}"></progress><br>${Math.round((goal.progress / goal.target) * 100)}% completed`
>     ])
> );
> dv.container.classList.add("cards-align-top");
> ```
> 
> ```dataviewjs
> const pages = dv.pages('"Review/Daily"')
>   .where((p) => "Writing" in p || "Workout" in p || "Reading" in p)
>   .sort((p) => p.file.day, "desc")
>   .map((p) =>
>     Object.create({
>       link: p.file.link,
>       day: p.file.day,
>       Writing: p.Writing,
>       Workout: p.Workout,
>       Reading: p.Reading,
>     })
>   );
> function getStreak(validate) {
>   let count = 0;
>   for (const note of pages) {
>     if (validate(note)) count++;
>     else break;
>   }
>   return count;
> }
> function getRecord(validate) {
>   let record = 0;
>   let count = 0;
>   for (const note of pages) {
>     if (validate(note)) {
>       count++;
>       record = Math.max(record, count);
>     } else {
>       count = 0;
>     }
>   }
>   return record;
> }
> const done = "✅";
> const skip = "🟥";
> const fileRows = pages
>   .filter((p) => p.day >= moment().subtract(1, "w"))
>   .sort((p) => p.day)
>   .map((note) => [
>     note.link,
>     note.Writing ? done : skip,
>     note.Workout ? done : skip,
>     note.Reading ? done : skip,
>   ]);
> const writing = [
>   getStreak((note) => note.Writing),
>   getRecord((note) => note.Writing),
> ];
> const workout = [
>   getStreak((note) => note.Workout),
>   getRecord((note) => note.Workout),
> ];
> const reading = [
>   getStreak((note) => note.Reading),
>   getRecord((note) => note.Reading),
> ];
> dv.table(
>   ["Habits", "✍🏼", "💪🏼", "📖"],
>   [
>     ...fileRows,
>     ["‎"],
>     ["**Streak**", writing[0], workout[0], reading[0]],
>     ["**Record**", writing[1], workout[1], reading[1]],
>   ]
> );
> ```

---
- ### Satisfaction #mcl/list-card 
	```dataviewjs  
	dv.span("**🏋️ Proudness 🏋️**")  
	const calendarData = {  
	colors: {  
	greeny: ["#B3FFD9", "#99FFC2", "#66FFB2", "#33FF99", "#00CC66"]
	},  
	entries: []  
	}  
	for(let page of dv.pages('"Review/Daily"').where(p=>p.Proudness)){  
	calendarData.entries.push({  
	date: page.file.name,  
	intensity: page.Proudness,  
	content: await dv.span(`[](${page.file.name})`), //for hover preview  
	})  
	}  
	renderHeatmapCalendar(this.container, calendarData) 
	```

---


---

> [!success]+ Remember
> **Even if we only did what we were capable of, we'd astound ourselves.** 
> 
> ***Start with small, incremental steps to establish a foundation. Gradually build a consistent rhythm and sustain it over time. Once you’re comfortable, repeat the process until you can move fluidly. From there, adapt and alternate your tempo as needed to match the demands of the task at hand.***

- #### Projects #mcl/list-card 
    - [[Project 1]]
    - [[Project 2]]
    - [[project 3]]
        - Collaboration 
- #### Learning & System
    - [[00 Home|Learning Goal 1]]
    - [[00 Home|Initiative 1]]
    - [[00 Home|Initiative 2]]
- #### Personal
    - **[[Goal Dashboard|Goals]]**
    - **[[Tasks Calendar|Calendar]]**


> [!multi-column]
> > [!summary] Recently Created
>>  ```dataview
> list
> from ""
> Sort file.ctime DESC
> limit 7
> 
>> [!Todo] Recently Updated
>>  ```dataview
>> 	list
>> 	from ""
>> 	Sort file.mtime DESC
>> 	limit 7
>>```
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
```meta-bind-button
style: destructive
label: View Tasks
hidden: true
id: tasks
action:
  type: command
  command: card-board:open-card-board-plugin-0
```
---

```meta-bind-button
style: destructive
label: Light Mode
id: light-mode
hidden: true
actions:
  - type: command
    command: theme:use-light
```
```meta-bind-button
style: primary
label: Dark Mode
id: dark-mode
hidden: true
actions:
  - type: command
    command: theme:use-dark
```


<button onclick="window.location.href='obsidian://open?vault=DevBrain&page=%5B%5B_Architecture%20Dashboard%5D%5D'">Architecture Dashboard</button>

[[_Architecture Dashboard]]

#todo/Low/Dev 
- [ ] Fix button so you don't need backlink
- [ ] Create dashboard for other folders using dataview queries.
- [ ] Create more Moc pg With data view queries

### To Access Full Vault
[Join the Hive](https://docs.google.com/forms/d/e/1FAIpQLSc-NvwAUS2e3dndizHwgbqrldnfTFBD74E_zAIPJtd7fZyQjg/viewform)
# Vault Info


- 🔖 Tagged:  favorite 
 `$=dv.list(dv.pages('#favorite').sort(f=>f.file.name,"desc").limit(10).file.link)`
- 〽️ Stats
	-  File Count: `$=dv.pages().length`
	

# The List
- 💻 Dev Quest
	- [ ] [[Dev Roadmaps By Priority#Main Long Quest | Main Quest]]
	- [ ] [[Dev Roadmaps By Priority#New Path | New Path of Exploration]]
	- [ ] [[Dev Roadmaps By Priority#Side Quest Revist |  Side Quest]]

