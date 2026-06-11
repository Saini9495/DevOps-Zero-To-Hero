# Linux Commands

## Introduction

Linux commands are instructions entered in the terminal to interact with the operating system. As a DevOps Engineer, most daily activities are performed through the command line, such as managing files, monitoring servers, troubleshooting issues, and deploying applications.

Understanding Linux commands is essential for:

* System Administration
* DevOps Engineering
* Cloud Computing
* Container Management
* Automation
* Server Troubleshooting

---

# Navigation Commands

## pwd (Print Working Directory)

Displays the current directory path.

### Syntax

```bash
pwd
```

### Example

```bash
pwd
```

### Output

```bash
/home/ubuntu
```

### Use Case

Useful when you want to know your current location in the filesystem.

---

## ls (List Files and Directories)

Displays files and directories in the current location.

### Syntax

```bash
ls
```

### Example

```bash
ls
```

### Output

```bash
Documents Downloads Pictures
```

### Common Options

List detailed information:

```bash
ls -l
```

Show hidden files:

```bash
ls -a
```

Detailed view including hidden files:

```bash
ls -la
```

Human-readable file sizes:

```bash
ls -lh
```

### DevOps Use Case

Checking configuration files and log directories.

---

## cd (Change Directory)

Used to move between directories.

### Syntax

```bash
cd <directory_name>
```

### Examples

Move into a directory:

```bash
cd Documents
```

Move one directory back:

```bash
cd ..
```

Go to home directory:

```bash
cd ~
```

Go to root directory:

```bash
cd /
```

### DevOps Use Case

Navigating application, log, and configuration directories.

---

# File and Directory Management

## mkdir (Make Directory)

Creates a new directory.

### Syntax

```bash
mkdir directory_name
```

### Example

```bash
mkdir devops
```

Create multiple directories:

```bash
mkdir docker kubernetes terraform
```

### DevOps Use Case

Organizing project files and infrastructure code.

---

## touch

Creates an empty file.

### Syntax

```bash
touch filename
```

### Example

```bash
touch notes.txt
```

Create multiple files:

```bash
touch app.py Dockerfile README.md
```

### DevOps Use Case

Creating configuration files and scripts.

---

## cp (Copy Files and Directories)

Copies files or directories.

### Syntax

```bash
cp source destination
```

### Example

```bash
cp notes.txt backup.txt
```

Copy directories:

```bash
cp -r project backup-project
```

### DevOps Use Case

Backing up configuration files before making changes.

---

## mv (Move or Rename)

Moves or renames files and directories.

### Rename File

```bash
mv old.txt new.txt
```

### Move File

```bash
mv file.txt /home/ubuntu/Documents
```

### DevOps Use Case

Moving deployment scripts and configuration files.

---

## rm (Remove)

Deletes files and directories.

### Delete File

```bash
rm file.txt
```

### Delete Directory

```bash
rm -r folder
```

### Force Delete

```bash
rm -rf folder
```

⚠️ Warning:

Never use:

```bash
rm -rf /
```

This can destroy the entire system.

### DevOps Use Case

Removing temporary files and old backups.

---

# Viewing File Content

## cat

Displays file content.

### Syntax

```bash
cat filename
```

### Example

```bash
cat notes.txt
```

### Multiple Files

```bash
cat file1.txt file2.txt
```

### DevOps Use Case

Viewing configuration files.

Example:

```bash
cat /etc/hosts
```

---

## head

Displays the first 10 lines of a file.

### Syntax

```bash
head filename
```

### Example

```bash
head app.log
```

Display first 20 lines:

```bash
head -20 app.log
```

### DevOps Use Case

Quickly checking the beginning of log files.

---

## tail

Displays the last 10 lines of a file.

### Example

```bash
tail app.log
```

Display live logs:

```bash
tail -f app.log
```

### DevOps Use Case

Monitoring application logs in real time.

---

# Search Commands

## grep

Searches text patterns inside files.

### Syntax

```bash
grep keyword filename
```

### Example

```bash
grep error app.log
```

Case-insensitive search:

```bash
grep -i error app.log
```

Count matching lines:

```bash
grep -c error app.log
```

### DevOps Use Case

Finding errors in log files.

Example:

```bash
grep ERROR application.log
```

---

## find

Searches files and directories.

