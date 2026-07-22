 # 02 - Git Workflow

> In the previous chapter, we learned what Git is, why it is used, and how it solves the problems of version control.
>
> Now it's time to understand the **Git Workflow**—the sequence of steps you'll follow in almost every Git project, from creating a repository to uploading your code to GitHub.

---

# What You'll Learn

By the end of this chapter, you will be able to:

- Initialize a Git repository
- Configure Git with your username and email
- Add files to the staging area
- Check the status of your project
- Commit changes to the local repository
- View commit history
- Connect your project to GitHub
- Push and pull changes
- Understand the complete Git workflow
- Solve the common **non-fast-forward** push error

---

# What is the Git Workflow?

A Git workflow is the sequence of steps used to manage changes in a project.

Instead of directly saving files to GitHub, Git follows a structured process that allows you to review and organize your work before sharing it.

Every change passes through different stages before reaching the remote repository.

---

# Git Workflow Diagram

```text
             Create / Modify Files
                      │
                      ▼
             Working Directory
                      │
                git add
                      │
                      ▼
              Staging Area
                      │
              git commit
                      │
                      ▼
            Local Repository
                      │
              git push
                      │
                      ▼
      Remote Repository (GitHub)
```

This workflow ensures that your work is properly tracked and organized before it is shared with others.

---

# Step 1 – Initialize a Repository

Before Git can track a project, it needs a repository(local repository).

Use the following command:

```bash
git init
```

### What does it do?

- Creates a hidden `.git` folder inside the current directory.
- Converts a normal folder into a Git repository.
- Starts tracking the project's history.

### Example

```bash
mkdir StudentManagement

cd StudentManagement

git init
```

Example output:

```text
Initialized empty Git repository in ...
```

---

# Step 2 – Configure Your Identity

Every commit stores information about the person who created it.

Configure your username:

```bash
git config user.name "Your Name"
```

Configure your email:

```bash
git config user.email "your@email.com"
```

### Global Configuration

If you want the same username and email to be used in every repository on your computer, add the `--global` option.

```bash
git config --global user.name "Your Name"

git config --global user.email "your@email.com"
```

### Check Configuration

Display all Git settings:

```bash
git config --list
```

Check only the username:

```bash
git config user.name
```

Check only the email:

```bash
git config user.email
```

---

# Step 3 – Add Files to the Staging Area

After creating or modifying files, Git does not automatically include them in the next commit.

You must first move them to the **Staging Area** using `git add`.

### Add a single file

```bash
git add file.txt
```

### Add multiple files

```bash
git add file1.txt file2.txt file3.txt
```

### Add every file

```bash
git add .
```

### Add files with a specific extension

```bash
git add *.java
```

---

# Check the Current Status

Use:

```bash
git status
```

This command shows:

- Untracked files
- Modified files
- Staged files
- Current branch

### Understanding the Colors

- **Red** → File is not staged yet.
- **Green** → File is staged and ready to commit.

---

# Step 4 – Commit Changes

A commit creates a permanent snapshot of your project.

Syntax:

```bash
git commit -m "Commit message"
```

Example:

```bash
git commit -m "Added login page"
```

### Why do we write commit messages?

A commit message describes what changes were made.

Good commit messages make the project history easy to understand.

---

# View Commit History

Display detailed history:

```bash
git log
```

Display a short history:

```bash
git log --oneline
```

Example:

```text
2ab3cd1 Added Login Page

8fd3410 Initial Commit
```

---

# Step 5 – Connect to GitHub

Your local repository and GitHub repository are separate.

To connect them:

```bash
git remote add origin <repository-url>
```

Here, **origin** is simply the default/alias name given to the remote repository.

### Verify the connection

```bash
git remote -v
```
Here, **-v** is Verbose

### Remove the connection

```bash
git remote remove origin
```

---

# Step 6 – Push Changes

Push uploads your local commits to GitHub.

For the **master** branch:

