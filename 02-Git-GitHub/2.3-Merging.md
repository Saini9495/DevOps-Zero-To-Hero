# Git Merging

## What is Git Merge?

Git Merge is a command used to combine changes from one branch into another branch.

When developers work on separate branches, their code changes remain isolated. Once the feature is complete, those changes need to be integrated into the main branch. This process is called **merging**.

### Definition

Git Merge combines the history of two branches and creates a unified version of the project.

---

# Why Do We Need Merge?

Imagine a team working on an e-commerce application.

Developer A is creating a Login Feature.

Developer B is creating a Payment Feature.

Developer C is fixing Bugs.

All developers work on separate branches.

```text
main
│
├── login-feature
├── payment-feature
└── bug-fix
```

Once development is completed, all branches need to be combined into the main branch.

This is done using Git Merge.

---

# How Merge Works

Example:

```text
main
  A
```

Create Feature Branch

```bash
git checkout -b feature-login
```

Add Commits

```text
main
  A

feature-login
  A → B → C
```

Switch to Main

```bash
git checkout main
```

Merge Feature Branch

```bash
git merge feature-login
```

Result

```text
main
A → B → C
```

Now the changes from feature-login are available in main.

---

# Merge Workflow

### Step 1: Create Branch

```bash
git checkout -b feature-login
```

### Step 2: Make Changes

```bash
git add .
git commit -m "Added login page"
```

### Step 3: Move to Main

```bash
git checkout main
```

### Step 4: Merge Branch

```bash
git merge feature-login
```

### Step 5: Delete Branch

```bash
git branch -d feature-login
```

---

# Types of Merge

Git supports multiple merge strategies.

## 1. Fast Forward Merge

This occurs when the target branch has not changed after creating the feature branch.

### Example

```text
A → B → C (feature)

A (main)
```

Merge

```bash
git merge feature
```

Result

```text
A → B → C (main)
```

Git simply moves the main pointer forward.

No merge commit is created.

### Advantages

* Clean history
* Simple structure
* Faster merge

### Disadvantages

* No record of branch existence

---

# 2. Three-Way Merge

Occurs when both branches have new commits.

### Example

```text
      D
     /
A → B
     \
      C
```

Main branch:

```text
A → B → D
```

Feature branch:

```text
A → B → C
```

Merge

```bash
git merge feature
```

Result

```text
      D
     / \
A → B   M
     \ /
      C
```

M = Merge Commit

Git creates a special commit that joins both histories.

### Advantages

* Preserves history
* Shows when merge happened
* Better for teams

### Disadvantages

* Commit graph becomes larger

---

# Merge Commit

A Merge Commit is a special commit created when Git combines two branch histories.

View merge commits:

```bash
git log --oneline
```

Example

```text
8f4d2c Merge branch 'feature-login'
```

---

# Merge Conflict

A Merge Conflict happens when Git cannot automatically decide which changes should be kept.

Usually occurs when:

* Same file modified
* Same line modified
* Same configuration edited

---

# Example of Merge Conflict

main branch:

```javascript
console.log("Hello World");
```

feature branch:

```javascript
console.log("Hello Git");
```

During merge:

```bash
git merge feature
```

Git displays:

```text
CONFLICT (content): Merge conflict in app.js
Automatic merge failed.
```

---

# Conflict Markers

Git inserts markers inside the file.

```javascript
<<<<<<< HEAD
console.log("Hello World");
=======
console.log("Hello Git");
>>>>>>> feature
```

Meaning:

HEAD = Current Branch

feature = Incoming Branch

---

# Resolving Merge Conflict

### Step 1

Open conflicted file

### Step 2

Choose correct content

```javascript
console.log("Hello World");
console.log("Hello Git");
```

### Step 3

Save File

### Step 4

Add Changes

```bash
git add .
```

### Step 5

Commit Merge

```bash
git commit -m "Resolved merge conflict"
```

Conflict resolved successfully.

---

# Checking Merge Status

```bash
git status
```

Example:

```text
You have unmerged paths.
```

After resolving:

```text
nothing to commit, working tree clean
```

---

# Abort Merge

If merge goes wrong:

```bash
git merge --abort
```

Git returns repository to previous state.

---

# Viewing Merge History

Simple History

```bash
git log
```

Compact History

```bash
git log --oneline
```

Graph View

```bash
git log --graph --oneline --all
```

Example

```text
* Merge branch 'feature-login'
|\
| * Added login page
* | Fixed bug
|/
```

---

# Best Practices

### Create Feature Branches

Never work directly on main.

### Pull Latest Code

Before merging:

```bash
git pull origin main
```

### Review Changes

```bash
git diff
```

### Resolve Conflicts Carefully

Never blindly delete code.

### Delete Merged Branches

```bash
git branch -d feature-login
```

Keeps repository clean.

---

# Real-Life Analogy

Imagine two writers editing the same book.

Writer A edits Chapter 1.

Writer B edits Chapter 2.

Combining both chapters is called a Merge.

If both writers edit the same paragraph differently, an editor must decide which version to keep.

That editor is you resolving a Merge Conflict.

---

# Merge vs Rebase

| Feature              | Merge | Rebase   |
| -------------------- | ----- | -------- |
| Preserves History    | Yes   | No       |
| Creates Merge Commit | Yes   | No       |
| Safe for Teams       | Yes   | Moderate |
| Cleaner History      | No    | Yes      |
| Easier for Beginners | Yes   | No       |

---

# Frequently Used Commands

```bash
git merge feature-login

git merge --abort

git log --graph

git log --oneline

git status

git diff

git branch -d feature-login
```

---

# Interview Questions

## What is Git Merge?

Git Merge combines changes from one branch into another branch.

---

## What is a Fast Forward Merge?

A merge where Git simply moves the branch pointer forward without creating a merge commit.

---

## What is a Three-Way Merge?

A merge that creates a new merge commit because both branches contain unique commits.

---

## What is a Merge Conflict?

A situation where Git cannot automatically determine which changes should be preserved.

---

## How do you resolve a Merge Conflict?

1. Open conflicted file
2. Edit manually
3. Remove conflict markers
4. Save file
5. git add .
6. git commit

---

## Difference Between Merge and Rebase?

Merge preserves branch history and creates merge commits.

Rebase rewrites history and creates a cleaner linear commit structure.

---

## How to Abort a Merge?

```bash
git merge --abort
```

---

## How to View Merge History?

```bash
git log --graph --oneline --all
```
