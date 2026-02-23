---
tags:
  - web
  - HTTP
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Custom HTTP Headers and Methods.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
### When and How to Use Custom HTTP Headers

HTTP servers often employ custom headers, such as X-Powered-By and X-Cache, for informational purposes. While HTTP allows extension headers like X-Forwarded-For and X-Pingback, their usage can impact interoperability. Consider these guidelines for effective use:

1. **Informational Use:** Utilize custom headers solely for conveying non-essential information. Clients and servers should gracefully handle scenarios where expected custom headers are absent.

2. **Behavior Modification:** Avoid using custom headers to alter HTTP method behavior, restricting such changes to the POST method. If the conveyed information is vital, include it in the body or URI of the request or response instead of relying on custom headers.

3. **WordPress Example:** Headers like X-Powered-By and X-Pingback in WordPress responses are informational and can be ignored without functionality loss. X-Forwarded-For is another informative header conveying the request source.

4. **Non-Informational Headers:** Headers like X-Example-Version, X-Example-Client-Id, and X-Example-Update-Type are not purely informational. Discourage their usage as they compromise URI and HTTP method conventions, weakening resource identification and operation definition.

5. **X-HTTP-Method-Override:** Use caution with headers like X-HTTP-Method-Override. Originally from Google, it allows method tunneling, demonstrated by a POST request with an overridden PUT method. Employ it judiciously to avoid conflicts with standard methods.

By following these guidelines, developers can harness the flexibility of custom headers without compromising system interoperability and maintain cleaner HTTP practices.

### When to Use Custom HTTP Methods
Avoid nonstandard custom HTTP methods for compatibility with off-the-shelf software. Design a controller resource for abstract operations and utilize the standard HTTP method POST.

- **WebDAV Methods**: WebDAV defines methods like PROPFIND, PROPPATCH, MOVE, LOCK, UNLOCK for distributed authoring and versioning.

- **Other Examples**: PATCH for partial updates, MERGE for resource merging.

- **Considerations**: Nonstandard methods are treated similarly to POST by proxies, caches, and HTTP libraries. Server-provided idempotency and safety guarantees are essential. Use custom methods only when interoperability is not a concern.