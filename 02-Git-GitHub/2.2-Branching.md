# Git Branching

## What is a Branch?

A branch in Git is an independent line of development that allows developers to work on features, bug fixes, or experiments without affecting the main codebase.

Think of a branch as a copy of your project where you can make changes safely. Once the work is completed and tested, it can be merged back into the main branch.

By default, Git creates a branch called **main** (older repositories may use **master**).

---

## Why Do We Need Branches?

Without branches, every developer would work directly on the main branch. This can create several problems:

* Unstable code in production
* Frequent bugs
* Difficult collaboration
* Risk of breaking existing features

Branches solve these problems by isolating development work.

### Benefits of Branching

* Develop new features independently
* Fix bugs without affecting production code
* Experiment with new ideas safely
* Multiple developers can work simultaneously
* Easier code review through Pull Requests

---

## Understanding Branches with an Example

Suppose you are building an E-Commerce website.

Current Project:

```text
main
```

Now you want to add:

* Login Feature
* Payment Gateway
* Shopping Cart

Instead of coding everything directly on main:

```text
main
├── feature-login
├── feature-payment
└── feature-cart
```

Each feature gets its own branch.

---

## Check Current Branch

To see all local branches:

```bash
git branch
```

Example Output:

```bash
* main
  feature-login
  feature-payment
```

The `*` symbol indicates the currently active branch.

---

## View Current Branch Only

```bash
git branch --show-current
```

Output:

```bash
main
```

---

## Create a New Branch

Syntax:

```bash
git branch <branch-name>
```

Example:

```bash
git branch feature-login
```

This creates a branch but does not switch to it.

Check branches:

```bash
git branch
```

Output:

```bash
* main
  feature-login
```

---

## Switch to Another Branch

Older Method:

```bash
git checkout feature-login
```

Modern Method:

```bash
git switch feature-login
```

Output:

```bash
Switched to branch 'feature-login'
```

Now any commits will be made on feature-login branch.

---

## Create and Switch in One Command

Older Method:

```bash
git checkout -b feature-login
```

Modern Method:

```bash
git switch -c feature-login
```

This command:

1. Creates the branch
2. Switches to it immediately

---

## Verify Branch Switching

```bash
git branch
```

Output:

```bash
main
* feature-login
```

The star indicates the active branch.

---

## Working on a Feature Branch

Example:

```bash
git switch -c feature-login
```

Create a file:

```bash
touch login.js
```

Add changes:

```bash
git add .
```

Commit changes:

```bash
git commit -m "Added login feature"
```

These changes exist only in the feature-login branch.

---

## Rename a Branch

Rename current branch:

```bash
git branch -m new-name
```

Example:

```bash
git branch -m login-feature
```

Rename another branch:

```bash
git branch -m old-name new-name
```

Example:

```bash
git branch -m feature-login login-feature
```

---

## Delete a Branch

Delete a merged branch:

```bash
git branch -d feature-login
```

Output:

```bash
Deleted branch feature-login
```

Git only allows deletion if the branch has already been merged.

---

## Force Delete a Branch

```bash
git branch -D feature-login
```

Use carefully.

This deletes the branch even if work is not merged.

---

## View All Local Branches

```bash
git branch
```

Example:

```bash
main
feature-login
feature-payment
```

---

## View Remote Branches

```bash
git branch -r
```

Example:

```bash
origin/main
origin/develop
```

---

## View Local and Remote Branches

```bash
git branch -a
```

Example:

```bash
* main
  feature-login
  remotes/origin/main
  remotes/origin/develop
```

---

## Branch Workflow in Real Projects

```text
main
│
├── feature-login
│
├── feature-payment
│
└── bug-fix
```

### Step 1

Create a feature branch:

```bash
git switch -c feature-login
```

### Step 2

Develop feature.

### Step 3

Commit changes.

```bash
git add .
git commit -m "Added login page"
```

### Step 4

Push branch.

```bash
git push origin feature-login
```

### Step 5

Create Pull Request.

### Step 6

Review code.

### Step 7

Merge into main.

---

## Real Life Analogy

Imagine a highway.

```text
Main Highway = main branch
Service Roads = feature branches
```

Traffic on the service road does not affect the highway.

After construction is completed, the service road connects back to the highway.

Similarly:

```text
feature-login
     ↓
Merge
     ↓
main
```

---

## Best Practices

### 1. Never Work Directly on Main

Avoid:

```bash
git commit -m "Random changes"
```

on the main branch.

Use feature branches instead.

---

### 2. Use Meaningful Branch Names

Good:

```bash
feature-login
feature-payment
bug-fix-navbar
```

Bad:

```bash
test1
abc
newbranch
```

---

### 3. Keep Branches Small

One branch = One feature.

Avoid combining multiple features in a single branch.

---

### 4. Delete Merged Branches

After merging:

```bash
git branch -d feature-login
```

This keeps the repository clean.

---

## Common Branch Commands Cheat Sheet

```bash
git branch

git branch feature-login

git switch feature-login

git checkout feature-login

git switch -c feature-login

git checkout -b feature-login

git branch -m old-name new-name

git branch -d feature-login

git branch -D feature-login

git branch -r

git branch -a
```

---

# Interview Questions

### 1. What is a Branch in Git?

A branch is an independent line of development that allows developers to work on features or bug fixes without affecting the main codebase.

---

### 2. Why Do We Use Branches?

* Isolate development
* Enable collaboration
* Prevent production issues
* Support parallel development

---

### 3. Difference Between Checkout and Switch?

| checkout          | switch                |
| ----------------- | --------------------- |
| Older command     | New command           |
| Multiple purposes | Branch switching only |
| More complex      | Easier to understand  |

Examples:

```bash
git checkout feature-login
```

```bash
git switch feature-login
```

---

### 4. Difference Between Local and Remote Branch?

| Local Branch           | Remote Branch                 |
| ---------------------- | ----------------------------- |
| Exists on your system  | Exists on GitHub              |
| Modified locally       | Shared with team              |
| Example: feature-login | Example: origin/feature-login |

---

### 5. How Do You Delete a Branch?

Safe delete:

```bash
git branch -d feature-login
```

Force delete:

```bash
git branch -D feature-login
```

---

### 6. How Do You View All Branches?

Local:

```bash
git branch
```

Remote:

```bash
git branch -r
```

Both:

```bash
git branch -a
```
