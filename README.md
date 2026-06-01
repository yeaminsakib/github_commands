```markdown
# Git & GitHub Crash Course – Step-by-Step Guide

## 1. What is Git & GitHub?

- **Git** – A version control system used **locally** on your computer to track changes, stage files, and commit snapshots.
- **GitHub** – An online platform that hosts Git repositories (folders) remotely, enabling collaboration and backup.
- **Repository (Repo)** – The remote folder on GitHub that stores your project and its version history.

---

## 2. Installing & Configuring Git

### Check Git Version
```bash
git --version
```

### Set Your Identity (Required for commits)
```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@gmail.com"
```

### View All Current Configurations
```bash
git config --list
```

### Change or Remove Your Name/Email
```bash
# Change name
git config --global user.name "New Name"

# Remove a specific setting
git config --global --unset user.name "Old Name"
```

> 💡 `--global` applies to all repositories on your system. Remove `--global` to configure per project.

---

## 3. SSH Key Setup (Secure Connection to GitHub)

### Generate SSH Key
```bash
# Go to home directory
cd ~

# List all files (including hidden)
ls -a

# Go to .ssh folder (create if not exists)
cd .ssh

# Generate new SSH key
ssh-keygen -o -t rsa -C "your-email@gmail.com"
```
- Follow prompts to save the key (press Enter for default location).
- Add the public key (`~/.ssh/id_rsa.pub`) to your GitHub account:  
  **GitHub → Settings → SSH and GPG keys → New SSH key**

---

## 4. Create & Initialize a Local Git Repository

### Create a New Project Folder
```bash
mkdir my-project
cd my-project
```

### Initialize Git in the Folder
```bash
git init
```
This creates a hidden `.git` folder – Git now tracks changes here.

### Check Repository Status
```bash
git status
```
Shows untracked, staged, or modified files.

---

## 5. Working with Files – Add, Restore, Unstage

### Create or Edit a File
```bash
echo "Hello World" > index.html
```

### Add Files to Staging Area
```bash
# Add a single file
git add index.html

# Add all files in current folder
git add .

# Add all files including subfolders
git add -A

# Add all .js files in current folder
git add *.js

