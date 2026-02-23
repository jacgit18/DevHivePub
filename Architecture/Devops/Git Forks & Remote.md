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
Here's your guide converted to clean and readable **Markdown format**:


# 🛠️ Guide: Working with Multiple Forks in Git

## 📌 Scenario

You and a teammate are both working on different forks of the same upstream repository. You want to:

1. Set your fork as `origin`.
2. Add your teammate’s fork as a remote (optional).
3. Fetch their branch/changes.
4. Merge them into your fork.
5. Push the merged updates to your own fork on GitHub.
6. Also in this scenario your following the leader in this case my teammate who is rebasing  from main which i usually have to do but once they get there branched merged then i will need to rebase from main.

---

## ✅ Step 1: Clone Your Fork or Initialize Repo

If you haven’t already:

```bash
git clone https://github.cloud.capitalone.com/YOURUSERNAME/collections-infra-bpa-workflows.git
cd collections-infra-bpa-workflows
```

---

## ✅ Step 2: Add Your Remote (Origin)

If not already done:

```bash
git remote add origin https://github.cloud.capitalone.com/YOURUSERNAME/collections-infra-bpa-workflows
```

Check remotes:

```bash
git remote -v
```

---

## ✅ Step 3: (Optional) Add Your Teammate's Fork as a Remote

You can name their remote anything, e.g., `teammate`:

```bash
git remote add teammate https://github.cloud.capitalone.com/EPR939/collections-infra-bpa-workflows
```

Or replace an existing one:

```bash
git remote set-url origin https://github.cloud.capitalone.com/EPR939/collections-infra-bpa-workflows
```

---

## ✅ Step 4: Fetch Their Branch

```bash
git fetch teammate
```

Or fetch a specific branch:

```bash
git fetch teammate CT58T-527-Immediate-Enrollment-Component-Tests
```

---

## ✅ Step 5: Merge Their Branch into Yours

Assuming you're on your local working branch:

```bash
git merge teammate/CT58T-527-Immediate-Enrollment-Component-Tests
```

---

## ✅ Step 6: Push to Your Fork

Push the changes back to your forked repo:

```bash
git push origin YOUR-BRANCH-NAME
```

If you changed your origin URL earlier and want to push back to your original fork:

```bash
git remote set-url origin https://github.cloud.capitalone.com/YOURUSERNAME/collections-infra-bpa-workflows
git push origin YOUR-BRANCH-NAME
```

---

## 🧠 Tips

- Always create a **new branch** before merging external code.
    
- Use `git log --oneline` or `git diff` to inspect changes after merging.
    
- Avoid directly committing to `main` unless necessary — use **feature branches**.
    
