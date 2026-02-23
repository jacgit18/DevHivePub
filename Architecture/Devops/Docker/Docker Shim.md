---
tags:
  - devops
  - Docker
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses docker shims.
Status: Done
Started: 
EditDate: 2024-02-22
Relates: 
Peer Reviewed: 0
dg-publish:
---
In the context of Docker, a "shim" refers to a small, intermediary component that facilitates communication between the Docker daemon and a container's individual processes. The purpose of a shim is to ensure proper interaction between Docker's higher-level management and orchestration functionalities and the lower-level container runtime.

When you run a Docker container, the Docker daemon is responsible for managing the container's lifecycle, resource allocation, networking, and more. However, the actual execution of the container's processes happens within a lower-level container runtime, such as `runc` (the default runtime used by Docker) or other runtimes like `containerd`.

The shim acts as a bridge between the Docker daemon and the container runtime. Its primary responsibilities include:

1. **Process Management:**
   When you start a container, the Docker daemon communicates with the shim to create, start, stop, and manage the container's processes. The shim is responsible for translating the commands and requests from the Docker daemon into the appropriate actions within the container runtime.

2. **I/O Handling:**
   The shim also manages the input and output (I/O) streams of the container's processes. It ensures that standard input, standard output, and standard error streams are properly connected to the container's processes and are relayed back to the Docker daemon for logging and monitoring.

3. **Signaling:**
   The shim handles signals (such as SIGTERM for graceful termination) sent to the container's processes. It ensures that signals are correctly forwarded to the appropriate processes and that they respond as expected.

4. **Exit Status Reporting:**
   When a container's process exits, the shim captures the exit status and communicates it back to the Docker daemon. This information is used to determine the container's overall exit status and to take appropriate actions based on that status.

5. **Cleanup:**
   After a container has finished running or has been stopped, the shim is responsible for performing necessary cleanup tasks within the container runtime, ensuring that resources are properly released.

Overall, the shim serves as an essential component that bridges the gap between the Docker daemon's high-level orchestration and the low-level details of process management and execution within the container runtime. It allows Docker to remain agnostic to the specifics of different container runtimes while providing a consistent interface for container management.

It's important to note that while shims play a crucial role in Docker's operation, they are not typically something that users need to directly interact with or configure. They are automatically managed by Docker and the underlying container runtime.