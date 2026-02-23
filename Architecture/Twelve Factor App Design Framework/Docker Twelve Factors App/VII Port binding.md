---
tags:
  - methodology
  - Docker
  - 12FactorApp
  - CodebaseDecision
  - networking
author:
  - jacgit18
  - chatgpt
Purpose: This documentation Twelve Factor App, factor seven in the context of Docker.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 1
dg-publish:
---
Port binding: Your app should be self-contained and bind to a specific port  for external access. Docker enables you to expose and map container ports to host ports, allowing external access to the app through a designated port. 

Your application's code should be designed to read configuration at runtime, including port numbers, from environment variables or configuration files weather you doing this development, staging, or production environment. 


`Expose` command in docker essentially exposes what port the container should listen on at runtime.

 >[!example] Docker port Mapping: 
```bash
docker run -p 5000:8080 --name containerName -d BaseImageName
```
The "-d" flag detaches, allowing background execution. Port 8080 or the Docker image exposed port is mapped to local port 5000 for browser access.

You can even map the same port number so image port 5000 can mapped to local port 5000

## Port binding In-Depth
Port binding is a fundamental networking concept used to associate a network application or service with a specific port number on a device's network interface. The process of port binding allows the application to listen for incoming network connections on that port. When a client device wants to communicate with the application, it sends data packets to the bound port, enabling the application to receive and process the data.

## Purpose of Port Binding
Port binding is necessary because multiple applications or services may be running on a device simultaneously, all of which may require network communication. To differentiate between these applications and ensure that the correct data is sent to the intended recipient, each application must be associated with a specific port.

![[Twelve Factor App Port binding]]


## Server-side Port Binding: 

In server applications, the port binding process typically involves the following steps:

1. Creating a socket: A socket is a software abstraction that represents the communication endpoint. It allows the application to send and receive data over the network. The server application creates a socket and specifies the transport protocol it wants to use (e.g., TCP or UDP) and the IP address to which the socket should be bound.

2. Binding the socket to a port: After creating the socket, the server application binds it to a specific port number. The combination of the IP address and port number uniquely identifies the server application's network endpoint.

3. Listening for incoming connections: Once the socket is bound to a port, the server application starts listening for incoming connections on that port. It waits for client devices to initiate a connection to the bound port.
    
4. Accepting incoming connections: When a client device establishes a connection to the bound port, the server application accepts the incoming connection, and a new socket is created to handle the communication with that specific client.
  
## Client-side Port Binding: 

In client applications, port binding is typically handled by the operating system rather than the application itself. When a client wants to establish a connection to a server, it specifies the server's IP address and the server's port number in the connection request. The operating system then assigns an available local port as the source port for the client-side of the connection.

The client's operating system handles the actual binding of the local port to the client application. It also manages the dynamic assignment of local ports, ensuring that no port conflicts occur between multiple outgoing connections.


## Dynamic Port Allocation:
In client-server communication, the server is usually bound to a well-known or registered port (e.g., HTTP on port 80). On the client side, when an application initiates a connection to the server, the operating system assigns a dynamically available local port as the source port for the client application. This dynamic port allocation allows multiple clients on the same device to communicate with the server concurrently without conflicting port numbers.
