# Undoing Changes

Mistakes are a normal part of development. Git provides several commands to undo changes safely, depending on **what you want to undo** and **whether the changes have been shared with others**.

The three primary ways to undo changes are:

- **Reset**
- **Restore (Checkout)**
- **Revert**

---

# Git Reset

`git reset` moves the current branch (**HEAD**) back to a previous commit.

Depending on the option used, it can also modify the **Staging Area** and **Working Directory**.

## Syntax

```bash
git reset --soft <commit-id>
git reset --mixed <commit-id>
git reset --hard <commit-id>
```

> **Note:** `git reset` without any option is equivalent to `git reset --mixed`.

> ⚠️ **Warning:** Reset rewrites Git history. Avoid using it on commits that have already been pushed to a shared repository.

---

## 1. Soft Reset

```bash
git reset --soft <commit-id>
```

Moves **HEAD** to an earlier commit while keeping:

- Working Directory ✅
- Staging Area ✅

The undone commits become **staged changes**, ready to commit again.

### Use Case

- Edit the previous commit.
- Combine multiple commits.
- Rewrite local commit history.

---

## 2. Mixed Reset (Default)

```bash
git reset --mixed <commit-id>
```

Moves **HEAD** and resets the **Staging Area**, but keeps the **Working Directory** unchanged.

Result:

- Working Directory ✅
- Staging Area ❌

Your files remain modified but become **unstaged**.

### Use Case

- Remove files from staging.
- Keep local changes without deleting them.

---

## 3. Hard Reset

```bash
git reset --hard <commit-id>
```

Moves **HEAD**, resets the **Staging Area**, and restores the **Working Directory** to match the selected commit.

Result:

- Working Directory ❌
- Staging Area ❌

All changes after that commit are permanently removed from your files.

### Use Case

Only when you're completely sure you don't need the changes anymore.

> ⚠️ This is the most destructive reset option.

---

# Git Restore

`git restore` discards uncommitted changes and restores files back to their last committed state.

Introduced in **Git 2.23**, it replaces many uses of `git checkout`.

---

## Restore a Single File

```bash
git restore filename
```

Example:

```bash
git restore a1.txt
```

---

## Restore All Modified Files

```bash
git restore .
```

---

# Git Checkout (Older Method)

Before Git 2.23, the same task was performed using `git checkout`.

Restore one file:

```bash
git checkout filename
```

Restore all files:

```bash
git checkout .
```

Although it still works, **git restore** is recommended because it has a single, clear purpose.

---

# Hands-on Practice

## Step 1

Create a file.

```
a1.txt
```

---

## Step 2

Commit it.

```bash
git add a1.txt
git commit -m "Add a1"
```

---

## Step 3

Open the file and add some extra text.

Do **not** commit it.

Check the status.

```bash
git status
```

Output:

```
modified: a1.txt
```

---

## Step 4

Restore the file.

```bash
git restore a1.txt
```

or

```bash
git checkout a1.txt
```

---

## Step 5

Check the status again.

```bash
git status
```

The file is restored to its last committed version.

---

# Git Revert

`git revert` undoes the changes made by a specific commit **without deleting Git history**.

Instead, Git creates a **new commit** that reverses the selected commit.

## Syntax

```bash
git revert <commit-id>
```

Example:

```bash
git revert a45bc92
```

---

## Why Use Revert?

- Safe for shared repositories.
- Doesn't rewrite commit history.
- Creates a clear record of what was undone.

---

# Reset vs Revert

| Feature | Reset | Revert |
|----------|-------|---------|
| Rewrites History | ✅ Yes | ❌ No |
| Creates New Commit | ❌ No | ✅ Yes |
| Safe for Shared Branches | ❌ No | ✅ Yes |
| Best Used For | Local commits | Shared commits |

---

# Additional Concepts

## Git Cherry-pick

`git cherry-pick` copies a specific commit from another branch and applies it to the current branch.

### Syntax

```bash
git cherry-pick <commit-id>
```

Example:

```bash
git cherry-pick 6a5b91c
```

### Use Cases

- Copy a bug fix from another branch.
- Bring one feature without merging the entire branch.
- Reuse individual commits.

If conflicts occur:

```bash
git cherry-pick --abort
```

This cancels the cherry-pick operation.

---

# Git Rebase

`git rebase` moves a sequence of commits onto a new base commit, creating a cleaner and more linear project history.

Unlike **merge**, rebase does **not** create a merge commit.

---

## Syntax

```bash
git switch feature
git rebase main
```

Git takes all commits from the **feature** branch and reapplies them on top of the latest commit from **main**.

---

## Why Use Rebase?

- Keeps history clean.
- Removes unnecessary merge commits.
- Makes project history easier to read.

---

## Important Warning

> ⚠️ Never rebase commits that have already been pushed and shared with others.

Rebasing changes commit hashes, which can create conflicts for other developers.

Use rebase only on your **local, unshared branches**.

---

## Abort a Rebase

If conflicts occur during a rebase, cancel it using:

```bash
git rebase --abort
```

Git restores the repository to the state before the rebase started.

---

# Summary

- **git reset** moves HEAD to an earlier commit and can modify the staging area and working directory.
- **Soft Reset** keeps staged changes.
- **Mixed Reset** keeps working files but unstages them.
- **Hard Reset** removes all changes after the selected commit.
- **git restore** restores files to their last committed state.
- **git checkout** can also restore files but is considered the older approach.
- **git revert** safely undoes a commit by creating a new commit.
- **git cherry-pick** copies a specific commit from another branch.
- **git rebase** creates a clean, linear history by replaying commits on a new base.
- Use **reset** for local history changes and **revert** for shared repositories.

---

➡️ **Next:** [06 - Additional Git Commands](06-Additional-Git-Commands.md)
