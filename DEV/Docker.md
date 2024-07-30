## 1. Introduction to Docker

### What is Docker?
Docker is an open-source platform designed to simplify the creation, deployment, and management of applications using container technology. Containers are lightweight, portable, and self-sufficient units that package an application along with its dependencies, ensuring that it runs consistently across different computing environments.

### Key Concepts
- **Containers**: Containers encapsulate an application and its dependencies into a single unit, making it portable across various environments. Unlike virtual machines, containers share the host OS kernel, which makes them more lightweight and faster to start.

- **Images**: Docker images are read-only templates used to create containers. An image contains everything needed to run an application, including the code, runtime, libraries, and environment variables. Images are built from a Dockerfile and can be versioned and shared.

- **Dockerfile**: A Dockerfile is a script consisting of a series of instructions on how to build a Docker image. It specifies the base image, copies files, installs dependencies, and defines the commands to run the application.

- **Docker Hub**: Docker Hub is a cloud-based registry service where Docker users can publish and share Docker images. It hosts a wide range of public and private images and facilitates collaboration and distribution.

### Basic Workflow
1. **Create a Dockerfile**: Write a Dockerfile to define the environment and steps required to build your application image. This file includes instructions to install dependencies, copy files, and specify the command to run the application.

2. **Build an Image**: Convert your Dockerfile into a Docker image using the `docker build` command. This process assembles the image according to the instructions in the Dockerfile.
```bash
docker build -t myapp .
```

3. **Run a Container**: Use the `docker run` command to create and start a container from your image. Containers are isolated from the host and other containers, ensuring a consistent runtime environment.
```bash
docker run -d -p 80:80 myapp
```

4. **Manage Containers**: Use Docker commands to manage the lifecycle of your containers, including starting, stopping, and inspecting their status.
```bash
docker ps           # List running containers
docker stop <container_id>  # Stop a container
docker rm <container_id>    # Remove a container
```

### Simplified Commands
- **Pull an Image**: Download a pre-built image from Docker Hub to use as a base or for running containers.
```bash
docker pull nginx
```

- **Run a Container**: Start a container from an image, mapping ports to expose services to the outside world.
```bash
docker run -d -p 80:80 nginx
```

- **List Running Containers**: Check which containers are currently running and their details.
```bash
docker ps
```

- **Stop a Container**: Stop a running container by its ID or name.
```bash
docker stop <container_id>
```

### Example Use Case
Docker is particularly useful for developing and deploying applications in environments where consistency is crucial. For example, if you're developing a web application, you can package it into a Docker container with its dependencies. This container can then be run on any system with Docker installed, ensuring that the application runs the same way regardless of the underlying infrastructure.

### Why Use Docker?
- **Consistency**: Docker containers provide a consistent environment from development to production, minimizing issues related to differences in software versions or configurations.
- **Isolation**: Containers keep applications isolated from one another, reducing the risk of conflicts and improving security.
- **Portability**: Containers can run on any system that supports Docker, making it easier to move applications between different environments, such as local development, staging, and production.
- **Efficiency**: Containers are more lightweight than traditional virtual machines, allowing for faster startup times and better resource utilization.

Docker streamlines the process of building, deploying, and managing applications, making it a valuable tool for modern software development and operations.

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

## 7. Docker Compose

### Installation
- **Install Docker Compose on Linux:**
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

- **Verify Installation:**
```bash
docker-compose --version
```

### Basic Commands
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

### `docker-compose.yml` File
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

### Common Options
- **services:** Define the individual services that make up your application.
- **image:** Specify the Docker image to use for the service.
- **build:** Build from a Dockerfile in the current directory or a specified path.
- **ports:** Map ports from the host to the container.
- **volumes:** Mount host directories or named volumes into the container.
- **environment:** Set environment variables for the service.

### Scaling Services
- **Scale a service to multiple instances:**
```bash
docker-compose up --scale <service>=<number>
```
Example:
```bash
docker-compose up --scale web=3
```

### Docker Compose Best Practices
- **Use environment variables for configuration:** Store sensitive information and environment-specific configurations outside the `docker-compose.yml` file.
- **Organize multi-container applications:** Keep related services together in the same `docker-compose.yml` file.
- **Utilize named volumes:** Ensure data persistence and easy volume management.
- **Leverage networks:** Use Docker Compose networks to enable communication between services.

## 8. Dockerfile

### Basic Instructions
- **FROM**: Specify the base image.
```Dockerfile
FROM ubuntu:20.04
```

- **RUN**: Execute a command during the build process.
```Dockerfile
RUN apt-get update && apt-get install -y python3
```

- **COPY**: Copy files/directories from the host to the image.
```Dockerfile
COPY . /app
```

- **ADD**: Similar to COPY, but also supports URLs and tar extraction.
```Dockerfile
ADD https://example.com/file.tar.gz /app
```

- **CMD**: Provide a default command to run when the container starts. Only one CMD instruction is allowed.
```Dockerfile
CMD ["python3", "/app/myapp.py"]
```

- **ENTRYPOINT**: Configure a container that will run as an executable.
```Dockerfile
ENTRYPOINT ["python3", "/app/myapp.py"]
```

- **EXPOSE**: Expose a port for the container.
```Dockerfile
EXPOSE 80
```

