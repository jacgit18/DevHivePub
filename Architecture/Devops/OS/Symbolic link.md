---
tags:
  - linux
  - fileSystem
author:
  - jacgit18
  - chatgpt
Status: Done
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses symbolic links in linux.
Started: 
EditDate: 2024-03-09
Relates: 
Peer Reviewed: 0
dg-publish:
---
In Linux, a soft link, also known as a symbolic link or symlink, is a special type of file that acts as a reference or pointer to another file or directory. It provides a way to create shortcuts or aliases to files and directories, allowing you to access them easily without having to navigate through the entire directory structure.

#todo/Low/Dev  
- [ ] Read more about symbolic links

Here are some key points about soft links in Linux:

1. Structure: A soft link is essentially a file that contains the path or location of the target file or directory. It has its own unique inode (an index node that stores metadata about the file) and filename. The target can be a file or a directory on the same file system or even on a different partition or device.

2. Symbolic Link: Unlike a hard link, which directly points to the underlying data blocks of a file, a soft link simply contains the path to the target. It does not have its own data blocks. Think of it as a shortcut or a signpost.

3. File Permissions and Ownership: Soft links have their own permissions and ownership separate from the target file or directory. The user creating the link needs appropriate permissions on the target to create the soft link.

4. Symlink Behavior: When you access a file or directory through a soft link, the operating system transparently follows the link and resolves the path to the actual target. This means that if you delete the link, the target file or directory remains unaffected.

5. Relative and Absolute Paths: Soft links can be created using either relative or absolute paths. Relative paths specify the path to the target relative to the location of the symlink itself, while absolute paths specify the complete path starting from the root directory.

6. Linking Files and Directories: Soft links can point to both files and directories. If a soft link points to a file, it behaves like a regular file. If it points to a directory, you can access and navigate the directory through the link.

7. Linking Across File Systems: Soft links can be used to link files and directories across different file systems or devices. However, if you delete or move the target file or directory, the link will become broken or "dangling."

Soft links provide flexibility and convenience in managing files and directories in Linux. They can be used to create shortcuts, organize file structures, simplify navigation, and facilitate the sharing of resources between different locations.