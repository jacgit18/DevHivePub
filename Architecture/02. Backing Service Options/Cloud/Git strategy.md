---
tags:
  - cloud
  - CapitalOne
  - bestPractices
  - RTIC
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 2025-02-25
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
Got it — so what you’re really proposing is **ephemeral “health snapshots” of `main`** to de-risk your PRs when `main` itself is unstable. That makes sense as a defensive tactic, but there are trade-offs worth dissecting:

---

## 🔍 Assumptions You’re Making

1. **Main should always be healthy** → In theory yes, but in practice your org isn’t enforcing that discipline (CI not blocking merges, insufficient test coverage, rushed approvals). You’re compensating for systemic failure.
    
2. **Copying main is safer than rebasing/merging** → That only shifts the problem; you’re still depending on main’s quality.
    
3. **Deleting temporary “main copies” will keep things clean** → People rarely delete consistently. Even if you do, Git history + branch proliferation can still get noisy.
    

---

## ⚔️ Counterarguments

- **Better fix:** Invest in gating merges. If `main` often breaks, the solution isn’t “create shadow mains,” it’s enforce CI/CD gates that reject failing builds. Otherwise, you’re building process around dysfunction.
    
- **Risk of drift:** Testing against yesterday’s “healthy main” might greenlight your PR, but merging into today’s unstable main still risks introducing hidden failures. You’ve only proven your code doesn’t break yesterday’s environment.
    
- **Maintenance overhead:** Even if you delete, you’re still creating a manual process. Repetition = more chances for mistakes (branch confusion, wrong merges, stale diffs).
    

---

## ✅ How to Formalize Your Approach (If You Still Want To)

Think of these as **ephemeral verification branches**, not permanent “alternate mains”:

1. **Snapshot Main**
    
    - At the start of your workday (or when raising a PR), check `main` health.
        
    - If failing, create `main-snapshot-YYYYMMDD` only if you need to verify.
        
2. **Rebase/Branch PR**
    
    - Rebase your PR branch onto `main-snapshot-YYYYMMDD`.
        
    - Run CI locally or in your forked pipeline.
        
3. **Verify**
    
    - If your PR builds/tests pass against snapshot but fails against current `main`, you’ve isolated the issue to someone else’s changes.
        
4. **Cleanup**
    
    - Delete `main-snapshot-*` once your PR merges or the issue is confirmed.
        
    - Keep only 1–2 snapshots max to avoid clutter.
        

---

## ⚡ Alternative Frameworks

Instead of rolling your own “shadow mains,” consider:

- **Feature branch test merges** → Some CI systems let you merge your branch with `main` _in the pipeline_ (without touching Git history) and run tests in that sandbox.
    
- **Staging branch** → A protected branch that merges only from green PRs. More reliable than daily snapshots.
    
- **Bisecting builds** → If main breaks, use `git bisect` or pipeline history to identify who introduced the failure instead of snapshotting.
    

---

So the sharper version of your idea isn’t “multiple mains,” it’s:  
👉 “Ephemeral snapshots of last-known-good main to isolate failures.”

But the deeper challenge you’re dancing around: your org has a **weak CI discipline problem**, and you’re building scaffolding around it.

---

Do you want me to push this further by drafting a **formal workflow doc** that frames your approach as a short-term band-aid while pointing toward the longer-term fix (stricter CI gating)?