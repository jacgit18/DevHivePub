---
tags:
  - web
  - protocol
  - OSI
  - DNS
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Internet Protocol.
Status: Refinement
Started: 
EditDate: 2024-01-31
Relates: 
Peer Reviewed: 0
dg-publish: false
---
![[Protocol.gif]]

#todo/BAU/noteRefine 
- [ ] clean up

Almost all the protocols we use and love on the backend are either built on top of TCP or UDP. That is why understanding the differences between this two help the engineer make the right choice. For instance, TCP is a stream-based connection-oriented protocol while UDP is a message based and connection-less. TCP provides reliable delivery at a cost of connection setup and re-transmission. While UDP starts faster but doesn’t have guaranteed delivery. Anything you build on top of these two protocols must adhere to their fundamental properties. TCP is not better than UDP, and UDP is not better than TCP. It all depends on what you are building.

Moving up the stack, the HTTP protocol was originally built on top of TCP because we wanted to send requests and responses reliably. As the web evolved and resources become richer, one connection was not sufficient to concurrently send multiple requests. So browsers started to establish more and more connections, the cost of connection setup for each request became so high.

HTTP/2 introduced application level streams so multiple requests can be sent on the same connection. Later HTTP/2 evolved and had to be rewritten on top of UDP with HTTP/3 to solve the TCP head of line problem. There are reasons for everything, the fundamental feature of TCP was the culprit of this move. It doesn’t mean TCP is bad the web has evolved in a way that TCP is no longer suitable. If we didn’t know how TCP works we would not have improved the HTTP protocol.

It is also important to know that using any protocol comes with a cost especially while building APIs. Understanding that cost will help you make better informed decisions. For example, using HTTP/2 might give you more HTTP request throughput, but the work the application needs to do to assemble the streams taxes the CPU, something [Lucidchart](https://www.lucidchart.com/techblog/2019/04/10/why-turning-on-http2-was-a-mistake/) learned the hard way.

Sometimes the backend architecture requires real-time Bidirectional communication protocols to build chatting, gaming apps or just communicating between two services. Protocols such as WebSockets, gRPC or just raw TCP/UDP can be used. If you know how a protocol works and what is the strength and weaknesses you will know when to use it.

Ultimately, learning communication protocols is important for a backend engineer, and it is possible to go as deep as desired in any protocol. Maybe one day you will write an RFC proposing a new protocol.

![[2025-12-23 17.38.10 photos.google.com 0d538aab8012.png]]


#### Website Hosting and Servers
   - Websites are hosted on servers.
   - Clients (like personal computers) connect to these servers through ISPs (Internet Service Providers).

#### Data Transmission in Packets
   - Data is broken down into packets with headers for efficient transmission.
   - These packets are guided by routers to avoid confusion.

#### Transmission Control Protocol (TCP) Layers
   - **Application Layer:**
     - Includes protocols like HTTP, HTTPS, SMTP, FTP used by internet browsers.
   - **Transport Layer:**
     - Houses TCP and UDP, facilitating communication between ports.

#### TCP Breaks Down Data
   - TCP breaks down data into packets with headers for reliable and ordered delivery.

#### Internet Layer
   - Attaches origin and destination IP addresses to packets.

#### DNS Resolution
   - When data reaches the internet layer, it may go through DNS (Domain Name System) resolution.
   - DNS checks the URL and domain names (like ".com") and matches them to IP addresses.

#### Network Layer and MAC Addressing
   - The network layer handles MAC (Media Access Control) addressing.

#### IP Address and DNS Caching
   - DNS checks the IP address associated with a URL.
   - Computers cache DNS information locally for quick retrieval.
   - If a site changes its IP address, accessing it may result in a 404 error due to outdated DNS information.

 The internet communication process involves the efficient transmission of data in packets, guided by various protocols and layers, with DNS playing a crucial role in matching URLs to IP addresses. Local caching helps improve the speed of accessing frequently visited websites, but outdated information can lead to errors. 



![[Network Protocols.gif]]



![[OSI Layer.jpg]]
<mark style="background: #BBFABBA6;">7 user levels with certain protocols are used  and data is created to be sent or is opened after received </mark>

<mark style="background: #BBFABBA6;">6 data is formatted and encryption is handled here </mark>

<mark style="background: #BBFABBA6;">5 handles if a connection is on or off </mark>

<mark style="background: #ABF7F7A6;">4 transport layer adds source and destination for ports and we use either udp or tcp </mark>

<mark style="background: #ABF7F7A6;">3 this layer  handles routing the source and destination are added and routers are used </mark>

<mark style="background: #FFB86CA6;">2 physical address are assigned to the data for the source and destination mac address and switches are used here </mark>

<mark style="background: #FFB86CA6;">1 is like the Ethernet   </mark>


![[OSI Layer.gif]]

![[Network security By Layer.gif]]

![[Network Protocols Applied.jpeg]]



HTTP, a stateless application-level request/response protocol, utilizes extensible semantics and self-descriptive message payloads for flexible interaction with network-based hypertext information systems. It operates through message exchange over a reliable transport or session-layer "connection." While state management mechanisms like cookies exist in HTTP, they facilitate session management on the server side without fundamentally rendering HTTP stateful.

Hypertext Transfer Protocol Secure is an extension of the Hypertext Transfer Protocol. It is used for secure communication over a computer network, and is widely used on the Internet. In HTTPS, the communication protocol is encrypted using Transport Layer Security or, formerly, Secure Sockets Layer.

The Simple Mail Transfer Protocol is an internet standard communication protocol for electronic mail transmission. Mail servers and other message transfer agents use SMTP to send and receive mail messages

The File Transfer Protocol is a standard communication protocol used for the transfer of computer files from a server to a client on a computer network. FTP is built on a client–server model architecture using separate control and data connections between the client and the server.





