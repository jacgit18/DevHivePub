---
Writing: false
Workout: false
Reading: false
Proudness: 1
---
## <% moment(tp.file.title,'YYYY-MM-DD').format("dddd, MMMM DD, YYYY") %>


<< [[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD').subtract(1, 'd').format('YYYY-MM-DD') %>|Yesterday]] | [[<% fileDate = moment(tp.file.title, 'YYYY-MM-DD').add(1, 'd').format('YYYY-MM-DD') %>|Tomorrow]] >>



> [!info]+ Productivity
> ```meta-bind
> INPUT[progressBar( minValue(0), maxValue(10)):Proudness]

---

> [!danger]+ Habit Tracker
> Writing: `INPUT[toggle(title(Writing)):Writing]` Workout: `INPUT[toggle:Workout]` Reading: `INPUT[toggle:Reading]`


### Accomplishments
- 1
- 2
- 3

### What Happened Today?


---
### New Tasks
- 

