---
tags:
  - API
  - REST
  - web
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses REST API.
Status: Done
Started: 
EditDate: 2024-03-02
Relates: 
Peer Reviewed: 0
dg-publish: true
---
An API, or Application Programming Interface, acts as a set of features and rules within a software program, facilitating interactions with other software or hardware. In the context of REST APIs, it provides public and private tools for accessing and manipulating REST resources through verbs such as GET, POST, PUT, and DELETE.

### Use Cases of RESTful API
- Building web services: RESTful APIs are commonly used to expose functionality and data from web applications to other systems or clients over the internet.  
- Integrating systems: RESTful APIs enable different systems and applications to communicate and share data with each other in a standardized and interoperable manner.  
- Mobile app development: RESTful APIs are often used as backend services for mobile apps, allowing them to interact with server-side resources and perform operations such as user authentication, data retrieval, and updates.  
- Internet of Things (IoT): RESTful APIs can be used to facilitate communication between IoT devices and backend servers, enabling real-time data exchange and control of connected devices.

### API vs Servers
APIs are deployed on servers, but it's important to understand that a server's capabilities extend far beyond hosting APIs. For instance, a server might be configured to perform regular tasks such as backing up your database every 24 hours, showcasing its versatile role in both maintenance and functionality.

APIs, fundamentally, are designed to implement protocols that enable data transfer between two or more applications. This communication is essential for integrating and extending the capabilities of different software systems.

Traditionally, a server refers to the physical hardware that hosts applications, often tasked with critical back-end functions like database access, and facilitating interactions (via APIs) with other server-hosted applications. This highlights a server's pivotal role in the underlying infrastructure that supports application functionalities.

It's crucial to note that the scope of APIs is not confined to server-side applications. APIs serve as a communication protocol between any two applications, regardless of where they are hosted. This broad applicability of APIs underscores their importance in building interconnected, efficient, and scalable digital ecosystems.

#### Understanding Declarative vs. Imperative APIs

Declarative APIs, often at the heart of what is referred to as “policy” or “intent-based” networking, focus on the "what" of operations. They represent a desired state system where the user specifies the end state they wish to achieve without detailing the steps required to get there. Essentially, with a declarative API, you instruct the system on the state you desire, saying: "Ensure this state is achieved," without concerning yourself with the how.

While it might seem that all API interactions are declarative, since they typically instruct the server on the desired outcome rather than the process to achieve it, the level of abstraction can vary. This variation affects how closely an API call might be perceived as declarative.

##### Conclusion: Declarative APIs Focus on the "What"

Conversely, imperative programming, which can be paralleled in API terms, emphasizes the "how" of operations. It involves commands that the computer executes to change the system's state, mirroring the imperative mood in language that issues commands. In the realm of APIs, Create, Update, or Delete operations (constituting three-quarters of CRUD operations) are imperative in nature as they direct the system to change its state. These API calls may range from vague to precise instructions on how to perform a task.

##### Conclusion: Many API Calls are Imperative

The distinction between declarative and imperative approaches in APIs is nuanced and often boils down to the level of abstraction and the atomicity of the operations requested. Describing API calls as purely declarative or imperative oversimplifies the complexity and diversity of API design and functionality. What is pivotal is understanding the abstraction level an API provides and how it allows users to articulate their intent or desired outcomes.

In essence, the debate over declarative vs. imperative APIs underscores the importance of clarity, abstraction, and the specificity of intent in API design and interaction.



### Representational State Transfer (REST)

REST, or Representational State Transfer, is not a specific technology but a set of software architecture design constraints aimed at ensuring efficient, reliable, and scalable systems. It centers around standardized methods, known as verbs, to produce predictable outcomes by handling structured data, typically in JSON or XML formats. Representational State Transfer describes the transition between states, symbolizing the exchange of representations between applications and servers.

#### Transition from Traditional Websites to Web Applications

Unlike traditional websites, where each page involves a complete HTML document, web applications follow a more resource-efficient approach. They download an application framework, style sheets, and JavaScript during the initial load. Subsequent navigation involves sending Universal Resource Identifier (URI) requests for specific web resources, enabling the application to dynamically update views without downloading entire documents.

#### Single Page Applications and REST Resources

This approach facilitates the creation of single-page applications and unified experiences across different platforms. For example, platforms like LinkedIn utilize the same REST resource to provide data for both web browsers and mobile applications.

#### API Design Considerations

While designed for program-to-program interactions, APIs are crafted to be understood and utilized by humans writing the code for those interactions. API design reveals insights into the underlying program, encompassing elements like business models, product features, and occasional bugs.

In essence, the synergy of REST and API forms the backbone of modern web development, offering scalable, efficient, and user-friendly solutions for building dynamic applications and interfaces.

## RESTful Routing
### RESTful Essence
- The addition of "ful" not only emphasizes completeness but also promotes the adoption of this technology/pattern by framing it within a word with positive connotations.

### Resource-Centric Approach
- At its core, RESTful routing revolves around the concept of resources representing entities in the system, such as articles, users, or any data that can undergo CRUD operations.

### CRUD Operations via HTTP
- The fundamental objective is to enable CRUD operations (Create, Read, Update, Delete) on these resources using the HTTP protocol, with each operation corresponding to a specific HTTP verb:
  - **GET:** Retrieve data.
  - **POST:** Create new data.
  - **PUT:** Update existing data.
  - **DELETE:** Remove data.

### Utilization of HTTP Verbs
- The strength of RESTful routing lies in its alignment with HTTP verbs, allowing developers to express actions succinctly and intuitively.

### Consistent and Elegant URLs
- RESTful routing involves creating URLs that are not only consistent but also aesthetically pleasing, promoting readability and maintainability for an overall elegant design.

In essence, RESTful routing provides a structured and intuitive approach to designing APIs and web applications. By aligning with REST principles, developers can create powerful systems adhering to standardized and efficient patterns, fostering best practices in the ever-evolving landscape of web development. Embrace the RESTful philosophy, and let the elegance of your APIs mirror the simplicity and power of the underlying principles.

## Flashcard
#API
What does API stand for;; Application Programming Interface.

What does RESTful stand for;; Representational State Transfer.

What is RESTful API;; an interface that allows systems to communicate and exchange data over HTTP.

What is it based on;; It is based on a set of principles that define how resources are identified and addressed over the web.

What are RESTful API used for;; API are used to expose functionality and data from web applications to other systems or clients over the internet.