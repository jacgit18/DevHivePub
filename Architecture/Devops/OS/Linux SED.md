---
tags:
  - linux
  - CLI
author:
  - jacgit18
  - chatgpt
Comments: 
Purpose: 
Status: Done
Started: 
EditDate: 2024-03-11
Relates: 
Peer Reviewed: 0
dg-publish:
---
`sed` (stream editor) is a powerful command-line tool used for text processing and manipulation. It allows you to perform various operations on text, such as search and replace, text deletion, text insertion, and more. Here's a real-world example of how `sed` can be used:

**Example: Search and Replace Text in a File**

Suppose you have a text file named `sample.txt` that contains the following text:

```plaintext
Hello, World!
This is a sample text file.
Let's use sed to replace "sample" with "modified".
```

You want to replace all occurrences of the word "sample" with "modified" in this file.

You can use `sed` to accomplish this task:

```bash
sed 's/sample/modified/g' sample.txt
```

Explanation of the command:

- `sed`: Calls the `sed` command.
- `'s/sample/modified/g'`: This is the `sed` command itself. It consists of:
  - `s`: Indicates a substitution operation.
  - `sample`: The text to search for.
  - `modified`: The text to replace "sample" with.
  - `g`: Stands for "global" and instructs `sed` to replace all occurrences in each line (not just the first one).

When you run this command, it will output the modified text to the standard output. If you want to save the changes back to the file, you can use the `-i` option like this:

```bash
sed -i 's/sample/modified/g' sample.txt
```

After running this command, the contents of `sample.txt` will be changed to:

```plaintext
Hello, World!
This is a modified text file.
Let's use sed to replace "modified" with "sample".
```

In this real-world example, `sed` is used to perform a search and replace operation on a text file. This is just one of the many tasks `sed` can handle, and it is widely used for text processing tasks in scripting, file editing, and automation.