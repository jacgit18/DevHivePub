---
tags:
  - web
  - MicroCodebaseDecision
  - comparison
  - HTTP
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses different types of storage around browsers.
Status: Refinement
Started: 
EditDate: 2024-01-30
Relates: 
Peer Reviewed: 0
dg-publish: false
---
### Cookie Storage

- **Capacity:** Limited to 4 KB.
- **HTML Support:** Compatible with HTML 4 and 5.
- **Access Method:** Accessed through `window` object, using `document.cookie` with associated methods.
- **Expiration:** Can be manually set.
- **Storage:** Persists on both the browser and server.
- **Request:** Sent with each HTTP request.

### Local Storage

- **Capacity:** Allows up to 10 MB storage.
- **HTML Support:** Supports HTML5.
- **Access Method:** Accessible via the `window` object, using `localStorage`.
- **Expiration:** Persistent; never expires.
- **Storage:** Local storage is stored exclusively in the browser.
- **Request:** Data stored in local storage is not sent with HTTP requests.

### Session Storage

- **Capacity:** Limited to 5 MB.
- **HTML Support:** Compliant with HTML5.
- **Access Method:** Accessed from the same tab through the `window` object using `sessionStorage`.
- **Expiration:** Expires upon tab closure.
- **Storage:** Exclusive to the browser; not stored on the server.
- **Request:** Data stored in session storage is not sent with HTTP requests.