# Docker Volumes

## What are Docker Volumes?

Docker Volumes are a mechanism used to persist data generated and used by Docker containers.

By default, when a container is deleted, all data stored inside the container is also removed. To prevent data loss, Docker provides Volumes.

Volumes store data outside the container's writable layer, allowing data to survive container deletion, recreation, and updates.

---

## Why Do We Need Volumes?

Imagine you are running a MySQL database inside a container.

```bash
docker run -d --name mysql-container mysql
```

All database files are stored inside the container.

Now suppose the container crashes or is removed:

```bash
docker rm mysql-container
```

The database data will also be deleted.

To avoid this problem, Docker Volumes are used.

Benefits:

* Data persistence
* Easy backup and restore
* Data sharing between containers
* Better performance
* Container lifecycle independent storage

---

## How Docker Stores Data

Without Volume:

```text
Container
│
├── Application Files
├── Logs
└── Database Data
```

Delete Container → Everything Lost

With Volume:

```text
Container
│
├── Application Files
│
Volume
│
├── Logs
└── Database Data
```

Delete Container → Data Remains Safe

---

## Types of Docker Volumes

Docker provides three ways to persist data.

### 1. Anonymous Volumes

Created automatically by Docker.

Example:

```bash
docker run -d -v /app/data nginx
```

Docker creates a random volume name.

Characteristics:

* Docker manages the volume
* Hard to identify
* Mostly used for temporary storage

Example:

```bash
docker volume ls
```

Output:

```text
DRIVER    VOLUME NAME

local     7df82c4e52f1e...
```

---

### 2. Named Volumes

Volumes created with a specific name.

Example:

```bash
docker volume create myvolume
```

Use it:

```bash
docker run -d \
-v myvolume:/app/data \
nginx
```

Advantages:

* Easy to manage
* Easy backup
* Easy reuse
* Recommended for databases

View volumes:

```bash
docker volume ls
```

Output:

```text
local myvolume
```

---

### 3. Bind Mounts

A local directory from the host machine is directly mapped into the container.

Example Linux:

```bash
docker run -d \
-v /home/ubuntu/data:/app/data \
nginx
```

Example Windows:

```bash
docker run -d ^
-v C:\Users\Rishabh\data:/app/data ^
nginx
```

Characteristics:

* Direct access to host files
* Best for development
* Changes reflect instantly

Example:

```text
Windows Folder
│
└── index.html

        ↓

Docker Container
│
└── /usr/share/nginx/html/index.html
```

---

## Creating a Volume

Create a volume:

```bash
docker volume create myvolume
```

Output:

```text
myvolume
```

---

## Listing Volumes

```bash
docker volume ls
```

Example Output:

```text
DRIVER    VOLUME NAME

local     myvolume
```

---

## Inspecting a Volume

```bash
docker volume inspect myvolume
```

Example Output:

```json
[
 {
  "Name": "myvolume",
  "Driver": "local",
  "Mountpoint": "/var/lib/docker/volumes/myvolume/_data"
 }
]
```

The Mountpoint shows the actual location where Docker stores volume data.

---

## Using a Volume with a Container

```bash
docker run -d \
--name nginx-container \
-v myvolume:/usr/share/nginx/html \
nginx
```

Explanation:

```text
myvolume                     -> Volume Name

/usr/share/nginx/html        -> Container Path
```

Data written inside the container path is automatically stored in the volume.

---

## Sharing Data Between Containers

Multiple containers can use the same volume.

```bash
docker run -d \
--name container1 \
-v myvolume:/data nginx
```

```bash
docker run -d \
--name container2 \
-v myvolume:/data ubuntu
```

Both containers can access the same files.

---

## Removing a Volume

Remove a specific volume:

```bash
docker volume rm myvolume
```

Remove unused volumes:

```bash
docker volume prune
```

Be careful:

```text
Deleted Volume = Deleted Data
```

---

## Practical Example

### Step 1: Create Volume

```bash
docker volume create nginx-data
```

### Step 2: Run Container

```bash
docker run -d \
--name my-nginx \
-v nginx-data:/usr/share/nginx/html \
nginx
```

### Step 3: Enter Container

```bash
docker exec -it my-nginx bash
```

### Step 4: Create File

```bash
echo "Hello Docker Volume" > /usr/share/nginx/html/index.html
```

### Step 5: Delete Container

```bash
docker rm -f my-nginx
```

### Step 6: Recreate Container

```bash
docker run -d \
--name my-nginx \
-v nginx-data:/usr/share/nginx/html \
nginx
```

Result:

```text
index.html still exists
```

Because the data is stored in the volume.

---

## Bind Mount vs Named Volume

| Feature     | Bind Mount      | Named Volume |
| ----------- | --------------- | ------------ |
| Managed By  | Host OS         | Docker       |
| Performance | Good            | Better       |
| Portability | Less            | More         |
| Backup      | Manual          | Easy         |
| Development | Excellent       | Good         |
| Production  | Not Recommended | Recommended  |

---

## Real Life Analogy

Think of:

```text
Container = Mobile Phone

Volume = Memory Card
```

If the phone breaks:

```text
Phone Deleted
```

The memory card still contains all photos and files.

Similarly:

```text
Container Deleted
```

Volume still contains all data.

---

## Common Docker Volume Commands

Create Volume

```bash
docker volume create myvolume
```

List Volumes

```bash
docker volume ls
```

Inspect Volume

```bash
docker volume inspect myvolume
```

Remove Volume

```bash
docker volume rm myvolume
```

Remove Unused Volumes

```bash
docker volume prune
```

---

## Interview Questions

### What is a Docker Volume?

A Docker Volume is a persistent storage mechanism that stores data outside the container lifecycle.

---

### Why are Volumes needed?

To prevent data loss when containers are removed or recreated.

---

### What are the types of Docker Volumes?

* Anonymous Volume
* Named Volume
* Bind Mount

---

### Difference between Bind Mount and Named Volume?

Bind Mount uses a host machine directory.

Named Volume is managed by Docker.

---

### Where does Docker store Volume data?

Linux:

```text
/var/lib/docker/volumes/
```

---

### Can multiple containers use the same Volume?

Yes, multiple containers can read and write data using the same volume.

---

## Summary

* Containers are temporary.
* Volumes provide persistent storage.
* Named Volumes are preferred for production.
* Bind Mounts are useful during development.
* Data inside a volume survives container deletion.
