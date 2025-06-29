# 🌟 Module 15: Git & GitHub Best Practices

Welcome to **Module 15: Git & GitHub Best Practices**, where you will consolidate your skills into practical, disciplined habits essential for professional software development.

---

## ✅ **1. Commit Practices**

### **1.1 Write Clear Commit Messages**

✔️ **Format:** `<type>(scope): message`

**Example:**

```markdown
feat(auth): add JWT-based authentication flow
````

✅ **Guidelines:**

* Use imperative mood (e.g., “Add feature” not “Added feature”)
* Keep under 50 characters for title
* Add detailed description if necessary (wrap at 72 characters)

---

### **1.2 Commit Frequently, But Logically**

✅ Avoid committing half-done work unless using WIP commits in feature branches.

✅ Each commit should represent a meaningful change.

---

## 🔧 **2. Branching Practices**

### **2.1 Use Feature Branches**

- ✔️ Keep `main` or `master` stable and deployable at all times.
- ✔️ Create branches per feature, bugfix, or experiment:

```bash
git checkout -b feature/login-page
```

---

### **2.2 Follow Team Branching Strategies**

✔️ **Examples:**

* Git Flow (feature, develop, release, hotfix)
* GitHub Flow (feature → main)
* Trunk-based (direct to main with feature flags)

✅ **Choose based on team size and deployment frequency.**

---

## 🚀 **3. Pull Request (PR) Practices**

- ✔️ Keep PRs focused and small for easier review.
- ✔️ Link related issues for context.
- ✔️ Request reviews proactively.
- ✔️ Always rebase or update before merging to avoid conflicts.

---

## 🔍 **4. Merging & Rebasing Practices**

### **4.1 Rebase for Clean History**

✅ `git rebase main` before merging feature branch to integrate latest changes cleanly.

---

### **4.2 Merge for Context Preservation**

✅ Use merge commits to maintain branching history in collaborative environments.

---

### **4.3 Avoid Rebasing Public Branches**

✔️ Never rebase shared/public branches to avoid rewriting history others depend on.

---

## 🗑️ **5. Cleaning Up**

✔️ Delete stale branches locally and remotely after merge:

```bash
git branch -d branch-name       # local
git push origin --delete branch-name  # remote
```

---

## 🔒 **6. Security & Governance**

✅ Use `.gitignore` to avoid committing sensitive files.
✅ Never store secrets in repos; use environment variables or secret managers.
✅ Protect main/release branches with:

* Required PR reviews
* Status checks (CI build)
* No force pushes

---

## 📦 **7. Working with Submodules**

- ✔️ Update submodule references responsibly.
- ✔️ Clone with `--recurse-submodules`.
- ✔️ Document submodule usage for team clarity.

---

## 🔄 **8. Collaboration & Communication**

- ✔️ Write detailed PR and issue descriptions.
- ✔️ Use Discussions for architectural debates.
- ✔️ Use Projects to track milestones and tasks transparently.

---

## 📝 **9. Coding Standards Automation**

- ✔️ Use pre-commit hooks to enforce linting and formatting.
- ✔️ Integrate tests in pre-push or CI workflows.
- ✔️ Use Husky (JS projects) or pre-commit framework (Python) for standardized hooks.

---

## ❗ **10. Common Pitfalls & Prevention**

| Pitfall                     | Prevention                                  |
| --------------------------- | ------------------------------------------- |
| Pushing broken code to main | Enforce PR reviews & CI checks              |
| Large unreviewed PRs        | Break into smaller, logical units           |
| Messy commit history        | Rebase before merging feature branches      |
| Merge conflicts             | Pull or rebase frequently                   |
| Committing secrets          | Use .gitignore and secret managers          |
| Ignoring submodule updates  | Commit submodule pointer updates diligently |
| Poor commit messages        | Follow Conventional Commits style           |

---

## 💡 **11. Professional Best Practices Checklist**

- ✔️ \[ ] Commit messages follow standards
- ✔️ \[ ] Feature branches used for all changes
- ✔️ \[ ] PRs linked to issues
- ✔️ \[ ] CI/CD integrated with status checks
- ✔️ \[ ] Hooks in place for linting/tests
- ✔️ \[ ] Main branch protected
- ✔️ \[ ] Secrets never committed
- ✔️ \[ ] Stale branches cleaned regularly
- ✔️ \[ ] Submodules managed with clarity
- ✔️ \[ ] Team understands branching strategy and workflows

---

## 🎯 **Summary**

In this module, you learned:

* Strategic commit, branching, and PR practices
* Merging vs rebasing decisions
* Security and governance essentials
* Pitfalls with preventive best practices
* Professional checklists for robust software delivery

👉 Proceed to [Module 16: CI/CD with GitHub Actions](../16_ci_cd/README.md) to **automate your build, test, and deploy pipelines for production-grade DevOps workflows**.

---

> *“Tools may change, but disciplined practices remain the foundation of reliable, scalable software engineering.”*

