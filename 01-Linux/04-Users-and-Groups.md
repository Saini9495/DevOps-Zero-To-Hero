# Linux Users and Groups

## Introduction

Linux is a multi-user operating system, meaning multiple users can access and work on the same system simultaneously.

To maintain security and proper resource management, Linux uses:

* Users
* Groups
* Permissions
* Ownership

Every file, process, and service in Linux is associated with a user and a group.

---

# What is a User?

A User is an account that can log in and interact with the Linux system.

Each user has:

* Username
* Password
* User ID (UID)
* Home Directory
* Default Shell

Examples:

```text
root
ubuntu
ec2-user
devops
jenkins
```

---

# Why Users are Important?

Users help Linux:

* Identify who is using the system
* Control access to files
* Improve security
* Prevent unauthorized actions
* Manage system resources

Example:

A developer should not have permission to modify database files.

---

# Types of Users

Linux generally has three types of users.

---

## 1. Root User

The root user is the super administrator of Linux.

### Features

* Full system access
* Can modify any file
* Can install software
* Can create and delete users
* Can stop critical services

### UID

```text
0
```

### Example

```bash
whoami
```

Output:

```text
root
```

### Warning

A mistake made by the root user can damage the entire system.

Example:

```bash
rm -rf /
```

Never run dangerous commands without understanding them.

---

## 2. Normal User

Regular users with limited permissions.

Examples:

```text
ubuntu
rishabh
devops
```

### Features

* Can access personal files
* Cannot modify system files
* Require sudo privileges for administrative tasks

### Example

```bash
whoami
```

Output:

```text
ubuntu
```

---

## 3. System Users

Created automatically by Linux for services and applications.

Examples:

```text
www-data
mysql
nginx
docker
```

### Purpose

Services run under separate accounts for security.

Example:

```text
Nginx → www-data
MySQL → mysql
```

---

# User Identification

Every user in Linux has a unique identifier.

---

## UID (User ID)

Unique numeric identifier assigned to a user.

Example:

```bash
id
```

Output:

```text
uid=1000(ubuntu)
```

### Common UID Ranges

| UID Range | Purpose      |
| --------- | ------------ |
| 0         | Root User    |
| 1-999     | System Users |
| 1000+     | Normal Users |

---

## GID (Group ID)

Every group also has a unique identifier.

Example:

```bash
id
```

Output:

```text
gid=1000(ubuntu)
```

---

# Creating Users

## useradd Command

Creates a new user account.

### Syntax

```bash
sudo useradd username
```

### Example

```bash
sudo useradd devops
```

Verify:

```bash
cat /etc/passwd | grep devops
```

---

## Create User with Home Directory

```bash
sudo useradd -m devops
```

Creates:

```text
/home/devops
```

---

## Set Password

```bash
sudo passwd devops
```

Example:

```bash
sudo passwd devops
```

Output:

```text
New password:
Retype new password:
```

---

# Deleting Users

## Delete User

```bash
sudo userdel devops
```

---

## Delete User with Home Directory

```bash
sudo userdel -r devops
```

Removes:

* User Account
* Home Directory
* User Files

---

# Modifying Users

Change username:

```bash
sudo usermod -l newname oldname
```

Change home directory:

```bash
sudo usermod -d /home/newuser username
```

Lock user account:

```bash
sudo usermod -L username
```

Unlock user account:

```bash
sudo usermod -U username
```

---

# What is a Group?

A Group is a collection of users.

Groups simplify permission management.

Instead of assigning permissions to each user individually, permissions can be assigned to a group.

---

# Why Groups are Important?

Suppose 20 developers need access to a project directory.

Without groups:

```text
Assign permissions individually to 20 users.
```

With groups:

```text
Create one group.
Add users.
Assign permissions once.
```

Much easier to manage.

---

# Creating Groups

## groupadd

Creates a new group.

### Syntax

```bash
sudo groupadd groupname
```

### Example

```bash
sudo groupadd developers
```

Verify:

