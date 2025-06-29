# ⚙️ Module 2: Git Basics (Comprehensive Edition)

Welcome to **Module 2: Git Basics**, where you will learn **every detail about fundamental Git commands** to build strong operational confidence.

---

## 📝 **1. git init**

🔧 **Purpose:**  
Initializes a new Git repository by creating a `.git` folder containing metadata and object database.

### **Syntax:**

```bash
git init [options] [directory]
````

### **Options:**

| Option                            | Description                                                            |
| --------------------------------- | ---------------------------------------------------------------------- |
| `--bare`                          | Creates a **bare repository** (used for remotes, no working directory) |
| `--template=<template_directory>` | Directory from which to copy pre-written hooks or configuration        |
| `--separate-git-dir=<git dir>`    | Place `.git` directory elsewhere                                       |
| `-q, --quiet`                     | Suppress output                                                        |

### **Examples:**

```bash
git init                # Initialize repo in current directory
git init myproject      # Create new folder and initialize repo there
git init --bare repo.git  # Initialize a bare repository
```

🔑 **Note:** Bare repositories are used as **central remotes**. They **cannot edit files directly**.

---

## 🔎 **2. git config**

🔧 **Purpose:**
Sets configuration variables to control Git behavior.

### **Syntax:**

```bash
git config [options] [key] [value]
```

### **Common Options:**

| Option     | Description                                             |
| ---------- | ------------------------------------------------------- |
| `--global` | Applies configuration to **current user across system** |
| `--system` | Applies configuration system-wide (admin access needed) |
| `--local`  | Applies configuration to **current repository** only    |
| `--list`   | Shows all config variables                              |
| `--unset`  | Removes a specific config key                           |
| `--edit`   | Opens config file in default editor                     |

### **Examples:**

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global core.editor "vim"
git config --list
git config --unset user.email
```

🔑 **Note:** Without any scope (`--global` or `--local`), it defaults to **local** in the current repo.

---

## 📂 **3. git status**

🔧 **Purpose:**
Displays the working directory and staging area status.

### **Syntax:**

```bash
git status [options]
```

### **Options:**

| Option                       | Description                                  |
| ---------------------------- | -------------------------------------------- |
| `-s, --short`                | Short format status output                   |
| `-b, --branch`               | Show branch and tracking info                |
| `--show-stash`               | Show if stash exists                         |
| `--ignored`                  | Show ignored files                           |
| `--untracked-files[=<mode>]` | Show untracked files (mode: no, normal, all) |

### **Examples:**

```bash
git status
git status -s
git status -sb
```

🔍 **Example Output (short):**

```
 M index.html   # Modified file
?? newfile.js   # Untracked file
```

---

## ➕ **4. git add**

🔧 **Purpose:**
Stages changes to be included in the next commit.

### **Syntax:**

```bash
git add [options] <pathspec>...
```

### **Options:**

| Option          | Description                                    |
| --------------- | ---------------------------------------------- |
| `-A`            | Stage all changes (tracked and untracked)      |
| `-u`            | Stage modifications and deletions only         |
| `-p, --patch`   | Stage parts of files interactively             |
| `-n, --dry-run` | Show files that would be added without staging |
| `-v, --verbose` | Verbose output                                 |
| `-i`            | Interactive staging                            |

### **Examples:**

```bash
git add index.html
git add .                 # Stage all in current directory
git add -A                # Stage all changes everywhere
git add -u                # Stage only updated and deleted files
git add -p script.js      # Stage file partially (hunks)
```

🔑 **Tip:** Use `git add -p` for **selective staging** within files (useful in production commits).

---

## ✅ **5. git commit**

🔧 **Purpose:**
Records staged changes to local repository with a message.

### **Syntax:**

```bash
git commit [options] [--] [<pathspec>...]
```

### **Common Options:**

| Option                    | Description                                            |
| ------------------------- | ------------------------------------------------------ |
| `-m "message"`            | Commit with message                                    |
| `-a`                      | Automatically stage tracked file changes before commit |
| `--amend`                 | Modify previous commit (message or content)            |
| `--no-edit`               | Amend without changing commit message                  |
| `-v, --verbose`           | Show diff in commit message editor                     |
| `--allow-empty`           | Create commit with no changes                          |
| `--squash <commit>`       | Combine commits while retaining history                |
| `--fixup <commit>`        | Prepare for autosquash rebase                          |
| `--author="Name <email>"` | Override author details                                |

