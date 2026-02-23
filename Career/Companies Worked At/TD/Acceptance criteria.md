---
tags:
  - agile
author:
  - jacgit18
Purpose: This documentation discusses acceptance criteria.
Status: Done
Started: 2023-12-12
EditDate: 
Relates: "[[User Stories]]"
dg-publish:
---
Crafting acceptance criteria is an iterative process that unfolds at the story's inception, matures in the middle, and gains additional insights towards completion. It is a crucial aspect written from the product perspective, defining scope and standing as one of the benchmarks for the definition of done.

Consider the following user story as an illustration:

> As a website visitor, I can see all flights departing from my selected airport to my desired destination on the selected day to pick a flight that meets my travel needs.

Within the acceptance criteria, complexities may surface, potentially leading to the identification of additional user stories for future development. Each acceptance criterion functions like a sequential list, detailing outcomes based on the process flow.

Multiple acceptance criteria can sometimes evolve into stories with their own acceptance criteria, emphasizing that the definition of ready is conventionally applied at the user story level rather than at the granularity of acceptance criteria.

>[!note] 
>User story can some time present as an acceptance criteria

For instance, the acceptance criteria for the aforementioned story could break down as follows:

- The visitor can see a list of all available flights that fit the criteria.
- If no flight fits the criteria, the visitor can choose to see alternative dates.
- If no flights fit the criteria, the visitor can choose to see alternate destinations.
- If no flight fits the criteria, the visitor can choose to see alternate departures.
- Once the visitor picks a flight, the booking window will be offered.

It is paramount to keep the criteria in scope concerning the story, differentiating it from out-of-scope elements, such as potential reward points for the visitor.

An additional example, "Fred requesting recommended training topics," demonstrates the interconnectedness of the acceptance criteria in a story:

```vb
Given Fred is logged into the website
And Fred has unfinished training topics
When Fred requests a training plan
Then Fred's customized training plan is viewable.
```

A guiding principle emerges: avoid working on stories that do not meet the definition of ready. This underscores the importance of a single user story containing multiple acceptance criteria, contributing to a comprehensive and well-defined understanding of the development scope.


## **Definition of Ready (DoR):**

The Definition of Ready serves as a collective agreement within the team, ensuring a shared understanding of the story, encompassing developers, BSA, and other stakeholders. Stories residing in limbo persist in backlogs until clarity is achieved, fostering collaboration and enhancing code quality.

### **Key Components of DoR:**

- **Clear Business Value:**
  - Articulation of the story's value to the business, emphasizing its significance.

- **Defect Management:**
  - A systematic approach to addressing and managing defects within the story.

- **Defined User Story:**
  - A narrative or overview that provides a clear understanding of the user story.

- **Alignment of Epics:**
  - Ensuring that epics align seamlessly with the overarching feature or theme.

- **Identification of Dependencies, Risks, & Constraints:**
  - Proactive identification and management of factors influencing the story.

- **Priority Identification:**
  - Clearly defined priority, facilitating effective sprint planning.

- **User Persona (if applicable):**
  - Integration of user personas when contextual relevance is evident.

- **Time Estimation:**
  - Providing a general estimate of effort, time, and complexity required.

- **Clear Acceptance Criteria & Data Sets:**
  - Specific conditions and data sets, derived from [[User Stories]].

- **Testability:**
  - Ensuring the story's testability, with a focus on target functionality.

- **Boundary Scope Guideline Alignment:**
  - Aligning the story's scope with future unknowns and establishing boundary guidelines.

- **Definition of Done (DoD):**
  - Establishing criteria that signify the completion of work.

**Responsibility for DoR:**

The responsibility for getting the story ready lies with Business Analysts (BSA). These parties collaborate in refining the product backlog, prioritizing stories, and populating sprint backlogs within pods. Product Owners play a pivotal role in this process, leveraging historical capacity and considering technical and external dependencies for informed decision-making. This collaborative effort ensures a business-aligned platform and sets the stage for successful sprint execution.



## **Definition of Done (DoD):**

The Definition of Done is a team-generated checklist encompassing seven key activities for a given user story of a specific type. This concise checklist ensures the holistic readiness of a feature, incorporating critical considerations:

1. **Pass Unit and Integration Tests:**
   - Verification that the user story successfully passes both unit and integration tests.

2. **Security Implementation:**
   - Confirmation that security measures are implemented to adhere to relevant regulations.

3. **Code Review Completion:**
   - The completion of a thorough code review, ensuring code quality and adherence to standards.

4. **Acceptance Criteria Met:**
   - Verification that all acceptance criteria outlined for the user story have been met.

5. **Dependency Resolution:**
   - All dependencies, including tasks and sub-tasks related to the user story, are accounted for and completed.

6. **Successful Test Case Execution:**
   - Execution of test cases with the verification that they are passing, ensuring the robustness of the implemented functionality.

7. **Defect-Free State:**
   - Confirmation that there are no open defects associated with the user story.

Upon the satisfactory completion of these checklist items, the user story is deemed done. Subsequently, deployment to the target environment is initiated, marking the culmination of the development cycle. This structured approach to the Definition of Done ensures a comprehensive and consistent standard for the completion and deployment of user stories.