```bash
cat /etc/group | grep developers
```

---

# Adding Users to Groups

### Syntax

```bash
sudo usermod -aG groupname username
```

### Example

```bash
sudo usermod -aG developers devops
```

Check membership:

```bash
groups devops
```

Output:

```text
devops developers
```

---

# Viewing User Information

## whoami

Displays current user.

```bash
whoami
```

Output:

```text
ubuntu
```

---

## id

Displays UID, GID, and groups.

```bash
id
```

Example:

```text
uid=1000(ubuntu)
gid=1000(ubuntu)
groups=1000(ubuntu),27(sudo)
```

---

## groups

Displays group memberships.

```bash
groups
```

---

## who

Shows logged-in users.

```bash
who
```

---

## w

Shows logged-in users and their activities.

```bash
w
```

---

# Switching Users

## su Command

Switch to another user account.

### Syntax

```bash
su username
```

### Example

```bash
su devops
```

Switch to root:

```bash
su -
```

---

# Sudo

## What is sudo?

Sudo stands for:

```text
Super User Do
```

Allows a normal user to execute commands with root privileges.

---

## Example

Update packages:

```bash
sudo apt update
```

Install software:

```bash
sudo apt install nginx
```

Restart service:

```bash
sudo systemctl restart nginx
```

---

# Why Use Sudo Instead of Root Login?

Security reasons.

Advantages:

* Better auditing
* Reduced risk
* Temporary privilege escalation
* Activity logging

---

# Important User Files

## /etc/passwd

Stores user account information.

View file:

```bash
cat /etc/passwd
```

Example Entry:

```text
ubuntu:x:1000:1000:Ubuntu User:/home/ubuntu:/bin/bash
```

Contains:

* Username
* UID
* GID
* Home Directory
* Login Shell

---

## /etc/group

Stores group information.

View:

```bash
cat /etc/group
```

Example:

```text
developers:x:1001:
```

---

## /etc/shadow

Stores encrypted passwords.

View:

```bash
sudo cat /etc/shadow
```

Example:

```text
ubuntu:$6$encrypted_password...
```

Only root can access this file.

---

# Real DevOps Examples

## Add Jenkins User

```bash
sudo useradd -m jenkins
```

---

## Add User to Docker Group

```bash
sudo usermod -aG docker ubuntu
```

Allows Docker commands without sudo.

---

## Add User to Sudo Group

Ubuntu:

```bash
sudo usermod -aG sudo devops
```

Verify:

```bash
groups devops
```

---

# Security Best Practices

### Use sudo instead of root login

Recommended.

---

### Remove inactive users

```bash
sudo userdel username
```

---

### Use strong passwords

Always enforce password policies.

---

### Follow Principle of Least Privilege

Give only the permissions required.

---

# Summary

Linux uses users and groups to manage access and security. Every user has a UID, every group has a GID, and permissions are assigned through ownership and group memberships. Understanding users, groups, and sudo access is essential for Linux Administration, Cloud Computing, and DevOps Engineering.

---

# Interview Questions

### What is a User?

A user is an account that can access and interact with a Linux system.

### What is a Group?

A group is a collection of users used for permission management.

### What is UID?

UID (User ID) is a unique numeric identifier assigned to a user.

### What is GID?

GID (Group ID) is a unique numeric identifier assigned to a group.

### What is the UID of the root user?

```text
0
```

### What is sudo?

sudo allows a user to execute commands with elevated privileges.

### Difference between su and sudo?

| su                              | sudo                                |
| ------------------------------- | ----------------------------------- |
| Switches user account           | Executes a command as another user  |
| Requires target user's password | Requires current user's password    |
| Provides full shell access      | Executes only the specified command |

### Which file stores user information?

```text
/etc/passwd
```

### Which file stores encrypted passwords?

```text
/etc/shadow
```

### Which file stores group information?

```text
/etc/group
```

### How do you add a user to a group?

```bash
sudo usermod -aG groupname username
```

### How do you check user information?

```bash
id username
```
