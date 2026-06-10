# OSI Model (Open Systems Interconnection)

## Introduction

OSI (Open Systems Interconnection) Model is a conceptual framework developed by ISO (International Organization for Standardization) to understand how data travels from one device to another over a network.

The OSI Model divides the communication process into 7 layers. Each layer performs a specific task and communicates with the layer above and below it.

OSI Model helps network engineers, system administrators, cloud engineers, and DevOps engineers troubleshoot networking issues efficiently.

---

## Why Do We Need OSI Model?

Imagine there is no standard method of communication between devices.

Different vendors would create their own communication methods, making interoperability difficult.

OSI Model provides:

* Standardized communication
* Easier troubleshooting
* Better network design
* Vendor independence
* Simplified learning of networking concepts

---

## OSI Model Layers

| Layer Number | Layer Name   |
| ------------ | ------------ |
| 7            | Application  |
| 6            | Presentation |
| 5            | Session      |
| 4            | Transport    |
| 3            | Network      |
| 2            | Data Link    |
| 1            | Physical     |

---

## Easy Memory Trick

From Layer 7 to Layer 1:

**All People Seem To Need Data Processing**

* A → Application
* P → Presentation
* S → Session
* T → Transport
* N → Network
* D → Data Link
* P → Physical

From Layer 1 to Layer 7:

**Please Do Not Throw Sausage Pizza Away**

* P → Physical
* D → Data Link
* N → Network
* T → Transport
* S → Session
* P → Presentation
* A → Application

---

# Layer 7 - Application Layer

## Purpose

This is the layer closest to the end user.

Applications use this layer to communicate with the network.

It provides network services directly to applications.

---

## Examples

* Google Chrome
* Mozilla Firefox
* Outlook
* WhatsApp
* Telegram

---

## Protocols

* HTTP
* HTTPS
* FTP
* SMTP
* POP3
* IMAP
* DNS

---

## Real-Life Example

When you type:

https://google.com

in your browser, the request originates from the Application Layer.

---

## DevOps Relevance

When troubleshooting:

* Website inaccessible
* API not responding
* DNS issues

You are often working at the Application Layer.

---

# Layer 6 - Presentation Layer

## Purpose

Responsible for data formatting and translation.

It ensures that data sent by one system can be understood by another system.

---

## Responsibilities

### Encryption

Converts readable data into encrypted form.

Example:

HTTPS uses TLS/SSL encryption.

---

### Decryption

Converts encrypted data back to readable form.

---

### Compression

Reduces data size before transmission.

---

### Data Translation

Converts data into a common format.

---

## Examples

* SSL
* TLS
* JPEG
* PNG
* GIF

---

## Real-Life Example

When you open a secure website:

https://amazon.com

TLS encryption is handled at this layer.

---

# Layer 5 - Session Layer

## Purpose

Responsible for creating, maintaining, and terminating communication sessions.

---

## Responsibilities

* Session Establishment
* Session Management
* Session Termination

---

## Real-Life Example

Imagine a Zoom Meeting.

Session Layer:

* Starts meeting
* Maintains connection
* Ends meeting

---

## Protocol Examples

* NetBIOS
* RPC
* PPTP

---

# Layer 4 - Transport Layer

## Purpose

Provides end-to-end communication between devices.

Responsible for reliable delivery of data.

---

## Responsibilities

* Error detection
* Flow control
* Data segmentation
* Reliability

---

## Protocols

### TCP

Transmission Control Protocol

Features:

* Reliable
* Connection-Oriented
* Error Checking
* Ordered Delivery

Examples:

* HTTPS
* SSH
* FTP

---

### UDP

User Datagram Protocol

Features:

* Fast
* Connectionless
* No Acknowledgement

Examples:

* Video Streaming
* Gaming
* DNS

---

## TCP Three-Way Handshake

Step 1:

Client → SYN → Server

Step 2:

Server → SYN-ACK → Client

Step 3:

Client → ACK → Server

Connection Established

---

