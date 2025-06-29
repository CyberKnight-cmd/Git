# 🔁 Module 5: Rebasing

Welcome to **Module 5: Rebasing**, where you will gain **complete mastery** of rebase operations, interactive editing, history rewriting, and advanced workflows.

---

## 🔄 **1. What is Rebasing?**

🔧 **Definition:**  
Rebase moves or combines a sequence of commits to a new base commit.

### 📝 **Why use rebase?**

✔️ Create a **linear project history**  
✔️ Clean up messy commits before merging  
✔️ Integrate upstream changes into your branch seamlessly

---

## 📝 **2. git rebase**

### **Syntax:**

```bash
git rebase [options] [<upstream> [<branch>]]
```

* **Upstream:** branch to rebase onto (e.g. `main`)
* **Branch:** (optional) the branch you want to rebase (default is current)

---

### **Common Options:**

| Option       | Description                                         |
| ------------ | --------------------------------------------------- |
| `-i`         | Interactive rebase to edit, squash, reorder commits |
| `--continue` | Continue rebase after conflict resolution           |
| `--abort`    | Abort rebase and return to pre-rebase state         |
| `--skip`     | Skip current patch if it cannot be applied          |
| `--onto`     | Rebase a selection of commits onto a different base |

---

### **Examples:**

#### 🔧 **Basic Rebase onto main**

```bash
git checkout feature/login
git rebase main
```

* Moves commits from `feature/login` on top of `main`.

---

#### 🔧 **Interactive Rebase (Editing history)**

```bash
git rebase -i HEAD~3
```

Opens an editor with last 3 commits:

```
pick a1b2c3 Commit message 1
pick d4e5f6 Commit message 2
pick g7h8i9 Commit message 3
```

✅ **Change ‘pick’ to:**

* `reword` to edit commit message
* `edit` to modify commit content
* `squash` to combine with previous commit
* `drop` to remove commit
* `fixup` like squash but discards commit message

Save and close to apply changes.

---

### 🔧 **Rebase with --onto (Advanced)**

#### Scenario: Move subset of commits onto another branch

```bash
git rebase --onto newbase oldbase feature
```

* **newbase:** where you want to move commits
* **oldbase:** common ancestor commit
* **feature:** branch containing commits

🔑 **Use-case:** When you want to replay some commits onto an entirely different branch.

---

## 🔄 **3. Rebase vs Merge**

| Rebase                              | Merge                                   |
| ----------------------------------- | --------------------------------------- |
| Rewrites history                    | Preserves full history                  |
| Creates linear commits              | Creates merge commits                   |
| Preferred for local changes cleanup | Preferred for public collaborative work |

✅ **Golden Rule:** Never rebase **shared/public branches** to avoid history confusion for others.

---

## ⚠️ **4. Edge Cases & Solutions**

| Situation                          | Behavior            | Solution                                                       |
| ---------------------------------- | ------------------- | -------------------------------------------------------------- |
| Conflicts during rebase            | Stops rebase        | Resolve conflicts, stage changes, then `git rebase --continue` |
| Cannot resolve conflict            | Blocks progress     | Use `git rebase --abort` to return to pre-rebase state         |
| Accidentally rebased public branch | Team history broken | Consider using `git reflog` to recover previous state          |

---

### 🔧 **Example: Resolving Conflict During Rebase**

1. Rebase stops with:

   ```
   CONFLICT (content): Merge conflict in file.txt
   ```

2. Edit file to resolve conflict.

3. Stage file:

   ```bash
   git add file.txt
   ```

4. Continue:

   ```bash
   git rebase --continue
   ```

5. Repeat for further conflicts.

---

## 📝 **5. Recovering from Failed Rebase**

🔧 **Abort Rebase**

```bash
git rebase --abort
```

🔧 **If rebase completed but messed up history**

1. Use reflog to find pre-rebase HEAD:

   ```bash
   git reflog
   ```

2. Reset back:

   ```bash
   git reset --hard HEAD@{n}
   ```

Where `n` is the position in reflog before rebase started.

---

## ❗ **6. Common Misunderstandings**

1. **Rebase deletes commits**

❌ It rewrites commits to new hashes but preserves content unless you drop them explicitly.

---

2. **Interactive rebase is risky**

✔️ It’s safe on local branches and powerful for history cleanup.

---

3. **Rebase is always better than merge**

❌ Rebase rewrites history, so use merge for collaborative branches to retain merge commits and context.

---

4. **You can’t rebase with uncommitted changes**

✔️ You must commit or stash changes before rebasing.

---

## 💡 **7. Best Practices**

- ✅ Use rebase to clean up commit history before merging features
- ✅ Never rebase public/shared branches
- ✅ Prefer `--interactive` for clear, meaningful commits
- ✅ Always check `git log` after rebasing to verify history

---

## 🎯 **Summary**

In this module, you learned:

* **Basic and interactive rebase workflows**
* **Using rebase with --onto for advanced rebasing**
* **Handling conflicts and aborting rebase**
* **Rebase vs merge conceptual clarity**
* **Recovering from rebase failures**
* **Common misunderstandings clarified**
---
* 👉 Proceed to [Bonus: Real-life Rebase Practial Applications](rebase-application/README.md) to *learn some very important lessons & practices.*
* 👉 Proceed to [Module 6: Remote Repositories](../6_remote_repositories/README.md) to master **pushing, pulling, remotes, and collaboration workflows**.

---

**Happy Learning!**

> *“Rebase is your brush for crafting clean history; use it wisely.”*
