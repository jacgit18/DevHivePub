---
tags:
  - API
  - HTTP
  - protocol
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the different constraint of an API.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: 
Peer Reviewed: 0
dg-publish: true
---
![[six-paths-of-pain-naruto-w2mrtj5sk0ccusoz.gif]]

### Decoding the Relationship Between REST and HTTP

In the realm of REST APIs, the intertwining of REST and HTTP is a common occurrence, but it's essential to understand that they are not intrinsically linked. Let's unravel the dynamics and explore how they coexist.

**Client > Cache > Server: The Web Triad**

Working with REST APIs often involves traversing the HTTP protocol, the backbone of the World Wide Web. However, it's crucial to recognize that REST and HTTP aren't inherently connected. They simply form a convenient partnership. While REST doesn't mandate running on HTTP, the prevalent usage of RESTful APIs over HTTP on the web has led to their colloquial association.

**Constraint Unveiling: The Essence of REST**

Breaking down the six design constraints of REST sheds light on its nature:

1. **Client-Server Architecture:**
   - Ensures a clear separation of concerns, with clients managing the user interface and servers handling data storage. This separation facilitates portability across diverse clients and interfaces.

2. **Statelessness:**
   - No client context or information is stored on the server between requests. The client is responsible for managing its session state, promoting self-contained and complete requests.

3. **Cacheability:**
   - Ingrained caching mechanisms optimize web architecture. REST responses must be explicitly marked as cacheable or non-cacheable, allowing efficient caching strategies.

4. **Layered System:**
   - Design must accommodate intermediary layers, ensuring clients remain agnostic to whether they connect directly to the server or via intermediaries like mirrors or CDNs. This enhances scalability and security.

5. **Code on Demand:**
   - Servers can transfer executable code (e.g., client-side JavaScript) to extend client functionality. While less common, it adds flexibility to REST.

6. **Uniform Interface:**
   - Further broken down into four constraints:
     - **Resource Identification in Requests:**
       - A URI specifies the desired resource, crucial in REST systems on the web.
     - **Resource Manipulation Through Representations:**
       - Clients, with the right access, can modify or delete resources based on their representations.
     - **Self-Descriptive Messages:**
       - Representations must describe their data format for reliable parsing.
     - **Hypermedia as the Engine of Application State (HATEOAS):**
       - Clients, upon accessing a resource, should discover all available resources and methods through provided hyperlinks.

**RESTful on the Web: The HTTP Dance**

When a REST service runs on the web over HTTP, providing access to a web resource, it earns the designation of a RESTful API. The essence lies in adhering to the six constraints while leveraging HTTP to interact with the service.

**Key HTTP Verbs for RESTful Interaction:**
- **POST:** Create a resource on the server.
- **GET:** Retrieve a resource from the server.
- **PUT:** Change or update the state of a resource.
- **DELETE:** Remove or delete a resource from the server.

In essence, the pairing of REST and HTTP, while not a strict mandate, has become a powerful and prevalent alliance, defining the landscape of web services. Understanding their collaboration unlocks the potential for building efficient, scalable, and interoperable systems.