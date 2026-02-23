---
tags:
  - Docker
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses namespaces.
Status: Done
Started: 
EditDate: 2024-02-22
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Namespace docker.jpg]]
In the context of Docker and operating systems, namespaces are a fundamental feature that provides process isolation and resource separation for running containers. Namespaces are a key building block that allows multiple processes to run in isolated environments, as if they were running on separate instances of the operating system. Each namespace encapsulates a specific aspect of the system's resources, creating a barrier that prevents processes in different namespaces from interfering with each other.


![[Control Groups.jpg]]
Docker uses various types of namespaces to provide isolation for different resources:

1. **PID Namespace (Process ID Namespace):**
   This namespace isolates the process IDs of different containers. Each container has its own unique set of process IDs, which means that process 1 in one container is not the same as process 1 in another container. This separation prevents one container's processes from affecting or interacting with processes in other containers.

2. **UTS Namespace (Hostname Namespace):**
   The UTS namespace allows each container to have its own hostname and domain name. This isolation is helpful in scenarios where containers need distinct identification, even if they are running on the same physical host.

3. **IPC Namespace (Inter-Process Communication Namespace):**
   IPC namespaces provide isolation for inter-process communication mechanisms like message queues and semaphores. Containers within different IPC namespaces can't directly interact with the IPC resources of other containers.

4. **Network Namespace:**
   Network namespaces isolate network-related resources, such as network interfaces, IP addresses, routing tables, and firewall rules. This allows containers to have their own network stack, making them appear as separate entities on the network.

5. **Mount Namespace:**
   Mount namespaces isolate the filesystem mounts seen by a container. This means that a container's filesystem can be different from the host system or other containers. Each container has its own isolated view of the filesystem, which enhances security and isolation.

6. **User Namespace:**
   User namespaces provide isolation of user and group IDs between the host and containers. This allows processes running in a container to have a different set of user and group IDs from those on the host, improving security by minimizing the privileges of containerized processes.

7. **Cgroup Namespace:**
   Control group (cgroup) namespaces enable separate cgroup hierarchies for containers. This allows for independent resource allocation and control over CPU, memory, and other resources for each container.

By leveraging these namespaces, Docker creates isolated and independent environments for running containers, ensuring that processes within each container are unaware of the presence of other containers and are isolated from their resources. This isolation helps enhance security, manage resource utilization, and enables better scalability for containerized applications.