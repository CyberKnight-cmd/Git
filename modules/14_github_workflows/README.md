# 🚀 Module 14: GitHub Workflows

Welcome to **Module 14: GitHub Workflows**, where you will master efficient collaboration using GitHub’s core features: forks, pull requests, issues, projects, discussions, and actions.

---

## 📝 **1. What are GitHub Workflows?**

🔧 **Definition:**  
Workflows define **how developers collaborate, review, merge, and deploy code** on GitHub.

✅ **Core components include:**

- **Forks & clones**
- **Branches**
- **Pull Requests (PRs)**
- **Issues & Discussions**
- **Projects & Boards**
- **GitHub Actions (covered in CI/CD Module)**

---

## 🔄 **2. Forking vs Cloning**

| Action | Purpose | Use Case |
|---|---|---|
| **Fork** | Copy repository to your account | Contribute to open-source projects |
| **Clone** | Copy repository to local machine | Work locally on your own or forked repo |

---

## 🔧 **3. Branching Strategy**

### **Common Strategies:**

1. **Feature branching:**  
Each feature/fix on its own branch from `main`.

2. **Git Flow:**  
Separate branches for `feature`, `develop`, `release`, and `hotfix`.

3. **Trunk-based:**  
Minimal branching, direct to `main` with feature flags.

✅ **Best Practice:**  
Agree on branching strategy within team to maintain consistency.

---

## 🔀 **4. Pull Requests (PRs)**

### **Workflow:**

1. **Fork or branch** repo
2. Make changes and commit
3. Push to remote
4. Open PR to target branch
5. Request reviews and resolve comments
6. Merge once approved

---

### **PR Options:**

| Option | Description |
|---|---|
| **Draft PR** | For ongoing work; reviewers know it’s incomplete |
| **Assignees** | People responsible for merging PR |
| **Reviewers** | People requested to review code |
| **Labels** | Tags for categorization (e.g. bug, enhancement) |
| **Linked Issues** | Closes associated issues automatically upon merge |

---

## 🔧 **5. Issues**

🔧 **Purpose:**  
Track bugs, enhancements, tasks, and questions.

### **Features:**

- Assign to team members  
- Labels for categorization  
- Milestones for tracking progress  
- Linked PRs for automatic closure

✅ **Example:**

```markdown
Issue Title: User login fails under heavy load

Description:
- Steps to reproduce
- Expected outcome
- Actual outcome

Labels: bug, high-priority
Assignee: @username
````

---

## 💬 **6. Discussions**

Used for **open-ended conversations** not tied to specific issues or PRs.

✅ **Best Use Cases:**

* Architectural decisions
* Community Q\&A
* General announcements

---

## 📊 **7. Projects & Boards**

GitHub Projects allow Kanban-style management of issues and PRs.

### **Workflow:**

1. Create Project board (Classic or Beta)
2. Add columns (To Do, In Progress, Done)
3. Link issues and PRs as cards
4. Track progress visually

✅ **Best Practice:** Integrate with milestones for release planning.

---

## 🔒 **8. Protected Branches**

To enforce workflows and code safety:

* Require PR reviews before merging
* Require status checks to pass (CI builds)
* Restrict force pushes and deletions

✅ **Setup:**
Settings → Branches → Add rule for `main` or `develop`.

---

## 📝 **9. CODEOWNERS**

🔧 **Purpose:**
Define default reviewers for specific files or directories.

### **Example (.github/CODEOWNERS):**

```
# Frontend code
frontend/ @frontend-team

# CI workflows
.github/workflows/ @devops-team
```

✅ **Outcome:** PRs touching these paths auto-request reviews from owners.

---

## ❗ **10. Common Pitfalls**

1. **Pushing directly to main without review.**

✅ Use protected branches with enforced PR reviews.

---

2. **Merging PRs without rebasing or updating.**

✅ Always pull latest or rebase to avoid conflicts post-merge.

---

3. **Unclear issue descriptions.**

✅ Use templates for issues and PRs to maintain clarity and standardization.

---

4. **Overusing forks within private repos.**

✅ Prefer branches for internal collaboration to avoid redundant clones.

---

## 💡 **11. Best Practices**

* ✅ Use PR templates to standardize merge requests
* ✅ Automate status checks via GitHub Actions before merges
* ✅ Protect main/release branches with review policies
* ✅ Define clear labels and milestones for issue management
* ✅ Assign reviewers and enforce CODEOWNERS for critical files
* ✅ Keep communication transparent via issues and discussions
* ✅ Regularly clean up stale branches

---

## 🎯 **Summary**

In this module, you learned:

* Forking, cloning, and branching strategies
* Pull Requests and review workflows
* Issue tracking, discussions, and project boards
* Protected branches and CODEOWNERS for governance
* Pitfalls and professional best practices

👉 Proceed to [Module 15: Best Practices](../15_best_practices/README.md) to get familiar with best practices.

---

> *“A disciplined GitHub workflow transforms chaos into collaboration – enabling scalable, high-quality software delivery.”*