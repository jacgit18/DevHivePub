---
tags:
  - career
  - dev
  - Domain
author:
  - jacgit18
Purpose: This documentation discusses Tracflo startup and the construction industry.
Status: Done
Started: 
EditDate: 2024-02-20
Relates: 
dg-publish:
---
**Tracflo: Digitizing Construction Workflow for Efficient Project Management**

Tracflo, a fintech company specializing in the construction industry, addresses the challenge of project delays due to contract disputes by revolutionizing the project management workflow. The root cause of these disputes often lies in disorganized paper documentation among project stakeholders, impacting financial agreements.

*Tracflo's Solution:*
Tracflo's innovative solution involves a platform that eliminates change orders by digitizing the entire construction project workflow. This includes documentation generated among various project parties, streamlining the process and expediting financial agreements.

*Key Features:*
- **Comprehensive Management:**
  - All contracts, finances, and paperwork are efficiently managed through the Tracflo app, involving everyone from project owners to contractors and subcontractors.
  - The app accommodates multiple user tiers, offering individual or shared access, fostering collaboration similar to a social media platform.

- **Document Sharing and Updates:**
  - Users can seamlessly share updated project costs, approval signatures, photos, videos, and other documentation.
  - The app allows different access levels based on roles, ensuring efficient project cost tracking.

*Main Goals:*
- The primary objective is to track the change order process, providing project managers with access to proper documentation from various parties to expedite financial agreements.
- Digitizing construction project documentation accelerates deal closures, streamlining communication among different stakeholders.

*Advanced Tracking:*
- Tracflo tracks labor and material rates akin to the stock market, capturing data on closing/open prices, high/low values, volume, estimates, and dates.
- The app facilitates data retrieval and utilization over weeks, months, and years.

*Workflow Hierarchy:*
- **Letters > Change Orders > Tickets:**
  - Letters are collections of change orders.
  - Change orders, in turn, are collections of tickets.

*Procore Integration:*
- Tracflo integrates with Procore, an all-in-one construction management software. This integration facilitates seamless data sharing between Procore and third-party systems, with notifications for data changes.

*Table Relation Dependency Order (Left to Right with Description):*


| Role | Markup | Action | User | File | Company |
|------|--------|--------|------|------|---------|

| Payment | Company_user  | Material_type  | Equipment_type  | Project | Contact  |
|------|--------|--------|------|------|---------|


| Break_material | Break_equipment | Letter  | Proj_user  | Proj | Proj_subcontractor |
|------|--------|--------|------|------|---------|



| Chg_order | Rev_letter | Labor_type | Rev_chg_order | Break_labor | Rev_tick | history |
|--------------|------------|------------|------------------|-------------|------------|---------|


Tracflo's approach aims to revolutionize project management in the construction industry, fostering collaboration, transparency, and efficiency.