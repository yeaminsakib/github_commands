# Git & GitHub Crash Course

## Remote Folder
```
Remote folder = Repository
Git -> locally ante pari and push korte parbo
GitHub -> Folder Host kore rakhe
```

## Git Version & Configuration
```bash
git --version
git config --global user.name "yeaminsakib"
git config --global user.email "yeaminsakib@gmail.com"
git config --list

git config --global user.name "changed name"
git config --global --unset user.name "name"
```

## SSH Key Generate and Link
```bash
cd ~
ls -a
cd .ssh
.ssh % ssh-keygen -o -t rsa -C "yeaminsakib@gmail.com"
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
git add .                  # Add all files in this folder
git add *.js               # Add all .js files
git add **/*.js            # Add all .js files recursively
```

### Restore or Unstage Files
```bash
git restore filename       # Restore file to last committed state
git rm --cached filename   # Unstage a file
```

### Check Differences
```bash
git diff                   # Show difference between files
git restore filename       # Revert changes in a file
```

## Git Commit and Uncommit
```bash
git commit -m "comment"    # Commit changes
git status                 # Check status
git log                    # Show all commits
```

### Undo Commits
```bash
git reset --soft HEAD^      # Undo commit but keep staged
git reset HEAD^             # Undo commit and unstage
git reset --hard HEAD^      # Undo commit and discard changes
```

## Git Head and Undo
```bash
git log                     # Show commit history
git log --oneline           # Show commit IDs in short format
git show                    # Show latest commit details
git show commit_id           # Show specific commit details
git show HEAD~Number         # Show older commit details
git checkout commitID        # Switch to specific commit
git checkout master          # Go back to master branch
```

## .gitignore
```bash
touch .gitignore
```

### Ignore Patterns
```
.env                      # Ignore .env folder
*.file_extension          # Ignore all files with this extension (.txt, .py, .js, etc.)
!name.file_extension      # Exception: include file even if extension ignored
node_modules/             # Ignore node_modules folder
```

## Git Shortcuts & Aliases
```bash
git config --list
git config
git config --global alias.s "status"   # Now `git s` = `git status`
git config --global --unset alias.st   # Remove alias
```

## Git Repository and Commit
```
GitHub account -> + -> New Repository -> Repository Name -> Description -> Private -> Add Readme File -> create Repository
```

## Connecting Local and Remote
```bash
git remote             # Check connected repo
git remote add origin repo_url
git remote -v          # Show verbose connection
```

## Pull & Push
```bash
git push -u origin main
git pull
```

## Branch & Merge
```
master or main are same
Master branch e shob add kora jabe na surutei jate problem na hoy..tai age new branch kore tate edit kore pore merge korbo main er sathe
```

### Create & Switch Branch
```bash
git branch branch_name      # Create new branch
git checkout branch_name    # Switch to branch
```

### Merge Branch into Master/Main
```bash
git checkout master
git merge branch_name
```

## MD Crashcourse
```
# (Placeholder for any additional Markdown course content)
```
