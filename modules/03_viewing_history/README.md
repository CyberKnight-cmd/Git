# 🔍 Module 3: Viewing History

Welcome to **Module 3: Viewing History**, where you will master how to **inspect your repository’s commit history, changes, and diffs efficiently**.

---

## 📝 **1. git log**

🔧 **Purpose:**  
Shows the commit history of the repository.

### **Syntax:**

```bash
git log [options] [<revision range>] [--] [<path>...]
````

### **Common Options:**

| Option                           | Description                                             |
| -------------------------------- | ------------------------------------------------------- |
| `--oneline`                      | Show condensed output (first 7 chars of hash + message) |
| `--graph`                        | Show ASCII graph of branches and merges                 |
| `--decorate`                     | Show branch, tag, HEAD references alongside commits     |
| `-p`                             | Show diffs introduced in each commit                    |
| `-n <num>` / `--max-count=<num>` | Limit output to last N commits                          |
| `--author=<pattern>`             | Filter commits by author                                |
| `--since=<date>`                 | Show commits more recent than date                      |
| `--until=<date>`                 | Show commits older than date                            |
| `--stat`                         | Show stats about files changed                          |
| `--reverse`                      | Show oldest commits first                               |
| `--follow <file>`                | Show history of a file, including renames               |

### **Examples:**

```bash
git log
git log --oneline --graph --decorate
git log -p -2
git log --author="Alice"
git log --since="last week"
git log --stat
git log --follow README.md
```

🔑 **Tip:** Combine `--graph`, `--oneline`, and `--decorate` for a **clear visual overview** of project history.

---

## 🔎 **2. git show**

🔧 **Purpose:**
Shows information about a specific commit, tag, or object.

### **Syntax:**

```bash
git show [options] <object>
```

### **Common Options:**

| Option              | Description                              |
| ------------------- | ---------------------------------------- |
| `--stat`            | Show diffstat summary                    |
| `--name-only`       | Show only names of changed files         |
| `--name-status`     | Show status + names of changed files     |
| `--pretty=<format>` | Change commit message formatting         |
| `-s, --no-patch`    | Suppress diff output, show only metadata |

### **Examples:**

```bash
git show 4f5a6b7
git show --stat HEAD
git show --name-only HEAD~1
git show --pretty=short 4f5a6b7
```

🔑 **Tip:** Useful to **review exact changes introduced by a commit** before merging or reverting.

---

## 📝 **3. git diff**

🔧 **Purpose:**
Shows differences between commits, branches, staging area, and working directory.

### **Syntax:**

```bash
git diff [options] [<commit>] [--] [<path>...]
```

### **Common Usage Scenarios:**

| Command                        | Description                                               |
| ------------------------------ | --------------------------------------------------------- |
| `git diff`                     | Differences in working directory not staged               |
| `git diff --staged`            | Differences between staging area and last commit          |
| `git diff <commit>`            | Differences between working directory and specific commit |
| `git diff <commit1> <commit2>` | Differences between two commits                           |
| `git diff <branch1> <branch2>` | Differences between branches                              |
| `git diff --name-only`         | Show only file names changed                              |
| `git diff --stat`              | Show summary of changes                                   |

### **Examples:**

```bash
git diff
git diff --staged
git diff HEAD~1
git diff feature/login main
git diff --name-only HEAD
```

🔑 **Tip:** Use `git diff --color-words` for word-diff highlighting in prose files.

---

## 🔁 **4. git reflog**

🔧 **Purpose:**
Shows a log of where HEAD and branch references have been, even if they are not reachable by `git log`.

### **Syntax:**

```bash
git reflog [options]
```

### **Examples:**

```bash
git reflog
git reflog show main
```

🔍 **Use Case:**
Recovering commits after an accidental reset or branch deletion.

---

## ❗ **Common Misunderstandings**

1. **git log shows all stashes**

❌ `git log` does **not** show stashes. Use `git stash list` for that.

---

2. **git diff shows committed changes**

❌ `git diff` shows **uncommitted changes** by default. To view committed differences, compare two commits:

```bash
git diff <commit1> <commit2>
```

---

3. **git show only works on commits**

❌ `git show` can display content of **tags, trees, and blobs**, not just commits.

---

4. **git reflog is same as git log**

❌ `git reflog` shows **local HEAD movements**, including orphan commits, resets, and rebase movements that are **not shown in git log**.

---

## 💡 **Tips**

✅ Use `git log --graph --all --decorate --oneline` to visualise the **entire repo structure**.

✅ `git diff --staged` before commits to **review what you are committing**.

✅ `git show HEAD~2:file.txt` views the file as it was two commits ago.

✅ Use `git log --follow <file>` to track file history across renames.

---

## 📌 **Summary**

In this module, you learned:

* **git log:** Inspect commit history with advanced options
* **git show:** View details of specific commits or objects
* **git diff:** Compare changes between commits, branches, and working directory
* **git reflog:** Recover lost commits and track HEAD movements
* **Common misunderstandings** clarified for confident usage

--- 

* 👉 Optional [Bonus Section : Recovering files after deletion](recovering-files-after-accidental-deletion/README.md) to master **creating, managing, and merging branches effectively**.
* 👉 Proceed to [Module 4: Branching & Merging](../4_branching_merging/README.md) to master **creating, managing, and merging branches effectively**.

---

**Happy Learning!**

> *“If you know how to view your project’s past, you gain complete control over its future.”*
