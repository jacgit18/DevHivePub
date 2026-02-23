---
tags:
  - Docker
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the purpose of bind mounts.
Status: Done
Started: 2024-01-09
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
A bind mount in containerization allows you to link a directory or file from the host machine to a directory inside the container, creating a shared view of the data. To persist changes made inside a container to the host machine, you would use a bind mount.

1. Create a bind mount when running the container, specifying the source (host) and target (container) directories:
   ```
   docker run -v /host/path:/container/path -it image_name
   ```

2. Make changes to the code within the container, and those changes will be reflected in both the container and the host machine due to the bind mount.

3. To ensure the changes persist on the host machine, save the changes within the container to the mounted directory.

This way, any modifications made inside the container are directly reflected on the host machine through the bind mount.


In a Docker Compose file, you can define bind mounts using the `volumes` key. Here's an example of how to set up a bind mount in a `docker-compose.yml` file:

```yaml
version: '3'

services:
  your_service_name:
    image: your_image_name
    volumes:
      - /host/path:/container/path
```

Replace `your_service_name` with the actual name of your service and `your_image_name` with the name of the Docker image you are using.

This configuration specifies a bind mount where the `/host/path` on the host machine is linked to the `/container/path` inside the container.

After defining the bind mount in your Docker Compose file, any changes made within the container to the linked path (`/container/path`) will be reflected on the host machine at `/host/path`, allowing the changes to persist on your local machine.


bind mounts are primarily configured during the runtime of a container, and they are not typically defined in a Dockerfile. In a Dockerfile, you focus on specifying the image's build instructions.

Bind mounts are established when you run a container using the `-v` or `--volume` option with the `docker run` command or by defining them in a Docker Compose file.

To persist changes in the code from within a container to the host machine, you would set up bind mounts as part of the container runtime configuration rather than within the Dockerfile itself.