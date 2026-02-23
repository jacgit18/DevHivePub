---
tags:
  - web
  - protocol
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses IP addresses.
Status: Done
Started: 
EditDate: 2024-01-30
Relates: 
Peer Reviewed: 0
dg-publish: false
---
An IP (Internet Protocol) address is a numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication. It serves two primary functions: host or network interface identification and location addressing. IP addresses enable devices to send and receive data across the Internet. 

There are two versions of IP addresses in use today: IPv4 and IPv6.


![[IPv4 Structure.png]]
**IPv4 (Internet Protocol version 4):**

IPv4 is the fourth version of the Internet Protocol and the most widely used. It consists of a 32-bit address, expressed as four sets of numbers separated by periods. IPv4 has a limited address space, providing approximately 4.3 billion unique addresses. The growth of the Internet and the increasing number of connected devices led to the exhaustion of available IPv4 addresses, prompting the need for a new protocol.

![[IPV6 Structure.png]]

**IPv6 (Internet Protocol version 6):**

IPv6 is the latest version of the Internet Protocol, designed to address the limitations of IPv4 and accommodate the growing number of devices connected to the Internet. IPv6 uses a 128-bit address, expressed in hexadecimal notation. This significantly expands the number of available unique addresses to an astronomical amount, ensuring sustainable growth for the Internet. IPv6 adoption is gradually increasing to support the evolving requirements of a connected world.

![[IPV6 vs IPV4.jpeg]]

![[ipv4viPV6.gif]]

## Recommended DNS  to Use

Phone DNS  
[1dot1dot1dot1.cloudflare-dns.com](http://1dot1dot1dot1.cloudflare-dns.com/)  
  
Network and PC DNS ipv4  
Primary DNS Server: 1.1.1.1  
Secondary DNS Server: 1.0.0.1  
  
ipv6  
2606:4700:4700::1111  
2606:4700:4700::1001  

## **Main Differences Between IPv6 and IPv4**

IPv4 and IPv6 are both addresses that are used to identify machines connected to a network. They are the same in principle but different in how they work. What are their differences? Below are the main differences between IPv4 and IPv6.

|Differences|IPv4|IPv6|
|---|---|---|
|Addressing Method|A numeric address, and its binary bits are separated by a dot (.)|An alphanumeric address whose binary bits are separated by a colon (:). It also contains hexadecimal.|
|Address Types|Unicast, broadcast, and multicast.|Unicast, multicast, and anycast.|
|Address Mask|Use for the designated network from host portion.|Not used.|
|Number of Header Fields|12|8|
|Length of Header Fields|20|40|
|Checksum|Has checksum fields.|No checksum fields.|
|Number of Classes|Class A to E.|Unlimited number of IP addresses.|
|Configuration|IP addresses and routes must be assigned.|Configuration is optional, depending on functions required.|
|VLSM|Support|Not Support|
|Fragmentation|Done by sending and forwarding routes.|Done by the sender.|
|Routing Information Protocol|Supported by the routed daemon.|RIP does not support IPv6. It uses static routes.|
|Network Configuration|Manually or with DHCP.|Autoconfiguration.|
|SNMP|SNMP is a protocol used for system management.|SNMP does not support IPv6.|
|Mobility & Interoperability|Relatively constrained network topologies to which move restrict mobility and interoperability capabilities.|IPv6 provides interoperability and mobility capabilities that are embedded in network devices.|
|DNS Records|Pointer (PTR) records, IN-ADDR.ARPA DNS domain|Pointer (PTR) records, IP6.ARPA DNS domain|
|IP to MAC resolution|Broadcast ARP|Multicast Neighbor Solicitation|
|Mapping|Uses ARP(Address Resolution Protocol) to map to MAC address.|Uses NDP(Neighbour Discovery Protocol) to map to MAC address.|
|Quality of Service (QoS)|QoS allows you to request packet priority and bandwidth for TCP/IP applications.|Currently, the IBM i implementation of QoS does not support IPv6.|