## Devices

* Firewalls
* Load Balancers

---

## DevOps Relevance

Common ports:

| Service    | Port |
| ---------- | ---- |
| HTTP       | 80   |
| HTTPS      | 443  |
| SSH        | 22   |
| MySQL      | 3306 |
| PostgreSQL | 5432 |
| Jenkins    | 8080 |

---

# Layer 3 - Network Layer

## Purpose

Responsible for routing packets from source to destination.

Determines the best path for data transmission.

---

## Responsibilities

* Routing
* Logical Addressing
* Path Selection

---

## Protocols

* IPv4
* IPv6
* ICMP

---

## Devices

* Router
* Layer 3 Switch

---

## Address Used

IP Address

Examples:

192.168.1.10

10.0.0.5

172.31.0.10

---

## Real-Life Example

You want to travel from Delhi to Mumbai.

Google Maps selects the best route.

Similarly, routers select the best network path.

---

## DevOps Relevance

AWS VPC

Subnets

Route Tables

Internet Gateway

NAT Gateway

All operate mainly at Layer 3.

---

# Layer 2 - Data Link Layer

## Purpose

Provides node-to-node communication within the same network.

Uses MAC addresses.

---

## Responsibilities

* Framing
* Error Detection
* Physical Addressing

---

## Address Used

MAC Address

Example:

00:1A:2B:3C:4D:5E

---

## Devices

* Switch
* Bridge

---

## Real-Life Example

A switch uses MAC addresses to determine where to send data inside a LAN.

---

## DevOps Relevance

Kubernetes networking

Container networking

VLAN configuration

Switching concepts

---

# Layer 1 - Physical Layer

## Purpose

Responsible for actual transmission of bits.

Handles hardware communication.

---

## Responsibilities

* Electrical Signals
* Optical Signals
* Cables
* Connectors

---

## Devices

* Hub
* Repeater
* Cable

---

## Examples

* Ethernet Cable
* Fiber Cable
* RJ45 Connector

---

## Real-Life Example

Physical wires carrying internet data from ISP to your router.

---

# Data Encapsulation Process

When data travels from sender to receiver:

Application Layer
↓
Presentation Layer
↓
Session Layer
↓
Transport Layer
↓
Network Layer
↓
Data Link Layer
↓
Physical Layer

At the receiver side, the process happens in reverse order.

---

# PDU (Protocol Data Unit)

| Layer        | PDU     |
| ------------ | ------- |
| Application  | Data    |
| Presentation | Data    |
| Session      | Data    |
| Transport    | Segment |
| Network      | Packet  |
| Data Link    | Frame   |
| Physical     | Bits    |

---

# OSI vs TCP/IP Model

| OSI          | TCP/IP         |
| ------------ | -------------- |
| Application  | Application    |
| Presentation | Application    |
| Session      | Application    |
| Transport    | Transport      |
| Network      | Internet       |
| Data Link    | Network Access |
| Physical     | Network Access |

---

# Interview Questions

## What is OSI Model?

OSI Model is a 7-layer conceptual framework used to understand network communication.

---

## Which layer handles routing?

Network Layer (Layer 3)

---

## Which layer uses IP Address?

Network Layer (Layer 3)

---

## Which layer uses MAC Address?

Data Link Layer (Layer 2)

---

## Difference between TCP and UDP?

TCP:

* Reliable
* Connection-oriented
* Slower

UDP:

* Fast
* Connectionless
* Less reliable

---

## Which layer is responsible for encryption?

Presentation Layer

---

## Which layer works with switches?

Data Link Layer

---

## Which layer works with routers?

Network Layer

---

## Explain OSI Model using a website request.

1. User enters URL in browser.
2. Application Layer generates request.
3. Presentation Layer encrypts data.
4. Session Layer creates session.
5. Transport Layer creates TCP connection.
6. Network Layer adds IP address.
7. Data Link Layer adds MAC address.
8. Physical Layer transmits bits through cable.
9. Server receives request and sends response back.
