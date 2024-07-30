
## 3. Basic Commands

### Images
- **Download an image from Docker Hub:**
```bash
docker pull <image>
```
Example:
```bash
docker pull ubuntu
```

- **List all downloaded images:**
```bash
docker images
```

- **Remove an image:**
```bash
docker rmi <image>
```
Example:
```bash
docker rmi ubuntu
```

### Containers
- **Run a container:**
```bash
docker run <image>
```
Example:
```bash
docker run ubuntu
```

- **List running containers:**
```bash
docker ps
```

- **List all containers (running and stopped):**
```bash
docker ps -a
```

- **Stop a running container:**
```bash
docker stop <container>
```
Example:
```bash
docker stop my_container
```

- **Remove a container:**
```bash
docker rm <container>
```
Example:
```bash
docker rm my_container
```

- **Run a command in a running container:**
```bash
docker exec -it <container> <command>
```
Example:
```bash
docker exec -it my_container /bin/bash
```

## 4. Advanced Commands

### Images
- **Build an image from a Dockerfile:**
```bash
docker build -t <tag> .
```
Example:
```bash
docker build -t myapp:latest .
```

- **Tag an image:**
```bash
docker tag <image> <repository>/<tag>
```
Example:
```bash
docker tag myapp:latest myrepo/myapp:latest
```

- **Push an image to a repository:**
```bash
docker push <repository>/<tag>
```
Example:
```bash
docker push myrepo/myapp:latest
```

### Containers
- **Start a stopped container:**
```bash
docker start <container>
```
Example:
```bash
docker start my_container
```

- **Restart a running container:**
```bash
docker restart <container>
```
Example:
```bash
docker restart my_container
```

- **View logs of a container:**
```bash
docker logs <container>
```
Example:
```bash
docker logs my_container
```

- **Inspect detailed information of a container:**
```bash
docker inspect <container>
```
Example:
```bash
docker inspect my_container
```

- **Create a new image from a container’s changes:**
```bash
docker commit <container> <repository>/<tag>
```
Example:
```bash
docker commit my_container myrepo/myapp:latest
```

## 5. Networking

### Basic Commands
- **List all networks:**
```bash
docker network ls
```

- **Create a network:**
```bash
docker network create <network>
```
Example:
```bash
docker network create my_network
```

- **Inspect a network:**
```bash
docker network inspect <network>
```
Example:
```bash
docker network inspect my_network
```

- **Connect a container to a network:**
```bash
docker network connect <network> <container>
```
Example:
```bash
docker network connect my_network my_container
```

- **Disconnect a container from a network:**
```bash
docker network disconnect <network> <container>
```
Example:
```bash
docker network disconnect my_network my_container
```

### Usage Examples
- **Run a container with a specific network:**
```bash
docker run --network <network> <image>
```
Example:
```bash
docker run --network my_network nginx
```

- **Create a bridge network:**
```bash
docker network create --driver bridge <network>
```
Example:
```bash
docker network create --driver bridge my_bridge_network
```

- **Create an overlay network (for Swarm mode):**
```bash
docker network create --driver overlay <network>
```
Example:
```bash
docker network create --driver overlay my_overlay_network
```

### Networking Concepts
- **Bridge Network**: The default network driver. Suitable for standalone containers that need to communicate on the same Docker host.
- **Overlay Network**: Used for multi-host network communication in Swarm mode. Allows containers running on different Docker hosts to communicate.
- **Host Network**: Removes network isolation between the container and the Docker host. The container shares the host's network stack.
- **None Network**: Disables networking for the container. Useful for isolated workloads that do not require network access.

