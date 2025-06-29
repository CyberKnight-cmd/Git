# 🏷️ Module 10: Tagging & Releases

Welcome to **Module 10: Tagging & Releases**, where you will master marking important commits with tags for version management and streamlined releases.

---

## 📝 **1. What is Tagging?**

🔧 **Definition:**  
Tags are **references to specific commits**, often used to mark **release versions (v1.0, v2.0.1)** or milestones.

✅ **Types of Tags:**

1. **Lightweight Tags:**  
Simple references to a commit (like a branch that never moves).

2. **Annotated Tags:**  
Full objects stored in Git with tagger name, email, date, and message. Recommended for releases.

---

## 🏷️ **2. Creating Tags**

### **Lightweight Tag**

🔧 **Syntax:**

```bash
git tag <tagname>
```

✅ **Example:**

```bash
git tag v1.0
```

✔️ Creates a lightweight tag pointing to current commit.

---

### **Annotated Tag**

🔧 **Syntax:**

```bash
git tag -a <tagname> -m "message"
```

✅ **Example:**

```bash
git tag -a v1.0 -m "Release version 1.0 with authentication module"
```

✔️ Creates an annotated tag with metadata and message.

---

### **Tagging Specific Commits**

🔧 **Syntax:**

```bash
git tag <tagname> <commit>
```

✅ **Example:**

```bash
git tag v0.9 abc123
```

✔️ Tags commit `abc123` instead of HEAD.

---

## 🔍 **3. Viewing Tags**

* **List all tags:**

  ```bash
  git tag
  ```

* **List tags with pattern:**

  ```bash
  git tag -l "v1.*"
  ```

* **Show tag details (annotated tags):**

  ```bash
  git show v1.0
  ```

---

## 🔧 **4. Deleting Tags**

* **Delete local tag:**

  ```bash
  git tag -d v1.0
  ```

* **Delete remote tag:**

  ```bash
  git push origin --delete tag v1.0
  ```

---

## 🔃 **5. Pushing Tags to Remote**

🔧 **Syntax:**

* **Push single tag:**

  ```bash
  git push origin v1.0
  ```

* **Push all tags:**

  ```bash
  git push origin --tags
  ```

✅ **Tip:**
Always push tags after creating release tags locally to ensure CI/CD pipelines pick them up.

---

## 📝 **6. Annotated vs Lightweight Tags: When to Use**

| Tag Type        | Use Case                             | Contains                                             |
| --------------- | ------------------------------------ | ---------------------------------------------------- |
| **Lightweight** | Quick personal bookmarks             | Just commit reference                                |
| **Annotated**   | Official releases, public versioning | Tagger info, date, message, GPG signature (optional) |

✅ **Recommendation:**
Always use **annotated tags for releases** for better traceability and changelogs.

---

## 🔑 **7. Signing Tags (GPG Signature)**

🔧 **Syntax:**

```bash
git tag -s <tagname> -m "message"
```

✅ **Example:**

```bash
git tag -s v1.0 -m "Signed release v1.0"
```

✔️ Creates a **cryptographically signed tag** if GPG is configured, increasing release authenticity.

---

## 🚀 **8. Creating Releases on GitHub**

🔧 **Steps:**

1. Push your tag to GitHub:

   ```bash
   git push origin v1.0
   ```

2. Go to **GitHub repository → Releases**

3. Click **“Draft a new release”**

4. Choose existing tag or create a new one

5. Add release title, description, changelog, and publish

✅ **Why releases matter?**
They provide downloadable source code, release notes, and integration with CI/CD deployments.

---

## ❗ **9. Common Misunderstandings**

1. **Tags move with commits**

❌ Tags are fixed references. Unlike branches, they do not move as commits are added.

---

2. **Deleting a tag locally deletes from remote**

❌ You need to delete it from remote explicitly:

```bash
git push origin --delete tag v1.0
```

---

3. **Lightweight tags are sufficient for releases**

✔️ Technically possible, but **annotated tags are recommended** for storing metadata and signing releases.

---

4. **Tagging commits changes history**

❌ Tags are simply pointers; they do not alter commit history.

---

## 💡 **10. Best Practices**

- ✅ Always use **annotated tags for official releases**
- ✅ Follow semantic versioning (e.g., v1.2.3) for clarity
- ✅ Push tags to remote immediately after creation
- ✅ Sign release tags for authenticity if distributing software publicly
- ✅ Keep release notes meaningful and consistent

---

## 🎯 **Summary**

In this module, you learned:

* Creating **lightweight and annotated tags**
* Viewing, deleting, and pushing tags
* Signing tags for authenticity
* Creating GitHub releases from tags
* Best practices for release versioning

👉 Proceed to [Module 11: Advanced Tools](../11_advanced_tools/README.md) to **debug, cherry-pick, bisect, blame, and manage complex repositories effectively.**.

--- 
> *“Tagging is your repository’s way of bookmarking milestones – version your journey with intention.”*