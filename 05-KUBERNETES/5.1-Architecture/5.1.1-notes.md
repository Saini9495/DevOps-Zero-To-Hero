# Kubernetes Architecture

## What is Kubernetes?

Kubernetes is an open-source container orchestration platform used to automate deployment, scaling, and management of containerized applications.

---

## Why Kubernetes?

Before Kubernetes:

- Manual container management
- No auto-healing
- Difficult scaling
- Downtime during updates

After Kubernetes:

- Auto Scaling
- Self Healing
- Load Balancing
- Rolling Updates
- High Availability

---

# Kubernetes Architecture

Kubernetes architecture consists of:

1. Control Plane (Master Node)
2. Worker Nodes

---

## High Level Architecture

                    Kubernetes Cluster
                           │
         ┌─────────────────┴─────────────────┐
         │                                   │
   Control Plane                      Worker Nodes
         │                                   │
 ┌───────┼────────┐                  ┌───────┼────────┐
 │       │        │                  │       │        │
API   Scheduler ETCD              Kubelet Container Runtime
Server                            Kube Proxy

---

# Control Plane Components

The Control Plane manages the entire cluster.

---

## API Server

API Server is the entry point of Kubernetes.

Responsibilities:

- Receives requests
- Validates requests
- Updates cluster state
- Communicates with ETCD

Example:

```bash
kubectl get pods
```

The command first goes to API Server.

---

## ETCD

ETCD is a distributed key-value database.

Responsibilities:

- Stores cluster state
- Stores configurations
- Stores secrets
- Stores deployment information

Think of ETCD as:

Database of Kubernetes Cluster

---

## Scheduler

Scheduler decides:

Which node should run the pod?

Responsibilities:

- Check available resources
- Select suitable node
- Assign pod to node

Example:

Pod needs:

2 CPU
2 GB RAM

Scheduler finds the best worker node.

---

## Controller Manager

Maintains desired state.

Example:

Desired Pods = 3

Current Pods = 2

Controller Manager creates one more pod.

Responsibilities:

- Node Controller
- Deployment Controller
- ReplicaSet Controller
- Endpoint Controller

---

# Worker Node Components

Worker Node runs applications.

---

## Kubelet

Agent running on every node.

Responsibilities:

- Communicate with API Server
- Create Pods
- Monitor Pods

Without Kubelet:

Node cannot join cluster.

---

## Container Runtime

Responsible for running containers.

Examples:

- containerd
- CRI-O
- Docker (deprecated)

Responsibilities:

- Pull images
- Create containers
- Stop containers

---

## Kube Proxy

Responsible for networking.

Responsibilities:

- Service discovery
- Traffic routing
- Load balancing

Example:

Request arrives at Service.

Kube Proxy forwards request to correct Pod.

---

# Request Flow

User
  ↓
kubectl
  ↓
API Server
  ↓
ETCD
  ↓
Scheduler
  ↓
Worker Node
  ↓
Kubelet
  ↓
Container Runtime
  ↓
Pod Created

---

# Pod Creation Flow

Step 1:
User creates deployment

Step 2:
API Server receives request

Step 3:
Configuration stored in ETCD

Step 4:
Scheduler selects node

Step 5:
Kubelet receives instruction

Step 6:
Container Runtime pulls image

Step 7:
Pod starts

---

# Real Life Example

Imagine a Restaurant.

Customer = User

API Server = Receptionist

Scheduler = Table Manager

ETCD = Register Book

Kubelet = Waiter

Container Runtime = Chef

Pod = Food

Worker Node = Kitchen

Restaurant Owner = Controller Manager

---

# Interview Questions

## What is Kubernetes Architecture?

Kubernetes Architecture consists of Control Plane and Worker Nodes.

---

## What is API Server?

API Server acts as the front-end of Kubernetes and handles all requests.

---

## What is ETCD?

ETCD is a distributed key-value store used to store cluster state.

---

## What is Scheduler?

Scheduler decides where Pods should run.

---

## What is Kubelet?

Kubelet is an agent running on every worker node.

---

## Difference Between Control Plane and Worker Node?

Control Plane:
Manages cluster.

Worker Node:
Runs applications.

---

## What happens when a Pod is created?

User → API Server → ETCD → Scheduler → Kubelet → Container Runtime → Pod