### Syntax

```bash
find path condition
```

### Example

```bash
find /home -name notes.txt
```

Find all log files:

```bash
find /var/log -name "*.log"
```

### DevOps Use Case

Finding configuration files and logs.

---

# Permissions and Ownership

## chmod

Changes file permissions.

### Syntax

```bash
chmod permissions filename
```

### Example

```bash
chmod 755 script.sh
```

### Meaning of 755

* Owner = Read, Write, Execute
* Group = Read, Execute
* Others = Read, Execute

### DevOps Use Case

Making deployment scripts executable.

```bash
chmod +x deploy.sh
```

---

## chown

Changes file ownership.

### Syntax

```bash
chown user:group filename
```

### Example

```bash
sudo chown ubuntu:ubuntu file.txt
```

### DevOps Use Case

Changing ownership of application files.

---

# System Monitoring Commands

## df

Displays disk space usage.

### Syntax

```bash
df -h
```

### Example Output

```bash
Filesystem Size Used Avail Use%
```

### DevOps Use Case

Checking server disk utilization.

---

## free

Displays memory usage.

### Syntax

```bash
free -h
```

### Example Output

```bash
Mem: 2Gi 1Gi 1Gi
```

### DevOps Use Case

Checking RAM consumption.

---

## top

Displays running processes in real time.

### Syntax

```bash
top
```

### Information Displayed

* CPU Usage
* Memory Usage
* Running Processes
* System Load

### DevOps Use Case

Troubleshooting high CPU or memory usage.

---

## htop

Improved version of top.

### Install

```bash
sudo apt install htop
```

### Run

```bash
htop
```

### Benefits

* Better UI
* Easier navigation
* Process management

---

# Networking Commands

## ping

Checks network connectivity.

```bash
ping google.com
```

---

## curl

Transfers data from URLs.

```bash
curl https://google.com
```

Check API response:

```bash
curl http://localhost:8080
```

---

## wget

Downloads files from the internet.

```bash
wget https://example.com/file.zip
```

---

# Process Management

## ps

Displays running processes.

```bash
ps aux
```

---

## kill

Terminates a process.

```bash
kill PID
```

Force kill:

```bash
kill -9 PID
```

---

# Service Management

## systemctl

Manages Linux services.

Check status:

```bash
systemctl status nginx
```

Start service:

```bash
sudo systemctl start nginx
```

Stop service:

```bash
sudo systemctl stop nginx
```

Restart service:

```bash
sudo systemctl restart nginx
```

Enable at boot:

```bash
sudo systemctl enable nginx
```

### DevOps Use Case

Managing web servers and application services.

---

# Log Management

## journalctl

View system logs.

View all logs:

```bash
journalctl
```

View service logs:

```bash
journalctl -u nginx
```

Follow logs:

```bash
journalctl -u nginx -f
```

### DevOps Use Case

Troubleshooting service failures.

---

# DevOps-Specific Commands

## Docker

List running containers:

```bash
docker ps
```

List images:

```bash
docker images
```

---

## Kubernetes

Check pods:

```bash
kubectl get pods
```

Check services:

```bash
kubectl get svc
```

Check deployments:

```bash
kubectl get deploy
```

---

# Common Command Combination

Find errors in logs:

```bash
cat app.log | grep ERROR
```

Count files:

```bash
ls | wc -l
```

Find and delete log files:

```bash
find . -name "*.log" -delete
```

---

# Summary

Linux commands are the primary way DevOps Engineers interact with servers. Mastering file management, permissions, monitoring, networking, process management, and service troubleshooting commands is essential for working with cloud infrastructure and production systems.

---

# Interview Questions

### What is the difference between cp and mv?

cp creates a copy of a file while mv moves or renames the file.

### What is the difference between grep and find?

grep searches inside files for text patterns, whereas find searches for files and directories.

### What is the purpose of chmod?

chmod changes file and directory permissions.

### What is the purpose of chown?

chown changes file ownership.

### What is the difference between top and htop?

Both monitor processes, but htop provides a more interactive and user-friendly interface.

### Which command is used to view live logs?

```bash
tail -f filename
```

or

```bash
journalctl -f
```

### Which command is used to check disk usage?

```bash
df -h
```

### Which command is used to check memory usage?

```bash
free -h
```
