# 🚀 30 Most Used Git Commands

```bash
# 1. Set your Git username globally
git config --global user.name "Your Name"

# 2. Set your Git email globally
git config --global user.email "your.email@example.com"

# 3. Initialize a new Git repository
git init

# 4. Clone a remote repository locally
git clone <repo-url>

# 5. Check the status of files in the repo
git status

# 6. Stage a specific file
git add <file>

# 7. Stage all changes in the directory
git add .

# 8. Commit staged changes with a message
git commit -m "Your commit message"

# 9. Add & commit all tracked files in one step
git commit -am "Your commit message"

# 10. View commit history
git log

# 11. Show changes of a specific commit
git show <commit-hash>

# 12. Show unstaged changes
git diff

# 13. Show staged changes ready to commit
git diff --staged

# 14. List all local branches
git branch

# 15. Create a new branch
git branch <branch-name>

# 16. Switch to another branch
git checkout <branch-name>

# 17. Create and switch to a new branch
git checkout -b <branch-name>

# 18. Merge another branch into current branch
git merge <branch-name>

# 19. Rebase commits on top of another branch
git rebase <branch-name>

# 20. Show remote repositories
git remote -v

# 21. Add a remote repository
git remote add origin <url>

# 22. Push commits to the remote repo
git push

# 23. Push and set upstream tracking branch
git push -u origin <branch>

# 24. Pull and merge changes from remote
git pull

# 25. Fetch changes from remote without merging
git fetch

# 26. Unstage a specific file
git reset <file>

# 27. Reset everything to the last commit
git reset --hard

# 28. Revert a commit by creating a new one
git revert <commit-hash>

# 29. Remove untracked files and folders
git clean -fd

# 30. Temporarily save changes for later
git stash
