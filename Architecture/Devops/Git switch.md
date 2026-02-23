---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
Both git switch and git checkout can be used to change branches, but they were created for different purposes and have key differences:

  

git switch (Newer, Safer)

  

Purpose: Specifically designed for switching branches

  

· Only changes branches

· Safer and more predictable

· Won't accidentally overwrite uncommitted changes



Always git pull --rebase over git pull but if conflict git rebase --abort then do git pull
Git status frequently 
Do git add fileName after resolving merge conflict instead of pressing button in vscode

Then git commit -am "message"

  

Examples:

  

```bash

# Switch to existing branch

git switch main

  

# Create and switch to new branch

git switch -c new-feature

  

# Switch to previous branch

git switch -

```

  

git checkout (Older, More Powerful)

  

Purpose: Multi-purpose tool that can:

  

· Switch branches

· Restore files from specific commits

· Check out specific commits, tags, or files

  

Examples:

  

```bash

# Switch to existing branch (same as git switch)

git checkout main

  

# Create and switch to new branch

git checkout -b new-feature

  

# Restore a file from HEAD (dangerous - can lose changes)

git checkout -- file.txt

  

# Check out a specific commit (detached HEAD)

git checkout abc123

```

  

Key Differences

  

Aspect git switch git checkout

Primary Purpose Branch switching only Multi-purpose tool

Safety Won't overwrite uncommitted changes Can accidentally overwrite files

File Operations ❌ Cannot restore files ✅ Can restore files from commits

Detached HEAD Requires --detach flag Directly supports

Intent Clear and specific Ambiguous

  

When to Use Which

  

Use git switch for:

  

· Switching between branches

· Creating new branches

· Daily branch navigation

  

Use git checkout for:

  

· Restoring files from specific commits

· Checking out specific commits/tags

· Operations that involve files rather than branches

  

Modern Recommendation

  

Use git switch for branch operations and git restore for file operations (the new dedicated command for restoring files):

  

```bash

# Instead of git checkout -- file.txt

git restore file.txt

  

# Instead of git checkout branch-name  

git switch branch-name

```

  

This separation makes commands more predictable and less error-prone!