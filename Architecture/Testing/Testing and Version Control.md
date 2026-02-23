---
tags:
  - versionControl
  - testing
  - CapitalOne
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
When working as a QA tester, it's crucial to manage your branches strategically, especially when testing multiple scenarios. Instead of creating one large branch, it's more effective to create multiple smaller branches, each focused on a specific set of tests. This approach is beneficial because the build process for these tests often runs in a cloud environment, where builds can fail for various reasons. By submitting smaller pull requests (PRs) with a few tests at a time, you minimize the risk of widespread issues and make it easier to identify and resolve any problems that arise. Smaller PRs also streamline the review process, making it easier for reviewers to focus on specific test cases and ensure thorough coverage.  
  
On the other hand, when writing features for a codebase, the approach to PRs can be slightly different. While it's still important to keep PRs manageable, they can generally be larger compared to those for QA testing. The size of the PR should align with the scope of the feature being developed. For instance, if you're working on a comprehensive feature that involves multiple components or significant changes, it might make sense to submit a larger PR. However, even in these cases, it's still beneficial to break down the work into logical segments to avoid overwhelming reviewers and to maintain a clear, organized workflow.  
  
The key takeaway is that smaller, focused PRs are generally more effective for QA testing due to the need for precise and isolated test scenarios, while feature development can accommodate slightly larger PRs, as long as they remain clear and coherent.

## GitHub PR
- **Side note:** Merging from another branch after a PR has been approved can trigger a SOD (Segregation of Duties) validator issue.
- **Break stories:** Split Jira tickets into negative and happy path scenarios and provide detailed information about the work involved.
- **Short PRs:** Keep pull requests small to minimize conflicts and make reviewing easier.
- Isolate refactors into their own branch.
- Separate new utility functions into their own branch before integrating them.
- Start with a rough draft of new code using non-clean, quick implementations.
- In a new branch, refine the changes by incorporating optimizations and the isolated utility functions.
