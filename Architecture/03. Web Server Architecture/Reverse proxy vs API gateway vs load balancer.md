---
tags:
  - proxy
  - API
  - loadBalancer
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the difference between reverse proxies, API gateway, and load balancer.
Status: Refinement
Started: 
EditDate: 2024-03-06
Relates: "[[Network Infrastructure to use]]"
Peer Reviewed: 0
dg-publish:
---
![[Proxy v Gateway v Balancer .jpeg]]

As modern websites and applications are like busy beehives, we use a variety of tools to manage the buzz. Here we'll explore three superheroes: Reverse Proxy, API Gateway, and Load Balancer.  

## [[API Gateway]]: postman  
- Delivers requests to the right services.  
- Ideal for bustling applications with numerous intercommunicating services.  

## [[Load Balancer]]: traffic cop
- Directs traffic evenly across servers, preventing bottlenecks  
- Essential for popular websites with heavy traffic and high demand.  
## [[Proxy |Reverse Proxy]]: change identity  
- Fetching data secretly, keeping servers hidden. 
- Perfect for shielding sensitive websites from cyber-attacks and prying eyes.  
  

![[loadvReverse.gif]]

In a nutshell, choose a Reverse Proxy for stealth, an API Gateway for organized communications, and a Load Balancer for traffic control. Sometimes, it's wise to have all three - they make a super team that keeps your digital kingdom safe and efficient.