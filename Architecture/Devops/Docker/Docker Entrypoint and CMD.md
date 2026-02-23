---
tags:
  - Docker
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the docker Entrypoint and CMD commands.
Status: Done
Started: 
EditDate: 2024-02-22
Relates: 
Peer Reviewed: 0
dg-publish:
---
Dockerfile, the "entry point" is a configuration that specifies the default command that should be run when a Docker container is started from the image created by that Dockerfile. It's like the initial process that kicks off when the container begins. This could be a script, an executable, or a command.

The "CMD" instruction in a Dockerfile is used to set the default command and its arguments that will be executed when the container is started, unless a command is provided when running the container. The CMD instruction can be overridden by providing a command when you start the container using the `docker run` command.

Use Entrypoint instead of CMD in Docker because it is immutable.

`Ctrl + p + q` to exit container but keep it running.

Here's an example of how they might be used in a Dockerfile:

```Dockerfile
FROM ubuntu:latest
COPY my_script.sh /my_script.sh
RUN chmod +x /my_script.sh
ENTRYPOINT ["/my_script.sh"]
CMD ["default_arg"]
```

In this example, the `ENTRYPOINT` specifies that the `/my_script.sh` script will be the initial process of the container. The `CMD` provides a default argument `default_arg` to the script. If you run the container without specifying a command, the script will be executed with the default argument. But you can also override the command by providing your own arguments when starting the container:

```bash
docker run my_image argument_override
```

This would run the container with the `my_script.sh` script and the argument "argument_override".


Certainly! Here are a few more examples to help you understand how the `CMD` and `ENTRYPOINT` instructions work in Dockerfiles:

**Example 1: Running a Simple Command**
```Dockerfile
FROM alpine:latest
CMD ["echo", "Hello, Docker!"]
```
In this case, if you run the container without specifying a command, it will execute the `echo "Hello, Docker!"` command as the default behavior.

**Example 2: Running a Python Script**
```Dockerfile
FROM python:3.9
COPY my_script.py /my_script.py
CMD ["python", "/my_script.py"]
```
If you don't provide a command when starting the container, it will execute the Python script `/my_script.py`.

**Example 3: Entrypoint with Arguments**
```Dockerfile
FROM ubuntu:latest
COPY entrypoint_script.sh /entrypoint_script.sh
RUN chmod +x /entrypoint_script.sh
ENTRYPOINT ["/entrypoint_script.sh"]
```
In this example, the `entrypoint_script.sh` will be executed as the initial process of the container. It can take additional arguments provided when you start the container.

**Example 4: Combining CMD and Entrypoint**
```Dockerfile
FROM nginx:latest
COPY custom-index.html /usr/share/nginx/html/index.html
CMD ["nginx", "-g", "daemon off;"]
```
Here, the default behavior is to start the Nginx web server with the provided configuration. The `CMD` specifies the command to run, and the `ENTRYPOINT` would be inherited from the base Nginx image.

**Example 5: Using Shell Form**
```Dockerfile
FROM ubuntu:latest
CMD echo "Hello from Docker!"
```
In this case, the `CMD` instruction uses the shell form, so the command will be executed within a shell. This allows you to use shell features like variable expansion.

Remember that the `CMD` instruction is often used to provide default command arguments, while the `ENTRYPOINT` instruction is used to specify the main command that's run when the container starts. They can be used separately or together depending on your use case.


# COPY Explained

In the Docker examples I provided, the `COPY` instruction is used to copy files or directories from the host machine (the machine where you're building the Docker image) into the image itself. This allows you to include files from your local filesystem into the Docker image you're creating.

Here's a breakdown of how the `COPY` instruction is used in the examples:

**Example 2: Running a Python Script**
```Dockerfile
COPY my_script.py /my_script.py
```
In this example, the `my_script.py` file from the host machine is copied into the root directory (`/`) of the Docker image. This makes the script available within the image so that it can be executed when the container is started.

**Example 3: Entrypoint with Arguments**
```Dockerfile
COPY entrypoint_script.sh /entrypoint_script.sh
```
Here, the `entrypoint_script.sh` file from the host machine is copied into the root directory of the Docker image. This script will be used as the entrypoint for the container, meaning it will be executed when the container starts.

**Example 4: Combining CMD and Entrypoint**
```Dockerfile
COPY custom-index.html /usr/share/nginx/html/index.html
```
In this case, the `custom-index.html` file from the host machine is copied into the `/usr/share/nginx/html/` directory within the Docker image. This replaces the default index file of the Nginx web server with the custom one you provided.

**Example 5: Using Shell Form**
```Dockerfile
COPY custom-script.sh /custom-script.sh
```
In this example, the `custom-script.sh` file from the host machine is copied into the Docker image. The script can then be used within the image, for example, as a file that's executed by a `CMD` or `ENTRYPOINT` instruction.

In all these cases, the `COPY` instruction helps include files from the host machine into the Docker image, enabling you to customize the image's contents and behavior.