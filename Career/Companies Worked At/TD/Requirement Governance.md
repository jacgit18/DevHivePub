---
tags:
  - bsa
author:
  - jacgit18
Purpose: This documentation discusses requirement governance.
Status: Done
Started: 
EditDate: 2024-02-20
Relates: 
dg-publish:
---
## **Approaches Comparison: Traditional vs. Adaptive**

| Traditional Approach                                 | Adaptive Approach                           |
| ---------------------------------------------------- | ------------------------------------------- |
| All requirements defined upfront                     | Enough detail for delivery and feedback     |
| Set phase gates                                      | Frequent reviews                            |
| Official reviews and sign offs                       | Oral, team agreements                       |
| All development is held to the approved requirements | Changes happen after delivery               |
| Changes are formally submitted and tracked           | Feedback becomes new requirements            |
|                                                      | Priority is constantly reviewed and updated |
|                                                      | Approvals on delivered functionality        |

### **Governance Examples: Traditional Approach**

1. All requirements must be verified and validated before review.
2. Requirements go through a formal review process with the team.
3. Business owner signs off (approves) requirements.
4. Any requirement changes are submitted using a change request form.
5. Changes are analyzed before approval or denial by the business owner.

### **Governance Examples: Adaptive Approach**

1. Any requirement is defined and put into the backlog.
2. Team and product owner agree on prioritization based on value.
3. Highest priority requirements are implemented.
4. Feedback on delivery is captured as new requirements in the backlog.
5. Bi-weekly review of backlog and corresponding backlog.

## **Maintaining Requirements**

- Requirements are essential well after implementation.
- Requirements emerge on a continuous cycle.
- Leveraging tracing and version control.
- Reusing requirements as baselines.

## **Presenting Requirements Changes**

*You are NOT the decision-maker. You present recommendations.*

- **Change:** Add functionality to feature.
- **Why:** Easier usability.
- **Potential ROI:** Increased revenue (from increased user adoption).
- **Risks:** More intensive to build, requires additional resources.
- **Impacts:** Quantify the risks (potential impacts) like an increase in budget, schedule delay, or changes due to resources.

### **Alternatives:**

1. **Not change feature**
   - No change in ROI, risk missing out on additional revenue through customer frustration.

2. **Change technology platform**
   - Ability to offer more features, increased revenue but increased cost and time.

**Recommendation:** Implement a small change to functionality and wait for solution delivery and feedback for further changes.

**Changes in Adaptive Requirements**

| Changes          | Risks                            | Impacts                          |
| ---------------- | -------------------------------- | -------------------------------- |
| Change a feature | Other features are not delivered | Lower ROI and delivery of value  |
|                  | Delighting the customer          | Higher ROI and delivery of value |

**Changes in Traditional Requirements**

| Changes          | Risks                                       | Impacts                          |
| ---------------- | ------------------------------------------- | -------------------------------- |
| Change a feature | Requires more time to complete than planned | Requirements must be reworked    |
|                  |                                             | Resources need to be rescheduled |
|                  |                                             | Delivery of solution delayed     |
|                  | Requires additional resources               | Budget increase                  |
|                  |                                             | Delayed schedule                 |