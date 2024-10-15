---
title: Docker
name: 4_docker
date: 2024-10-15
draft: false
tags:
  - SystemDesign
share: "true"
---

# Docker Guidelines

## Dockerfile Best Practices

### Use Official Base Images

- **Why**: Official images are maintained and frequently updated, ensuring reliability and security.
- **How**:
  ```dockerfile
  FROM node:14-alpine
  ```

### Minimize Image Size

- **Why**: Smaller images lead to faster deployments and reduced storage costs.
- **How**:
  - Use minimal base images (e.g., Alpine Linux).
  - Remove unnecessary packages and files.
  - Combine commands to reduce layers.

  ```dockerfile
  RUN apt-get update && \
      apt-get install -y package1 package2 && \
      rm -rf /var/lib/apt/lists/*
  ```

### Leverage Caching

- **Why**: Utilizing Docker’s layer caching speeds up builds.
- **How**:
  - Order commands from least to most frequently changing.
  - Place frequently changing commands towards the bottom.

  ```dockerfile
  COPY package.json ./
  RUN npm install
  COPY . .
  ```

### Use Multi-Stage Builds

- **Why**: Reduce final image size by excluding build dependencies.
- **How**:
  ```dockerfile
  FROM golang:1.16 AS builder
  WORKDIR /app
  COPY . .
  RUN go build -o myapp

  FROM alpine:latest
  WORKDIR /root/
  COPY --from=builder /app/myapp .
  CMD ["./myapp"]
  ```

### Optimize Layer Usage

- **Why**: Fewer layers can lead to more efficient images.
- **How**:
  - Combine related commands using `&&`.
  - Clean up temporary files within the same `RUN` statement.

### .dockerignore File

- **Why**: Excludes unnecessary files from the build context, speeding up builds and reducing image size.
- **How**:
  ```plaintext
  node_modules
  *.log
  .git
  ```

### Specify Exact Versions

- **Why**: Ensures consistent builds by avoiding unexpected updates.
- **How**:
  ```dockerfile
  FROM python:3.8.10-slim
  ```

### Run as Non-Root User

- **Why**: Enhances security by minimizing the potential impact of container compromises.
- **How**:
  ```dockerfile
  RUN useradd -m appuser
  USER appuser
  ```


## Image Versioning and Tagging

- **Consistency**: Always tag images with specific versions rather than `latest`.
  ```shell
  docker build -t myapp:1.0.0 .
  ```
  
- **Semantic Versioning**: Use semantic versioning (MAJOR.MINOR.PATCH) to indicate changes.
- **Automated Tags**: Integrate with CI/CD to automate version tagging based on commits or releases.

## Security Best Practices

### Regularly Update Images

- **Action**: Rebuild images with the latest base images and dependencies to include security patches.

### Scan Images for Vulnerabilities

- **Tools**: Use scanners like **Clair**, **Trivy**, or **Docker Security Scanning**.
  ```shell
  trivy image myapp:1.0.0
  ```

### Limit Container Privileges

- **Action**:
  - Avoid running containers as root.
  - Use Docker’s `--cap-drop` and `--cap-add` to fine-tune capabilities.
  - Enable read-only file systems when possible.
  
  ```shell
  docker run --cap-drop=ALL --read-only myapp:1.0.0
  ```

### Use Secrets Management

- **Action**: Store sensitive data outside images using Docker Secrets or environment variables managed securely.
  
  ```shell
  docker secret create db_password ./db_password.txt
  ```

## Resource Management

### Set Resource Limits

- **Why**: Prevent containers from consuming excessive resources, ensuring system stability.
- **How**:
  ```shell
  docker run -m 512m --cpus="1.0" myapp:1.0.0
  ```

### Monitor Resource Usage

- **Tools**: Utilize monitoring solutions like **Prometheus**, **Grafana**, or **Docker Stats**.
  ```shell
  docker stats
  ```

## Networking

### Use User-Defined Networks

- **Why**: Provides better isolation and DNS-based service discovery.
- **How**:
  ```shell
  docker network create mynetwork
  docker run --network=mynetwork myapp:1.0.0
  ```