### **Examples:**

```bash
git commit -m "Add footer section"
git commit -am "Quick fix for header padding"
git commit --amend -m "Updated commit message"
```

🔑 **Note:** `git commit -am` **only stages modified tracked files**; it does not stage new untracked files.

---

## 🔄 **6. git log**

🔧 **Purpose:**
Displays commit history.

### **Syntax:**

```bash
git log [options] [<revision range>] [--] [<path>...]
```

### **Common Options:**

| Option               | Description                          |
| -------------------- | ------------------------------------ |
| `--oneline`          | Condensed view (hash + message)      |
| `--graph`            | ASCII graph of branch/merge history  |
| `--decorate`         | Show branch and tag names            |
| `-p`                 | Show diffs introduced in each commit |
| `-n <number>`        | Show last N commits                  |
| `--author=<pattern>` | Filter commits by author             |
| `--since="date"`     | Show commits after date              |
| `--until="date"`     | Show commits before date             |
| `--stat`             | Show summary of changes per commit   |

### **Examples:**

```bash
git log
git log --oneline --graph --decorate
git log -p -2
git log --author="Alice"
git log --since="2 weeks ago"
```

🔑 **Tip:** Combine `--oneline`, `--graph`, and `--decorate` for a clear **branch history view**.

---

## 🔁 **7. git clone**

🔧 **Purpose:**
Creates a local copy of a remote repository.

### **Syntax:**

```bash
git clone [options] <repo> [<directory>]
```

### **Common Options:**

| Option                 | Description                                     |
| ---------------------- | ----------------------------------------------- |
| `--depth <depth>`      | Create a **shallow clone** with limited history |
| `--branch <branch>`    | Clone specific branch                           |
| `--single-branch`      | Clone only specified branch                     |
| `--recurse-submodules` | Clone all submodules recursively                |

### **Examples:**

```bash
git clone https://github.com/user/repo.git
git clone --depth 1 https://github.com/user/repo.git
git clone --branch develop --single-branch https://github.com/user/repo.git
```

🔑 **Note:** Shallow clones are useful for CI/CD pipelines to reduce clone time.

---

## 🔀 **8. git checkout**

🔧 **Purpose:**
Switch branches or restore files.

### **Syntax:**

```bash
git checkout [options] <branch or commit>
git checkout [options] -- <filepaths>
```

### **Options:**

| Option                  | Description                                     |
| ----------------------- | ----------------------------------------------- |
| `-b <branch>`           | Create and switch to new branch                 |
| `-B <branch>`           | Create or reset branch to starting point        |
| `--detach`              | Checkout specific commit in detached HEAD state |
| `--orphan <new-branch>` | Create new branch with no history               |

### **Examples:**

```bash
git checkout feature/login
git checkout -b hotfix/navbar
git checkout -- index.html   # Restore file from last commit
git checkout 4f5a6b7         # Checkout specific commit (detached HEAD)
```

🔑 **Tip:** Git 2.23+ recommends `git switch` for branch switching and `git restore` for file restoration for clarity.

---

## ❗ **Common Mistakes**

1. **Using `git commit -am` for new files**

Fails because `-a` only stages modified tracked files, not new files.

---

2. **Forgetting `--global` in config**

Without `--global`, settings apply only to the current repository, causing confusion in new repos.

---

3. **Using `git checkout` for file restoration without intention**

Overwrites local changes without warning.

---

4. **Assuming `git clone` includes all branches**

By default it fetches all branches, but only checks out the **default branch**. Use `git branch -a` to see others.

---

## 💡 **Pro Tips**

- ✅ Always check `git status` before commits
- ✅ Use `git log --oneline --graph` to visualise branch history
- ✅ Write descriptive commit messages summarising **what changed and why**
- ✅ Try out all the commands by yourself, cuz there's no freaking way anyone would remember this BS.

---

## 📌 **Summary**

In this module, you learned:

* All major **parameters and options** of foundational Git commands
* Practical real-world usage examples
* Common mistakes to avoid
* Pro tips for effective workflow

👉 Proceed to [Module 3: Viewing History](../3_viewing_history/README.md) to master **log analysis, diffs, and commit inspection**.

---

**Happy Learning!**

> *“Knowing every flag and nuance makes you not just a Git user, but a Git power user.”*

