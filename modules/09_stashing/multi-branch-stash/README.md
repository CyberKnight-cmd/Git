## 🎁 **Bonus: Multi-branch Stash Workflows & Real Team Conflict Resolutions**

### 📝 **Scenario 1: Switching Tasks Across Branches Using Stash**

**Context:**  
You’re working on `feature/login` and receive an urgent bug fix task on `main`. Your working directory has multiple changes, including untracked files.

### **Steps:**

1. Stash all changes (including untracked):

    ```bash
    git stash push -u -m "WIP: login form redesign"
    ```

2. Switch to `main`:

    ```bash
    git checkout main
    ```

3. Fix the urgent bug, commit, and push.

4. Switch back to your feature branch:

    ```bash
    git checkout feature/login
    ```

5. Apply your stash:

    ```bash
    git stash pop
    ```

✅ **Outcome:**  
Your incomplete login work is restored seamlessly without dirty commits polluting the history.

---

### 📝 **Scenario 2: Using Stash Across Branches for Hotfix Integration**

**Context:**  
You have stashed WIP changes on `feature/payment` but realise the same changes are needed on `feature/subscription`.

### **Steps:**

1. Stash your work with a clear message:

    ```bash
    git stash push -m "WIP: payment processing validations"
    ```

2. Switch to `feature/subscription`:

    ```bash
    git checkout feature/subscription
    ```

3. Apply the stash:

    ```bash
    git stash apply stash@{0}
    ```

✅ **Outcome:**  
Changes from `feature/payment` are applied to `feature/subscription`. Adjust and commit as needed.

---

### 📝 **Scenario 3: Conflict Resolution During Stash Apply**

**Context:**  
Applying a stash causes merge conflicts because files have diverged since stashing.

### **Steps to resolve:**

1. Apply the stash:

    ```bash
    git stash apply
    ```

2. Git will output:

    ```
    Auto-merging filename.txt
    CONFLICT (content): Merge conflict in filename.txt
    ```

3. Open the conflicted files, resolve manually, and mark as resolved:

    ```bash
    git add filename.txt
    ```

4. Complete stash application:

    ```bash
    git stash drop stash@{0}
    ```

✅ **Outcome:**  
Your stash is merged into current changes with conflicts resolved safely.

---

### 📝 **Scenario 4: Using `git stash branch` for Clean Workflow**

**Context:**  
Your stash has become large and you want to continue work on it in an isolated branch.

### **Steps:**

1. Create a new branch directly from stash:

    ```bash
    git stash branch payment-refactor stash@{0}
    ```

✅ **Outcome:**  
A new branch `payment-refactor` is created at the stash’s original base commit with stash changes applied, and the stash entry is dropped automatically.

---

## ❗ **Key Lessons Learned**

* ✔️ Stashes are **global to the repo** – can be applied on any branch  
* ✔️ Always use **meaningful stash messages** for clarity in multi-stash workflows  
* ✔️ Use `git stash branch` for large or risky stashes to avoid polluting current branches  
* ✔️ Resolve stash conflicts as you would with merges – Git treats them similarly  
* ✔️ Clean up old stashes with `git stash list` + `git stash drop` to keep your stash list organised

--- 

* 👉 Proceed to [Bonus Scenario : Advanced Stash Scenarios For Team Workflows](advanced-scenarios/README.md) to master Multi-branch Stash and avoid confusions.
* 👉 Proceed to [Module 10: Tagging & Releases](../10_tagging_releases/README.md) to master **version tagging and release management in Git**.
---

> *“Stash workflows are your personal save points in Git – use them wisely to move fearlessly between tasks.”*

