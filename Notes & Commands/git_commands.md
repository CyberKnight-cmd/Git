# 🚀 50 Most Used Git Commands

```bash
# 1. Set your Git username globally
git config --global user.name "Your Name"

# 2. Set your Git email globally
git config --global user.email "your.email@example.com"

# 3. Check Git configuration
git config --list

# 4. Initialize a new Git repository
git init

# 5. Clone a remote repository locally
git clone <repo-url>

# 6. Check the status of files in the repo
git status

# 7. Stage a specific file
git add <file>

# 8. Stage all files in the directory
git add .

# 9. Commit staged changes with a message
git commit -m "Your commit message"

# 10. Add and commit all tracked files
git commit -am "Your commit message"

# 11. View commit history
git log

# 12. Show a simplified one-line log
git log --oneline

# 13. Show the last commit
git log -1

# 14. Show changes of a specific commit
git show <commit-hash>

# 15. Show unstaged changes
git diff

# 16. Show staged changes ready to commit
git diff --staged

# 17. List all local branches
git branch

# 18. Create a new branch
git branch <branch-name>

# 19. Rename the current branch
git branch -m <new-name>

# 20. Delete a branch locally
git branch -d <branch-name>

# 21. Delete a branch forcefully
git branch -D <branch-name>

# 22. Switch to another branch
git checkout <branch-name>

# 23. Create and switch to a new branch
git checkout -b <branch-name>

# 24. Merge another branch into current branch
git merge <branch-name>

# 25. Rebase commits on top of another branch
git rebase <branch-name>

# 26. Abort a rebase in progress
git rebase --abort

# 27. Continue a rebase after resolving conflicts
git rebase --continue

# 28. Show remote repositories
git remote -v

# 29. Add a remote repository
git remote add origin <url>

# 30. Remove a remote
git remote remove origin

# 31. Push commits to the remote repo
git push

# 32. Push and set upstream branch
git push -u origin <branch>

# 33. Push all branches
git push --all

# 34. Pull and merge changes from remote
git pull

# 35. Fetch changes from remote without merging
git fetch

# 36. Unstage a file
git reset <file>

# 37. Unstage all files
git reset

# 38. Reset everything to last commit (keep changes)
git reset --mixed

# 39. Reset and discard all changes
git reset --hard

# 40. Revert a commit by creating a new one
git revert <commit-hash>

# 41. Remove untracked files and folders
git clean -fd

# 42. Temporarily save changes for later
git stash

# 43. Apply last stashed changes
git stash apply

# 44. List all stashed changes
git stash list

# 45. Drop the latest stash
git stash drop

# 46. Apply and remove the last stash
git stash pop

# 47. Show changes in a stash
git stash show -p

# 48. Tag a commit with a version label
git tag v1.0

# 49. List all tags
git tag

# 50. Checkout a specific file from a previous commit
git checkout <commit-hash> -- <file>
