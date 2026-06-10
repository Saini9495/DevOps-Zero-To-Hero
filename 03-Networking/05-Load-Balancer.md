# Load Balancer

## What is a Load Balancer?

A Load Balancer is a networking component that distributes incoming client requests across multiple backend servers. Its primary purpose is to prevent a single server from becoming overloaded and to ensure high availability of applications.

In modern cloud environments, Load Balancers are widely used to handle millions of requests efficiently.

---

## Why Do We Need a Load Balancer?

Imagine you have a website hosted on a single server.

```text
Users
  |
  |
Server-1
```

### Problems

1. Single Point of Failure

   * If Server-1 crashes, the entire application becomes unavailable.

2. Performance Issues

   * A large number of users can overload the server.

3. Limited Scalability

   * Cannot easily handle increased traffic.

---

## Solution: Load Balancer

A Load Balancer sits between users and application servers.

```text
                 Users
                    |
                    |
            +----------------+
            | Load Balancer  |
            +----------------+
               /        \
              /          \
      +---------+    +---------+
      | Server1 |    | Server2 |
      +---------+    +---------+
```

The Load Balancer distributes traffic among available servers.

Benefits:

* High Availability
* Better Performance
* Scalability
* Fault Tolerance
* Improved User Experience

---

## How Does a Load Balancer Work?

Step 1:
User sends a request.

```text
User --> Load Balancer
```

Step 2:
Load Balancer receives the request.

Step 3:
Load Balancer decides which server should handle the request.

Step 4:
Request is forwarded to the selected server.

Step 5:
Server sends the response back through the Load Balancer.

```text
User --> Load Balancer --> Server
User <-- Load Balancer <-- Server
```

---

## Real-Life Example

Consider a Toll Plaza.

```text
Cars = Requests

Toll Booths = Servers

Traffic Controller = Load Balancer
```

If all cars use a single booth:

```text
Car Car Car Car Car
          |
          V
      Booth-1
```

Long queue forms.

Instead:

```text
Cars
 |
 |
Traffic Controller
 /      |      \
B1      B2      B3
```

Traffic is distributed efficiently.

---

# Types of Load Balancers

## Layer 4 Load Balancer

Works at OSI Layer 4 (Transport Layer).

Protocols:

* TCP
* UDP

Decisions are made using:

* Source IP
* Destination IP
* Port Number

Example:

* AWS Network Load Balancer (NLB)

Architecture:

```text
Client
   |
Layer 4 LB
   |
Backend Servers
```

### Advantages

* Extremely Fast
* Low Latency
* High Performance

### Disadvantages

* Cannot inspect HTTP content
* Limited routing capabilities

---

## Layer 7 Load Balancer

Works at OSI Layer 7 (Application Layer).

Protocols:

* HTTP
* HTTPS

Can inspect:

* URL
* Hostname
* Headers
* Cookies

Example:

* AWS Application Load Balancer (ALB)
* NGINX
* HAProxy

Architecture:

```text
Client
   |
Layer 7 LB
   |
Backend Servers
```

### Advantages

* Smart Routing
* URL Based Routing
* Host Based Routing
* SSL Termination

### Disadvantages

* Slightly Slower than Layer 4
* More Resource Consumption

---

# Layer 4 vs Layer 7 Load Balancer

| Feature           | Layer 4   | Layer 7         |
| ----------------- | --------- | --------------- |
| OSI Layer         | Transport | Application     |
| Protocols         | TCP/UDP   | HTTP/HTTPS      |
| Speed             | Faster    | Slightly Slower |
| URL Routing       | No        | Yes             |
| Header Inspection | No        | Yes             |
| SSL Termination   | Limited   | Supported       |
| Example           | AWS NLB   | AWS ALB         |

---

# Load Balancing Algorithms

A Load Balancer uses algorithms to determine where requests should be sent.

---

## 1. Round Robin

Requests are distributed sequentially.

Example:

```text
Request 1 --> Server 1
Request 2 --> Server 2
Request 3 --> Server 3
Request 4 --> Server 1
Request 5 --> Server 2
```

Advantages:

* Simple
* Easy to Implement

Disadvantages:

* Does not consider server load

---

## 2. Least Connections

Traffic is sent to the server with the fewest active connections.

Example:

```text
Server-1 : 100 Connections
Server-2 : 20 Connections

Next Request --> Server-2
```

Advantages:

* Better Load Distribution

Disadvantages:

* More Processing Required

---

## 3. Weighted Round Robin

Some servers receive more traffic than others.

Example:

```text
Server-1 Weight = 3
Server-2 Weight = 1
```

Traffic:

```text
S1
S1
S1
S2
```

Useful when servers have different capacities.

---

## 4. IP Hash

Client IP determines the backend server.

Example:

```text
Client A --> Server 1
Client B --> Server 2
```

Advantages:

* Session Persistence

Disadvantages:

* Uneven Distribution

---

# Health Checks

A Load Balancer continuously checks backend servers.

Example:

```text
Load Balancer
      |
      |
      V
GET /health
```

If server responds:

```text
200 OK
```

Server is healthy.

If server does not respond:

```text
Timeout
```

Server is marked unhealthy.

---

## Healthy Scenario

```text
Load Balancer
   /      \
  /        \
S1         S2
```

Traffic goes to both servers.

---

## Unhealthy Scenario

```text
Load Balancer
     |
     |
    S1

S2 = Down
```

Traffic automatically stops going to S2.

---

# SSL Termination

A Layer 7 Load Balancer can decrypt HTTPS traffic before forwarding requests.

```text
Client
  |
HTTPS
  |
Load Balancer
  |
HTTP
  |
Backend Servers
```

Benefits:

* Reduced Server Load
* Easier Certificate Management

---

# Load Balancer in AWS

## Application Load Balancer (ALB)

Works at Layer 7.

Supports:

* HTTP
* HTTPS
* Path-Based Routing
* Host-Based Routing

Example:

```text
/api/*  --> API Servers

/admin/* --> Admin Servers
```

---

## Network Load Balancer (NLB)

Works at Layer 4.

Supports:

* TCP
* UDP
* TLS

Best for:

* High Performance Applications
* Gaming
* Real-Time Systems

---

# Load Balancer in Kubernetes

Kubernetes Services can expose applications through Load Balancers.

Example:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: LoadBalancer
```

Cloud providers automatically provision a Load Balancer.

---

# Interview Questions

## What is a Load Balancer?

A Load Balancer distributes incoming traffic across multiple backend servers to improve availability, scalability, and performance.

---

## Why is a Load Balancer important?

* High Availability
* Fault Tolerance
* Scalability
* Better Resource Utilization

---

## What is the difference between ALB and NLB?

ALB:

* Layer 7
* HTTP/HTTPS
* URL Routing

NLB:

* Layer 4
* TCP/UDP
* High Performance

---

## What is a Health Check?

A mechanism used by the Load Balancer to determine whether backend servers are healthy and capable of handling requests.

---

## What is Session Persistence?

A feature where requests from the same client are consistently routed to the same backend server.

---

## Which Load Balancer does Kubernetes use?

When a Service type is LoadBalancer, cloud providers such as AWS create an external Load Balancer automatically.

---

## What are the most commonly used Load Balancers?

* AWS ALB
* AWS NLB
* NGINX
* HAProxy
* F5 BIG-IP
* Traefik
