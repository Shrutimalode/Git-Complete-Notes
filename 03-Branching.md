# Git Branching

Branching is one of Git's most powerful features. It allows developers to work on new features, bug fixes, or experiments without affecting the main codebase.

---

# What is Branching?

Branching means creating a separate line of development from the main branch so that you can work independently without disturbing the original code.

A **branch** is simply a lightweight, movable pointer to a specific commit. Creating a branch is almost instantaneous because Git doesn't copy your entire project—it only creates another pointer to an existing commit.

---

# Why do we use Branches?

Without branches, every developer would work directly on the main branch, making it easy to introduce bugs into production code.

Branches allow developers to:

- Develop new features independently.
- Fix bugs without affecting stable code.
- Experiment safely.
- Work in parallel with other developers.
- Keep the main branch clean and production-ready.

---

# Understanding HEAD

**HEAD** is Git's pointer to your current working location.

Normally:

```
HEAD
  ↓
main
  ↓
Latest Commit
```

When you switch branches, Git simply moves the HEAD pointer.

Example:

```
HEAD
  ↓
feature-login
  ↓
Latest Commit
```

If HEAD points directly to a commit instead of a branch, Git enters a **Detached HEAD** state.

---

# Types of Branches

## 1. Main (Master) Branch

The default branch created after the first commit.

It usually contains:

- Stable code
- Tested code
- Production-ready code

---

## 2. Feature Branch

A branch created to develop a new feature.

Example:

```
main
   │
   └── feature-login
```

Benefits:

- Keeps the main branch safe.
- Developers can work independently.
- Multiple features can be developed simultaneously.

---

## 3. Release Branch

Created when the project is almost ready for release.

Used for:

- Final testing
- Bug fixes
- Documentation
- Version updates

Example:

```
main
   │
   └── release-v2.0
```

---

## 4. Hotfix Branch

Created directly from the main branch to fix urgent production issues.

Example:

```
main
   │
   └── hotfix-login-bug
```

After fixing the issue, it is merged back into the main branch immediately.

---

# Git Flow

These branch types closely resemble a popular workflow called **Git Flow**.

Git Flow introduces another branch called **develop** between **main** and **feature** branches.

Typical structure:

```
main
  │
develop
 ├── feature-login
 ├── feature-payment
 ├── feature-profile
```

Git Flow is commonly used in large software projects but is optional.

---

# Branch Commands

## List Local Branches

```bash
git branch
```

or

```bash
git branch --list
```

---

## List Remote Branches

```bash
git branch -r
```

---

## List All Branches

```bash
git branch -a
```

---

## Show Branches with Latest Commit

```bash
git branch -v
```

---

## Create a New Branch

```bash
git branch branch-name
```

Example:

```bash
git branch feature-login
```

---

## Switch to a Branch

Using the newer command:

```bash
git switch branch-name
```

Using the older command:

```bash
git checkout branch-name
```

Example:

```bash
git switch feature-login
```

---

## Create and Switch to a Branch

Older method:

```bash
git checkout -b branch-name
```

Newer method:

```bash
git switch -c branch-name
```

Example:

```bash
git switch -c feature-login
```

---

## Push a Branch

```bash
git push origin branch-name
```

Example:

```bash
git push origin feature-login
```

---

## Pull a Branch

```bash
git pull origin branch-name
```

---

## Merge a Branch

Run this command while on the branch you want to merge into (usually **main**).

```bash
git merge branch-name
```

Example:

```bash
git merge feature-login
```

---

## Delete a Local Branch

Safe delete:

```bash
git branch -d branch-name
```

Force delete:

```bash
git branch -D branch-name
```

---

## Delete a Remote Branch

```bash
git push origin --delete branch-name
```

---

## View Branch History

```bash
git log --oneline --graph --all
```

This command visually displays all branches and their commit history.

---

# Hands-on Practice

## Step 1

Initialize a repository.

```bash
git init
```

---

## Step 2

Create three files.

```
a1.txt
a2.txt
a3.txt
```

---

## Step 3

Commit each file separately on the main branch.

Example:

```bash
git add a1.txt
git commit -m "Add a1"

git add a2.txt
git commit -m "Add a2"

git add a3.txt
git commit -m "Add a3"
```

---

## Step 4

Create a feature branch.

```bash
git switch -c feature
```

---

## Step 5

Create two files.

```
x1.txt
x2.txt
```

Commit them separately.

---

## Step 6

Check commit history.

```bash
git log --oneline
```

Output:

```
Add x2
Add x1
Add a3
Add a2
Add a1
```

Notice that the feature branch contains all commits from the main branch plus the new commits.

---

## Step 7

Switch back to the main branch.

```bash
git switch main
```

Check the log again.

```bash
git log --oneline
```

Output:

```
Add a3
Add a2
Add a1
```

The commits for **x1** and **x2** are not visible because they exist only on the feature branch.

---

## Step 8

Merge the feature branch.

```bash
git merge feature
```

Now check the log again.

```bash
git log --oneline
```

All commits will now appear on the main branch.

---

# What This Demonstrates

- A new branch starts with the complete history of the branch from which it was created.
- Changes made on one branch remain isolated until merged.
- The main branch remains unaffected while work continues on another branch.
- Branches allow multiple developers to work simultaneously without conflicts.
- Git requires at least one commit before creating a new branch.
- The names **main** and **master** are conventions and can be changed.

---

# Summary

- Branches provide isolated lines of development.
- They allow multiple developers to work independently.
- **HEAD** always points to the currently checked-out branch.
- Feature, Release, Hotfix, and Main are the most common branch types.
- Branches become part of another branch only after a **merge**.
- Git branches are lightweight because they are pointers to commits, not copies of the project.

## Next Chapter

➡️ **Next:** [04 - Git Merging](04-Merging.md)
