---
tags:
  - security
  - vulnerability
  - OSI
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses attack vectors.
Status: Done
Started: 2024-02-04
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: true
---
![[Security By OSI Layer.jpeg]]

1. **Physical Layer:**
   - *Attack Vector:* Physical tampering, cable tapping, or electromagnetic interception.
   - *Example:* Eavesdropping on unencrypted network cables.

2. **Data Link Layer:**
   - *Attack Vector:* MAC address spoofing, ARP spoofing, or VLAN hopping.
   - *Example:* ARP poisoning to redirect traffic in a local network.

3. **Network Layer:**
   - *Attack Vector:* IP spoofing, ICMP attacks, or routing attacks.
   - *Example:* IP spoofing to deceive routers about the source of network packets.

4. **Transport Layer:**
   - *Attack Vector:* SYN/ACK attacks, session hijacking, or DDoS attacks.
   - *Example:* SYN flood attacks overwhelming a server with connection requests.

5. **Session Layer:**
   - *Attack Vector:* Session hijacking, man-in-the-middle attacks.
   - *Example:* Intercepting and taking control of an established session.

6. **Presentation Layer:**
   - *Attack Vector:* Malformed data injections or code injections.
   - *Example:* SQL injection targeting application layer vulnerabilities.

7. **Application Layer:**
   - *Attack Vector:* Cross-site scripting (XSS), SQL injection, or phishing.
   - *Example:* Exploiting vulnerabilities in a web application through XSS to steal user data.

Understanding these attack vectors at each layer helps in implementing effective security measures and mitigating potential threats.

