---
tags:
  - Docker
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses docker networks.
Status: Done
Started: 
EditDate: 2024-02-22
Relates: 
Peer Reviewed: 0
dg-publish:
---
In Docker, networks play a crucial role in facilitating communication between containers. When you run multiple containers, they may need to communicate with each other for various reasons, such as sharing data or providing services.

#### Docker Bridge Network From Scratch
#todo/Low/Dev 
- [ ] https://labs.iximiuz.com/tutorials/container-networking-from-scratch

Here are some key points about Docker networks:

1. **Default Bridge Network:**
   - When you run Docker containers without specifying a network, they are attached to the default bridge network.
   - Containers on the same bridge network can communicate with each other using container names as hostnames.

2. **User-Defined Networks:**
   - Docker allows you to create custom networks to isolate containers and control communication between them.
   - You can create a network using the `docker network create` command.

3. **Aliases:**
   - Containers on the same network can be given aliases, allowing them to refer to each other by these aliases.

4. **Service Discovery:**
   - Networks enable service discovery, meaning containers can find and communicate with each other using their container names or aliases.

5. **External Connectivity:**
   - Networks can be configured to provide external connectivity, allowing containers to communicate with services outside the Docker environment.

6. **Linking Containers:**
   - In the past, Docker used the concept of linking containers for communication. However, with modern Docker versions, it's recommended to use user-defined networks instead.

7. **Built-in Drivers:**
   - Docker supports different network drivers, such as bridge, overlay, macvlan, and others, each serving specific use cases.

8. **Docker Compose:**
   - Docker Compose uses YAML files to define multi-container applications. Within a Compose file, you can specify networks, their drivers, and connect services to these networks.

Example Docker Compose snippet:

```yaml
version: '3'
services:
  web:
    image: nginx
    networks:
      - frontend
  api:
    image: myapi
    networks:
      - frontend
      - backend
networks:
  frontend:
  backend:
```

In this example, two networks (`frontend` and `backend`) are defined, and the services (`web` and `api`) are connected to these networks.

Understanding and effectively using Docker networks is crucial for building scalable and maintainable containerized applications.