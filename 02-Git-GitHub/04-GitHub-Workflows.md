# GitHub Workflows

## What is GitHub?

GitHub is a cloud-based platform that hosts Git repositories and provides collaboration features such as Pull Requests, Issues, Actions, Code Reviews, and Project Management.

### Why GitHub?

* Store code online
* Collaborate with team members
* Maintain version history
* Automate CI/CD pipelines
* Open-source contribution

---

## Git vs GitHub

| Git                    | GitHub                 |
| ---------------------- | ---------------------- |
| Version Control System | Cloud Hosting Platform |
| Installed Locally      | Runs on Cloud          |
| Tracks Code Changes    | Hosts Git Repositories |
| Works Offline          | Requires Internet      |

### Example

Git = Diary

GitHub = Cloud Storage for Diary

---

## Local to Remote Workflow

A typical developer workflow:

Developer
↓
Working Directory
↓
Staging Area
↓
Local Repository
↓
Remote Repository (GitHub)

### Step 1: Initialize Repository

```bash
git init
```

Creates a new Git repository.

---

### Step 2: Add Files

```bash
git add .
```

Moves files to staging area.

---

### Step 3: Commit Changes

```bash
git commit -m "Initial Commit"
```

Creates a snapshot of code.

---

### Step 4: Connect GitHub Repository

```bash
git remote add origin https://github.com/username/repository.git
```

Verify Remote:

```bash
git remote -v
```

Output:

origin https://github.com/user/repo.git (fetch)

origin https://github.com/user/repo.git (push)

---

### Step 5: Push Code

```bash
git push -u origin main
```

The `-u` flag sets upstream branch.

Future pushes:

```bash
git push
```

---

## Create Remote Repository

### Using GitHub UI

1. Login to GitHub
2. Click New Repository
3. Enter Repository Name
4. Select Public or Private
5. Click Create Repository

GitHub provides commands:

```bash
git remote add origin <repo-url>
git branch -M main
git push -u origin main
```

---

## Clone Repository

Downloads a remote repository to local machine.

```bash
git clone https://github.com/user/project.git
```

Output:

```bash
project/
├── README.md
├── src/
└── package.json
```

Move inside repository:

```bash
cd project
```

---

## Pull Changes

Downloads and merges latest changes.

```bash
git pull origin main
```

Equivalent to:

```bash
git fetch
git merge
```

---

## Fetch Changes

Downloads changes but does not merge them.

```bash
git fetch
```

Useful when you want to inspect changes before merging.

### Difference Between Fetch and Pull

Git Fetch:

Remote → Local

No merge.

Git Pull:

Remote → Local → Merge

Automatic merge.

---

## Branch Workflow

### Why Use Branches?

Suppose a team is developing:

* Login Feature
* Payment Feature
* Dashboard Feature

Instead of working directly on main:

```text
main
│
├── login-feature
├── payment-feature
└── dashboard-feature
```

Every developer works independently.

---

## Pull Request (PR)

A Pull Request is a request to merge code from one branch into another.

Example:

```text
feature-login
      │
      ▼
Pull Request
      │
      ▼
main
```

### Pull Request Workflow

1. Create Feature Branch

```bash
git checkout -b feature-login
```

2. Make Changes

3. Commit Changes

```bash
git commit -m "Added Login Feature"
```

4. Push Branch

```bash
git push origin feature-login
```

5. Create Pull Request on GitHub

6. Team Reviews Code

7. Merge Pull Request

---

## Why Pull Requests Are Important?

* Code Review
* Better Collaboration
* Detect Bugs Early
* Maintain Code Quality
* Team Approval Process

---

## Fork Workflow

Used mostly in Open Source Projects.

### What is Fork?

A fork is a personal copy of another repository.

Example:

Original Repository
↓
Fork
↓
Your GitHub Account

### Fork Workflow

Original Repository
↓
Fork
↓
Clone Fork
↓
Create Branch
↓
Make Changes
↓
Push Changes
↓
Create Pull Request

---

## Clone vs Fork

### Clone

Copies repository to local machine.

```bash
git clone repo-url
```

### Fork

Copies repository to your GitHub account.

Used when you don't have write access.

---

## GitHub Actions

GitHub Actions is GitHub's CI/CD service.

It automates:

* Build
* Test
* Security Checks
* Deployment

### Workflow

Developer Pushes Code
↓
GitHub Action Triggered
↓
Build
↓
Test
↓
Deploy

---

## Simple GitHub Action Example

File:

.github/workflows/node.yml

```yaml
name: Node CI

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: 20

      - run: npm install

      - run: npm test
```

### What Happens?

1. Code pushed to main
2. Runner starts
3. Repository cloned
4. Dependencies installed
5. Tests executed

---

## Common GitHub Features

### Issues

Used for:

* Bug Tracking
* Feature Requests
* Task Management

### Discussions

Community conversations.

### Wiki

Documentation section.

### Projects

Kanban board for project tracking.

### Releases

Versioned software releases.

---

## Best Practices

### Commit Frequently

Bad:

```bash
git commit -m "changes"
```

Good:

```bash
git commit -m "Added User Authentication"
```

---

### Keep Main Stable

Never develop directly on main.

Use feature branches.

---

### Use Pull Requests

Every major change should go through review.

---

### Write Good README

Include:

* Project Description
* Installation Steps
* Usage Guide
* Screenshots

---

### Protect Main Branch

Enable:

* Pull Request Approval
* Status Checks
* Branch Protection Rules

---

## Frequently Used Commands

```bash
git clone <url>

git status

git add .

git commit -m "message"

git branch

git checkout -b feature

git push origin feature

git pull origin main

git fetch

git remote -v

git log --oneline
```

---

# Interview Questions

### What is GitHub?

GitHub is a cloud platform for hosting Git repositories and collaborating on code.

---

### What is Pull Request?

A Pull Request is a request to merge changes from one branch into another branch.

---

### Difference Between Clone and Fork?

Clone copies repository locally.

Fork copies repository into your GitHub account.

---

### Difference Between Fetch and Pull?

Fetch downloads changes.

Pull downloads and merges changes.

---

### What is GitHub Actions?

GitHub Actions is GitHub's CI/CD automation service.

---

### Why Use Pull Requests?

* Code Review
* Collaboration
* Maintain Quality
* Team Approval

---

### What is Upstream Branch?

A remote branch tracked by a local branch.

Example:

```bash
git push -u origin main
```

The `-u` flag sets upstream tracking.
