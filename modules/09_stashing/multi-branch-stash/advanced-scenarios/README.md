
## 🎁 **Bonus+: Advanced Stash Scenarios for Team Workflows**

### 📝 **Scenario 5: Stashing During Long-running Code Reviews**

**Context:**  
You’re working on `feature/analytics` when a code review requests changes on `feature/dashboard`. You’re midway through complex changes and want to avoid mixing contexts.

### **Steps:**

1. Stash current work:

    ```bash
    git stash push -m "WIP: analytics pipeline refactor"
    ```

2. Switch to the review branch:

    ```bash
    git checkout feature/dashboard
    ```

3. Make requested changes, commit, and push.

4. Return to your original branch:

    ```bash
    git checkout feature/analytics
    ```

5. Apply your stash:

    ```bash
    git stash pop
    ```

✅ **Outcome:**  
Effortless context switching while keeping your working directory clean and focused per task.

---

### 📝 **Scenario 6: Team Stash Coordination**

**Context:**  
Multiple developers are working on the same feature branch. You stash your changes for quick testing on `main`, but your teammates also push updates to the feature branch in the meantime.

### **Risks & Solutions:**

✔️ **Risk:**  
Applying stash after pulling changes might cause conflicts.

✔️ **Solution:**

1. Before stashing, commit WIP changes locally (in a temporary branch) instead of stashing if you plan to pull remote updates.

    ```bash
    git checkout -b wip/feature-partial
    git add .
    git commit -m "WIP: partial feature changes"
    ```

2. Pull updates into feature branch.

3. Merge WIP branch back when ready:

    ```bash
    git merge wip/feature-partial
    ```

4. Delete temporary WIP branch:

    ```bash
    git branch -d wip/feature-partial
    ```

✅ **Lesson Learned:**  
**Prefer commits over stash** for multi-developer branches to avoid stash conflicts and untracked coordination.

---

### 📝 **Scenario 7: Recovering Dropped Stash via Reflog**

**Context:**  
You accidentally dropped a stash with important work.

### **Steps to recover:**

1. Use reflog to locate lost stash commit:

    ```bash
    git reflog
    ```

2. Look for entries like:

    ```
    stash@{0}: WIP on feature: abc1234 commit message
    ```

3. Checkout the commit hash:

    ```bash
    git checkout abc1234
    ```

4. Create a new branch to recover work:

    ```bash
    git checkout -b stash-recovery
    ```

✅ **Outcome:**  
Your accidentally dropped stash is recovered via Git’s reflog safety net.

---

### 📝 **Scenario 8: Using Stash with Patches**

**Context:**  
You want to save stash as a patch file to share with teammates without pushing to remote.

### **Steps:**

1. Create a patch from stash:

    ```bash
    git stash show -p stash@{0} > changes.patch
    ```

2. Share `changes.patch` with teammates.

3. They can apply it with:

    ```bash
    git apply changes.patch
    ```

✅ **Outcome:**  
Quick sharing of WIP changes without polluting remote branches.

---

## ❗ **Key Advanced Lessons**

- ✔️ Stashing is local – commits are safer for team WIP sharing  
- ✔️ Reflog can recover **dropped stashes** if still in history  
- ✔️ Convert stash to patch for lightweight change sharing  
- ✔️ Avoid stashing in **public integration branches** – leads to confusion in teams
---

* 👉 Proceed to [Module 10: Tagging & Releases](../10_tags/README.md) to master **version tagging and release management in Git**.

> *“When your workflow feels chaotic, stash gives you the power to pause, refocus, and re-enter development with confidence.”*