```bash
git push origin master
```

For the **main** branch:

```bash
git push origin main
```

---

# Step 7 – Pull Changes

Pull downloads the latest changes from GitHub to your local repository.

For **master**:

```bash
git pull origin master
```

For **main**:

```bash
git pull origin main
```

Always pull before starting new work if multiple developers are working on the same project.

---

# Complete Git Workflow

```text
Create Files
      │
      ▼
git init
      │
      ▼
git add
      │
      ▼
git status
      │
      ▼
git commit
      │
      ▼
git remote add origin
      │
      ▼
git push
      │
      ▼
GitHub Repository
      ▲
      │
git pull
```

---

# Hands-on Task 1

### Objective

Practice the basic Git workflow.

### Steps

1. Create a new folder.
2. Initialize it as a Git repository.
3. Create five HTML files.
4. Add all files to the staging area.
5. Verify using `git status`.
6. Commit each file separately.
7. Create a repository on GitHub.
8. Connect the local repository.
9. Push all commits to GitHub.

---

# Hands-on Task 2 – Understanding the Non-Fast-Forward Error

This task demonstrates one of the most common Git errors beginners face.

## Setup

Create four folders:

- Folder1
- Folder2
- Folder3
- Folder4

---

## Folder1

- Initialize Git.
- Create `a1.txt` and `a2.txt`.
- Commit both files.
- Connect to GitHub.
- Push the commits.

GitHub now contains:

```
a1.txt

a2.txt
```

---

## Folder2

- Initialize Git.
- Connect it to the same GitHub repository.
- Pull the repository.

Both files should now appear locally.

---

## Folder3

- Initialize Git.
- Create `b1.txt` and `b2.txt`.
- Commit them.
- Connect to the same GitHub repository.
- Try to push.

Git displays:

```text
! [rejected] master -> master (non-fast-forward)
error: failed to push some refs...
```

---

# Why Does This Error Occur?

GitHub already contains commits that your local repository does not have.

Your local history is **behind** the remote history.

Git blocks the push because accepting it would overwrite commits already stored on GitHub.

---

# The Golden Rule

Before pushing your changes:

1. Pull the latest changes from GitHub.
2. Let your local history match the remote history.
3. Resolve conflicts if needed.
4. Push again.

Always remember:

> **Pull first, then Push.**

---

# Folder4 (Correct Approach)

1. Initialize a new repository.
2. Connect it to GitHub.
3. Pull the existing repository.
4. Verify the downloaded files.
5. Create `b1.txt` and `b2.txt`.
6. Commit them.
7. Push again.

This time, the push succeeds because both histories are synchronized.

---

# Common Mistakes

❌ Forgetting to run `git init`

❌ Forgetting to configure Git

❌ Committing without checking `git status`

❌ Using poor commit messages

❌ Pushing without pulling recent changes

❌ Assuming Git automatically tracks new files

---

# Interview Questions

1. What is a Git workflow?
2. What does `git init` do?
3. Why do we use `git add`?
4. Explain the staging area.
5. What is the purpose of `git commit`?
6. Difference between `git log` and `git log --oneline`.
7. What is `origin`?
8. Difference between `git push` and `git pull`.
9. What is the non-fast-forward error?
10. How do you resolve the non-fast-forward error?

---

# Summary

In this chapter, you learned how a project moves through Git, from creating files to uploading them to GitHub.

You also practiced the complete Git workflow and understood why Git sometimes prevents a push when your local repository is behind the remote repository.

Understanding this workflow is essential because almost every Git command you'll learn later builds on these concepts.

---

## Next Chapter

Now that you know how to create repositories, make commits, and upload your work, it's time to learn how developers work independently without affecting each other's code.

In the next chapter, you'll learn about **Git Branching**, including what branches are, why they are used, how `HEAD` works, and how to create, switch, and manage branches.

➡️ **Next:** [03 - Git Branching](03-Branching.md)
