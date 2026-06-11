# Linux File System

## What is a File System?

A File System is the method used by an operating system to organize, store, manage, and retrieve files and directories on a storage device.

In Linux, everything is treated as a file, including:

* Regular files
* Directories
* Hardware devices
* Processes
* Network sockets

The Linux File System follows a hierarchical tree structure that starts from a single root directory.

---

# Linux Directory Structure

Everything in Linux begins from the Root Directory:

```bash
/
```

Unlike Windows, Linux does not use drive letters such as C:, D:, or E:.

Example:

Windows:

```text
C:\Users\Rishabh\Documents
```

Linux:

```bash
/home/rishabh/Documents
```

---

# Linux File System Hierarchy

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

---

# Important Linux Directories

## 1. Root Directory (/)

The top-most directory in Linux.

Every file and directory exists under this directory.

Example:

```bash
cd /
```

View root contents:

```bash
ls /
```

---

## 2. Home Directory (/home)

Contains personal directories of users.

Example:

```bash
/home/rishabh
/home/ubuntu
/home/devops
```

When a new user is created, Linux automatically creates a home directory.

Example:

```bash
sudo useradd devops
```

Creates:

```bash
/home/devops
```

### DevOps Use Case

Most engineers store scripts, projects, and configuration files inside their home directory.

---

## 3. Root User Home (/root)

This is the home directory of the root user.

Example:

```bash
/root
```

Root user has complete control over the system.

### Difference

```text
/home/ubuntu  -> Normal User
/root         -> Root User
```

---

## 4. Configuration Directory (/etc)

Stores system-wide configuration files.

One of the most important directories in Linux.

Examples:

```bash
/etc/passwd
/etc/group
/etc/hosts
/etc/fstab
/etc/ssh/sshd_config
```

### Common Use Cases

Check hostname:

```bash
cat /etc/hostname
```

View user accounts:

```bash
cat /etc/passwd
```

### DevOps Use Case

Most application and service configurations are stored in `/etc`.

Examples:

* Nginx
* Apache
* Docker
* SSH

---

## 5. Binary Directory (/bin)

Contains essential command binaries required for system operation.

Examples:

```bash
/bin/ls
/bin/cp
/bin/mv
/bin/cat
```

Verify location:

```bash
which ls
```

Output:

```bash
/bin/ls
```

---

## 6. System Binary Directory (/sbin)

Contains system administration commands.

Examples:

```bash
/sbin/reboot
/sbin/fdisk
/sbin/iptables
```

Usually used by root users.

---

## 7. User Programs Directory (/usr)

Stores installed software and user applications.

Structure:

```text
/usr
├── bin
├── sbin
├── lib
└── share
```

Examples:

```bash
/usr/bin/python3
/usr/bin/docker
```

### DevOps Use Case

Most installed applications are stored here.

---

## 8. Variable Data Directory (/var)

Stores data that changes frequently.

Examples:

```bash
/var/log
/var/cache
/var/spool
```

### Important Location

```bash
/var/log
```

Contains logs for:

* Nginx
* Apache
* Docker
* System Services

Example:

```bash
cd /var/log
ls
```

### DevOps Use Case

Log analysis and troubleshooting.

---

## 9. Temporary Directory (/tmp)

Stores temporary files.

Example:

```bash
/tmp
```

Files in this directory may be deleted automatically after reboot.

Create file:

```bash
touch /tmp/test.txt
```

### DevOps Use Case

Temporary script outputs and debugging files.

---

## 10. Device Directory (/dev)

Contains device files.

In Linux, hardware devices are represented as files.

Examples:

```bash
/dev/sda
/dev/sdb
/dev/null
/dev/random
```

### Common Example

Discard output:

```bash
ls > /dev/null
```

### DevOps Use Case

Disk management and hardware troubleshooting.

---

## 11. Process Directory (/proc)

Virtual file system containing process information.

Examples:

```bash
/proc/cpuinfo
/proc/meminfo
```

View CPU Information:

```bash
cat /proc/cpuinfo
```

View Memory Information:

```bash
cat /proc/meminfo
```

### DevOps Use Case

Monitoring system resources.

---

## 12. Boot Directory (/boot)

Contains files required for system startup.

Examples:

```bash
/boot/vmlinuz
/boot/grub
```

### Important Components

* Linux Kernel
* GRUB Bootloader

### DevOps Use Case

Troubleshooting boot failures.

---

## 13. Media Directory (/media)

Used for automatically mounted devices.

Examples:

```bash
/media/usb
/media/cdrom
```

USB drives often appear here.

---

## 14. Mount Directory (/mnt)

Used for manually mounted storage devices.

Example:

Mount a disk:

```bash
sudo mount /dev/sdb1 /mnt
```

### DevOps Use Case

Attaching EBS volumes and external storage.

---

## 15. Optional Software Directory (/opt)

Used for third-party applications.

Examples:

```bash
/opt/google
/opt/tomcat
```

### DevOps Use Case

Installing custom applications.

---

# File Types in Linux

## Regular File

Examples:

```bash
notes.txt
script.sh
app.py
```

---

## Directory

Example:

```bash
Documents/
Downloads/
```

---

## Symbolic Link

Shortcut to another file.

Create:

```bash
ln -s original.txt shortcut.txt
```

---

## Device File

Example:

```bash
/dev/sda
```

---

# Absolute and Relative Paths

## Absolute Path

Starts from root (/).

Example:

```bash
/home/ubuntu/project/app.py
```

Can be accessed from anywhere.

---

## Relative Path

Starts from current directory.

Example:

```bash
project/app.py
```

Depends on current location.

---

# Check Current Directory Structure

Show current directory:

```bash
pwd
```

List contents:

```bash
ls
```

Recursive view:

```bash
tree
```

Install tree:

```bash
sudo apt install tree
```

Example:

```bash
tree /home/ubuntu
```

---

# Linux File System in Cloud and DevOps

As a DevOps Engineer, the most commonly used directories are:

```text
/etc      -> Configurations
/var/log  -> Logs
/home     -> Projects
/tmp      -> Temporary Files
/proc     -> System Information
/dev      -> Device Information
/usr      -> Installed Software
```

Real-world troubleshooting often involves:

* Checking logs in `/var/log`
* Editing configurations in `/etc`
* Monitoring CPU using `/proc`
* Mounting storage in `/mnt`

---

# Summary

The Linux File System follows a hierarchical structure starting from the root directory (`/`). Understanding the purpose of directories such as `/etc`, `/var`, `/proc`, `/dev`, and `/usr` is essential for system administration, cloud computing, and DevOps engineering.

---

# Interview Questions

### What is the Linux Root Directory?

The root directory (`/`) is the top-most directory in Linux from which all other directories originate.

### What is stored in `/etc`?

System-wide configuration files.

### What is stored in `/var`?

Variable data such as logs, caches, and spool files.

### What is `/proc`?

A virtual file system containing process and kernel information.

### What is `/dev`?

A directory containing device files representing hardware devices.

### Difference between `/home` and `/root`?

`/home` contains directories of normal users, while `/root` is the home directory of the root user.

### Difference between Absolute and Relative Paths?

Absolute paths start from `/`, while relative paths start from the current working directory.

### Which directory contains system logs?

```bash
/var/log
```

### Which directory contains configuration files?

```bash
/etc
```
