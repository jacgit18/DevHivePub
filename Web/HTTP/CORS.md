---
tags:
  - web
  - HTTP
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Cross-Origin Resource Sharing.
Status: Done
Started: 
EditDate: 2024-01-31
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[CORS.gif]]
Cross-Origin Resource Sharing (CORS) is an HTTP-header based mechanism facilitating secure resource sharing between web pages from distinct origins. It enables a server to specify which external origins (domains, schemes, or ports) are permitted to load resources, safeguarding against unauthorized access.

When initiating a cross-origin request, such as calling an API from a different domain, the browser sends a preliminary "preflight" request to the server. This request includes headers detailing the intended HTTP method and other headers to be utilized in the actual request. The server responds, indicating whether the requested operation is allowed.

For instance, if front-end JavaScript hosted at [https://domain-a.com](https://domain-a.com/) seeks data from [https://domain-b.com/data.json](https://domain-b.com/data.json), CORS ensures that [https://domain-b.com](https://domain-b.com) explicitly permits this access. CORS serves as a vital security measure, promoting controlled and secure cross-origin interactions while preventing unauthorized resource access.