### Manage Port Exposure

- **Action**:
  - Only expose necessary ports.
  - Use Docker’s port mapping to manage accessibility.
  
  ```shell
  docker run -p 8080:80 myapp:1.0.0
  ```

## Data Management

### Use Volumes for Persistent Data

- **Why**: Ensures data persists beyond the container lifecycle.
- **How**:
  ```shell
  docker volume create mydata
  docker run -v mydata:/var/lib/data myapp:1.0.0
  ```

### Avoid Storing Data in Images

- **Action**: Do not embed dynamic or persistent data within Docker images. Use volumes or external storage solutions instead.

## Naming Conventions

### Containers

- **Format**: `<project>_<service>_<instance>`
- **Example**: `webapp_api_1`

### Images

- **Format**: `<repository>/<image>:<tag>`
- **Example**: `mycompany/webapp:1.0.0`

### Networks and Volumes

- **Format**: `<project>_<resource>`
- **Example**: `webapp_network`, `webapp_data`

## Logging and Monitoring

### Centralize Logs

- **Why**: Simplifies log management and analysis.
- **How**: Use logging drivers or external systems like **ELK Stack** or **Graylog**.
  ```shell
  docker run --log-driver=json-file myapp:1.0.0
  ```

### Implement Monitoring Solutions

- **Tools**: **Prometheus**, **Grafana**, **Datadog**, **New Relic**.
- **Action**: Monitor container metrics, application performance, and system health.

## Deployment Guidelines

### Use Orchestration Tools

- **Tools**: **Kubernetes**, **Docker Swarm**, **Apache Mesos**
- **Why**: Facilitates scalable, reliable deployments with features like load balancing, service discovery, and automated rollouts.

### Automate Deployments

- **Action**: Integrate Docker with CI/CD pipelines using tools like **Jenkins**, **GitLab CI/CD**, or **GitHub Actions**.
- **Benefit**: Ensures consistent and repeatable deployments.

## CI/CD Integration

### Automate Image Builds

- **Action**: Trigger Docker builds automatically on code commits or merges.
- **Example (GitHub Actions)**:
  ```yaml
  name: CI

  on:
    push:
      branches: [ main ]

  jobs:
    build:
      runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v2
        - name: Build Docker Image
          run: docker build -t myapp:${{ github.sha }} .
  ```

### Implement Automated Testing

- **Action**: Run tests within Docker containers to ensure consistency.
- **Benefit**: Detect issues early in the development pipeline.

## Maintenance and Cleanup

### Regularly Prune Unused Resources

- **Action**: Remove dangling images, stopped containers, unused volumes, and networks.
  ```shell
  docker system prune -a
  ```

### Rotate and Backup Data

- **Action**: Implement data backup strategies for persistent volumes.
- **Tools**: **rsync**, **Volume Backup Plugins**, cloud storage solutions.

## Troubleshooting Tips

- **Inspect Containers**:
  ```shell
  docker inspect <container_id>
  ```
  
- **View Logs**:
  ```shell
  docker logs <container_id>
  ```
  
- **Access Container Shell**:
  ```shell
  docker exec -it <container_id> /bin/sh
  ```
  
- **Check Network Connectivity**:
  ```shell
  docker network inspect <network_name>
  ```

- **Diagnose with Docker Events**:
  ```shell
  docker events
  ```

## Examples

### Sample Dockerfile

```dockerfile
# Use official Node.js LTS version
FROM node:14-alpine

# Set working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package.json package-lock.json ./
RUN npm install --production

# Copy application code
COPY . .

# Expose the application port
EXPOSE 3000

# Define the entry point
CMD ["node", "server.js"]
```

### Docker Compose Example

```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/app
      - web_data:/var/lib/web
    environment:
      NODE_ENV: production
    networks:
      - webnet

  db:
    image: postgres:13
    restart: always
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    volumes:
      - db_data:/var/lib/postgresql/data
    networks:
      - webnet

volumes:
  web_data:
  db_data:

networks:
  webnet:
```

**Happy Dockering!** 🚀
