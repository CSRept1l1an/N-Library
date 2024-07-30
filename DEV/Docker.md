
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

## 6. Docker Volumes

### Volume Commands
- **List all volumes:**
```bash
docker volume ls
```

- **Create a volume:**
```bash
docker volume create <volume>
```
Example:
```bash
docker volume create my_volume
```

- **Inspect a volume:**
```bash
docker volume inspect <volume>
```
Example:
```bash
docker volume inspect my_volume
```

- **Remove a volume:**
```bash
docker volume rm <volume>
```
Example:
```bash
docker volume rm my_volume
```

### Using Volumes with Containers
- **Mount a volume to a container:**
```bash
docker run -v <volume>:/path/in/container <image>
```
Example:
```bash
docker run -v my_volume:/data ubuntu
```

- **Mount a host directory as a volume:**
```bash
docker run -v /path/on/host:/path/in/container <image>
```
Example:
```bash
docker run -v /host/data:/container/data ubuntu
```

- **Named volumes:**
```bash
docker run --name <container> -v <volume>:/path/in/container <image>
```
Example:
```bash
docker run --name my_container -v my_volume:/data ubuntu
```

### Volume Usage Examples
- **Persist data between container runs:**
```bash
docker run -v my_volume:/data ubuntu echo "Hello, World!" > /data/hello.txt
```

- **Access data stored in a volume:**
```bash
docker run -v my_volume:/data ubuntu cat /data/hello.txt
```

### Volume Drivers
- **Default local driver**: Creates volumes stored on the local Docker host.
- **Third-party volume drivers**: Allows volumes to be stored on external storage systems (e.g., AWS EBS, NFS).

### Best Practices
- **Use volumes for persistent data storage:** Ensure data is not lost when containers are removed or recreated.
- **Leverage volume drivers:** Utilize external storage systems for scalability and reliability.
- **Organize volume usage:** Use named volumes for clarity and easier management.

### 7. Docker Compose

#### Installation
- **Install Docker Compose on Linux:**
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

- **Verify Installation:**
```bash
docker-compose --version
```

#### Basic Commands
- **Start services defined in a `docker-compose.yml` file:**
```bash
docker-compose up
```
Use the `-d` flag to run in detached mode:
```bash
docker-compose up -d
```

- **Stop and remove containers, networks, images, and volumes:**
```bash
docker-compose down
```

- **Build or rebuild services:**
```bash
docker-compose build
```

- **View output from services:**
```bash
docker-compose logs
```
Use the `-f` flag to follow logs in real-time:
```bash
docker-compose logs -f
```

- **Execute a command in a running service:**
```bash
docker-compose exec <service> <command>
```
Example:
```bash
docker-compose exec web /bin/bash
```

- **List all running services:**
```bash
docker-compose ps
```

#### `docker-compose.yml` File
Example structure of a `docker-compose.yml` file:
```yaml
version: '3'
services:
web:
image: nginx
ports:
  - "80:80"
volumes:
  - ./html:/usr/share/nginx/html
db:
image: postgres
environment:
  POSTGRES_DB: exampledb
  POSTGRES_USER: exampleuser
  POSTGRES_PASSWORD: examplepass
volumes:
  - db_data:/var/lib/postgresql/data
volumes:
db_data:
```

#### Common Options
- **services:** Define the individual services that make up your application.
- **image:** Specify the Docker image to use for the service.
- **build:** Build from a Dockerfile in the current directory or a specified path.
- **ports:** Map ports from the host to the container.
- **volumes:** Mount host directories or named volumes into the container.
- **environment:** Set environment variables for the service.

#### Scaling Services
- **Scale a service to multiple instances:**
```bash
docker-compose up --scale <service>=<number>
```
Example:
```bash
docker-compose up --scale web=3
```

#### Docker Compose Best Practices
- **Use environment variables for configuration:** Store sensitive information and environment-specific configurations outside the `docker-compose.yml` file.
- **Organize multi-container applications:** Keep related services together in the same `docker-compose.yml` file.
- **Utilize named volumes:** Ensure data persistence and easy volume management.
- **Leverage networks:** Use Docker Compose networks to enable communication between services.

By using Docker Compose, you can manage multi-container applications efficiently, streamline the development workflow, and ensure consistent environments across different stages of the application lifecycle.