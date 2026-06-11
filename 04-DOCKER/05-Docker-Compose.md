# Docker Compose

## What is Docker Compose?

Docker Compose is a tool that allows us to define and manage multiple Docker containers using a single YAML file (`docker-compose.yml`).

Instead of running multiple `docker run` commands manually, we can define all services, networks, and volumes inside one file and start everything with a single command.

---

## Why Docker Compose?

Imagine you have a full-stack application:

* Frontend (React)
* Backend (Node.js)
* Database (MongoDB)

Without Docker Compose:

```bash
docker run -d --name mongo mongo

docker run -d --name backend backend-image

docker run -d --name frontend frontend-image
```

Managing multiple containers becomes difficult.

With Docker Compose:

```bash
docker compose up -d
```

Everything starts automatically.

---

## Problems Solved by Docker Compose

### Before Compose

* Multiple docker run commands
* Difficult container management
* Manual networking
* Manual volume creation
* Hard to replicate environments

### After Compose

* Single YAML file
* Easy deployment
* Automatic networking
* Better maintainability
* Consistent environments

---

## Docker Compose Architecture

```text
docker-compose.yml
        │
        ▼
 Docker Compose
        │
 ┌──────┼──────┐
 ▼      ▼      ▼

Frontend Backend MongoDB
Container Container Container
```

Docker Compose reads the YAML file and creates all required containers.

---

## Installation Verification

Check Docker Compose version:

```bash
docker compose version
```

Output:

```bash
Docker Compose version v2.x.x
```

---

## Structure of docker-compose.yml

```yaml
services:
  service_name:
    image: image_name
```

Example:

```yaml
services:
  nginx:
    image: nginx
```

---

## First Docker Compose Example

Create a file:

```yaml
services:
  nginx:
    image: nginx
    ports:
      - "80:80"
```

Run:

```bash
docker compose up -d
```

Check:

```bash
docker ps
```

Stop:

```bash
docker compose down
```

---

## Important Keywords

### services

Defines containers.

```yaml
services:
  nginx:
    image: nginx
```

---

### image

Specifies Docker image.

```yaml
image: nginx
```

---

### build

Build image from Dockerfile.

```yaml
build: .
```

Docker Compose will look for Dockerfile in current directory.

---

### ports

Maps host port to container port.

```yaml
ports:
  - "3000:3000"
```

Meaning:

```text
Host Port       Container Port
3000      --->      3000
```

---

### volumes

Used for persistent storage.

```yaml
volumes:
  - myvolume:/app/data
```

---

### environment

Pass environment variables.

```yaml
environment:
  MONGO_URI=mongodb://mongo:27017
```

or

```yaml
environment:
  - MONGO_URI=mongodb://mongo:27017
```

---

### container_name

Custom container name.

```yaml
container_name: backend
```

---

### restart

Container restart policy.

```yaml
restart: always
```

Options:

```text
no
always
unless-stopped
on-failure
```

---

## Complete Node.js + MongoDB Example

Project Structure

```text
project/
│
├── Dockerfile
├── docker-compose.yml
├── package.json
└── index.js
```

---

### Dockerfile

```dockerfile
FROM node:18

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["node","index.js"]
```

---

### docker-compose.yml

```yaml
services:

  backend:
    build: .
    container_name: backend

    ports:
      - "3000:3000"

    depends_on:
      - mongo

    environment:
      MONGO_URI: mongodb://mongo:27017/mydb

  mongo:
    image: mongo
    container_name: mongodb

    ports:
      - "27017:27017"

    volumes:
      - mongodb-data:/data/db

volumes:
  mongodb-data:
```

---

## depends_on

Controls startup order.

```yaml
depends_on:
  - mongo
```

Docker Compose starts MongoDB first and then backend.

---

## Named Volumes

```yaml
volumes:
  mongodb-data:
```

Attach:

```yaml
volumes:
  - mongodb-data:/data/db
```

Data remains safe even if container is removed.

---

## Docker Compose Commands

### Start Services

```bash
docker compose up
```

---

### Start in Background

```bash
docker compose up -d
```

---

### Stop Services

```bash
docker compose stop
```

---

### Restart Services

```bash
docker compose restart
```

---

### View Running Services

```bash
docker compose ps
```

---

### View Logs

```bash
docker compose logs
```

Specific Service:

```bash
docker compose logs backend
```

---

### Build Images

```bash
docker compose build
```

---

### Pull Images

```bash
docker compose pull
```

---

### Remove Everything

```bash
docker compose down
```

---

### Remove Containers + Volumes

```bash
docker compose down -v
```

---

## Networking in Docker Compose

Docker Compose automatically creates a network.

Example:

```yaml
services:
  backend:
    build: .

  mongo:
    image: mongo
```

Backend can directly communicate using:

```text
mongodb://mongo:27017
```

Where:

```text
mongo = service name
```

No need to use IP addresses.

---

## Real-Life Analogy

Imagine a restaurant.

Without Compose:

* Hire Chef
* Hire Waiter
* Hire Cashier
* Hire Manager

One by one.

With Compose:

Restaurant Manager hires everyone automatically.

Single command:

```bash
docker compose up -d
```

Everything starts together.

---

## Docker vs Docker Compose

| Docker                    | Docker Compose            |
| ------------------------- | ------------------------- |
| Single Container          | Multiple Containers       |
| Manual Commands           | Single YAML File          |
| Manual Networking         | Automatic Networking      |
| More Configuration        | Centralized Configuration |
| Hard to Manage Large Apps | Easy to Manage Large Apps |

---

## Advantages of Docker Compose

* Easy deployment
* Less manual work
* Automatic networking
* Easy scaling
* Reproducible environments
* Better project organization

---

## Common Interview Questions

### What is Docker Compose?

Docker Compose is a tool used to define and manage multi-container Docker applications using a YAML configuration file.

---

### What is docker-compose.yml?

A configuration file that defines services, networks, volumes, ports, and environment variables.

---

### Difference between Docker and Docker Compose?

Docker manages individual containers while Docker Compose manages multiple containers together.

---

### What is depends_on?

It specifies container startup order.

---

### How do containers communicate in Docker Compose?

Containers communicate using service names because Docker Compose automatically creates a network.

---

### What is the use of volumes in Docker Compose?

Volumes provide persistent storage so data remains even if containers are deleted.

---

### What command is used to start all services?

```bash
docker compose up -d
```

---

### What command removes services and networks?

```bash
docker compose down
```