- **ENV**: Set environment variables.
```Dockerfile
ENV APP_ENV=production
```

- **VOLUME**: Mount a host directory or named volume.
```Dockerfile
VOLUME /data
```

- **WORKDIR**: Set the working directory for the container.
```Dockerfile
WORKDIR /app
```

### Example Dockerfile
```Dockerfile
# Use an official Python runtime as a parent image
FROM python:3.8-slim

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the current directory contents into the container at /usr/src/app
COPY . .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```

### Common Dockerfile Patterns
- **Multi-stage Builds**: Optimize the build process by reducing the final image size.
```Dockerfile
FROM golang:1.16 as builder
WORKDIR /app
COPY . .
RUN go build -o myapp

FROM alpine:latest
COPY --from=builder /app/myapp /myapp
CMD ["/myapp"]
```

- **Cache Dependencies**: Separate the installation of dependencies to leverage Docker's layer caching.
```Dockerfile
FROM node:14
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
CMD ["node", "server.js"]
```

- **Minimal Base Images**: Use minimal base images like `alpine` to reduce image size.
```Dockerfile
FROM alpine:3.12
RUN apk add --no-cache python3 py3-pip
COPY . /app
WORKDIR /app
RUN pip3 install -r requirements.txt
CMD ["python3", "app.py"]
```

### Best Practices
- **Minimize Layers**: Combine multiple RUN instructions into a single one to reduce the number of layers.
- **Leverage Caching**: Order instructions to maximize the use of Docker’s build cache.
- **Keep Images Small**: Use minimal base images and clean up unnecessary files to reduce image size.
- **Use Multi-stage Builds**: Separate the build and runtime environments to optimize the final image.

## 9. Security Best Practices

### General Guidelines
- **Run Containers as Non-Root Users:**
- Running containers as the root user can pose security risks. It's best to create a non-root user in your Dockerfile.
```Dockerfile
FROM ubuntu:20.04
RUN useradd -ms /bin/bash nonrootuser
USER nonrootuser
```

- **Minimize the Number of Layers:**
- Each layer in a Docker image represents a potential attack surface. Combine multiple commands into a single `RUN` instruction to reduce layers.
```Dockerfile
RUN apt-get update && apt-get install -y \
	package1 \
    package2 \
    package3 && \
    rm -rf /var/lib/apt/lists/*
```

- **Use Official and Trusted Base Images:**
- Always start with a minimal, trusted base image. Official images from Docker Hub are typically maintained and updated for security.
```Dockerfile
FROM python:3.8-slim
```

- **Regularly Update Base Images:**
- Keep your base images up-to-date with security patches and updates.
```bash
docker pull ubuntu:latest
```

- **Scan Images for Vulnerabilities:**
- Use tools like Clair, Trivy, or Docker Bench for Security to scan images for vulnerabilities.
```bash
trivy image myapp:latest
```

### Docker Security Tools
- **Clair:**
- Clair is an open-source project for the static analysis of vulnerabilities in application containers (currently including appc and docker).
```bash
clair-scanner myapp:latest
```

- **Trivy:**
- Trivy is a comprehensive and easy-to-use vulnerability scanner for containers.
```bash
trivy image myapp:latest
```

- **Docker Bench for Security:**
- Docker Bench for Security is a script that checks for dozens of common best practices around deploying Docker containers in production.
```bash
docker run -it --net host --pid host --cap-add audit_control \
-v /var/lib:/var/lib -v /var/run/docker.sock:/var/run/docker.sock \
--label docker_bench_security \
docker/docker-bench-security
```

### Network Security
- **Use Private Networks:**
- Isolate containers from the public network by using Docker’s network features.
```bash
docker network create --driver bridge my_private_network
```

- **Limit Container Capabilities:**
- Reduce the capabilities of containers to the minimum required for them to function correctly.
```bash
docker run --cap-drop ALL --cap-add NET_ADMIN my_container
```

- **Restrict Ports:**
- Avoid exposing unnecessary ports and restrict the range of ports that are exposed.
```bash
docker run -p 127.0.0.1:8080:8080 my_container
```

### Data and Secrets Management
- **Use Docker Secrets:**
- Store and manage sensitive data using Docker secrets.
```bash
echo "mysecret" | docker secret create my_secret -
docker service create --name my_service --secret my_secret my_image
```

- **Encrypt Data in Transit and at Rest:**
- Use TLS to encrypt data transmitted between containers and ensure that data stored within containers is encrypted.

- **Avoid Hardcoding Secrets:**
- Do not hardcode sensitive information (such as passwords or API keys) in your Dockerfiles or environment variables.

### Image Signing and Verification
- **Use Docker Content Trust:**
- Docker Content Trust (DCT) provides the ability to use digital signatures for data sent to and received from remote Docker registries, ensuring that the image’s content is from a trusted source.
```bash
export DOCKER_CONTENT_TRUST=1
docker pull myrepo/myimage:latest
```

### Monitoring and Auditing
- **Monitor Container Activity:**
- Use tools like Prometheus and Grafana to monitor container metrics and logs.
```bash
docker run -d --name prometheus -p 9090:9090 prom/prometheus
```

- **Audit Docker Daemon Configuration:**
- Regularly audit your Docker daemon configuration and runtime options to ensure they comply with security best practices.