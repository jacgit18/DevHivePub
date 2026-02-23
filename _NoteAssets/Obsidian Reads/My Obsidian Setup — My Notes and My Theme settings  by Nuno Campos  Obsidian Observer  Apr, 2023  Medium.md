---
tags: 
author: 
Status: 
Started: 
EditDate: 
Relates:
---
## How do I manage my PKM notes and what theme I’m using


I’ve been using Obsidian as my second brain for a year now. I’ve tried other note-taking apps along the way, because I love to check all trendy stuff, but no other gives me the same versatility and customization power as Obsidian. Obsidian checks all my requisites for PKM, tasks, projects, daily journal…

This article starts a series where I’m going to review, after 1 year of usage, my Obsidian configuration, plugins, and workflows.

![](https://miro.medium.com/v2/resize:fit:700/1*wKBkEaGjDWnPn3rLXEvVyQ.png)

My Homepage. Image by [Nuno Campos](https://medium.com/@nuno.f.s.campos)

## How do I organize my PKM notes?

I use both folders and tags to organize my knowledge notes. I know I could do it only with tags, but it doesn’t feel right to me to put all notes in the same folder. Maybe it’s the fear that Obsidian will disappear suddenly and I have all the notes in the same folder and need to organize them by folder again 😵💫. Anyway, as I said, I have my knowledge notes organized by the main subjects of my sysadmin work, like Active Directory, Exchange, DNS, etc. But I also use tags because it allows me to set multiple subjects to a note. For each subject/folder, I have a MOC that lists all the notes with the subject’s tag, and all tasks and daily journal entries with that tag. This way I can see all actions related to a subject and when did they take place.

![](https://miro.medium.com/v2/resize:fit:700/1*qx3G5t2Sv1m78gYYDeGfbQ.png)

MOC for SQL. Image by [Nuno Campos](https://medium.com/@nuno.f.s.campos)

```
# sql---```dataview  TABLE without ID file.link as "Note Title", file.mday as "Last Modified"  FROM #sql and #type/noteWHERE file.name != this.file.name SORT file.name asc  ```## ✅ Tasks```tasksdescription includes #tag_namesort by start date```## 🧾Daily Log```queryblock:(/.*🧾.+#tag_name.*/ OR /.*🧾.+#tag_name.*/)```
```

Then for each PKM note, I also include a similar code to show tasks and daily journal entries that have a backlink to that note. This way I can see when I used a specific knowledge note in a task or daily event.

![](https://miro.medium.com/v2/resize:fit:700/1*WvwCt42TsLYbUok0NyxpmQ.png)

PKM Note. Image by [Nuno Campos](https://medium.com/@nuno.f.s.campos)

```
## ✅ Tasks```tasksdonedescription includes note_namesort by start date```## 🧾Daily Log```query block:(/.*🧾.+note_name.*/ OR /.*🧾.+note_name.*/)```
```

## Note Capture

I use [QuickAdd](https://github.com/chhoumann/quickadd) to create almost everything in my vault. Let’s look at the PKM note macro:

![](https://miro.medium.com/v2/resize:fit:700/1*n9Jr_oC2_aL0L2-ggJVfCg.gif)

QuickAdd: new note macro. Image by [Nuno Campos](https://medium.com/@nuno.f.s.campos)

This `New Note`choice is composed by 2 separate macros. In the first macro, it asks for the subject, which is nothing but the folders inside the PKM root. For this, I’m using javascript code that I found online and adapted for my workflow:

```
module.exports = async (params) => {    const {quickAddApi: {inputPrompt}} = params;    const files = app.vault.getMarkdownFiles().filter(f => f.path.includes("01 PKM/") && f.name == f.parent.name +".md" && f.name != "01 PKM.md" )    const pickedFile = await params.quickAddApi.suggester(        (file) => file.basename,        files    )    await params.quickAddApi.executeChoice('AddNewNote', {Subject: pickedFile.basename})}
```

This will get all files inside `01 PKM`that have the same name as the parent folder (the MOCs). In other words, it will get all folders that have a folder note. The `AddnewNote`is the name of the QuickAdd choice to send the selected subject (the second macro). `Subject` is the name of the variable in the second macro.

![](https://miro.medium.com/v2/resize:fit:587/1*vJZURVuBcBK8YpLpXffwrw.png)

New note 2nd macro. Image by [Nuno Campos](https://medium.com/@nuno.f.s.campos)

![](https://miro.medium.com/v2/resize:fit:587/1*yYTEj4Z19eaBdonIE2Eekw.png)

New note 2nd macro. Image by [Nuno Campos](https://medium.com/@nuno.f.s.campos)

![](https://miro.medium.com/v2/resize:fit:589/1*UeUffAuzLxqA-6gKuXpAQw.png)

New note 2nd macro. Image by [Nuno Campos](https://medium.com/@nuno.f.s.campos)

![](https://miro.medium.com/v2/resize:fit:590/1*LybqFwqQKZ-rkqmDo3f0qA.png)

New note 2nd macro. Image by [Nuno Campos](https://medium.com/@nuno.f.s.campos)

## Highlight Notes

Some situations on my PKM workflow require note highlighting. For example, notes requiring review. I’m using Colorful Note Borders to set a border color base on a frontmatter value. In this case, notes with `status: review`will have an orange border.

![](https://miro.medium.com/v2/resize:fit:700/1*JHTdVsUUlFeJ5LUWPPsfQQ.png)

In the next parts, I’m going to review my tasks, projects, and daily journal workflows. I’m also going to list all plugins that I have installed.