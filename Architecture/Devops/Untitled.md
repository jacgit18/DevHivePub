---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
Here's a refined and expanded explanation of the provided Docker commands and other associated shell commands:

---

### **`docker ps`**

- **Purpose**: Lists all **running** Docker containers.
    
- **Usage**:
    
    ```bash
    docker ps
    ```
    
    - Shows a table with information like `CONTAINER ID`, `IMAGE`, `STATUS`, `PORTS`, etc.
- **To List All Containers**: (running or stopped)
    
    ```bash
    docker ps -a
    ```
    

---

### **Starting an Existing Container**

- Use the `CONTAINER ID` or `NAME` from `docker ps -a` to start a container:
    
    ```bash
    docker start <container_id_or_name>
    ```
    
- Example:
    
    ```bash
    docker start 20108660be91
    ```
    

---

### **Tree Command**

- **Purpose**: Displays the directory structure in a tree-like format.
- **`-I` Flag**: Excludes specific directories or files (e.g., `node_modules` or `coverage`).
- **Usage**:
    
    ```bash
    tree -I 'node_modules|coverage'
    ```
    
    - Excludes `node_modules` and `coverage` from the output.

---

### **Executing Commands in a Docker Container**

- **Command**: `docker exec`
- **Flags**:
    - `-it`: Runs the command interactively in the terminal.
- **Usage**:
    
    ```bash
    docker exec -it <container_name_or_id> <command>
    ```
    
- **Examples**:
    1. Update packages in a container:
        
        ```bash
        docker exec -it cautious-barnacle_postgres_1 apt-get update
        ```
        
    2. Install a package (e.g., `nano` editor):
        
        ```bash
        docker exec -it cautious-barnacle_postgres_1 apt-get install nano
        ```
        

---

### **Connecting to a Database Using `psql`**

- Switch to a specific PostgreSQL database using `\c`:
    
    ```sql
    \c proDB
    ```
    
    - `proDB` is the target database name.

---

### **Running a New PostgreSQL Container**

- **Command**: `docker run`
- **Flags**:
    - `--name`: Assigns a name to the container.
    - `-e`: Sets environment variables (e.g., `POSTGRES_USER`, `POSTGRES_PASSWORD`, and `POSTGRES_DB`).
    - `-p`: Maps the host port to the container port (e.g., `5432:5432`).
    - `-d`: Runs the container in detached mode (in the background).
- **Example**:
    
    ```bash
    docker run --name some-postgres \
      -e POSTGRES_USER=postgres \
      -e POSTGRES_PASSWORD=post \
      -e POSTGRES_DB=proDB \
      -p 5432:5432 \
      -d postgres
    ```
    

---

### **Expanded Tips & Best Practices**

1. **Check Running Containers**:
    
    ```bash
    docker ps
    ```
    
    - Use `docker ps -q` to get only container IDs.
2. **Inspect Container Details**:
    
    ```bash
    docker inspect <container_id_or_name>
    ```
    
    - Displays detailed information (e.g., IP address, environment variables).
3. **View Container Logs**:
    
    ```bash
    docker logs <container_id_or_name>
    ```
    
4. **Stop a Running Container**:
    
    ```bash
    docker stop <container_id_or_name>
    ```
    
5. **Remove a Container**:
    
    ```bash
    docker rm <container_id_or_name>
    ```
    
6. **Remove an Image**:
    
    ```bash
    docker rmi <image_id_or_name>
    ```
    
7. **Shortcut for Interactive Shell**:
    
    - Open an interactive terminal in a running container:
        
        ```bash
        docker exec -it <container_name_or_id> bash
        ```
        
    - For Alpine-based containers, use:
        
        ```bash
        docker exec -it <container_name_or_id> sh
        ```
        
8. **Restart a Stopped Container**:
    
    ```bash
    docker restart <container_id_or_name>
    ```
    
9. **Pull a Specific Image**:
    
    ```bash
    docker pull postgres:14-alpine
    ```
    
    - Downloads the specified version of an image (e.g., `Postgres` version `14-alpine`).

---

### **Creating a Bash Script for the Commands**

If you frequently run these commands, you can create a script for easier execution:

**`docker_helper.sh`**:

```bash
#!/bin/bash

echo "Available Options:"
echo "1. List running containers"
echo "2. Start a container"
echo "3. Run a PostgreSQL container"
echo "4. Exec into a container"
echo "5. Show container logs"
echo "6. Exit"

read -p "Select an option: " option

case $option in
  1)
    docker ps
    ;;
  2)
    read -p "Enter container ID or name: " container
    docker start "$container"
    ;;
  3)
    docker run --name some-postgres \
      -e POSTGRES_USER=postgres \
      -e POSTGRES_PASSWORD=post \
      -e POSTGRES_DB=proDB \
      -p 5432:5432 \
      -d postgres
    ;;
  4)
    read -p "Enter container name or ID: " container
    docker exec -it "$container" bash
    ;;
  5)
    read -p "Enter container name or ID: " container
    docker logs "$container"
    ;;
  6)
    echo "Exiting..."
    exit 0
    ;;
  *)
    echo "Invalid option."
    ;;
esac
```

Make it executable and run:

```bash
chmod +x docker_helper.sh
./docker_helper.sh
```