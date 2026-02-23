---
tags:
  - bsa
  - business
  - CapitalOne
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses life cycle of business requirements.
Status: Done
Started: 2023-12-12
EditDate: 
Relates: "[[Attributes of Requirements & User Stories]]"
dg-publish:
---

![[Requirement life cycle.svg]]

# Business Requirements 
Business requirements which are drivers for user stories and all this work refer to the high-level needs/wants and objectives of the organization or stakeholders that drive the development of a product or service.

These requirements are typically contained inside within [[User Stories#**Themes In-Depth** |Themes]] which represent a higher level of abstraction that allows teams to understand the broader context and purpose of the work they are doing.

Each theme may encompass multiple business requirements that collectively contribute to achieving a specific business goal.

The identification and prioritization of themes are crucial in guiding the development team to work on the most valuable and impactfull features or improvements.

## **Translating Business Needs to Technical Requirements:**

### **Identify and Consider:**
   - Organization position and its impact on structure.
   - Priority of needs and wants.
   - Applicability of requirements, justifying their value, complexity, cost, and legal aspects.
   - External constraints, geopolitical factors, regulations, and legal considerations.
   - Business as usual (BAU) operations.
   - Alternative actions, potential risks, and hurdles.
   - Requirements must encompass specific conditions, focus on a defined subject, articulate vital actions, adhere to established business rules, and culminate in an outcome that aligns seamlessly with business objectives.

### Requirement Types
Features contribute to both [[Functional Requirements]] and non-functional requirements, they are typically derived from functional requirements as specific capabilities or functionalities that the system must provide to satisfy user needs. 

[[Non-Functional Requirements]], on the other hand, define the criteria for how those features should perform or behave to meet broader system objectives. Both types of requirements are essential for effectively designing, implementing, and evaluating a system.

[[Testing Stages Relationship |Requirements in testing context]]
when testing look for bugs ask if the behavior defined in the codebase is intended because it could be a known or unknown bug or just a lot more complexity or something just ask questions.


### **Understanding Stakeholder Needs:**
**Needs of Stake Holders drives user wants
>[!note]
> Determine stakeholders' incentives, influences, and motivations, and subsequently, categorize and prioritize them. When assessing these factors, consider that smaller issues may require fewer needs to define. Conversely, in scenarios involving the rebuilding of functionality, as seen with Tracflo, or the creation of something entirely new, the number of needs and scope may significantly expand.
#### Needs + Wants + Data = Business Requirements:
   - Business needs arise from factors like customer complaints, market changes, and process inefficiencies.
   - Stakeholder incentives, influences, and motivations should be identified, categorized, and prioritized.
   - Consider the scope, organizational culture, and established information when determining user wants.
   - Assess data relevance, quality, volume, availability, and accessibility.

### Data Considerations
- **Data Relevance:** Assess the pertinence of the data to the project objectives.
- **Data Quality:** Evaluate the accuracy and reliability of the available data.
- **Data Volume:** Determine the quantity of data required for the project.
- **Data Availability:** Ensure that necessary data is accessible when needed.
- **Data Accessibility (Format):** Consider the format in which the data is stored or presented.

**Additional Considerations:**
- **Data Types:** Distinguish between database (db) data and documentation.
- **Time Period:** Clarify the timeframe for data availability, especially with sensitive information subject to regulatory compliance.
- **Applicability:** Evaluate the relevance of the data and the specific information it contains.

### **Assumptions and Constraints:**
   - **Assumptions:** Identify, document, confirm accuracy, and manage risks associated with unproven factors.
   - **Constraints:** Recognize impositions or restrictions on the project, including business, technical, and external constraints.
   - **Triple Constraint:** Consider the interplay of budget, time, and scope in project management.

## Resolving Requirement Conflicts
Address conflicts effectively through various techniques:

1. **Multivoting:**
   - Utilize multivoting to prioritize conflicting requirements, allowing team members to collectively express preferences and reach a consensus.

2. **Weighted Ranking Voting:**
   - Apply weighted ranking voting to assign priority levels to conflicting requirements based on their relative significance.

3. **Delphi Technique:**
   - Implement the Delphi technique by creating a survey leveraging the expertise of relevant stakeholders. Aggregate and analyze the results to inform decision-making.

4. **Expert Review of Survey Results:**
   - During the review of survey outcomes, involve experts to assess and validate the results, ensuring a comprehensive and well-informed decision-making process.

## Requirement Life Cycle 
The project life cycle encompasses several key stages: Identification, Definition, Verification, Validation, Approval, and Implementation. This cycle allows for iteration, permitting a return to the Definition stage until approval is secured. The process may loop back from the Verified stage to Implementation and ultimately culminate in retirement.

It's crucial to note that change is not automatically implemented, emphasizing the non-linear nature of the life cycle.

**Decision-Making and Stakeholder Roles**

Determining who makes decisions and identifying the primary customer or focus of need are pivotal aspects. The RACI framework, representing Responsible, Accountable, Consulted, and Informed, aids in clarifying responsibilities for creating, delivering, reviewing, and validating. 

- **Responsible:** Those tasked with executing specific actions.
- **Accountable:** The individual ultimately answerable for the success or failure of a task or decision.
- **Consulted:** Those whose input is sought before making a decision or taking action.
- **Informed:** Those kept in the loop about decisions or actions but are not directly involved.

Additionally, recognizing that a conversation can serve as another form of traceability, fostering communication and understanding across stakeholders. This ensures a comprehensive approach to decision-making and project progression.


## Requirements in Different Context
In the context of business systems analysis and QA engineering, functional and non-functional requirements refer to similar concepts but are approached and interpreted somewhat differently based on the role's focus.

## 1. Functional Requirements

### Business System Analyst Context:
Functional requirements describe what the system should do, essentially focusing on the features and capabilities the system needs to support the business processes. For example:
- "The system must allow users to log in with a username and password."
- "The system should generate a sales report."

The analyst ensures these requirements align with business needs.

### QA Engineering Context:
For QA, functional requirements guide the development of test cases that verify the system’s behavior. The QA engineer translates these requirements into specific tests to confirm that each function works as intended, such as:
- Testing login flows
- Data validations
- Report generation

QA ensures each function works per the specifications.

## 2. Non-Functional Requirements

### Business System Analyst Context:
Non-functional requirements (NFRs) refer to how the system should perform rather than what it should do. They include:
- Performance
- Security
- Scalability
- Usability
- Reliability

These requirements support the overall quality of the user experience and system stability.

### QA Engineering Context:
For QA, NFRs are crucial in designing tests for things like performance, load, and security. The QA engineer validates these attributes through specific testing types, such as:
- Stress testing
- Load testing
- Security testing

QA ensures that the system meets performance standards and handles expected (or unexpected) usage loads effectively.

## Similarities and Differences

### Similarities:
- In both contexts, functional and non-functional requirements are documented, managed, and serve as the foundation for designing and validating the system.
- Both roles ultimately aim to ensure that the system meets business expectations.

### Differences:
- Business analysts focus on capturing and defining requirements to support the business.
- QA engineers focus on interpreting and validating those requirements. QA takes an implementation-focused approach, working with requirements to create test plans that confirm each aspect meets the intended specifications.

## Summary:
While functional and non-functional requirements have similar definitions across these contexts, the focus shifts:
- Business analysts capture requirements to guide development.
- QA engineers validate these requirements to ensure the system behaves and performs as expected.


