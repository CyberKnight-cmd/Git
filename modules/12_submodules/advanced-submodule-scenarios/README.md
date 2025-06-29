# 🎁 **Bonus: Advanced Submodule Scenarios & GitHub Actions Integration**

---

## 📝 **1. Scenario: Using Submodules for Plugin-Based Architectures**

### **Context:**

You maintain a **main game engine repository** and want to integrate plugins developed as separate repositories.

### **Workflow:**

1. Add each plugin as a submodule:

    ```bash
    git submodule add https://github.com/org/plugin-physics plugins/physics
    git submodule add https://github.com/org/plugin-ai plugins/ai
    ```

2. Developers work within plugin repos independently.

3. Update plugin in main repo when stable:

    ```bash
    cd plugins/physics
    git pull origin main
    cd ../..
    git add plugins/physics
    git commit -m "Updated physics plugin to latest version"
    ```

✅ **Outcome:**  
Modular plugin development with clean separation and version control.

---

## 📝 **2. Scenario: Forked Submodules with Team Customization**

### **Context:**

Using a third-party library as submodule but needing team-specific patches.

### **Workflow:**

1. Fork the third-party repo to your organization’s GitHub.

2. Add **your fork** as submodule:

    ```bash
    git submodule add https://github.com/org/forked-lib vendor/lib
    ```

3. Make changes in your forked submodule.

4. Push changes to **your fork’s remote**, not the upstream.

5. Update main repo’s submodule pointer as usual.

✅ **Outcome:**  
Full control over submodule without altering upstream. Upstream can still be pulled into fork when needed.

---

## 📝 **3. Scenario: Managing Submodules Across Multiple Branches**

### **Context:**

You have multiple release branches (e.g. v1.x, v2.x) that use **different versions of the same submodule**.

### **Workflow:**

- Checkout branch v1.x and update submodule to v1 compatible commit:

    ```bash
    git checkout v1.x
    cd lib
    git checkout v1-compatible
    cd ..
    git add lib
    git commit -m "Set lib submodule to v1 compatible"
    ```

- Checkout branch v2.x and update submodule similarly to v2 compatible commit.

✅ **Outcome:**  
Branch-specific submodule versions tracked cleanly for stable releases.

---

## 📝 **4. Scenario: Nested Submodules (Submodules within Submodules)**

### **Context:**

Repo A includes Repo B as submodule, and Repo B includes Repo C as submodule.

### **Workflow:**

- Clone Repo A with full nested initialization:

    ```bash
    git clone --recurse-submodules <repo-A-url>
    ```

- If already cloned without recurse:

    ```bash
    git submodule update --init --recursive
    ```

✅ **Outcome:**  
Complete nested submodule tree is initialized for development.

---

## 🔧 **5. Using GitHub Actions with Submodules**

### **Problem:**  
By default, GitHub Actions **does not clone submodules** when checking out code.

---

### **Solution:**

Use `actions/checkout` with submodules enabled in your workflow YAML:

```yaml
- name: Checkout repo with submodules
  uses: actions/checkout@v4
  with:
    submodules: recursive
````

---

### **Use Case: CI Build Requiring Submodule Dependencies**

```yaml
name: Build with Submodules

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repo with submodules
      uses: actions/checkout@v4
      with:
        submodules: recursive

    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.10'

    - name: Install dependencies
      run: |
        cd submodule_folder
        pip install -r requirements.txt

    - name: Run tests
      run: |
        pytest tests/
```

✅ **Outcome:**
Your GitHub Actions workflows will have **submodules ready for builds, testing, and deployments** without manual initialization.

---

## ❗ **6. Common Pitfalls in CI/CD**

1. **Forgetting submodule initialization**
   ✅ Always set `submodules: recursive` in `actions/checkout`.

---

2. **Using outdated submodule commits in CI**
   ✅ Commit updated submodule references to main repo before triggering workflows.

---

3. **Secrets management in submodules**
   ✅ Avoid committing sensitive `.env` or keys inside submodules. Use GitHub secrets in workflows instead.

---

## 💡 **7. Best Practices**

* ✅ Keep submodules minimal and modular
* ✅ Prefer forks for customization to avoid upstream conflicts
* ✅ Commit submodule pointers after every relevant update
* ✅ Use `actions/checkout` with `submodules: recursive` in workflows
* ✅ Document submodule setup in README for clarity across teams
* ✅ Audit nested submodules to avoid unintentional bloat

* 👉 Proceed to [Module 13: Git Hooks & Automation](../13_git_hooks/README.md) to explore **automating workflows with hooks like pre-commit, post-merge, and CI triggers**.
---

> *“Submodules unlock true modularity, but require disciplined management and CI/CD awareness to integrate seamlessly in professional pipelines.”*

