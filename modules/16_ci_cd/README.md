# 🚀 Module 16: CI/CD with GitHub Actions

Welcome to **Module 16: CI/CD with GitHub Actions**, where you will automate building, testing, and deploying your code seamlessly within GitHub.

---

## 📝 **1. What is CI/CD?**

🔧 **CI (Continuous Integration):**  
Automatically **build and test code** every time you push changes to detect errors early.

🔧 **CD (Continuous Deployment/Delivery):**  
Automatically **deploy code to production** (Deployment) or **prepare releases for manual deployment** (Delivery).

✅ **Benefits:**

- Faster release cycles  
- Improved code quality  
- Reduced manual errors

---

## 🌐 **2. What is GitHub Actions?**

GitHub Actions is GitHub’s built-in CI/CD platform enabling:

✔️ Workflow automation based on GitHub events  
✔️ Running scripts in containers or VMs  
✔️ Integrating with thousands of prebuilt actions

---

## 🔧 **3. Core Components**

| Component | Description |
|---|---|
| **Workflow** | Automation defined in `.github/workflows/*.yml` |
| **Job** | Runs on a runner, composed of steps |
| **Step** | Single task (e.g., checkout code, run tests) |
| **Runner** | Machine executing jobs (GitHub-hosted or self-hosted) |
| **Action** | Reusable packaged commands |

---

## 📝 **4. Sample Workflow: Node.js CI**

```yaml
name: Node.js CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v4

    - name: Use Node.js
      uses: actions/setup-node@v4
      with:
        node-version: '18'

    - run: npm ci
    - run: npm run build --if-present
    - run: npm test
```

✅ **Outcome:**
Builds, installs dependencies, runs tests on every push or PR to `main`.

---

## 🔧 **5. Common Use Cases**

✔️ Run unit tests on PRs
✔️ Build and deploy websites
✔️ Publish packages to npm or PyPI
✔️ Lint code before merging
✔️ Trigger container builds and push to Docker Hub
✔️ Deploy apps to AWS, Azure, GCP

---

## 🔧 **6. Using Secrets**

Store sensitive data securely:

1. Go to **Repo → Settings → Secrets and variables → Actions → New repository secret**.
2. Reference in workflow:

```yaml
env:
  SECRET_KEY: ${{ secrets.SECRET_KEY }}
```

✅ **Best Practice:** Never hardcode secrets in workflows.

---

## 📝 **7. Example: Python CI/CD with Deployment**

```yaml
name: Python CI/CD

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v4

    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.10'

    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt

    - name: Run tests
      run: |
        pytest

  deploy:
    needs: build
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v4

    - name: Deploy to production server
      run: |
        ssh user@server_ip 'cd /app && git pull && systemctl restart app'
      env:
        SSH_KEY: ${{ secrets.SSH_KEY }}
```

✅ **Outcome:** Builds and tests code, then deploys to production via SSH.

---

## 🔧 **8. Matrix Builds**

Run jobs in parallel with different configurations:

```yaml
strategy:
  matrix:
    python-version: [3.8, 3.9, 3.10]
```

✅ **Use case:** Test compatibility across versions or OS.

---

## ❗ **9. Common Pitfalls**

| Issue                                       | Solution                                            |
| ------------------------------------------- | --------------------------------------------------- |
| **Secrets not available**                   | Ensure you set repo/environment secrets             |
| **Job fails due to missing dependencies**   | Install dependencies explicitly in workflow         |
| **Workflow triggers too frequently**        | Refine `on:` triggers for efficiency                |
| **Long running jobs exhaust minutes quota** | Optimize scripts; use self-hosted runners if needed |

---

## 💡 **10. Best Practices**

- ✅ Keep workflows modular and focused
- ✅ Reuse actions instead of rewriting scripts
- ✅ Use caching (`actions/cache`) to speed up installs
- ✅ Protect deployment jobs with manual approval if needed
- ✅ Separate build/test and deploy jobs for clarity
- ✅ Name workflows and jobs descriptively
- ✅ Store secrets securely using GitHub Secrets
- ✅ Monitor Actions usage to manage cost (private repos have minute quotas)
- ✅ Review permissions with `permissions:` key to adhere to least privilege principle

---

## 🔧 **11. Advanced: Manual Approvals & Environments**

For production deployments, require approvals:

```yaml
environment:
  name: production
  url: https://yourapp.com
```

✅ **Setup:** Define environment in repo → Environments → add reviewers for deployment protection.

---

## 🎯 **Summary**

In this module, you learned:

* What CI/CD is and its benefits
* GitHub Actions core concepts and structure
* Real-world workflow examples for Node.js and Python
* Secrets management and matrix builds
* Common pitfalls with preventive strategies
* Best practices for scalable automation

---

> *“CI/CD transforms development from manual toil into a streamlined, reliable pipeline – empowering rapid innovation with confidence.”*
