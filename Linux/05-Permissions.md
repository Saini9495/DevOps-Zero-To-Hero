# Linux Permissions

## Introduction

Linux is a multi-user operating system where multiple users can access the same system simultaneously.

To protect files and directories from unauthorized access, Linux uses a permission system.

Permissions determine:

* Who can access a file
* Who can modify a file
* Who can execute a file
* Who can delete a file

Without permissions, any user could modify or delete important system files.

---

# Why Permissions Are Important?

Imagine a production server containing:

```text
Application Code
Database Backups
Configuration Files
SSH Keys
```

If every user had full access:

* Files could be deleted accidentally
* Sensitive data could be leaked
* Servers could be compromised

Linux permissions prevent these issues.

---

# Viewing Permissions

Use:

```bash
ls -l
```

Example:

```bash
-rwxr-xr-- 1 ubuntu developers 2048 Jun 10 deploy.sh
```

Let's understand each part.

---

# Understanding Permission Structure

```text
-rwxr-xr--
```

Breakdown:

```text
-   rwx   r-x   r--
│    │     │     │
│    │     │     └── Others
│    │     └──────── Group
│    └────────────── Owner
└────────────────── File Type
```

---

# File Types

First character represents file type.

| Symbol | Meaning          |
| ------ | ---------------- |
| -      | Regular File     |
| d      | Directory        |
| l      | Symbolic Link    |
| c      | Character Device |
| b      | Block Device     |

Example:

Regular file:

```text
-rw-r--r--
```

Directory:

```text
drwxr-xr-x
```

Symbolic link:

```text
lrwxrwxrwx
```

---

# Permission Categories

Linux permissions are divided into three categories.

## Owner (User)

Person who owns the file.

Example:

```text
ubuntu
```

---

## Group

Users belonging to the assigned group.

Example:

```text
developers
```

---

## Others

Everyone else on the system.

---

# Permission Types

Linux uses three basic permissions.

## Read (r)

Numeric Value:

```text
4
```

Allows:

* View file contents
* Read configuration files

Example:

```bash
cat notes.txt
```

---

## Write (w)

Numeric Value:

```text
2
```

Allows:

* Modify files
* Delete files
* Add data

Example:

```bash
echo "hello" >> notes.txt
```

---

## Execute (x)

Numeric Value:

```text
1
```

Allows:

* Execute scripts
* Run programs

Example:

```bash
./deploy.sh
```

---

# Numeric Permission Calculation

Permission values are calculated using:

```text
Read    = 4
Write   = 2
Execute = 1
```

---

## 7 = rwx

```text
4 + 2 + 1 = 7
```

Permission:

```text
rwx
```

---

## 6 = rw-

```text
4 + 2 = 6
```

Permission:

```text
rw-
```

---

## 5 = r-x

```text
4 + 1 = 5
```

Permission:

```text
r-x
```

---

## 4 = r--

```text
4
```

Permission:

```text
r--
```

---

# Common Permission Values

## 777

```text
rwx rwx rwx
```

Everyone has full access.

### Risk

Very insecure.

Avoid in production environments.

---

## 755

```text
rwx r-x r-x
```

Owner:

* Read
* Write
* Execute

Group:

* Read
* Execute

Others:

* Read
* Execute

Commonly used for:

```text
Scripts
Directories
Applications
```

---

## 644

```text
rw- r-- r--
```

Owner:

* Read
* Write

Group:

* Read

Others:

* Read

Commonly used for:

```text
Configuration Files
Text Files
```

---

## 600

```text
rw-------
```

Owner only.

Used for:

```text
SSH Keys
Passwords
Secrets
```

---

## 700

```text
rwx------
```

Owner has full control.

No access for anyone else.

---

# chmod Command

Used to change permissions.

Syntax:

```bash
chmod permissions file
```

---

## Example

```bash
chmod 755 deploy.sh
```

Verify:

```bash
ls -l deploy.sh
```

Output:

```text
-rwxr-xr-x
```

---

## Another Example

```bash
chmod 644 nginx.conf
```

Output:

```text
-rw-r--r--
```

---

# Symbolic Permissions

Instead of numbers, Linux also supports symbols.

## User Categories

| Symbol | Meaning |
| ------ | ------- |
| u      | User    |
| g      | Group   |
| o      | Others  |
| a      | All     |

---

# Add Permission

Add execute permission:

```bash
chmod u+x deploy.sh
```

---

# Remove Permission

