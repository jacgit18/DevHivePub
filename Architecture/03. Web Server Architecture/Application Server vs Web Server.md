---
tags:
  - servers
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the difference between Application Server and Web Servers.
Status: Refinement
Started: 
EditDate: 2024-01-31
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Web Server vs Web App.png]]

As many have said before, web servers handle HTTP petitions, while application servers handle petitions for distributed components. So, maybe the easiest way to understand the difference is to compare the two products in regards to programming environment they offer. 

## Web Server -> Programming Environment 
- IIS : ASP (.NET) 
- Tomcat : Servlet 
- Jetty : Servlet 
- Apache : Php, CGI 

## Application Servers -> Programming Environment 
- MTS : COM+ 
- WAS : EJB 
- JBoss : EJB 
- WebLogic Application Server : EJB 

The crucial difference is that application servers support some distributed component technology, providing features like remote invocation and distributed transactions, like EJB in Java world or COM+ on Microsoft platform. Http server often support some more simple programming environments, often scripting, like ASP (.NET) in case of Microsoft or Servlet--based, including JSP and many other in case of Java or PHP and CGI in case of Apache. 

Other capabilities like load-balancing, clustering, session-failover, connection pooling etc. that used to be in the realm of application servers, are becoming available on web servers as well directly or through some third party products. 

Finally, it is worth noting that the picture is further distorted with "lightweight containers" like Spring Framework, that often supplement the purpose of application servers in more simple manner and without the application server infrastructure. And since distribution aspect in applications is moving from distributed component towards service paradigm and SOA architecture, there is less and less space left for traditional application servers. 

In short, 

The web server is a server that serves static web pages to users via HTTP requests. 

The application server is a server that hosts the business logic for a system. 

It often hosts both long-running/batch processes and/or interop services not meant for human consumption (REST/JSON services, SOAP, RPC, etc). 

Reference: [Stack Overflow](https://stackoverflow.com/questions/936197/what-is-the-difference-between-application-server-and-web-server#:~:text=In%20short,,SOAP,%20RPC,%20etc)