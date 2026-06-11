# Docker Introduction

## What is Docker?

Docker is an open-source containerization platform that allows developers to package applications along with all their dependencies into lightweight, portable containers.

A container contains:

* Application Code
* Runtime Environment
* Libraries
* Dependencies
* Configuration Files

This ensures that the application runs consistently across different environments such as development, testing, and production.

---

## Why Docker?

Before Docker, developers often faced the "It works on my machine" problem.

Different environments could have:

* Different Operating Systems
* Different Library Versions
* Different Runtime Versions
* Different Configurations

Docker solves these issues by packaging everything required to run the application inside a container.

### Benefits of Docker

### 1. Consistent Environment

Applications behave the same way across all environments.

Example:

* Developer Machine → Works
* Testing Server → Works
* Production Server → Works

### 2. Fast Deployment

Containers start within seconds.

### 3. Resource Efficient

Containers share the host OS kernel and consume fewer resources than Virtual Machines.

### 4. Easy Scalability

Multiple container instances can be created quickly to handle increased traffic.

### 5. Portability

Containers can run on:

* Local Machine
* Cloud Platforms
* Virtual Machines
* Physical Servers

---

## Problems Solved by Docker

### Traditional Deployment

Application requires:

* Node.js
* Python
* Java
* Nginx
* Database

Each server needs manual installation and configuration.

Issues:

* Dependency Conflicts
* Version Mismatch
* Environment Differences
* Deployment Errors

### Docker-Based Deployment

Package everything into a container.

Result:

* Same application
* Same dependencies
* Same behavior everywhere

---

## What is Containerization?

Containerization is the process of packaging an application along with its dependencies into an isolated unit called a container.

Characteristics:

* Lightweight
* Portable
* Fast
* Secure
* Isolated

---

## Virtual Machine vs Container

### Virtual Machine

A Virtual Machine includes:

* Application
* Dependencies
* Guest Operating System
* Hypervisor

Architecture:

Application
↓
Guest OS
↓
Hypervisor
↓
Host OS
↓
Hardware

Advantages:

* Strong Isolation
* Independent Operating System

Disadvantages:

* High Resource Usage
* Slow Boot Time

---

### Container

A Container includes:

* Application
* Dependencies

Architecture:

Application
↓
Container Runtime
↓
Host OS
↓
Hardware

Advantages:

* Lightweight
* Fast Startup
* Efficient Resource Utilization

Disadvantages:

* Shares Host OS Kernel

---

## Docker Architecture

Docker follows a Client-Server Architecture.

### Components

### Docker Client

Used by users to interact with Docker.

Examples:

```bash
docker build
docker run
docker pull
docker push
```

### Docker Daemon (dockerd)

Background service responsible for:

* Building Images
* Running Containers
* Managing Networks
* Managing Volumes

### Docker Registry

Stores Docker Images.

Examples:

* Docker Hub
* Private Registry

### Docker Images

Read-only templates used to create containers.

Example:

```bash
docker pull nginx
```

nginx is an image.

### Docker Containers

Running instances of Docker Images.

Example:

```bash
docker run nginx
```

This creates and starts a container.

---

## Docker Workflow

### Step 1

Write Application Code

### Step 2

Create Dockerfile

### Step 3

Build Docker Image

```bash
docker build -t myapp .
```

### Step 4

Run Container

```bash
docker run -d -p 3000:3000 myapp
```

### Step 5

Application is available to users

---

## Key Docker Components

### Docker Engine

Core Docker software responsible for container management.

Contains:

* Docker Daemon
* Docker CLI
* REST API

### Docker Image

Blueprint for containers.

Examples:

* nginx
* ubuntu
* node
* mysql

### Docker Container

Running instance of an image.

### Docker Registry

Storage location for Docker Images.

### Docker Hub

Public registry maintained by Docker.

Website:

https://hub.docker.com

---

## Real-Life Analogy

Imagine opening a restaurant.

### Traditional Deployment

Each branch needs:

* Chef
* Ingredients
* Equipment

Everything must be configured manually.

### Docker Deployment

Prepare a complete food package.

Every branch receives the same package.

Result:

Same taste everywhere.

Docker Container = Food Package

---

## Basic Docker Commands

Check Docker Version

```bash
docker --version
```

Check Docker Information

```bash
docker info
```

Download Image

```bash
docker pull nginx
```

Run Container

```bash
docker run nginx
```

List Running Containers

```bash
docker ps
```

List All Containers

```bash
docker ps -a
```

Stop Container

```bash
docker stop container_id
```

Remove Container

```bash
docker rm container_id
```

---

## Advantages of Docker

* Lightweight
* Portable
* Faster Deployment
* Better Resource Utilization
* Simplified CI/CD
* Easy Scaling
* Environment Consistency

---

## Limitations of Docker

* Shares Host OS Kernel
* Less Isolation than Virtual Machines
* Learning Curve for Beginners

---

# Interview Questions

### What is Docker?

Docker is an open-source containerization platform that packages applications and their dependencies into lightweight containers, ensuring consistency across environments.

---

### What is Containerization?

Containerization is the process of packaging an application and its dependencies into isolated containers that can run consistently on any system.

---

### Difference Between VM and Container?

| Virtual Machine     | Container             |
| ------------------- | --------------------- |
| Includes Guest OS   | Shares Host OS Kernel |
| Heavyweight         | Lightweight           |
| Slow Startup        | Fast Startup          |
| More Resource Usage | Less Resource Usage   |

---

### What is Docker Engine?

Docker Engine is the core Docker service that builds, runs, and manages containers.

---

### What is Docker Image?

A Docker Image is a read-only template used to create Docker Containers.

---

### What is Docker Hub?

Docker Hub is a public registry used to store and share Docker Images.

---

### What is the Difference Between Docker Image and Container?

Image:

* Blueprint
* Read Only

Container:

* Running Instance
* Read Write

Example:

Image = Class

Container = Object

---

### Why is Docker Popular in DevOps?

Docker provides:

* Consistent Environments
* Faster Deployments
* Better Scalability
* CI/CD Integration
* Cloud Compatibility
