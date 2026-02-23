---
tags:
  - web
  - servers
  - MacroCodebaseDecision
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses proxies.
Status: Refinement
Started: 
EditDate: 2024-01-30
Relates: 
Peer Reviewed: 0
dg-publish: false
---
In computer networking, a proxy server is a server application that acts as an intermediary between a client requesting a resource and the server providing that resource.  

- **Forward Proxy** serves clients and forwards their requests to external servers.
- **Reverse Proxy** serves as an intermediary for clients and forwards requests to backend servers.
- **Proxy** is a general term encompassing both forward and reverse proxy servers.

The distinction lies in the direction of the proxying: whether it is forwarding client requests to external servers (forward proxy) or forwarding external requests to backend servers (reverse proxy).


## 1\. Proxies

Proxies are intermediary servers that stand between clients and other servers. They play a critical role in enhancing performance, security, and reliability in various network scenarios.


```typescript
import * as http from 'http';
import * as httpProxy from 'http-proxy';

const proxy = httpProxy.createProxyServer({});

const server = http.createServer((req, res) => {
  console.log(`Proxying request to: ${req.url}`);

  // Proxy the request to the target server
  proxy.web(req, res, { target: 'http://example.com' });
});

const PORT = 3000;

server.listen(PORT, () => {
  console.log(`Proxy Server listening on port ${PORT}`);
});
```

This example uses the `http-proxy` library to create a simple HTTP proxy server. Requests to the proxy server are forwarded to `http://example.com`. You can modify the target URL or add more advanced features based on your specific use case.
![[Proxy.jpeg]]

## 1.1 Forward Proxy

Client champion: Acts as your personal gatekeeper, filtering your internet access and protecting your identity. Think of it like a VPN for your everyday browsing.  
  
Security shield: Hides your IP address, deflects malicious attacks, and controls content access, keeping your browsing safe and secure.  
  
Performance booster: Caches frequently accessed content, reducing load times and giving you a smoother web experience.

A forward proxy is a server that acts on behalf of clients to make requests to other servers. Forward proxies can be used for various purposes, such as providing anonymity, enforcing security policies, and caching content.


```typescript
import * as http from 'http';
import * as httpProxy from 'http-proxy';

const proxy = httpProxy.createProxyServer({});

const server = http.createServer((req, res) => {
  console.log(`Forwarding request to: ${req.url}`);

  // Proxy the request to the target server
  proxy.web(req, res, { target: req.url, changeOrigin: true });
});

const PORT = 3000;

server.listen(PORT, () => {
  console.log(`Forward Proxy Server listening on port ${PORT}`);
});
```


`proxy.web(req, res, { target: req.url, changeOrigin: true });` is a key part of creating a forward proxy in the example. Let me explain the significance:

- `proxy.web(req, res, { target: req.url, changeOrigin: true });`: This line utilizes the `http-proxy` library to forward the incoming HTTP request to the target specified in `req.url`. Here, `req.url` contains the target URL that the client is trying to access. The `changeOrigin: true` option modifies the `Host` header in the request to match the target, which can be crucial when forwarding requests to servers that rely on the `Host` header for proper functioning.

In the context of a forward proxy:

- **Forward Proxy:** Forwards client requests to a variety of servers on behalf of the client. The client is unaware of the target server, and the proxy handles the communication with the target server. In this example, `proxy.web` is used to forward the client's request to the specified target server based on the `req.url`.

A forward proxy is typically used to provide anonymity, content filtering, or caching for clients, as the clients make requests through the proxy, and the target servers do not see the original client IP addresses.


## 1.2 Reverse Proxy


  
Server guardian: Stands guard before your precious backend servers, shielding them from the harsh realities of the internet.  
  
Load balancer: Distributes traffic across multiple servers, ensuring smooth performance even under heavy load.  
  
Security fortress: Encrypts communication, filters out malicious requests, and acts as a single point of entry for better security control.


A reverse proxy is a server that handles client requests on behalf of other servers. Reverse proxies can provide load balancing, SSL termination, and content caching, among other benefits.


```typescript
import * as http from 'http';
import * as httpProxy from 'http-proxy';

const proxy = httpProxy.createProxyServer({});

const server = http.createServer((req, res) => {
  console.log(`Handling request for: ${req.url}`);

  // Proxy the request to the target server
  proxy.web(req, res, { target: 'http://localhost:3001' });
});

const PORT = 3000;

server.listen(PORT, () => {
  console.log(`Reverse Proxy Server listening on port ${PORT}`);
});
```

In this example:

- `proxy.web(req, res, { target: 'http://localhost:3001' });`: This line utilizes the `http-proxy` library to forward the incoming HTTP request to the target server specified in the `target` option. In this case, the target server is set to `http://localhost:3001`. Requests to the reverse proxy are forwarded to the specified target server.

This example sets up a basic reverse proxy that listens on port 3000. Incoming requests are then forwarded to the target server at `http://localhost:3001`. Adjust the target URL or add more features based on your specific requirements. Reverse proxies are commonly used for load balancing, SSL termination, or serving multiple services under a single domain.

![](https://miro.medium.com/v2/resize:fit:700/1*oeUPfO992X54Q15f39Nsig.png)

Forward Proxy vs Reverse Proxy



## Proxy server vs VPN 

Proxy and VPN defined. A VPN secures all your network traffic, while a proxy works on an application level. They both hide your IP address, but only a VPN redirects your internet data through an encrypted tunnel. A proxy is suitable for browsing the internet, but it's not as safe and secure as a VPN.