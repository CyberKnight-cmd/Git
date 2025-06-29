# 📥 Module 9: Stashing

Welcome to **Module 9: Stashing**, where you will master temporarily saving your uncommitted changes to switch tasks seamlessly without losing work.

---

## 📌 **1. What is Git Stash?**

🔧 **Definition:**  
Git stash **temporarily shelves changes** (modified or staged) so you can work on something else, and reapply them later.

✅ Useful when:

- Switching branches to work on urgent fixes
- Saving incomplete work without committing messy changes
- Experimenting without polluting commit history

---

## 📝 **2. git stash**

### **Basic Syntax:**

```bash
git stash [options]
````

### **What does it do?**

* Saves changes in **tracked files** (by default)
* Reverts working directory to last commit

---

### **Example:**

```bash
git stash
```

✔️ Saves current changes as a stash entry and cleans working directory.

---

## 📝 **3. Common Options**

| Command                                 | Description                                                       |
| --------------------------------------- | ----------------------------------------------------------------- |
| `git stash save "message"`              | Save stash with custom message (legacy syntax, still widely used) |
| `git stash push -m "message"`           | Recommended modern syntax to save stash with message              |
| `git stash -u` or `--include-untracked` | Stash untracked files as well                                     |
| `git stash -a` or `--all`               | Stash untracked + ignored files                                   |
| `git stash list`                        | List all stashes                                                  |
| `git stash show`                        | Show summary of latest stash                                      |
| `git stash show -p`                     | Show detailed diff of latest stash                                |
| `git stash apply`                       | Reapply latest stash                                              |
| `git stash apply stash@{n}`             | Apply specific stash                                              |
| `git stash pop`                         | Apply and delete stash                                            |
| `git stash drop stash@{n}`              | Delete specific stash                                             |
| `git stash clear`                       | Delete all stashes                                                |

---

## 🔧 **4. git stash push (Modern Syntax)**

### **Example with message:**

```bash
git stash push -m "WIP: fixing login bug"
```

✔️ Saves stash with clear context for later reference.

---

## 🔧 **5. git stash apply vs pop**

| Command           | Effect                                       |
| ----------------- | -------------------------------------------- |
| `git stash apply` | Applies stash but keeps it in stash list     |
| `git stash pop`   | Applies stash and removes it from stash list |

---

## 📝 **6. Applying Specific Stash**

### **Syntax:**

```bash
git stash apply stash@{2}
```

✔️ Useful when managing multiple stashes simultaneously.

---

## 🔄 **7. git stash branch**

🔧 **Purpose:**
Creates a new branch, checks it out, and applies stash in one command.

### **Syntax:**

```bash
git stash branch <branchname> [stash]
```

### **Example:**

```bash
git stash branch bugfix/login stash@{1}
```

✅ **Why useful?**
When you want to continue stashed work in a separate branch directly.

---

## ⚠️ **8. Edge Cases & Behaviour**

| Situation                              | Behaviour                                   | Solution                                     |
| -------------------------------------- | ------------------------------------------- | -------------------------------------------- |
| Merge conflicts during apply           | Stash apply stops                           | Resolve conflicts, then `git add <file>`     |
| Applying stash on different branch     | Works if files exist on branch              | Otherwise leads to merge conflicts           |
| Stashing untracked files               | Requires `-u` or `--include-untracked` flag | Always review with `git status` before stash |
| Using stash on clean working directory | Creates empty stash entry                   | Check with `git stash list`                  |

---

## ❗ **9. Common Misunderstandings**

1. **Stash saves everything**

❌ By default, it saves only **tracked modified and staged files**. Use `-u` for untracked, `-a` for untracked + ignored files.

---

2. **Apply deletes stash**

❌ `apply` keeps stash, only `pop` deletes after applying.

---

3. **Stash is branch specific**

❌ Stashes are global to the repository and can be applied on any branch (be cautious).

---

4. **Cannot name stashes**

✔️ You can name them using:

```bash
git stash push -m "message"
```

or

```bash
git stash save "message"
```

---

## 💡 **10. Best Practices**

- ✅ Always use meaningful stash messages for clarity
- ✅ Prefer `git stash push` over legacy `save`
- ✅ Use `git stash branch` for continuing work in a new branch cleanly
- ✅ Run `git stash list` periodically and clear unneeded stashes to avoid clutter
- ✅ Remember `stash` is not a replacement for commits; use it for short-term task switching

---

## 🎯 **Summary**

In this module, you learned:

* **What stash is and why it is useful**
* Using `git stash`, `apply`, `pop`, `drop`, `clear`, and `branch`
* Including untracked and ignored files in stash
* Handling stash conflicts and applying specific stashes
* Common misunderstandings and professional best practices

---
* 👉 Proceed to [Bonus Scenario : Multi-branch Stash Workflows & Real Team Conflict Resolutions](multi-branch-stash/README.md) to master Multi-branch Stash and avoid confusions.

* 👉 Proceed to [Module 10: Tagging & Releases](../10_tagging_releases/README.md) to master **version tagging and release management in Git**.

---

> *“Stashing is like putting your ideas in a safe – retrieve them later without losing focus on urgent work.”*


