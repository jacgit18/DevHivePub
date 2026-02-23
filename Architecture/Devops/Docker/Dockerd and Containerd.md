---
tags:
  - Docker
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses difference between Dockerd and Containerd.
Status: Done
Started: 
EditDate: 2024-02-22
Relates: 
Peer Reviewed: 0
dg-publish:
---
Docker and dockerd, as well as container and containerd, are related terms in the context of containerization and container management, but they refer to different components within the container ecosystem.

## Docker vs. dockerd:
   - **Docker:** Docker is a platform that enables developers to automate the deployment, scaling, and management of applications using containerization. Docker provides a command-line interface (CLI) and a graphical user interface (GUI) to interact with containers. It also includes the Docker Engine, which is responsible for building, running, and managing containers. However, Docker as a company and project also encompasses various other tools and services.
   
   - **dockerd:** This term specifically refers to the Docker daemon, which is the background service that manages Docker containers on a system. It is responsible for creating, running, and monitoring containers. Dockerd listens to Docker API requests and manages the Docker containers, images, volumes, and networks.

2. **Container vs. containerd:**
   - **Container:** A container is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software, including the code, runtime, system tools, libraries, and settings. Containers provide a consistent and isolated environment for applications to run, making them portable across different computing environments.
   - **containerd:** Containerd is an industry-standard core container runtime that provides the basic functionality to manage containers. It is designed to be a low-level container runtime focused on executing containers reliably and efficiently. Containerd itself doesn't provide the higher-level functionalities that Docker does, such as the CLI interface, image building tools, or orchestration features. It serves as a building block for container platforms like Docker and Kubernetes.

In summary, Docker is a comprehensive platform that includes tools for creating, managing, and orchestrating containers, while dockerd specifically refers to the Docker daemon responsible for managing containers within the Docker ecosystem. Similarly, a container is a self-contained software unit, while containerd is a core runtime component used for managing containers at a lower level, often forming the basis for more comprehensive container solutions.