---
tags:
  - linux
  - cron
  - scripting
  - automation
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: Refinement
Started: 
EditDate: 2024-03-11
Relates: 
Peer Reviewed: 0
dg-publish:
---
```bash
* * * * *  /home/jac/Sync/DevMindMap/sync.sh

#job will run only once at startup.  
Cron Job Special Strings


@reboot /path/to/your/script.sh  
  
  
@hourly. The job will run once an hour.  
  
@daily or @midnight. These strings will run the task every day at midnight.  
  
@weekly. Use this to run jobs once a week at midnight on Sunday.  
  
@monthly. This special string runs a command once on the first day of every month.  
  
@yearly. Use this to run a task once a year at midnight on January 1st.

```


