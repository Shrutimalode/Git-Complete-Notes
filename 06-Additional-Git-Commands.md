# Additional Git Commands

Apart from the basic Git workflow, there are several useful commands that help manage repositories, configure Git, save temporary work, create releases, and maintain clean projects.

This chapter covers:

- Forking
- Global Configuration
- Editing Commits
- Unstaging Files
- .gitignore
- Tags
- Git Stash
- Remote Commands

---

# Forking

A **Fork** is your personal copy of someone else's GitHub repository under your own GitHub account.

Unlike **git clone**, which only creates a local copy, forking creates a separate remote repository that you own.

## Typical Workflow

Clone your fork:

```bash
git clone <your-fork-url>
```

Add the original repository as **upstream**:

```bash
git remote add upstream <original-repository-url>
```

Fetch the latest changes from the original repository:

```bash
git fetch upstream
```

### Why Use Forking?

- Contribute to open-source projects.
- Work independently without affecting the original repository.
- Keep your fork synchronized with the original project.

---

# Global Configuration

Git stores your username and email with every commit.

## Set Username

```bash
git config --global user.name "Your Name"
```

## Set Email

```bash
git config --global user.email "your@email.com"
```

These settings apply to every Git repository on your computer.

---

## Remove Username

```bash
git config --global --unset user.name
```

---

## Remove Email

```bash
git config --global --unset user.email
```

---

## Edit Global Configuration

```bash
git config --global --edit
```

Opens the global Git configuration file in your default editor.

---

# Editing the Last Commit

Sometimes you need to fix the most recent commit.

Git provides:

```bash
git commit --amend
```

This command allows you to:

- Change the commit message.
- Add forgotten files to the last commit.

Example:

```bash
git add file.txt
git commit --amend
```

> ⚠️ Avoid amending commits that have already been pushed to a shared repository because it changes the commit history.

---

# Unstage a File

To remove a file from the staging area without deleting your changes:

```bash
git restore --staged <file-name>
```

Example:

```bash
git restore --staged index.html
```

The file returns to the **Working Directory**, while your changes remain intact.

---

# .gitignore

Some files should never be committed to Git, such as:

- Log files
- Temporary files
- Build folders
- Environment files
- IDE settings

These files are listed inside a **.gitignore** file.

Create or edit it:

```bash
vi .gitignore
```

Example:

```
node_modules/
*.log
.env
target/
bin/
```

View the contents:

```bash
cat .gitignore
```

See ignored files:

```bash
git status --ignored
```

---

# Git Tags

Tags mark important commits, usually for software releases.

Example:

```
v1.0
v1.1
v2.0
```

---

## Create a Tag

```bash
git tag v1.0
```

---

## Tag a Specific Commit

```bash
git tag v1.1 <commit-id>
```

---

## List All Tags

```bash
git tag -l
```

---

## Push Tags

```bash
git push origin --tags
```

By default, Git does **not** push tags with a normal `git push`.

---

## Delete a Local Tag

```bash
git tag -d v1.0
```

---

## Delete a Remote Tag

```bash
git push origin --delete v1.0
```

---

# Git Stash

Sometimes you're working on unfinished code but need to switch branches.

Instead of committing incomplete work, you can **stash** it.

Git temporarily saves your changes and restores a clean working directory.

---

## Save Current Changes

```bash
git stash
```

---

## View All Stashes

```bash
git stash list
```

Example:

```
stash@{0}
stash@{1}
stash@{2}
```

---

## Apply a Stash

```bash
git stash apply stash@{0}
```

The stash remains stored after applying.

---

## Pop a Stash

```bash
git stash pop
```

Restores the latest stash and removes it from the stash list.

---

## Delete a Stash

```bash
git stash drop stash@{0}
```

---

## Stash a Specific File

```bash
git stash push -m "Work in progress" <file-name>
```

Example:

```bash
git stash push -m "Login page" login.html
```

---

# Remote Commands

## Remove Remote Repository

```bash
git remote remove origin
```

Removes the connection between your local repository and the remote repository.

---

## Clone a Repository

```bash
git clone <repository-url>
```

Example:

```bash
git clone https://github.com/username/project.git
```

This downloads:

- Complete project files
- Complete commit history
- Branches
- Repository metadata

---

# Summary

- **Fork** creates your own copy of another GitHub repository.
- **git config** manages your Git username and email.
- **git commit --amend** edits the most recent commit.
- **git restore --staged** removes files from the staging area.
- **.gitignore** prevents unwanted files from being tracked.
- **Tags** mark important commits such as software releases.
- **Git Stash** temporarily saves unfinished work without creating a commit.
- **git clone** downloads a complete repository to your local machine.
- **git remote remove origin** disconnects a local repository from its remote.

---

🎉 **Congratulations!**

You have now covered the core Git concepts, including:

- Git Basics
- Git Workflow
- Branching
- Merging
- Undoing Changes
- Additional Git Commands

You now have a strong foundation to start collaborating on real-world Git and GitHub projects.
