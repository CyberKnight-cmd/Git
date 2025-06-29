# 🌿 Module 4: Branching & Merging

Welcome to **Module 4: Branching & Merging**, where you will master **creating, managing, and integrating branches effectively** in Git.

---

## 🌱 **1. git branch**

🔧 **Purpose:**  
Lists, creates, renames, and deletes branches.

### **Syntax:**

```bash
git branch [options] [branch-name]
````

### **Common Options:**

| Option          | Description                                           |
| --------------- | ----------------------------------------------------- |
| `-a`            | List all branches (local + remote)                    |
| `-r`            | List only remote branches                             |
| `-d`            | Delete a branch (safe, prevents deletion if unmerged) |
| `-D`            | Force delete a branch (even if unmerged)              |
| `-m <new-name>` | Rename current branch                                 |
| `-M <new-name>` | Force rename branch                                   |
| `--merged`      | List branches merged into current HEAD                |
| `--no-merged`   | List branches not merged                              |

### **Examples:**

```bash
git branch
git branch feature/login
git branch -d feature/old
git branch -D hotfix/temp
git branch -m main master
git branch -a
```

🔑 **Tip:** Use `git branch --merged` to clean up merged branches.

---

## 🔀 **2. git checkout**

🔧 **Purpose:**
Switches branches or restores files.

> ⚠️ **Note:** From Git 2.23+, `git switch` is recommended for branch switching.

### **Syntax:**

```bash
git checkout <branch>
git checkout -b <new-branch>
```

### **Examples:**

```bash
git checkout feature/login
git checkout -b hotfix/navbar
```

---

## 🔄 **3. git switch (New alternative)**

🔧 **Purpose:**
Switch branches clearly (introduced in Git 2.23).

### **Syntax:**

```bash
git switch [options] <branch>
git switch -c <new-branch>
```

### **Examples:**

```bash
git switch develop
git switch -c feature/cart
```

---

## 🔗 **4. git merge**

🔧 **Purpose:**
Combines changes from one branch into another.

### **Syntax:**

```bash
git merge [options] <branch>
```

### **Common Options:**

| Option      | Description                                          |
| ----------- | ---------------------------------------------------- |
| `--no-ff`   | Create merge commit even if fast-forward is possible |
| `--ff-only` | Refuse to merge unless fast-forward is possible      |
| `--squash`  | Combine changes without recording merge commit       |
| `--abort`   | Abort merge in progress (if conflicts)               |

### **Examples:**

```bash
git merge feature/login
git merge --no-ff feature/api
git merge --squash feature/docs
```

---

### 🔧 **Fast-forward vs. Non-fast-forward**

* **Fast-forward:** If current branch has no new commits, pointer simply moves forward.
* **Non-fast-forward (`--no-ff`):** Creates a merge commit preserving history, preferred for feature merges in teams.


---

## 🔁 **6. Resolving Merge Conflicts**

When Git cannot merge automatically:

1. Git marks conflict areas with:

   ```
   <<<<<<< HEAD
   Your changes
   =======
   Incoming changes
   >>>>>>> feature/branch
   ```

2. Edit files to resolve manually.

3. Stage resolved files:

   ```bash
   git add <file>
   ```

4. Complete merge:

   ```bash
   git commit
   ```

---

## ❗ **Common Misunderstandings**

1. **Deleting a branch deletes commits**

❌ Deleting a branch **does not delete commits** if they are reachable from other refs.

---

2. **Rebase is dangerous always**

❌ Rebase is powerful for **local clean-ups**; it is only dangerous on public branches due to history rewriting.

---

3. **Merge commits clutter history**

✔️ They record **real integration points**, essential for team collaboration clarity.

---

4. **Fast-forward merges are always preferred**

❌ Using `--no-ff` retains branch context, important for **feature merges** in team workflows.

---

## 💡 **Tips**

- ✅ Use `git branch -vv` to see tracking branches and last commit summaries
- ✅ Delete merged branches regularly to keep repo clean
- ✅ Use `git merge --squash` to combine feature changes without merge commit
- ✅ Rebase your feature branch onto main before merging for a cleaner history

---

## 📌 **Summary**

In this module, you learned:

* **Creating, listing, renaming, deleting branches**
* **Switching branches with checkout and switch**
* **Merging branches (fast-forward and no-ff)**
* **Resolving merge**
* **Common misunderstandings and professional tips**

---

* 👉 Proceed to [Bonus Section 1: Tips & Tricks – Using Vim Editor During Merge Conflicts](using-vim-properly/README.md) to be accustomed by how shitty and confusing can merging be.
* 👉 Proceed to [Bonus 2: Case Studies – Critical Merging Situations](more-about-merging/README.md) to get familiar with critical merging situations so there's no window left for confusion. (It's harder than people think it is)
* 👉 Proceed to [Module 5: Rebasing](../5_rebasing/README.md) to master rebasing.

---

**Happy Learning!**

> *“Branching lets you build features fearlessly; merging brings your code home.”*