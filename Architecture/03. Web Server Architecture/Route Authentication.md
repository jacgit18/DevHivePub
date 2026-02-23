---
tags:
  - routes
  - security
  - auth
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses route authentication.
Status: Done
Started: 2024-01-01
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
It's generally a good practice to leave authentication off for routes that handle user registration and login. These routes are typically the entry points for new users or users attempting to establish a session. Once a user is authenticated and has a valid session, subsequent requests to protected routes should be authenticated.  
  
Here's why:  
  
1. **User Registration:** Users need to be able to register without being authenticated. Otherwise, new users wouldn't be able to create accounts.  
  
2. **User Login:** Similarly, users need to be able to log in without requiring authentication. This is the process by which users obtain authentication credentials (like tokens or sessions).  
  
3. **Verification and Validation:** Even though the routes are unauthenticated, you should still implement thorough verification and validation. This includes checking the user's credentials, validating input, and ensuring security measures like password hashing.  
  
However, once a user is authenticated, you should protect sensitive routes and data by ensuring that only authenticated users can access them. This is commonly done through mechanisms like tokens, sessions, or other authentication methods.  
  
Remember to implement proper security practices, such as using HTTPS, securely storing passwords, and validating input to prevent security vulnerabilities.