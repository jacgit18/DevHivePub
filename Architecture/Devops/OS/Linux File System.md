---
tags:
  - linux
  - fileSystem
  - OS
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses Linux home directory.
Status: Done
Started: 
EditDate: 2024-03-11
Relates: 
Peer Reviewed: 1
dg-publish:
---
## home

- Each user has its own /home folder.
- Storage of your personal files and documents.
- Each user can only access their own /home folder unless they use admin permissions.
- It has some hidden directories that start with a dot. e.g. .cache, .config. These hidden folders are used by different applications for their settings. You can see them by using the ls -a command in the terminal.
- You can back up the hidden directories and restore them in a new system. After reinstalling your applications, the settings will be restored.

## root
home folder of a root user

- A directory where only a root user has access.

## root sign /


- Every single file and directory starts from the root directory.
- Only root user has write privilege under this directory.
- Please note that /root is root user’s home directory, which is not same as /.