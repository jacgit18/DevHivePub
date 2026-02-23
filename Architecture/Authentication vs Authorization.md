---
tags:
  - API
  - web
  - OS
  - databases
  - cloud
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the distinction between Authentication and Authorization.
Status: Done
Started: 
EditDate: 2024-03-03
Relates: 
Peer Reviewed: 0
dg-publish: true
---
Authentication verifies identity, like recognizing someone at your home's door. Authorization determines access levels, allowing distinctions such as entering the house but not the bedroom. Testing various user types ensures robust authentication and authorization. The business logic involves delineating responsibilities among different parties like for example manger and employee. Implementing conditional render logic based on user roles and hiding frontend features enhances both security and user experience. 


- **Identification:** Determining the entity making an API request.
  
- **Authentication:** Verifying the identity of the requester. Web applications typically use a username-password combination, checking it against stored records for authenticity.
  
- **Authorization:** Confirming if the requester is allowed to perform the intended action. For example, a web app may permit viewing a page but restrict editing to administrators.
  
- **Questions for User Management:**
  
  - *Onboarding Developers:*
    - Do you have an existing user account management system for API access? Consider OAuth key provision.
    - If lacking user management, outline the signup process. Is it user-friendly via web browsers? Define user tiers for simplicity.
    - Identify necessary user information access.

  - *Maintaining and Managing Accounts:*
    - Can users reset passwords? Design a user-friendly interface for account management.
    - Monitor user activity; consider providing users with monitoring capabilities.
    - Implement user account revocation. Explore approval or screening processes.
    - Assess reporting and analytics needs for user engagement and retention.

  - *Integrating API Users into Business:*
    - Map developer activity into sales, support, and ERP systems.
    - Structure API keys to associate developers with applications, customers, and end-users.
    - Integrate user data with existing profiles or user data systems, explore single sign-on (SSO) options.
    - Provide developers with access to usage data for incentivizing usage.

- **Identification Techniques:**
  
  - Session-Based Authentication.
  - OAuth.
  - Usernames and Passwords.
  - Fortify Authentication with SSL.