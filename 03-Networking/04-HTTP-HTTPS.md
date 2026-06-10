# HTTP and HTTPS

## Introduction

Whenever we open a website in a browser, the browser communicates with a web server. This communication happens using a protocol called HTTP or HTTPS.

Example:

When you type:

https://www.google.com

Your browser sends a request to Google's server and the server sends back a response containing the webpage.

---

# What is HTTP?

HTTP stands for HyperText Transfer Protocol.

It is an application-layer protocol used for communication between a client and a server.

HTTP defines how requests and responses should be exchanged over the internet.

Default Port:

80

---

# Components of HTTP Communication

There are two main components:

1. Client
2. Server

Example:

Browser → Client

Google Server → Server

Flow:

Browser
↓
HTTP Request
↓
Web Server
↓
HTTP Response
↓
Browser

---

# HTTP Request

When a user visits a website, the browser sends an HTTP request.

Example:

GET /index.html HTTP/1.1
Host: google.com

Components of Request:

* Method
* URL
* Headers
* Body (optional)

---

# HTTP Methods

## GET

Used to retrieve data.

Example:

GET /users

Returns user data.

---

## POST

Used to create new resources.

Example:

POST /users

Creates a new user.

---

## PUT

Used to update an existing resource completely.

Example:

PUT /users/1

Updates user information.

---

## PATCH

Used to update specific fields.

Example:

PATCH /users/1

Updates only selected fields.

---

## DELETE

Used to remove resources.

Example:

DELETE /users/1

Deletes user.

---

# HTTP Response

After receiving a request, the server sends a response.

Example:

HTTP/1.1 200 OK

Content-Type: text/html

<html>
Website Content
</html>

Response Contains:

* Status Code
* Headers
* Response Body

---

# HTTP Status Codes

Status codes indicate whether the request was successful.

---

## 1xx Informational

100 Continue

Indicates processing has started.

---

## 2xx Success

Request completed successfully.

### 200 OK

Request successful.

### 201 Created

Resource created successfully.

### 204 No Content

Success but no content returned.

---

## 3xx Redirection

Browser must take additional action.

### 301 Moved Permanently

Permanent redirect.

Example:

http://google.com

redirects to

https://google.com

### 302 Found

Temporary redirect.

---

## 4xx Client Errors

Problem on client side.

### 400 Bad Request

Invalid request.

### 401 Unauthorized

Authentication required.

### 403 Forbidden

Permission denied.

### 404 Not Found

Requested resource does not exist.

---

## 5xx Server Errors

Problem on server side.

### 500 Internal Server Error

Unexpected server issue.

### 502 Bad Gateway

Invalid response from upstream server.

### 503 Service Unavailable

Server temporarily unavailable.

---

# Limitations of HTTP

HTTP sends data in plain text.

Problems:

* Anyone can read transmitted data.
* Passwords can be intercepted.
* Sensitive information is exposed.

Example:

Public WiFi

Attacker
↓
Reads Data
↓
Username
Password

This is why HTTPS was introduced.

---

# What is HTTPS?

HTTPS stands for HyperText Transfer Protocol Secure.

HTTPS = HTTP + SSL/TLS Encryption

Default Port:

443

HTTPS encrypts communication between client and server.

---

# Benefits of HTTPS

## 1. Encryption

Data is converted into unreadable format.

Example:

Password = admin123

Encrypted Data:

A7x92Kj!@#

Only intended receiver can decrypt it.

---

## 2. Authentication

Verifies that the website is genuine.

Example:

You are actually connected to Google and not a fake website.

---

## 3. Integrity

Ensures data is not modified during transmission.

---

# SSL vs TLS

SSL = Secure Sockets Layer

TLS = Transport Layer Security

TLS is the modern and secure version.

Nowadays people often say SSL certificate even though TLS is actually used.

---

# SSL/TLS Handshake

Before encrypted communication starts, a handshake occurs.

Step 1:

Client sends request.

Browser → Server

---

Step 2:

Server sends SSL/TLS certificate.

Server → Browser

---

Step 3:

Browser verifies certificate.

Checks:

* Certificate Authority
* Expiry Date
* Domain Name

---

Step 4:

Session key is generated.

---

Step 5:

Encrypted communication starts.

Browser ↔ Server

All data is now encrypted.

---

# What is an SSL Certificate?

An SSL certificate is a digital certificate that verifies website identity.

Example:

[www.google.com](http://www.google.com)

Certificate issued by trusted Certificate Authority.

Popular Certificate Authorities:

* DigiCert
* Sectigo
* GlobalSign
* Let's Encrypt

---

# How HTTPS Works (Real Example)

Suppose you login to Gmail.

Without HTTPS:

Email
Password

Travel as plain text.

Anyone can read them.

With HTTPS:

Email
Password

Encrypted before transmission.

Even if intercepted, the attacker cannot read them.

---

# HTTP vs HTTPS

| Feature         | HTTP     | HTTPS  |
| --------------- | -------- | ------ |
| Security        | No       | Yes    |
| Encryption      | No       | Yes    |
| Authentication  | No       | Yes    |
| Data Integrity  | No       | Yes    |
| Port            | 80       | 443    |
| SEO Ranking     | Lower    | Better |
| Browser Warning | Possible | No     |

---

# HTTP in DevOps

A DevOps Engineer frequently works with:

* Web Servers
* Reverse Proxies
* Load Balancers
* APIs
* Kubernetes Ingress
* SSL Certificates

Examples:

NGINX

Apache

HAProxy

AWS ALB

Kubernetes Ingress

Understanding HTTP and HTTPS is essential for troubleshooting production issues.

---

# Common Commands

Check Headers

curl -I https://google.com

---

View Full Response

curl -v https://google.com

---

Check SSL Certificate

openssl s_client -connect google.com:443

---

# Real-Life Analogy

Imagine sending a postcard.

HTTP:

Anyone handling the postcard can read the message.

HTTPS:

Message is placed inside a locked box.

Only sender and receiver have the key.

---

# Interview Questions

## What is HTTP?

HTTP is an application-layer protocol used for communication between a client and a server.

---

## What is HTTPS?

HTTPS is HTTP secured using SSL/TLS encryption.

---

## What is the default port of HTTP?

80

---

## What is the default port of HTTPS?

443

---

## Difference between HTTP and HTTPS?

HTTP transfers data in plain text.

HTTPS encrypts data before transmission.

---

## What is SSL Certificate?

A digital certificate used to verify website identity and establish secure communication.

---

## What is TLS Handshake?

A process through which client and server establish a secure encrypted connection before exchanging data.

---

## Why is HTTPS important?

It provides:

* Encryption
* Authentication
* Integrity

and protects sensitive data from attackers.
