# Docker Networks

## What are Docker Networks?

Docker Networks allow containers to communicate with each other and with external systems.

By default, each container runs in an isolated environment. Docker networking provides connectivity between containers, hosts, and external networks.

---

## Why Do We Need Docker Networks?

Imagine you have:

* Frontend Container
* Backend Container
* Database Container

The frontend needs to talk to the backend.

The backend needs to talk to the database.

Without networking, containers cannot communicate with each other.

Docker Networks solve this problem.

### Real-Life Analogy

Think of containers as people living in different houses.

A Docker Network acts like a mobile network that allows them to call each other.

Without a network, they cannot communicate.

---

## Docker Network Architecture

```text
Internet
    |
Docker Host
    |
-------------------------
|                       |
Frontend Container      |
|                       |
Backend Container       |
|                       |
Database Container      |
-------------------------
        |
   Docker Network
```

All containers connected to the same Docker Network can communicate with each other using container names.

---

## Types of Docker Networks

Docker provides several network drivers:

### 1. Bridge Network

This is the default network type.

When a container is created without specifying a network, Docker automatically attaches it to the bridge network.

#### Features

* Single-host communication
* Containers communicate using IP addresses
* Most commonly used

#### Check Bridge Network

```bash
docker network ls
```

Output:

```text
NETWORK ID     NAME      DRIVER
abc123         bridge    bridge
```

#### Run Container on Bridge Network

```bash
docker run -d --name nginx nginx
```

Inspect Network:

```bash
docker network inspect bridge
```

---

### 2. Host Network

In Host mode, the container shares the host machine's network stack.

No separate container IP is assigned.

#### Features

* Better performance
* No NAT translation
* Direct access to host network

#### Example

```bash
docker run --network host nginx
```

#### Use Cases

* High-performance applications
* Monitoring tools
* Network-intensive workloads

---

### 3. None Network

The container has no network access.

#### Example

```bash
docker run --network none nginx
```

#### Features

* Fully isolated
* No internet access
* No communication with other containers

#### Use Cases

* Security testing
* Offline processing

---

### 4. Overlay Network

Used in Docker Swarm.

Allows communication between containers running on multiple Docker hosts.

#### Example Architecture

```text
Host-1
  |
Container-A

Overlay Network

Host-2
  |
Container-B
```

Container-A can communicate with Container-B even though they are on different servers.

#### Use Cases

* Docker Swarm
* Distributed Applications
* Multi-host Deployments

---

## List Existing Networks

```bash
docker network ls
```

Example Output:

```text
NETWORK ID     NAME      DRIVER
abc123         bridge    bridge
def456         host      host
ghi789         none      null
```

---

## Create a Custom Network

```bash
docker network create mynetwork
```

Verify:

```bash
docker network ls
```

Output:

```text
NETWORK ID     NAME
xyz123         mynetwork
```

---

## Inspect a Network

Inspecting provides detailed information.

```bash
docker network inspect mynetwork
```

Information includes:

* Network ID
* Subnet
* Gateway
* Connected Containers
* Driver Type

---

## Run Containers on Custom Network

### Start MongoDB

```bash
docker run -d \
--name mongo \
--network mynetwork \
mongo
```

### Start Application Container

```bash
docker run -d \
--name app \
--network mynetwork \
nodeapp
```

Now both containers can communicate.

---

## Container-to-Container Communication

Inside the application:

```javascript
mongodb://mongo:27017
```

Notice:

We are using:

```text
mongo
```

instead of

```text
172.17.0.5
```

Docker automatically provides DNS resolution.

Container names become hostnames.

---

## Connect Existing Container to a Network

```bash
docker network connect mynetwork app
```

Verify:

```bash
docker inspect app
```

---

## Disconnect Container from Network

```bash
docker network disconnect mynetwork app
```

---

## Remove Network

```bash
docker network rm mynetwork
```

Remove all unused networks:

```bash
docker network prune
```

---

## Common Docker Network Commands

### List Networks

```bash
docker network ls
```

### Create Network

```bash
docker network create mynetwork
```

### Inspect Network

```bash
docker network inspect mynetwork
```

### Connect Container

```bash
docker network connect mynetwork app
```

### Disconnect Container

```bash
docker network disconnect mynetwork app
```

### Delete Network

```bash
docker network rm mynetwork
```

---

## Practical Example

Create Network

```bash
docker network create project-network
```

Run MongoDB

```bash
docker run -d \
--name mongo \
--network project-network \
mongo
```

Run Backend

```bash
docker run -d \
--name backend \
--network project-network \
mybackend
```

Run Frontend

```bash
docker run -d \
--name frontend \
--network project-network \
myfrontend
```

Communication Flow:

```text
Frontend
   |
Backend
   |
MongoDB
```

All containers communicate through the same Docker Network.

---

## Advantages of Docker Networks

### Isolation

Containers communicate only within allowed networks.

### Security

Limits unnecessary exposure.

### Service Discovery

Containers communicate using names.

### Scalability

Easy to add more containers.

### Flexibility

Supports multiple networking modes.

---

## Interview Questions

### What is Docker Networking?

Docker Networking allows communication between containers, hosts, and external systems.

---

### What is the default network in Docker?

Bridge Network.

---

### Difference Between Bridge and Host Network?

| Bridge Network        | Host Network        |
| --------------------- | ------------------- |
| Separate container IP | Uses host IP        |
| Better isolation      | Less isolation      |
| Default network       | Performance focused |

---

### How Do Containers Communicate?

Containers communicate through Docker Networks using container names or IP addresses.

---

### What is Overlay Network?

A network driver that enables communication between containers running on different Docker hosts.

---

### What is Docker DNS?

Docker automatically provides DNS resolution so containers can communicate using container names.

---

## Summary

* Docker Networks enable container communication.
* Bridge is the default network.
* Host shares the host network stack.
* None provides complete isolation.
* Overlay is used in Docker Swarm.
* Containers can communicate using container names.
* Custom networks improve security and service discovery.
