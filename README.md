# Docker 
Use This Pdf :
[Docker.pdf](https://github.com/user-attachments/files/17485684/Docker.pdf)


![WhatsApp Image 2024-10-24 at 09 59 44_193092aa](https://github.com/user-attachments/assets/462c3e26-cd0f-4eb7-af08-70aae8b9ca01)

![WhatsApp Image 2024-10-24 at 09 59 45_a1f3bbd9](https://github.com/user-attachments/assets/ac2194b1-8131-4a08-bb48-b05623e9bae6)


# Topics
```json
Intro
What is Docker?
Why we need Docker?
What is a container?
Architecture of Docker
Docker vs. Virtual Machines
Flow of Docker
What is a DockerFile?
What is Docker Registry?
Docker Installation on Windows
Docker Installation on Mac
Docker Installation on Linux
Creating a Demo Project - React Web App
How to create a DockerFile?
How to build a Docker Image?
Managing and Running Containers
Useful Info for Containers
Managing Images
Updating a Project
Pre-defined Images
Running a Container in Interactive Mode
Pushing an Image to DockerHub
How to Pull Images Remotely
Docker Volume
Mount Binds in Docker
Working with APIs
Container with Local Database
Project with Multiple Containers
Docker Network
What is Docker Compose?
Docker Compose for Multiple Containers
Docker Compose with Network
Docker Compose with Volume
Docker Compose with Port Binding
```

# Introduction
Docker is a platform designed to simplify the process of building, shipping, and running applications in containers. Containers allow developers to package applications with all the necessary components, such as libraries and dependencies, and deploy them in a consistent environment.

# 1. What is Docker?
Docker is an open-source platform that automates the deployment of applications inside containers. It enables developers to package applications into standardized units for development, shipment, and deployment.

 -- Check Docker Version

```bash
docker --version
```
# 2. Why Do We Need Docker?
```bash
Consistency Across Environments: Ensures that the application runs the same way in development, staging, and production.
Isolation: Applications run in isolation from one another.
Resource Efficiency: Containers are lightweight and use fewer resources than virtual machines.
```
3. What is a Container?
A container is a lightweight, standalone, executable package that includes everything needed to run a piece of software.

-- List Running Containers
```bash
docker ps
```
-- List All Containers (Including Stopped)

```bash
docker ps -a
```

# 4. Architecture of Docker
```bash
Docker Client: The interface users interact with.

Docker Daemon: Runs on the host machine, manages images, containers, networks, and storage volumes.

Docker Registry: Stores Docker images (e.g., Docker Hub).

Images and Containers:

Image: A read-only template with instructions.
Container: A runnable instance of an image.
```
-- Check Docker Info

```bash
docker info
```
# 5. Docker vs. Virtual Machines
```
- Docker Containers:

Share the host OS kernel.
Faster startup times.
Less resource-intensive.

- Virtual Machines:

Include a guest OS.
Slower to start.
More resource-intensive.
```
# 6. Flow of Docker
```bash
Write Code: Develop your application.
Create Dockerfile: Define how to build your image.
Build Image: Use docker build.
Run Container: Use docker run.
Push to Registry (Optional): Use docker push.
```

# 7. What is a DockerFile?
A Dockerfile is a script containing a series of instructions on how to build a Docker image.
```bash
Basic Commands in a Dockerfile:
FROM: Sets the base image.
COPY or ADD: Copies files/directories into the image.
RUN: Executes commands in a new layer.
CMD: Specifies the default command to run.
EXPOSE: Informs Docker that the container listens on the specified network ports at runtime.
```
# 8. What is Docker Registry?
A Docker registry is a storage and distribution system for named Docker images.

- Login to Docker Hub

```bash
docker login
```
- Pull an Image from Docker Hub

```bash
docker pull ubuntu:latest
```

# 9. Docker Installation on Windows
Download Docker Desktop from Docker's official website.

Install Docker Desktop by running the installer and following the prompts.

Verify Installation

```bash
docker --version
```
# 10. Creating a Demo Project - Spring Boot
- Generate a Spring Boot Application

Use Spring Initializr to generate a new project.

- Navigate to Project Directory

```bash
cd my-spring-boot-app
Build the Project

```
```bash
- build the project
./mvnw clean package

```
# 11. How to Create a DockerFile?
Create a file named Dockerfile in the root directory of your project.

Example Dockerfile for Spring Boot

# Dockerfile
```bash
FROM openjdk:17-jdk-slim
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]

```
# 12. How to Build a Docker Image?
# Build the Docker Image

```bash
docker build -t my-spring-boot-app .
```
```json
-t: Tag the image with a name.
.: Use the current directory as the build context.
```

# 13. Managing and Running Containers
# Run the Docker Container

```bash
docker run -d -p 8080:8080 --name my-running-app my-spring-boot-app
```
```json
-d: Run container in detached mode.
-p: Map host port to container port.
--name: Assign a name to the container.
```
# List Running Containers

```bash
docker ps
```
# Stop a Container

```bash
docker stop my-running-app
```

# Remove a Container

```bash
docker rm my-running-app
```

# 14. Useful Info for Containers
# View Logs

```bash
docker logs my-running-app
```
# Inspect a Container

```bash
docker inspect my-running-app
```
# Access a Running Container

```bash
docker exec -it my-running-app /bin/bash
```
# 15. Managing Images
# List Images

```bash
docker images
```
# Remove an Image

```bash
docker rmi my-spring-boot-app
```

# Tagging an Image

```bash
docker tag my-spring-boot-app username/my-spring-boot-app:v1.0
```

# 16. Updating a Project
# Make Code Changes and rebuild your application.

```bash
./mvnw clean package
```

# Rebuild Docker Image

```bash
docker build -t my-spring-boot-app .
```

# Run Updated Container

```bash
docker stop my-running-app
docker rm my-running-app
docker run -d -p 8080:8080 --name my-running-app my-spring-boot-app
``` 
# 17. Pre-defined Images
# Pull a Pre-defined Image

```bash
docker pull redis
```
# Run a Container from the Image

```bash
docker run -d --name my-redis redis
```
# 18. Running a Container in Interactive Mode
# Start a Container with Interactive Shell

```bash
docker run -it ubuntu /bin/bash
```
```json
-it: Interactive terminal.
ubuntu: Image name.
/bin/bash: Command to run.
```
# 19. Pushing an Image to DockerHub
# Login to Docker Hub

```bash
docker login
```
# Tag Your Image
```bash
docker tag my-spring-boot-app username/my-spring-boot-app:v1.0
```

# Push the Image

```bash
docker push username/my-spring-boot-app:v1.0
```

# 20. How to Pull Images Remotely
# Pull an Image from Docker Hub

```bash
docker pull username/my-spring-boot-app:v1.0
```

# Run the Pulled Image

```bash
docker run -d -p 8080:8080 --name my-remote-app username/my-spring-boot-app:v1.0
```

# 21. Docker Volume
# Create a Volume

```bash
docker volume create my_volume
```

# List Volumes

```bash
docker volume ls
```

# Run a Container with a Volume

```bash
docker run -d -v my_volume:/data --name my-data-container alpine
```

# 22. Mount Binds in Docker
# Run a Container with a Bind Mount

```bash
docker run -d -v /host/path:/container/path --name my-bind-container my-image
```
Example:
```bash
docker run -d -v $(pwd)/logs:/app/logs --name my-log-app my-spring-boot-app
```
#23. Working with APIs
# # Expose Ports in Dockerfile

# Dockerfile
```bash
EXPOSE 8080
```
-  Run Container with Port Mapping
```bash
docker run -d -p 8080:8080 --name my-api-app my-spring-boot-app
```
-- Test the API
```bash
curl http://localhost:8080/api/endpoint
```
# 24. Container with Local Database
Run a Database Container (MySQL)

```bash
docker run -d \
  --name my-mysql \
  -e MYSQL_ROOT_PASSWORD=rootpassword \
  -e MYSQL_DATABASE=mydb \
  -e MYSQL_USER=myuser \
  -e MYSQL_PASSWORD=mypassword \
  mysql:latest

```
# Connect Application to Database

Ensure your application’s database configuration points to my-mysql as the host.

# 25. Project with Multiple Containers
# Create a Network

```bash
docker network create my-network
```
# Run Database Container on Network

```bash
docker run -d --network=my-network --name=my-mysql mysql

```
# Run Application Container on Network

```bash
docker run -d --network=my-network --name=my-app my-spring-boot-app
```
# 26. Docker Network
List Networks

```bash
docker network ls
```
# Inspect a Network

```bash
docker network inspect my-network
```

# Remove a Network

```bash
docker network rm my-network
```

# 27. What is Docker Compose?
Docker Compose is a tool for defining and running multi-container Docker applications using a YAML file.

# -- Check Docker Compose Version

```bash
docker-compose --version
```
# 28. Docker Compose for Multiple Containers
#  -- Create docker-compose.yml

```yml
version: '3.8'
services:
  app:
    build: .
    ports:
      - "8080:8080"
    depends_on:
      - db
  db:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: mydb
```
# Start Services

```bash
docker-compose up -d
```
Stop Services
```

docker-compose down
```
# 29. Docker Compose with Network
Define Networks in docker-compose.yml

```yaml
version: '3.8'
services:
  app:
    build: .
    networks:
      - my-network
  db:
    image: mysql:latest
    networks:
      - my-network
networks:
  my-network:
    driver: bridge
```

# 30. Docker Compose with Volume
Define Volumes in docker-compose.yml

```yaml
version: '3.8'
services:
  db:
    image: mysql:latest
    volumes:
      - db_data:/var/lib/mysql
volumes:
  db_data:
```
# 31. Docker Compose with Port Binding
Specify Port Mapping in docker-compose.yml

```yaml
version: '3.8'
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
```
# Additional Commands

Build Images with Docker Compose

```bash
docker-compose build
```
# -- View Logs

```bash
docker-compose logs -f
```
# -- Scale Services

```bash
docker-compose up -d --scale app=3
```
Note: Replace placeholders like username, my-spring-boot-app, and paths with your actual values.
