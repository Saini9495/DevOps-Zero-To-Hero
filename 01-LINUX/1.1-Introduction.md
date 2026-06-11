# Linux Introduction

## What is Linux?

Linux is an open-source operating system kernel created by Linus Torvalds in 1991. It is one of the most widely used operating systems in the world, especially in servers, cloud platforms, embedded systems, and DevOps environments.

An Operating System (OS) acts as an interface between the user and computer hardware. Linux manages hardware resources such as CPU, memory, storage devices, and networking components while providing services to applications.

Today, Linux powers:

* Most cloud servers
* Supercomputers
* Android smartphones
* IoT devices
* Enterprise data centers
* Container platforms such as Docker and Kubernetes

---

## History of Linux

### Unix

Linux was inspired by the Unix operating system, which was developed in the 1970s.

### MINIX

A teaching operating system called MINIX inspired Linus Torvalds to create Linux.

### Linux Kernel (1991)

Linus Torvalds released the first version of the Linux kernel in 1991.

### GNU Project

The GNU Project provided many essential tools and utilities that, together with the Linux kernel, formed a complete operating system commonly referred to as GNU/Linux.

---

## What is an Operating System?

An Operating System is software that manages computer hardware and software resources.

Responsibilities include:

* Process Management
* Memory Management
* File Management
* Device Management
* Security
* User Management

Examples:

* Linux
* Windows
* macOS

---

## Why Linux is Important for DevOps?

Linux is considered the foundation of modern DevOps.

Most cloud providers use Linux-based virtual machines:

* AWS EC2
* Azure Virtual Machines
* Google Compute Engine

Most DevOps tools run natively on Linux:

* Docker
* Kubernetes
* Jenkins
* Terraform
* Ansible
* Prometheus
* Grafana

As a DevOps Engineer, daily tasks often involve:

* Managing Linux servers
* Monitoring processes
* Troubleshooting applications
* Managing permissions
* Writing shell scripts
* Deploying applications

Without Linux knowledge, becoming a successful DevOps Engineer is extremely difficult.

---

## Features of Linux

### 1. Open Source

Linux source code is publicly available.

Benefits:

* Free to use
* Customizable
* Community support
* Transparency

### 2. Multi-User

Multiple users can work on the same system simultaneously.

Example:

A server can host multiple developers and administrators.

### 3. Multi-Tasking

Linux can run multiple programs at the same time.

Example:

A server can run:

* Nginx
* Jenkins
* Docker
* MySQL

simultaneously.

### 4. Security

Linux provides strong security mechanisms.

Examples:

* User permissions
* File ownership
* Firewalls
* SELinux

### 5. Stability

Linux servers can run for months or even years without requiring reboots.

### 6. Portability

Linux can run on:

* Laptops
* Servers
* Mobile devices
* Embedded systems
* Raspberry Pi

### 7. Networking Support

Linux offers powerful networking capabilities.

Examples:

* SSH
* FTP
* DNS
* VPN
* Web Servers

---

## Linux Architecture

```text
User
  │
  ▼
Shell
  │
  ▼
Kernel
  │
  ▼
Hardware
```

### User

The person interacting with the system.

Examples:

* System Administrator
* DevOps Engineer
* Developer

### Shell

The shell is a command-line interpreter.

It accepts commands from users and sends them to the kernel.

Popular shells:

* Bash
* Zsh
* Fish
* Sh

Example:

```bash
pwd
ls
mkdir devops
```

### Kernel

The kernel is the heart of Linux.

Functions of the kernel:

#### Process Management

Controls running processes.

#### Memory Management

Allocates and manages RAM.

#### Device Management

Communicates with hardware devices.

#### File System Management

Handles files and directories.

#### Security

Manages user permissions and access control.

### Hardware

Physical components:

* CPU
* RAM
* Hard Disk
* Network Card
* USB Devices

---

## Linux Distributions

A Linux Distribution is a complete operating system built around the Linux kernel.

### Ubuntu

Most beginner-friendly Linux distribution.

Used in:

* Cloud Servers
* DevOps Labs
* Learning

### Debian

Known for stability and reliability.

### Fedora

Provides cutting-edge features.

### RHEL (Red Hat Enterprise Linux)

Enterprise-grade Linux distribution.

Used by:

* Banks
* Enterprises
* Large Organizations

### CentOS

Historically a free alternative to RHEL.

### Rocky Linux

Popular replacement for CentOS.

---

## Linux File Structure Overview

Everything in Linux starts from the root directory:

```bash
/
```

Important directories:

```bash
/
├── home
├── root
├── etc
├── var
├── bin
├── usr
├── tmp
├── proc
├── dev
└── opt
```

Examples:

```bash
/home/ubuntu
/etc/passwd
/var/log
```

---

## Linux in Cloud Computing

Linux dominates cloud infrastructure.

Popular cloud services:

### AWS

* EC2
* ECS
* EKS

### Azure

* Virtual Machines
* AKS

### Google Cloud

* Compute Engine
* GKE

Most Kubernetes clusters run Linux-based worker nodes.

---

## Linux in Containers

Containers rely heavily on Linux kernel features.

Examples:

* Namespaces
* Control Groups (cgroups)
* Overlay File Systems

Container platforms:

* Docker
* Podman
* Kubernetes

---

## Real-World Example

Think of Linux as a hotel.

### Hardware

The building.

### Kernel

The hotel manager.

### Shell

Reception desk.

### User

Guests.

When a guest requests a room:

1. Guest talks to Reception.
2. Reception contacts Manager.
3. Manager allocates room resources.
4. Guest gets access.

Similarly:

1. User enters command.
2. Shell receives command.
3. Kernel processes request.
4. Hardware executes operation.

---

## Advantages of Linux

* Free and open-source
* Highly secure
* Stable and reliable
* Excellent performance
* Strong community support
* Ideal for servers
* Best choice for DevOps and Cloud

---

## Linux vs Windows

| Feature        | Linux       | Windows       |
| -------------- | ----------- | ------------- |
| Cost           | Free        | Paid          |
| Source Code    | Open Source | Closed Source |
| Security       | High        | Moderate      |
| Performance    | Excellent   | Good          |
| Customization  | High        | Limited       |
| Server Usage   | Very High   | Moderate      |
| Resource Usage | Low         | Higher        |

---

## Summary

Linux is the backbone of modern cloud computing and DevOps. Most production servers, Kubernetes clusters, Docker hosts, and cloud environments run Linux. A strong understanding of Linux is essential for anyone pursuing a career in DevOps, Cloud Engineering, Site Reliability Engineering (SRE), or System Administration.

---

# Interview Questions

### What is Linux?

Linux is an open-source operating system kernel that manages hardware resources and allows software applications to communicate with hardware.

### What is a Kernel?

The kernel is the core component of an operating system responsible for managing CPU, memory, devices, files, and processes.

### Why is Linux preferred in DevOps?

Because Linux is stable, secure, lightweight, highly customizable, and widely used in cloud and server environments.

### What is the difference between Linux and Unix?

Unix is a proprietary operating system family, while Linux is an open-source Unix-like operating system.

### Name some popular Linux distributions.

* Ubuntu
* Debian
* Fedora
* RHEL
* Rocky Linux

### What is a Linux Distribution?

A Linux distribution is a complete operating system built using the Linux kernel along with system utilities and package management tools.

### What are the main components of Linux Architecture?

* User
* Shell
* Kernel
* Hardware

### What is the role of the Shell?

The shell acts as an interface between the user and the kernel and executes user commands.
