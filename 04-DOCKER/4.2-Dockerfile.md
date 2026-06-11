# Dockerfile

## What is a Dockerfile?

A Dockerfile is a text file that contains a set of instructions used to automatically build a Docker Image.

Instead of manually installing dependencies, copying source code, and configuring environments every time, we can define everything inside a Dockerfile.

When Docker reads the Dockerfile, it executes each instruction step by step and creates an image.

---

## Why Do We Need Dockerfile?

Imagine you have a Node.js application.

To run it manually:

1. Install Node.js
2. Install dependencies
3. Copy source code
4. Configure environment
5. Start application

Doing this repeatedly on every server is time-consuming and error-prone.

Dockerfile automates the entire process.

### Benefits

* Consistent environment
* Automated image creation
* Easy deployment
* Version controlled infrastructure
* Faster CI/CD pipelines

---

## Dockerfile Workflow

```text
Dockerfile
    ↓
docker build
    ↓
Docker Image
    ↓
docker run
    ↓
Container
```

---

## Common Dockerfile Instructions

### 1. FROM

Specifies the base image.

Every Dockerfile starts with FROM.

Example:

```dockerfile
FROM node:18
```

Here:

* node = Official Node.js image
* 18 = Version

Docker first downloads this image and then builds on top of it.

---

### 2. WORKDIR

Sets the working directory inside the container.

Example:

```dockerfile
WORKDIR /app
```

Equivalent Linux command:

```bash
cd /app
```

All future commands run inside this directory.

---

### 3. COPY

Copies files from local machine to container.

Example:

```dockerfile
COPY . .
```

Meaning:

```text
Current Folder → Container Current Folder
```

Another example:

```dockerfile
COPY package.json .
```

Copies package.json into current container directory.

---

### 4. RUN

Executes commands while building the image.

Example:

```dockerfile
RUN npm install
```

This command installs all project dependencies during image creation.

Multiple RUN instructions create multiple image layers.

Example:

```dockerfile
RUN apt update
RUN apt install -y curl
```

---

### 5. EXPOSE

Documents which port the application uses.

Example:

```dockerfile
EXPOSE 3000
```

This tells Docker that the application listens on port 3000.

Note:

EXPOSE does not publish the port.

Port mapping happens using:

```bash
docker run -p 3000:3000 image-name
```

---

### 6. CMD

Defines the default command executed when a container starts.

Example:

```dockerfile
CMD ["node","index.js"]
```

When container starts:

```bash
node index.js
```

runs automatically.

Only one CMD should be used.

If multiple CMD instructions exist, Docker uses the last one.

---

### 7. ENTRYPOINT

ENTRYPOINT defines a fixed command that always runs.

Example:

```dockerfile
ENTRYPOINT ["node"]
```

Container will always execute node.

Any extra arguments passed to docker run are appended.

Example:

```bash
docker run myapp index.js
```

Internally:

```bash
node index.js
```

---

## CMD vs ENTRYPOINT

| CMD                        | ENTRYPOINT                          |
| -------------------------- | ----------------------------------- |
| Can be overridden          | Hard to override                    |
| Provides default arguments | Provides fixed executable           |
| Flexible                   | More strict                         |
| Optional                   | Used when command should always run |

Example:

```dockerfile
CMD ["node","index.js"]
```

Override:

```bash
docker run image-name bash
```

Docker runs bash instead.

ENTRYPOINT example:

```dockerfile
ENTRYPOINT ["node"]
```

```bash
docker run image-name app.js
```

Docker executes:

```bash
node app.js
```

---

## COPY vs ADD

### COPY

Copies files and folders.

Example:

```dockerfile
COPY app.js .
```

---

### ADD

Can do everything COPY can do plus:

* Extract tar files automatically
* Download files from URLs

Example:

```dockerfile
ADD app.tar.gz .
```

Docker automatically extracts the archive.

Recommendation:

Use COPY unless ADD features are specifically required.

---

## Complete Dockerfile Example

### Project Structure

```text
Node-App
│
├── package.json
├── package-lock.json
├── index.js
└── Dockerfile
```

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

## Build Docker Image

```bash
docker build -t myapp .
```

Explanation:

* build → Build image
* -t → Tag name
* myapp → Image name
* . → Current directory

Verify:

```bash
docker images
```

---

## Run Docker Container

```bash
docker run -d -p 3000:3000 myapp
```

Explanation:

* run → Start container
* -d → Detached mode
* -p → Port mapping
* myapp → Image name

Check running containers:

```bash
docker ps
```

---

## Docker Image Layers

Each Dockerfile instruction creates a layer.

Example:

```dockerfile
FROM node:18
COPY package.json .
RUN npm install
COPY . .
```

Layers:

1. Base Node Image
2. Package File Layer
3. Dependency Layer
4. Application Layer

Docker caches layers to speed up future builds.

---

## Best Practices

### Copy package files first

Good:

```dockerfile
COPY package*.json ./
RUN npm install
COPY . .
```

This improves build caching.

---

### Use Specific Versions

Bad:

```dockerfile
FROM node:latest
```

Good:

```dockerfile
FROM node:18
```

---

### Use .dockerignore

Example:

```text
node_modules
.git
.env
```

Avoids copying unnecessary files.

---

## Real-Life Analogy

Think of a Dockerfile as a Recipe.

Recipe = Dockerfile

Ingredients = Source Code

Cook = Docker Engine

Prepared Dish = Docker Image

Served Food = Docker Container

The same recipe always produces the same dish.

---

# Interview Questions

### What is Dockerfile?

A Dockerfile is a text file containing instructions used to build Docker images automatically.

---

### Difference between Image and Container?

Image is a blueprint.

Container is a running instance of that image.

---

### Difference between CMD and ENTRYPOINT?

CMD provides default commands that can be overridden.

ENTRYPOINT provides fixed commands that always run.

---

### Difference between COPY and ADD?

COPY only copies files.

ADD can also extract archives and download files from URLs.

---

### What happens when docker build is executed?

Docker reads the Dockerfile, executes instructions sequentially, creates layers, and finally generates an image.

---

### Why is WORKDIR used?

WORKDIR sets the default working directory inside the container for all future commands.
