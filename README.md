# Git & GitHub Complete Crash Course (All-in-One Command Cheat Sheet)

Git is a version control system used to track code changes locally, and GitHub is a cloud platform used to store and manage Git repositories online.

---

## Full Git Workflow (Start to Finish)

```bash
# Check Git version
git --version

# Configure Git (first time only)
git config --global user.name "Your Name"
git config --global user.email "you@gmail.com"
git config --list

# (Optional) Change or remove config
git config --global user.name "New Name"
git config --global --unset user.name


# Create project and initialize Git
mkdir project_name
cd project_name
git init

# Check status
git status


# SSH Key setup (GitHub login)
cd ~
ssh-keygen -o -t rsa -C "you@gmail.com"
cat ~/.ssh/id_rsa.pub
# Copy and add to GitHub SSH keys


# Add files to staging area
git add filename
git add .
git add -A
git add *.js


# Check changes
git diff


# Restore / unstage files
git restore filename
git rm --cached filename


# Commit changes
git commit -m "Initial commit"


# View commit history
git log
git log --oneline
git show
git show commit_id
git show HEAD~2


# Undo commits
git reset --soft HEAD^
git reset HEAD^
git reset --hard HEAD^   # (danger: deletes changes)


# Checkout old commit / switch version
git checkout commit_id
git checkout main


# GitHub remote setup
git remote
git remote add origin repo_url
git remote -v


# Push & Pull
git push -u origin main
git push
git pull


# Clone repository
git clone repo_url


# Branching system
git branch branch_name
git checkout branch_name
git checkout -b branch_name
git branch


# Merge branch into main
git checkout main
git merge branch_name


# Delete branch
git branch -d branch_name


# .gitignore setup
touch .gitignore
# Example content:
# .env
# node_modules/
# *.log
# *.zip


# Git alias (shortcut commands)
git config --global alias.s "status"
git s
git config --global --unset alias.s


# Fix push error (common issue)
git pull origin main
git push origin main


# Full GitHub project workflow
mkdir project
cd project
git init
git add .
git commit -m "Initial commit"
git remote add origin repo_url
git push -u origin main


# Daily use commands
git status
git add .
git commit -m "message"
git push
git pull
git log --oneline
git branch
git checkout -b feature_branch
git merge feature_branch
