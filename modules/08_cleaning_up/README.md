# 🧹 Module 8: Cleaning Up

Welcome to **Module 8: Cleaning Up**, where you will learn to keep your Git repository neat by removing untracked files, cleaning ignored files, and pruning stale references safely.

---

## 🗑 **1. git clean**

🔧 **Purpose:**  
Remove untracked files and directories from your working directory.

### **Syntax:**

```bash
git clean [options]
```

### **Common Options:**

| Option | Description                                |
| ------ | ------------------------------------------ |
| `-n`   | Dry run – show what will be deleted        |
| `-f`   | Force deletion (required to perform clean) |
| `-d`   | Include directories                        |
| `-x`   | Remove ignored files as well               |
| `-X`   | Remove only ignored files                  |
| `-q`   | Quiet mode                                 |

---

### **Examples:**

* **Preview what will be deleted:**

  ```bash
  git clean -n
  ```

* **Delete untracked files:**

  ```bash
  git clean -f
  ```

* **Delete untracked files and directories:**

  ```bash
  git clean -fd
  ```

* **Delete ignored files too (careful):**

  ```bash
  git clean -fx
  ```

* **Delete only ignored files, keep others:**

  ```bash
  git clean -fX
  ```

---

### ⚠️ **Edge Cases & Warnings**

| Situation                           | Behavior                       | Solution                                                   |
| ----------------------------------- | ------------------------------ | ---------------------------------------------------------- |
| Running without `-f`                | Does nothing                   | Always add `-f` to execute deletion                        |
| Deleting ignored files accidentally | Removes configs, build folders | Use `-n` before `-fx` or `-fX`                             |
| Cannot clean files                  | File permissions issue         | Check ownership or run with elevated permissions (caution) |

---

## 🌿 **2. git prune**

🔧 **Purpose:**
Remove unreachable (orphaned) objects from local repository. Used mainly during maintenance to reduce repo size.

### **Syntax:**

```bash
git prune [options]
```

### **Common Options:**

| Option              | Description              |
| ------------------- | ------------------------ |
| `-n` or `--dry-run` | Show what will be pruned |
| `-v`                | Verbose output           |

---

### **Example:**

* Preview prunable objects:

  ```bash
  git prune -n
  ```

* Prune unreachable objects:

  ```bash
  git prune
  ```

✅ **Note:**
Usually run internally with `git gc` (garbage collection). Running prune alone is rarely needed in normal workflows.

---

## 🗃 **3. git gc (Garbage Collection)**

🔧 **Purpose:**
Optimize repository by compressing file history and cleaning up unnecessary files and refs.

### **Syntax:**

```bash
git gc [options]
```

### **Common Options:**

| Option           | Description                                                    |
| ---------------- | -------------------------------------------------------------- |
| `--prune=<date>` | Prune unreachable objects older than date (default is 2 weeks) |
| `--aggressive`   | Optimize more thoroughly (slower)                              |
| `--auto`         | Run gc only if needed (default in most Git operations)         |

---

### **Example:**

* Run garbage collection safely:

  ```bash
  git gc
  ```

* Aggressive garbage collection:

  ```bash
  git gc --aggressive
  ```

✅ **Tip:**
Regular `git gc` keeps your repo fast and compact, especially in large projects.

---

## 🔃 **4. git remote prune**

🔧 **Purpose:**
Clean up stale references to deleted remote branches.

### **Syntax:**

```bash
git remote prune <remote>
```

### **Example:**

* Prune deleted branches from `origin`:

  ```bash
  git remote prune origin
  ```

---

## ❗ **5. Common Misunderstandings**

1. **git clean removes tracked files**

❌ It only deletes untracked files or ignored files if specified.

---

2. **Prune deletes local branches**

❌ `git prune` deletes unreachable objects, not branches. Use `git branch -d` or `-D` for deleting branches.

---

3. **Garbage collection is dangerous**

✔️ `git gc` is safe. It cleans and optimizes your repository without affecting current data.

---

4. **Pruning remotes deletes branches from the remote repo**

❌ It only deletes your **local references** to branches deleted on remote.

---

## 💡 **6. Best Practices**

* ✅ Always run `git clean -n` before cleaning
* ✅ Schedule `git gc` periodically in large repos
* ✅ Run `git remote prune origin` to keep remote refs clean
* ✅ Avoid `git clean -fx` unless absolutely sure – it removes ignored files too
* ✅ Combine cleaning with regular backups for safety

---

## 🎯 **Summary**

In this module, you learned:

* Cleaning untracked and ignored files with **git clean**
* Removing unreachable objects with **git prune**
* Optimizing your repository with **git gc**
* Pruning stale remote branches with **git remote prune**
* Best practices to keep your project neat and efficient

👉 Proceed to [Module 9: Stashing](../9_stashing/README.md) to master **temporarily saving work with stashes for seamless context switching**.

---

> *“Clean repos aren’t just beautiful; they are faster, safer, and easier to manage.”*

