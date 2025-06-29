## 🎁 **Bonus 1: Tips & Tricks – Using Vim Editor During Merge Conflicts**

Many Git merge, rebase, or commit operations open the **Vim editor** by default. If you’re unfamiliar with Vim, here’s a quick survival guide:

### 📝 **Opening Vim**

When Git opens Vim for commit messages or rebase instructions:

- You enter in **Normal mode** by default.

---

### ✏️ **Basic Vim Modes**

| Mode | How to enter | Description |
|---|---|---|
| Normal | Press `Esc` | Navigation and commands |
| Insert | Press `i` | Type/edit text |
| Visual | Press `v` | Select text |
| Command-line | Press `:` | Enter commands (save, quit, etc.) |

---

### ✅ **Key Commands for Git Tasks**

| Action | Command |
|---|---|
| Enter insert mode | `i` |
| Save and quit | `:wq` then `Enter` |
| Quit without saving | `:q!` then `Enter` |
| Delete a line | `dd` |
| Navigate lines | Arrow keys or `j` (down), `k` (up) |
| Replace character | `r<char>` |
| Undo last change | `u` |

---

### 🔄 **For Rebase Interactive**

When rebasing with:

```bash
git rebase -i HEAD~3
````

* Vim opens with a list like:

  ```
  pick abc123 First commit
  pick def456 Second commit
  pick ghi789 Third commit
  ```

* To edit:

  1. Move cursor to the word `pick`.
  2. Press `r` then type `s` to replace it with `squash`, or `i` to enter insert mode and edit.
  3. Press `Esc` to return to normal mode.

* Save and exit with `:wq`.

---

🔑 **Tip:** If you prefer another editor (like Nano or VSCode), set it globally:

```bash
git config --global core.editor "nano"
# or for VSCode
git config --global core.editor "code --wait"
```

---

