## 🎁 **Bonus: Recovering Commits After Accidental Reset or Branch Deletion**

Sometimes you might accidentally:

- Run `git reset --hard HEAD~1` and lose a commit  
- Delete a branch with valuable work

Here’s how to recover:

### 🔎 **1. Using git reflog**

`git reflog` records **all movements of HEAD**, including resets and deletions (locally).

🔧 **Steps to recover a lost commit:**

1. View reflog:

    ```bash
    git reflog
    ```

    Example Output:

    ```
    a1b2c3d HEAD@{0}: reset: moving to HEAD~1
    d4e5f6g HEAD@{1}: commit: Added new footer section
    ...
    ```

2. Identify the commit hash or reference you lost (e.g., `HEAD@{1}`).

3. Checkout the lost commit:

    ```bash
    git checkout <commit-hash>
    ```

4. To restore it to your branch, either:

    - **Create a new branch from it:**

        ```bash
        git checkout -b recovered-feature
        ```

    - **Cherry-pick it into your current branch:**

        ```bash
        git cherry-pick <commit-hash>
        ```

---

### 🔄 **2. Recovering a deleted branch**

If you deleted a branch locally:

1. Find its last commit in reflog or with:

    ```bash
    git reflog show <deleted-branch>
    ```

2. Recreate the branch:

    ```bash
    git checkout -b <branch-name> <commit-hash>
    ```

---

### ⚠️ **Note on reflog availability**

- `git reflog` is **local only**. If you deleted a branch on remote, check if others have it, or recover using:

    ```bash
    git checkout -b <branch-name> origin/<branch-name>
    ```

if the remote still retains it.

---

✅ **Summary:**  
`git reflog` is your **lifeline for recovery**. Always check it before assuming work is lost forever.

> *“With reflog, nothing is ever truly lost – only forgotten temporarily.”*


