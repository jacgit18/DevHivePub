---
tags:
  - web
  - protocol
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Border Gateway Protocol.
Status: Done
Started: 2024-01-31
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: false
---
Border Gateway Protocol (BGP) is a standardized exterior gateway protocol used to exchange routing and reachability information between different autonomous systems (ASes) on the Internet. An autonomous system is a collection of IP networks and routers under the control of a single organization that presents a common routing policy to the internet.

Key features of BGP include:

1. **Path Vector Protocol:** BGP uses a path vector algorithm to make routing decisions based on the path, policies, and metrics associated with routes.

2. **Path Attributes:** BGP uses various attributes (e.g., AS path, next-hop, origin) to describe the paths it can take to reach a particular destination network.

3. **Policy-Based Routing:** BGP allows network administrators to define policies, influencing the selection of routes based on criteria such as path length, network policies, and other routing metrics.

4. **Inter-Domain Routing:** BGP is specifically designed for routing between different autonomous systems, making it an inter-domain routing protocol.

5. **Stability and Scalability:** BGP is designed to provide a stable and scalable routing framework for the Internet, adapting to changes in network topology while avoiding unnecessary routing information exchanges.

BGP plays a crucial role in the global internet routing system, facilitating the exchange of routing information between different internet service providers (ISPs) and ensuring efficient and reliable data transmission across the Internet.