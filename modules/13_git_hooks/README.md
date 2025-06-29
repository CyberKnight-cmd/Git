# ⚙️ Module 13: Git Hooks & Automation

Welcome to **Module 13: Git Hooks & Automation**, where you will master leveraging Git’s built-in hook system to automate tasks, enforce standards, and streamline workflows.

---

## 📝 **1. What are Git Hooks?**

🔧 **Definition:**  
Git hooks are **scripts that Git executes before or after events** such as commit, push, merge, etc.

✅ **Use cases include:**

- Linting code before commits  
- Running unit tests automatically  
- Preventing pushes to protected branches  
- Updating version numbers pre-tag  
- Triggering CI/CD or deployment scripts

---

## 🔍 **2. Hook Locations & Structure**

✔️ Hooks are located in:

```

<repo>/.git/hooks/

```

✅ **Default hooks are sample files ending with `.sample`.**

To activate a hook:

1. Remove `.sample` extension  
2. Ensure script is executable:

```bash
chmod +x pre-commit
```

---

## 🔧 **3. Commonly Used Git Hooks**

| Hook                   | Trigger                                               | Typical Usage                                |
| ---------------------- | ----------------------------------------------------- | -------------------------------------------- |
| **pre-commit**         | Before `git commit` runs                              | Linting, code formatting, tests              |
| **prepare-commit-msg** | Before commit message editor shows up                 | Auto-generating commit messages              |
| **commit-msg**         | After commit message entered, before commit finalizes | Enforce commit message standards             |
| **post-commit**        | After commit completes                                | Notifications, post-commit actions           |
| **pre-push**           | Before `git push` executes                            | Tests, preventing pushes to main             |
| **pre-rebase**         | Before rebase starts                                  | Checks before rebasing                       |
| **post-merge**         | After merge completes                                 | Installing dependencies, database migrations |
| **post-checkout**      | After `git checkout`                                  | Environment setup for branch                 |
| **pre-receive**        | On remote repo before refs updated                    | Server-side validation                       |
| **update**             | On remote for each ref push                           | More granular server validation              |
| **post-receive**       | On remote after refs updated                          | Triggering deployments or CI                 |

---

## 🔧 **4. Example: Pre-commit Hook for Linting**

### **Create `.git/hooks/pre-commit` with:**

```bash
#!/bin/bash

echo "Running pre-commit checks..."

# Run linter
eslint .

if [ $? -ne 0 ]; then
  echo "Lint errors found. Commit aborted."
  exit 1
fi

echo "All checks passed. Proceeding with commit."
```

✅ **Outcome:** Prevents commits if linting fails.

---

## 🔧 **5. Example: Commit-msg Hook to Enforce Format**

```bash
#!/bin/bash

# Regex for valid commit message
pattern="^(feat|fix|docs|style|refactor|test|chore): .{1,50}"

msg=$(cat $1)

if [[ ! $msg =~ $pattern ]]; then
  echo "Invalid commit message format."
  echo "Use: <type>: <subject>"
  exit 1
fi
```

✅ **Outcome:** Enforces conventional commits style.

---

## 🔧 **6. Example: Post-merge Hook for Dependency Installation**

```bash
#!/bin/bash

echo "Merge completed. Installing dependencies..."
npm install
```

✅ **Outcome:** Ensures environment is up-to-date after merges.

---

## 🔧 **7. Automating with Husky**

🔧 **Husky** is a popular tool to manage Git hooks easily in JavaScript projects.

### **Setup:**

```bash
npm install husky --save-dev
npx husky install
```

### **Add a hook:**

```bash
npx husky add .husky/pre-commit "npm test"
```

✅ **Outcome:** Husky handles hook scripts, cross-platform, with better configuration control.

---

## ❗ **8. Common Misunderstandings & Pitfalls**

1. **Hooks are shared with clones by default**

❌ Local hooks are not cloned. You must distribute them via:

* Husky (JS projects)
* Adding scripts + setup instructions in README
* Creating your own `.githooks` folder and installing via scripts

---

2. **Hooks run automatically for all users**

❌ Only if installed and executable on their local environment.

---

3. **Hooks can modify remote repositories**

❌ Client-side hooks only affect local behavior. Use server-side hooks (pre-receive, update, post-receive) for remote enforcement.

---

4. **Pre-push hook prevents force pushes**

❌ You need server-side policies or protected branches to enforce that.

---

## 💡 **9. Best Practices**

* ✅ Use pre-commit hooks to maintain code quality
* ✅ Combine hooks with CI for layered safety
* ✅ Document hook setup for new team members
* ✅ Prefer Husky for cross-platform hook management in JS projects
* ✅ Keep hook scripts fast; offload heavy tasks to CI
* ✅ Use commit-msg hooks to enforce commit conventions
* ✅ For server hooks, coordinate with your DevOps team and repository hosting platform

---

## 🚀 **10. Advanced: Server-Side Hooks for Deployment**

If managing your own Git server:

* **post-receive hook** can trigger automated deployments after pushes:

```bash
#!/bin/bash
git --work-tree=/var/www/app --git-dir=/var/repo.git checkout -f
systemctl restart app
```

✅ **Outcome:** Automates deployment after successful push.

---

## 🎯 **Summary**

In this module, you learned:

* What Git hooks are and how they work
* Common hook types with examples
* Managing hooks with Husky
* Server-side hooks for automated deployments
* Pitfalls and professional best practices

👉 Proceed to [Module 14: GitHub Workflows](../14_github_workflows/README.md) to master **pull requests, forks, issues, projects, and collaboration patterns for high-performance teams.**

---

> *“Hooks transform Git from a version control tool into an automated guardian of your codebase – use them wisely.”*