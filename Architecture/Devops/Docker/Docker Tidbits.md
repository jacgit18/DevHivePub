---
tags:
  - Docker
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses tips to with using docker.
Status: Done
Started: 
EditDate: 2024-02-22
Relates: 
Peer Reviewed: 0
dg-publish:
---
Containerizing [[Microservices VS Monolithic Architecture |Microservices]] enhances isolation, employing two "COPY" commands to facilitate dependencies through layered caching in Docker. Utilizing official Docker images from reputable sources, like the node official image, ensures reliability.

For robust security management, Linux commands within Docker RUN, linking commands, and Docker USER effectively handle permissions.

Start afresh using `docker prune` to rectify issues with a problematic images but it's a powerful command that should be used with caution. The `docker prune` command is designed to clean up unused resources, such as dangling images, stopped containers, and networks. It can help free up disk space and remove unnecessary clutter.

You should be mindful of the consequences, as it will remove all stopped containers, networks not used by at least one container, and all dangling images. If you have containers or images that you may need later, make sure to back them up or tag them appropriately before running `docker prune` to avoid unintentional data loss.

Opt for the Alpine image when building a custom one to begin with a clean slate.

Avoid using "latest" as it might not genuinely represent the latest version.

Verify your images with a Docker image command to ensure correctness, especially when dealing with multiple tags.

Consider using bind mounts for configuration or ENV files, demonstrated by the example command:
```bash
docker run -d --name containerName -v /path/to/env:/path/in/container -e ENV_FILE=/path/in/container/envfile.env imageNameToBaseContainerOn
```

Efficiently cache dependencies by running `mvn dependency:resolve` when making no changes to eliminate the need for fetching dependencies multiple times.

For a MySQL Docker run example:
```bash
docker run --name test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=test -e MYSQL_DATABASE=mydatabase -e MYSQL_USER=myuser -e MYSQL_PASSWORD=mypassword -d --env-file /path/to/env/file mysql
```
The "-e" flag sets environment variables.

Docker volumes serve as mirrors, reflecting container contents and providing enduring databases for data persistence. They function as a singular source of truth, accommodating log files and diverse data types across distinct storage spaces.