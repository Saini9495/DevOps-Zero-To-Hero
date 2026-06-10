# Git Basics

## What is Git?

Git is a **Distributed Version Control System (DVCS)** that helps developers track changes in source code, collaborate with teams, and maintain different versions of a project.

Git was created by Linus Torvalds in 2005 for Linux kernel development.

### Key Features

* Tracks file changes over time
* Maintains version history
* Supports collaboration among multiple developers
* Allows rollback to previous versions
* Fast and lightweight
* Distributed architecture

---

## Why Git?

Before Git, developers often shared project files manually, which caused problems such as:

* Overwriting each other's code
* Losing previous versions
* Difficulty tracking changes
* No backup mechanism

Git solves these problems.

### Benefits of Git

### 1. Version Control

Every change is recorded.

Example:

Version 1 → Login Page

Version 2 → Added Registration Page

Version 3 → Added Password Reset

Git allows you to return to any previous version.

---

### 2. Collaboration

Multiple developers can work on the same project simultaneously.

Example:

Developer A → Login Feature

Developer B → Payment Feature

Developer C → Dashboard

Git combines all changes efficiently.

---

### 3. Backup

Repositories can be pushed to GitHub, providing cloud backup.

Even if the local machine crashes, code remains safe.

---

### 4. Branching

Developers can create isolated environments for testing new features without affecting production code.

---

### 5. Easy Rollback

If a deployment introduces bugs, Git can restore a previous stable version.

---

## Git Architecture

Git works using four major areas.

```text
Working Directory
        ↓
Staging Area
        ↓
Local Repository
        ↓
Remote Repository (GitHub)
```

### 1. Working Directory

The directory where you create and modify files.

Example:

```bash
index.html
app.js
style.css
```

These files exist only on your computer.

---

### 2. Staging Area

Temporary area where changes are prepared before committing.

```bash
git add app.js
```

Now Git knows which changes should be included in the next commit.

Think of it as a shopping cart before checkout.

---

### 3. Local Repository

Stores commits on your machine.

```bash
git commit -m "Added Login Feature"
```

Commit creates a snapshot of the project.

---

### 4. Remote Repository

Hosted repository on platforms such as GitHub.

```bash
git push origin main
```

This uploads local commits to GitHub.

---

## Git Workflow

### Step 1: Create or Modify Code

```bash
echo "Hello Git" > app.js
```

---

### Step 2: Check Status

```bash
git status
```

Shows modified, staged, and untracked files.

---

### Step 3: Add Files to Staging Area

Single file:

```bash
git add app.js
```

All files:

```bash
git add .
```

---

### Step 4: Commit Changes

```bash
git commit -m "Added app.js"
```

Creates a permanent snapshot.

---

### Step 5: Push to GitHub

```bash
git push origin main
```

Uploads code to remote repository.

---

## Installation

### Ubuntu

```bash
sudo apt update
sudo apt install git -y
```

Verify installation:

```bash
git --version
```

---

### Windows

Download Git from:

https://git-scm.com

Verify installation:

```bash
git --version
```

---

## Configure Git

Git needs identity information for commits.

### Configure Username

```bash
git config --global user.name "Rishabh Saini"
```

### Configure Email

```bash
git config --global user.email "yourmail@gmail.com"
```

### Verify Configuration

```bash
git config --list
```

### Check Specific Values

```bash
git config user.name

git config user.email
```

---

## Create Repository

Initialize Git in current folder.

```bash
git init
```

Output:

```bash
Initialized empty Git repository
```

Git creates a hidden `.git` directory.

This folder contains all Git metadata.

---

## Repository Status

```bash
git status
```

Possible states:

### Untracked

Git doesn't know about the file.

### Modified

File changed after commit.

### Staged

Ready for commit.

### Committed

Stored in repository history.

---

## Add Files

### Add Single File

```bash
git add index.js
```

### Add Multiple Files

```bash
git add file1 file2
```

### Add All Files

```bash
git add .
```

---

## Commit Changes

### Basic Commit

```bash
git commit -m "Initial Commit"
```

### Commit Staged Files

```bash
git commit -m "Added Authentication"
```

Good commit messages:

```bash
Added login page

Fixed payment bug

Updated README
```

Bad commit messages:

```bash
done

updated

final
```

---

## Commit History

### Full History

```bash
git log
```

Displays:

* Commit ID
* Author
* Date
* Message

---

### One-Line History

```bash
git log --oneline
```

Example:

```bash
c7d82f2 Added Login Page

8ab72ef Created Project
```

---

## Difference Between Files

### View Changes

```bash
git diff
```

Shows line-by-line modifications.

Example:

```diff
-Hello
+Hello World
```

---

## Remove File

```bash
git rm file.txt
```

Removes file and stages deletion.

Commit afterward:

```bash
git commit -m "Removed file"
```

---

## Rename File

```bash
git mv old.txt new.txt
```

Commit:

```bash
git commit -m "Renamed file"
```

---

## Understanding HEAD

HEAD is a pointer to the current commit.

Example:

```text
Commit A
Commit B
Commit C ← HEAD
```

HEAD indicates where you currently are in the repository.

Check current HEAD:

```bash
git log --oneline
```

---

## Real-Life Analogy

Imagine Git as a CCTV camera.

* Files = Activity
* Commit = Recorded Footage
* Branch = Alternate Route
* GitHub = Cloud Backup
* Rollback = Rewind Footage

Whenever you create a commit, Git records a snapshot of your project.

---

# Interview Questions

### What is Git?

Git is a distributed version control system used to track source code changes and collaborate with developers.

---

### Difference Between Git and GitHub?

Git:

* Tool installed locally
* Tracks changes

GitHub:

* Cloud platform
* Hosts Git repositories

---

### What is a Commit?

A commit is a snapshot of project files at a specific point in time.

---

### What is Staging Area?

An intermediate area where changes are prepared before committing.

---

### What is HEAD?

HEAD is a pointer that references the currently checked-out commit.

---

### Difference Between git add and git commit?

git add:
Moves changes to staging area.

git commit:
Stores staged changes permanently in repository history.

---

### What Does git init Do?

Creates a new Git repository by generating a hidden `.git` directory.

---

### How Do You Check Repository Status?

```bash
git status
```

---

### How Do You See Commit History?

```bash
git log
```

or

```bash
git log --oneline
```
