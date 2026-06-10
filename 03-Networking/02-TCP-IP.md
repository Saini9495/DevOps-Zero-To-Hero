# TCP/IP Model

## What is TCP/IP?

TCP/IP (Transmission Control Protocol / Internet Protocol) is a set of communication protocols that enables computers and devices to communicate over the Internet and private networks.

It is the foundation of modern networking and is used by almost every device connected to the Internet.

Unlike the OSI model, which is mainly a conceptual model, TCP/IP is a practical model used in real-world networking.

---

## Why TCP/IP is Important?

Without TCP/IP:

- Computers would not be able to communicate over the Internet.
- Websites would not open.
- Emails could not be sent.
- Online gaming and video streaming would not work.

Every time you open a website, send a message, or stream a video, TCP/IP protocols are working behind the scenes.

---

## TCP/IP Architecture

The TCP/IP model consists of 4 layers:

```text
+---------------------+
| Application Layer   |
+---------------------+
| Transport Layer     |
+---------------------+
| Internet Layer      |
+---------------------+
| Network Access Layer|
+---------------------+
```

---

# 1. Application Layer

The Application Layer is the top layer of the TCP/IP model.

It provides network services directly to end-user applications.

Examples:

- Google Chrome
- Firefox
- WhatsApp
- Outlook
- Postman

Protocols:

| Protocol | Purpose |
|-----------|-----------|
| HTTP | Website Communication |
| HTTPS | Secure Website Communication |
| FTP | File Transfer |
| SMTP | Sending Emails |
| POP3 | Receiving Emails |
| IMAP | Email Synchronization |
| DNS | Domain Name Resolution |
| SSH | Secure Remote Access |

Example:

When you open:

https://google.com

Your browser uses HTTP/HTTPS protocols from the Application Layer.

---

# 2. Transport Layer

The Transport Layer is responsible for communication between applications.

Main Responsibilities:

- Reliable communication
- Error detection
- Flow control
- Data segmentation
- End-to-end communication

Protocols:

- TCP
- UDP

---

# TCP (Transmission Control Protocol)

TCP is a connection-oriented protocol.

It ensures:

- Data reaches destination
- Data reaches in correct order
- Missing packets are retransmitted

Features:

- Reliable
- Ordered delivery
- Error checking
- Acknowledgements
- Flow control

Examples:

- HTTPS
- SSH
- FTP
- Banking Applications
- Email

### Real Life Example

Imagine sending an important document through courier.

You want:

- Delivery confirmation
- Correct delivery
- Re-delivery if lost

This is how TCP works.

---

## TCP Three-Way Handshake

Before communication begins, TCP establishes a connection.

### Step 1: SYN

Client sends SYN request.

```text
Client ------ SYN ------> Server
```

Meaning:

"I want to establish a connection."

---

### Step 2: SYN-ACK

Server responds.

```text
Client <--- SYN-ACK ----- Server
```

Meaning:

"I received your request and I'm ready."

---

### Step 3: ACK

Client sends ACK.

```text
Client ------ ACK ------> Server
```

Meaning:

"Connection established."

---

### Connection Established

```text
Client <==== Data Transfer ====> Server
```

---

## TCP Packet Flow Example

Suppose:

Client sends:

```text
Packet 1
Packet 2
Packet 3
```

If Packet 2 gets lost:

```text
Packet 1 ✓
Packet 2 ❌
Packet 3 ✓
```

TCP automatically requests Packet 2 again.

This makes TCP reliable.

---

# UDP (User Datagram Protocol)

UDP is a connectionless protocol.

It does not establish a connection before sending data.

It simply sends packets.

Features:

- Fast
- Lightweight
- No acknowledgements
- No retransmission
- Less overhead

Examples:

- Online Gaming
- Video Streaming
- Voice Calls
- DNS Queries
- Live Broadcasting

---

## Real Life Example

Imagine a live cricket match.

If one frame is lost:

Nobody notices.

But if the stream pauses every second to recover lost packets, the experience becomes poor.

Therefore UDP is preferred.

---

## TCP vs UDP

| Feature | TCP | UDP |
|----------|------|------|
| Reliability | Yes | No |
| Connection | Required | Not Required |
| Speed | Slower | Faster |
| Acknowledgement | Yes | No |
| Error Recovery | Yes | No |
| Packet Ordering | Yes | No |
| Streaming | Not Preferred | Preferred |
| Gaming | Not Preferred | Preferred |

---

# 3. Internet Layer

The Internet Layer is responsible for routing packets from source to destination.

Main Protocol:

- IP (Internet Protocol)

Functions:

- Logical addressing
- Routing
- Packet forwarding

Example:

Your laptop:

```text
192.168.1.10
```

Google Server:

```text
142.250.xxx.xxx
```

The Internet Layer finds the best route between them.

---

## IPv4

IPv4 uses 32-bit addresses.

Example:

```text
192.168.1.1
```

Total possible addresses:

```text
4.3 Billion
```

---

## IPv6

IPv6 uses 128-bit addresses.

Example:

```text
2001:db8::1
```

Benefits:

- Huge address space
- Better scalability
- Future-proof

---

# 4. Network Access Layer

This layer is responsible for actual physical communication.

It handles:

- MAC Addresses
- Network Cards
- Ethernet
- Wi-Fi

Examples:

- Ethernet Cable
- Wi-Fi
- Switches
- NIC Cards

---

## Data Flow Example

Suppose you open:

https://google.com

### Step 1

Application Layer:

Browser generates HTTP request.

↓

### Step 2

Transport Layer:

TCP breaks data into packets.

↓

### Step 3

Internet Layer:

IP assigns source and destination addresses.

↓

### Step 4

Network Access Layer:

Data is transmitted through Ethernet or Wi-Fi.

↓

### Step 5

Google Server receives request.

↓

### Step 6

Response comes back through same layers.

---

# OSI vs TCP/IP

| OSI Model | TCP/IP Model |
|------------|-------------|
| Application | Application |
| Presentation | Application |
| Session | Application |
| Transport | Transport |
| Network | Internet |
| Data Link | Network Access |
| Physical | Network Access |

---

# Why TCP/IP is Used Instead of OSI?

- Simpler architecture
- Practical implementation
- Internet standard
- Widely supported
- Easier deployment

OSI is mainly used for learning concepts.

TCP/IP is used in real networks.

---

# DevOps Perspective

As a DevOps Engineer, TCP/IP knowledge is important because:

- Kubernetes networking uses TCP/IP.
- Docker containers communicate using TCP/IP.
- Load Balancers work using TCP/IP.
- DNS depends on TCP/IP.
- CI/CD pipelines communicate over TCP/IP.
- AWS networking is based on TCP/IP.

---

# Interview Questions

## What is TCP/IP?

TCP/IP is a suite of communication protocols used for networking and Internet communication.

---

## How many layers are there in TCP/IP?

4 Layers:

1. Application
2. Transport
3. Internet
4. Network Access

---

## Difference between TCP and UDP?

TCP is reliable and connection-oriented.

UDP is faster and connectionless.

---

## Why is TCP reliable?

Because it uses:

- Acknowledgements
- Retransmission
- Sequence Numbers
- Error Checking

---

## What is Three-Way Handshake?

A process used by TCP to establish a connection.

Steps:

1. SYN
2. SYN-ACK
3. ACK

---

## Why does DNS use UDP?

Because DNS queries are small and speed is more important than reliability.

---

## Which protocol is used by HTTPS?

TCP

---

## Which protocol is used by Online Gaming?

Mostly UDP

---

## Which layer handles routing?

Internet Layer

---

## What is the role of IP?

IP provides addressing and routing between devices.