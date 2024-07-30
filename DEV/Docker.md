
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
