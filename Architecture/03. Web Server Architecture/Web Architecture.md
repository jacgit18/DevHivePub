---
tags:
  - web
  - systemDesign
author:
  - jacgit18
Purpose: This documentation discusses Web Architecture.
Status: Refinement
Started: 
EditDate: 2024-03-07
Relates: 
Peer Reviewed: 0
dg-publish:
---
-   Client–Server 
    
    -   The separation of concerns is the core theme of the Web’s client-server constraints. The Web is a client-server based system, in which clients and servers have distinct parts to play. They may be implemented and deployed independently, using any language or technology, so long as they conform to the Web’s uniform interface. 
        
-   Uniform Interface 
    
    -   The interactions between the Web’s components—meaning its clients, servers, and network-based intermediaries—depend on the uniformity of their interfaces. If any of the components stray from the established standards, then the Web’s communication system breaks down. 
        
    -   Web components interoperate consistently within the uniform interface’s four constraints, which Fielding identified as: 
        
        -   Identification of resources -  URI 
            
        
-   Manipulation of resources through representations 
    
    -   Clients manipulate representations of resources. The same exact resource can be represented to different clients in different ways. For example, a document might be represented as HTML to a web browser, and as JSON to an automated program. The key idea here is that the representation is a way to interact with the resource but it is not the resource itself. This conceptual distinction allows the resource to be represented in different ways and formats without ever changing its identifier. 
        
    
-   Self-descriptive messages 
    
    -   A resource’s desired state can be represented within a client’s request message. A resource’s current state may be represented within the response message that comes back from a server. As an example, a wiki page editor client may use a request message to transfer a representation that suggests a page update (new state) for a server-managed web page (resource). It is up to the server to accept or deny the client’s request. 
        
    -   The self-descriptive messages may include metadata to convey additional details regarding the resource state, the representation format and size, and the message itself. An HTTP message provides headers to organize the various types of metadata into uniform fields. 
        
    
-   Hypermedia as the engine of application state (HATEOAS) 
    
    -   A resource’s state representation includes links to related resources. Links are the threads that weave the Web together by allowing users to traverse information and applications in a meaningful and directed manner. The presence, or absence, of a link on a page is an important part of the resource’s current state. 
        
    -   The four interface constraints are summarized in the following subsections. 
        
    
-   Layered System 
    
    -   The layered system constraints enable network-based intermediaries such as proxies and gateways to be transparently deployed between a client and server using the Web’s uniform interface. Generally speaking, a network-based intermediary will intercept client-server communication for a specific purpose. Network-based intermediaries are commonly used for enforcement of security, response caching, and load balancing. 
        
    
    -   The stateless constraint dictates that a web server is not required to memorize the state of its client applications. As a result, each client must include all of the contextual information that it considers relevant in each interaction with the web server. Web servers ask clients to manage the complexity of communicating their application state so that the web server can service a much larger number of clients. This trade-off is a key contributor to the scalability of the Web’s architectural style. 
        
    
    -   The Web makes heavy use of code-on-demand, a constraint which enables web servers to temporarily transfer executable programs, such as scripts or plug-ins, to clients. Code-on-demand tends to establish a technology coupling between web servers and their clients, since the client must be able to understand and execute the code that it downloads on-demand from the server. For this reason, code-on-demand is the only constraint of the Web’s architectural style that is considered optional. Web browser-hosted technologies like Java applets, JavaScript, and Flash exemplify the code-on-demand constraint.