Remove write permission:

```bash
chmod g-w deploy.sh
```

---

# Give Permission to Everyone

```bash
chmod a+x deploy.sh
```

---

# Ownership

Every file has an owner and group.

View ownership:

```bash
ls -l
```

Example:

```text
-rw-r--r-- ubuntu developers notes.txt
```

Owner:

```text
ubuntu
```

Group:

```text
developers
```

---

# chown Command

Changes ownership.

Syntax:

```bash
chown owner file
```

Example:

```bash
sudo chown devops notes.txt
```

---

# Change Owner and Group

```bash
sudo chown devops:developers notes.txt
```

Verify:

```bash
ls -l
```

---

# chgrp Command

Changes group ownership.

Syntax:

```bash
sudo chgrp developers notes.txt
```

---

# Directory Permissions

Permissions work differently on directories.

---

## Read Permission

Allows viewing directory contents.

```bash
ls directory
```

---

## Write Permission

Allows:

* Create files
* Delete files
* Rename files

---

## Execute Permission

Allows entering a directory.

```bash
cd directory
```

---

# Example Directory Permission

```text
drwxr-xr-x
```

Equivalent:

```text
755
```

Meaning:

Owner:

```text
Read Write Execute
```

Group:

```text
Read Execute
```

Others:

```text
Read Execute
```

---

# Recursive Permission Changes

Apply permissions to all files and subdirectories.

Example:

```bash
chmod -R 755 project
```

Change ownership recursively:

```bash
sudo chown -R ubuntu:ubuntu project
```

---

# Special Permissions

Linux provides special permissions.

---

## SUID (Set User ID)

Runs a file with owner's privileges.

Example:

```bash
passwd
```

Check:

```bash
ls -l /usr/bin/passwd
```

Output:

```text
-rwsr-xr-x
```

Notice:

```text
s
```

---

## SGID (Set Group ID)

Runs with group privileges.

Useful for shared directories.

---

## Sticky Bit

Used on directories.

Example:

```text
/tmp
```

Check:

```bash
ls -ld /tmp
```

Output:

```text
drwxrwxrwt
```

Meaning:

Users can only delete their own files.

---

# Umask

Determines default permissions.

Check:

```bash
umask
```

Example Output:

```text
0022
```

Default permissions:

Files:

```text
644
```

Directories:

```text
755
```

---

# Real DevOps Examples

## Make Deployment Script Executable

```bash
chmod +x deploy.sh
```

---

## Secure SSH Private Key

```bash
chmod 600 id_rsa
```

---

## Give Jenkins Access

```bash
sudo chown jenkins:jenkins workspace
```

---

## Secure Kubernetes Config

```bash
chmod 600 ~/.kube/config
```

---

# Security Best Practices

### Avoid 777

Bad:

```bash
chmod 777 file
```

Good:

```bash
chmod 755 script.sh
chmod 644 config.txt
```

---

### Follow Least Privilege Principle

Give only the permissions required.

---

### Protect Sensitive Files

Use:

```bash
chmod 600
```

for:

* SSH Keys
* Secrets
* Password Files

---

# Summary

Linux permissions control access to files and directories. Each file has an owner, group, and permission set. Understanding chmod, chown, chgrp, numeric permissions, symbolic permissions, ownership, and special permissions is essential for Linux Administration, Cloud Computing, DevOps, Docker, Kubernetes, and AWS environments.

---

# Interview Questions

### What are the three permission types in Linux?

* Read (r)
* Write (w)
* Execute (x)

---

### What does chmod do?

Changes file or directory permissions.

---

### What does chown do?

Changes file ownership.

---

### What is the difference between chmod and chown?

| chmod               | chown             |
| ------------------- | ----------------- |
| Changes permissions | Changes ownership |

---

### What does 755 mean?

```text
rwxr-xr-x
```

Owner has full permissions.

Group and others have read and execute permissions.

---

### What does 644 mean?

```text
rw-r--r--
```

Owner can read and write.

Others can only read.

---

### Why is chmod 777 dangerous?

Because everyone gets full read, write, and execute access.

---

### What is SUID?

Allows a file to run with the owner's privileges.

---

### What is Sticky Bit?

Allows users to delete only their own files in a shared directory.

---

### What command shows file permissions?

```bash
ls -l
```

### What command changes permissions recursively?

```bash
chmod -R 755 directory
```

### What command changes ownership recursively?

```bash
sudo chown -R user:group directory
```
