# Git & GitHub Crash Course

## Remote Folder
```
Remote folder = Repository
Git -> Used locally to stage and push changes
GitHub -> Hosts the repository/folder online
```

## Git Version & Configuration
```bash
git --version
git config --global user.name "x"
git config --global user.email "x@gmail.com"
git config --list

#if i want to change name then
git config --global user.name "changed name"
git config --global --unset user.name "name"
```

## SSH Key Generate and Link
```bash
cd ~
ls -a
cd .ssh
.ssh % ssh-keygen -o -t rsa -C "x@gmail.com"
```

## Git Folder Create and Pull/Push
```bash
mkdir folder_name
cd folder
git init

git status
```

### Adding Files
```bash
git add filename           # Add single file
git add -A                 # Add all files including directories
git add .                  # Add all files in current folder
git add *.js               # Add all .js files
git add **/*.js            # Add all .js files recursively in subdirectories
```

### Restore or Unstage Files
```bash
git restore filename       # Restore file to last committed state
git rm --cached filename   # Unstage a file (remove from staging area)
```

### Check Differences
```bash
git diff                   # Show difference between working directory and staging area
git restore filename       # Revert changes in a file
```

## Git Commit and Uncommit
```bash
git commit -m "comment"    # Commit changes with a message
git status                 # Check current repository status
git log                    # Show all commit history
```

### Undo Commits
```bash
git reset --soft HEAD^      # Undo commit but keep changes staged
git reset HEAD^             # Undo commit and unstage changes
git reset --hard HEAD^      # Undo commit and discard all changes permanently
```

## Git Head and Undo
```bash
git log                     # Show complete commit history
git log --oneline           # Show commit history with short IDs
git show                    # Show latest commit details
git show commit_id          # Show specific commit details
git show HEAD~Number        # Show details of older commits (e.g., HEAD~2)
git checkout commitID       # Switch to specific commit (detached HEAD state)
git checkout master         # Return to master/main branch
```

## .gitignore
```bash
touch .gitignore
```

### Ignore Patterns
```
.env                      # Ignore .env file
*.file_extension          # Ignore all files with specific extension
!name.file_extension      # Exception: include this file even if extension is ignored
node_modules/             # Ignore entire node_modules folder
```

## Git Shortcuts & Aliases
```bash
git config --list
git config
git config --global alias.s "status"   # Now `git s` works as shortcut for `git status`
git config --global --unset alias.st   # Remove an existing alias
```

## Git Repository and Commit
```
GitHub account -> + -> New Repository -> Repository Name -> Description -> Private/Public -> Add README File -> Create Repository
```

## Connecting Local and Remote
```bash
git remote             # Check if any remote repository is connected
git remote add origin repo_url    # Connect local repo to remote repository
git remote -v          # Show verbose connection details with URLs
```

## Pull & Push
```bash
git push -u origin main    # Push changes to remote repository and set upstream
git pull                   # Fetch and merge changes from remote repository
```

## Branch & Merge
```
Master and Main refer to the default branch
To avoid directly adding unstable code to the main branch, create a separate branch first.
Make changes in the new branch, then merge it back to main after testing.
```

### Create & Switch Branch
```bash
git branch branch_name      # Create a new branch
git checkout branch_name    # Switch to the specified branch
# OR use combined command:
git checkout -b branch_name # Create and switch to new branch in one command
```

### Merge Branch into Master/Main
```bash
git checkout master         # Switch to master/main branch
git merge branch_name       # Merge the specified branch into current branch
```

## MD Crashcourse
```
# Markdown Basics

## Headers
# H1
## H2
### H3

## Text Formatting
**Bold** or __Bold__
*Italic* or _Italic_
~~Strikethrough~~

## Lists
- Unordered item
- Another item

1. Ordered item
2. Another item

## Links
[Link Text](https://example.com)

## Images
![Alt Text](image-url.jpg)

## Code
`inline code`
```code block```

## Tables
| Header 1 | Header 2 |
|----------|----------|
| Cell 1   | Cell 2   |
```
