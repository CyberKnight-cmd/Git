# 🛠️ Module 11: Advanced Git Tools

Welcome to **Module 11: Advanced Git Tools**, where you will master powerful features to debug, cherry-pick, bisect, blame, and manage complex repositories effectively.

---

## 🧩 **1. git bisect**

🔧 **Purpose:**  
Helps find the **exact commit that introduced a bug** using binary search.

### **Workflow:**

1. Start bisect:

    ```bash
    git bisect start
    ```

2. Mark current commit as bad:

    ```bash
    git bisect bad
    ```

3. Mark a known good commit:

    ```bash
    git bisect good <commit>
    ```

✔️ Git will checkout midpoint commit. Test it:

- If it’s good: `git bisect good`
- If it’s bad: `git bisect bad`

🔁 Repeat until Git finds the faulty commit.

4. After identification, end bisect:

    ```bash
    git bisect reset
    ```

---

### ⚠️ **Edge Cases & Tips**

- **Automating tests with bisect:**

    ```bash
    git bisect run <script>
    ```

    Runs the provided script on each commit, marking good/bad based on exit code.

✅ **Best practice:** Always reset after bisect to return to HEAD.

---

## 🍒 **2. git cherry-pick**

🔧 **Purpose:**  
Apply a specific commit from one branch onto another.

### **Syntax:**

```bash
git cherry-pick <commit>
````

✅ **Example:**

```bash
git cherry-pick abc123
```

✔️ Applies commit `abc123` to current branch.

---

### **Options:**

| Option        | Description                                   |
| ------------- | --------------------------------------------- |
| `-x`          | Append note about cherry-picked commit origin |
| `--no-commit` | Apply changes without committing (staged)     |
| `--continue`  | Continue after conflict resolution            |
| `--abort`     | Abort cherry-pick                             |

---

### ⚠️ **Edge Cases & Warnings**

* **Conflicts:** Cherry-pick may cause conflicts like merges; resolve and continue.
* **Multiple commits:**

  ```bash
  git cherry-pick A..B
  ```

  Picks all commits from A (excluded) up to B (included).

✅ **Best practice:** Use sparingly to avoid confusing histories.

---

## 🕵️‍♂️ **3. git blame**

🔧 **Purpose:**
Show **who last modified each line** of a file with commit references.

### **Syntax:**

```bash
git blame <file>
```

✅ **Example:**

```bash
git blame app.py
```

✔️ Displays author, commit hash, and timestamp for each line.

---

### **Options:**

| Option             | Description                             |
| ------------------ | --------------------------------------- |
| `-L <start>,<end>` | Blame specific line range               |
| `-e`               | Show author email                       |
| `-p`               | Output in raw format for scripts        |
| `--since=<date>`   | Limit to changes after date             |
| `--reverse`        | Show commits modifying lines in reverse |

---

### ⚠️ **Common Misunderstandings**

1. **Blame shows who wrote the line originally**

❌ It shows **who last modified** the line, not necessarily the original author.

---

## 🔍 **4. git reflog**

🔧 **Purpose:**
Shows history of all changes to HEAD including branch switches, resets, rebases, even unreachable commits.

### **Syntax:**

```bash
git reflog
```

✅ **Example:**

```bash
git reflog
```

✔️ Useful to recover lost commits after reset or rebase.

---

### ⚠️ **Edge Cases:**

* Reflog is **local only**, not shared with remote.
* Entries expire (default 90 days).

✅ **Best practice:** Check reflog before concluding a commit is unrecoverable.

---

## 🔗 **5. git rebase -i (Interactive Rebase)**

🔧 **Purpose:**
Edit, reorder, squash, or delete commits in your branch history.

### **Syntax:**

```bash
git rebase -i <base-commit>
```

✅ **Example:**

```bash
git rebase -i HEAD~5
```

✔️ Opens interactive editor with:

* `pick`: use commit
* `reword`: edit commit message
* `edit`: amend commit
* `squash`: combine with previous
* `fixup`: squash without commit message
* `drop`: delete commit

---

### ⚠️ **Edge Cases & Warnings**

* **Interactive rebase rewrites history.** Avoid on public branches.
* **Conflicts:** Resolve after each change, then `git rebase --continue`.

✅ **Best practice:** Use for cleaning up local commit history before merging PRs.

---

## 🧪 **6. git filter-branch & BFG Repo-Cleaner**

🔧 **Purpose:**
Rewrite entire history (dangerous if used improperly) to:

* Remove sensitive data (passwords, keys)
* Delete large files permanently

### **git filter-branch syntax:**

```bash
git filter-branch --tree-filter 'rm -f password.txt' HEAD
```

✅ **Example:**

```bash
git filter-branch --force --index-filter \
"git rm --cached --ignore-unmatch secrets.txt" \
--prune-empty --tag-name-filter cat -- --all
```

---

### ⚠️ **Limitations:**

* Slow on large repos
* BFG Repo-Cleaner is recommended alternative:

🔧 **BFG Example:**

```bash
bfg --delete-files secrets.txt
```

✅ **Best practice:** Backup repo before running destructive history rewrites.

---

## ❗ **7. Common Misunderstandings**

1. **git cherry-pick merges branches**

❌ It only applies selected commits; does not merge histories.

---

2. **Blame shows original author**

❌ Shows last modifier, not necessarily original creator.

---

3. **Reflog is global**

❌ Reflog is local to your machine.

---

4. **filter-branch is safe**

❌ It rewrites history; use carefully with backups and coordination in teams.

---

## 💡 **8. Best Practices**

* ✅ Use `bisect` for debugging regression bugs efficiently
* ✅ Use `cherry-pick` sparingly to avoid history complexity
* ✅ Use `blame` with context – last modifier ≠ original author
* ✅ Leverage `reflog` for recovery before declaring lost commits
* ✅ Practice interactive rebase on dummy repos before production use
* ✅ Use BFG instead of filter-branch for large history rewrites

---

## 🎯 **Summary**

In this module, you learned:

* **git bisect** for debugging regressions
* **git cherry-pick** for selective commit application
* **git blame** for line-level authorship
* **git reflog** for recovering unreachable commits
* **Interactive rebase** for history clean-up
* **filter-branch & BFG** for permanent history rewrites

👉 Proceed to [Module 12: Git Submodules](../12_submodules/README.md) to master **managing repositories within repositories for modular projects**.

---

> *“Advanced Git commands are power tools – wield them wisely to debug, recover, and manage history like a pro.”*

