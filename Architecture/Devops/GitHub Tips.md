---
tags:
  - versionControl
  - bestPractices
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses some best practices around git.
Status: Done
Started: 
EditDate: 2024-02-22
Relates: 
Peer Reviewed: 0
dg-publish:
---
When forking a repository, refrain from adding collaborators to preserve pull request permissions. This ensures that any collaborator cannot make a request and merge without approval from the master repository.

A pull request, although not exclusive to Git, is a GitHub feature primarily used for code review. It is essential to maintain a downstream approach, pulling changes from the master repository.

Practice squash merging by condensing all commits into one in the Git history of the main branch. Commit frequently with intent and test regularly to ensure code stability.

#todo/Low/Dev  
- [ ] https://dev.to/samuelfaure/how-atomic-git-commits-dramatically-increased-my-productivity-and-will-increase-yours-too-4a84

For instance:

```bash
git checkout feature/dev-78_post_letter
git checkout feature/dev-80_get_by_id_letter_endpoint
git merge --squash feature/dev-78_post_letter
```

Execute small changes in branches to minimize dependencies. Prefer drafting pull requests instead of directly creating them. Note that draft PRs might not be available in all GitHub repositories, and you can refer to GitHub documentation for details.

Handle merge conflicts diligently to maintain code integrity during the collaboration process.

![[merge & Rebase.jpeg]]

Git rebase to merge a feature branch at the tip of a get main so basically whatever the last commit the future branch that you created gets appended to the end of that.

## Update branch to latest 
```bash
git checkout develop 
git pull 
git checkout previousBranch 
git stash if uncommitted changes or staged changes ???? 
git merge develop  

git stash # To add changes to stash stack 
git stash list # Shows list of stashed changes 
git stash apply stash@{0} # Retrieve stash 
git stash clear # Clear stash list  

git add –A  
git commit -m "changed thing" 
git push
```