# Add all .js files in any subfolder
git add **/*.js
```

### Unstage a File (Remove from Staging Area)
```bash
git rm --cached index.html
```

### Discard Changes in a File (Restore to Last Committed State)
```bash
git restore index.html
```

### See Differences (Working Directory vs Staging Area)
```bash
git diff
```

---

## 6. Committing Changes

### Commit Staged Files with a Message
```bash
git commit -m "Initial commit – added index.html"
```

### View Commit History
```bash
git log                  # Full details
git log --oneline        # Compact view (short commit IDs)
```

### View Latest or Specific Commit Details
```bash
git show                 # Latest commit
git show <commit-id>     # Specific commit (use first 4-6 chars)
git show HEAD~2          # Two commits ago
```

---

## 7. Undoing Commits (Soft, Mixed, Hard)

| Command | Effect |
|---------|--------|
| `git reset --soft HEAD^` | Undo commit, keep changes **staged** |
| `git reset HEAD^` | Undo commit, keep changes **unstaged** |
| `git reset --hard HEAD^` | Undo commit, **discard all changes** (dangerous) |

> `HEAD^` = one commit before latest. Use `HEAD~2` for two commits back.

### Example
```bash
git log --oneline        # See commits
git reset --soft HEAD^   # Undo last commit, keep files staged
git status               # Verify
```

---

## 8. Moving Between Commits (Detached HEAD)

### Switch to a Specific Commit
```bash
git checkout <commit-id>
```
You are now in **detached HEAD** state – changes made here won't belong to a branch unless you create one.

### Return to Latest Commit on Main Branch
```bash
git checkout main
# or
git checkout master
```

---

## 9. Ignoring Files – `.gitignore`

### Create the File
```bash
touch .gitignore
```

### Example `.gitignore` Rules
```
# Ignore environment file
.env

# Ignore all .log files
*.log

# Exception – include this specific .log file
!important.log

# Ignore entire node_modules folder
node_modules/

# Ignore OS metadata
.DS_Store
```

> Always commit `.gitignore` before adding other files.

---

## 10. Git Aliases (Shortcuts)

### Create an Alias
```bash
git config --global alias.s "status"
```
Now `git s` works like `git status`.

### List All Aliases
```bash
git config --list | grep alias
```

### Remove an Alias
```bash
git config --global --unset alias.s
```

---

## 11. Create a Remote Repository on GitHub

1. Log in to GitHub.
2. Click **+** → **New repository**.
3. Enter **Repository name**.
4. Add **Description** (optional).
5. Choose **Public** or **Private**.
6. ✅ **Add a README file** (optional but recommended).
7. Click **Create repository**.

---

## 12. Connect Local Repo to Remote (GitHub)

### Check Existing Remote Connections
```bash
git remote               # List remote names
git remote -v            # Show URLs (verbose)
```

### Add Remote Repository
```bash
git remote add origin https://github.com/your-username/repo-name.git
```
- `origin` – default name for the remote.
- Replace URL with your GitHub repo URL (SSH or HTTPS).

---

## 13. Push Code to GitHub

### First Push (Set Upstream)
```bash
git push -u origin main
```
- `-u` links local `main` to remote `main` (so future pushes can use just `git push`).

### Subsequent Pushes
```bash
git push
```

### Pull Latest Changes from GitHub
```bash
git pull
```
Fetches and merges remote changes into your local branch.

---

## 14. Branches – Create, Switch, Merge

### Why Branches?
- Keep unstable or experimental code separate from `main`.
- Test changes in a branch, then merge back when ready.

### Create a New Branch
```bash
git branch feature-login
```

### Switch to a Branch
```bash
git checkout feature-login
```

### Create & Switch in One Command
```bash
git checkout -b feature-login
```

### Merge Branch into Main
```bash
git checkout main               # Switch to main branch
git merge feature-login         # Merge changes from feature-login into main
```

### List All Branches
```bash
git branch
```

### Delete a Branch (After Merging)
```bash
git branch -d feature-login
```

---

## 15. Complete Workflow Example

```bash
# 1. Create project
mkdir my-app && cd my-app
git init

# 2. Create and ignore files
echo "node_modules/" > .gitignore
touch index.html

# 3. Stage and commit
git add .
git commit -m "Initial commit"

# 4. Create branch for new feature
git checkout -b add-style

# 5. Make changes, stage, commit
echo "body { margin: 0; }" > style.css
git add style.css
git commit -m "Add basic CSS"

# 6. Merge back to main
git checkout main
git merge add-style

# 7. Connect remote and push
git remote add origin <your-repo-url>
git push -u origin main
```

---

## Quick Reference Card

| Task | Command |
|------|---------|
| Status | `git status` |
| Add all | `git add .` |
| Commit | `git commit -m "msg"` |
| Undo last commit (keep changes) | `git reset --soft HEAD^` |
| Undo last commit (discard changes) | `git reset --hard HEAD^` |
| See history | `git log --oneline` |
| Create branch | `git checkout -b branch-name` |
| Merge branch | `git checkout main` → `git merge branch-name` |
| Push | `git push -u origin main` |
| Pull | `git pull` |
```

---

## How to Use This File

1. **Copy the entire content above**
2. Open any text editor (VS Code, Notepad, etc.)
3. Paste the content
4. Save the file as `git-crash-course.md`
5. Open it in any Markdown viewer (GitHub, VS Code with preview, Typora, etc.)

Or run this in your terminal to create it directly:

```bash
cat > git-crash-course.md << 'EOF'
[PASTE THE ENTIRE CONTENT HERE]
EOF
```

The file is now ready for easy copy-pasting of commands! 🚀
