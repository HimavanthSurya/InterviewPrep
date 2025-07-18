# 1. How to create modules in README file

In this file we will document how to use markdown to create an engaging readme

# 2. What we will learn in this lesson

    - How to create a markdownfile
    - How to write markdown syntax
    - How to format code in markdown
    - How to embed images in markdown

# 3. Extensions we need are

1. _github_ markdown preview by Marr Briener
2. Markdown Emoji by Matt Briener

# Emoji link

You can find all the emoji's here:

<https://www.webfx.com/tools/emoji-cheat-sheet/>

# Other Markdown Editors we can use

1. Mac : **MacDown**
2. Windows : **ghostwriter** or **MarkdownEditor**

# Git Commands for Real-Time Projects - Complete Guide

## 1. Initial Setup & Configuration

### First-time Git Setup

```bash
# Set your identity (required for commits)
git config --global user.name "John Doe"
git config --global user.email "john.doe@company.com"

# Set default branch name
git config --global init.defaultBranch main

# Set default editor
git config --global core.editor "code --wait"  # VS Code
git config --global core.editor "vim"          # Vim

# Configure line ending handling
git config --global core.autocrlf true   # Windows
git config --global core.autocrlf input  # Mac/Linux

# Set pull strategy
git config --global pull.rebase true

# View all configurations
git config --list
```

### SSH Key Setup (for secure authentication)

```bash
# Generate SSH key
ssh-keygen -t rsa -b 4096 -C "your.email@company.com"

# Add SSH key to SSH agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa

# Copy public key to clipboard (add to GitHub/GitLab)
cat ~/.ssh/id_rsa.pub
```

## 2. Repository Setup

### Cloning Existing Repository

```bash
# Clone repository
git clone https://github.com/company/ecommerce-api.git
cd ecommerce-api

# Clone specific branch
git clone -b develop https://github.com/company/ecommerce-api.git

# Clone with SSH
git clone git@github.com:company/ecommerce-api.git
```

### Initialize New Repository

```bash
# Initialize new repository
git init

# Add remote origin
git remote add origin https://github.com/company/new-project.git

# Verify remotes
git remote -v
```

## 3. Daily Development Workflow

### Starting a New Feature

```bash
# Check current status
git status

# Pull latest changes from main
git checkout main
git pull origin main

# Create and switch to feature branch
git checkout -b feature/user-authentication

# Alternative: Create branch and switch
git branch feature/user-authentication
git checkout feature/user-authentication

# Push new branch to remote
git push -u origin feature/user-authentication
```

### Making Changes

```bash
# Check what files changed
git status

# See detailed changes
git diff

# See changes in a specific file
git diff src/controllers/UserController.cs

# Stage specific files
git add src/controllers/UserController.cs
git add src/models/User.cs

# Stage all changes
git add .

# Stage all tracked files (excluding new files)
git add -u

# Interactive staging
git add -i
```

### Committing Changes

```bash
# Commit with message
git commit -m "feat: implement user authentication with JWT"

# Commit with detailed message
git commit -m "feat: implement user authentication

- Add JWT token generation
- Implement login/logout endpoints
- Add password hashing with bcrypt
- Update user model with authentication fields

Closes #123"

# Commit all tracked changes (skip staging)
git commit -a -m "fix: resolve login validation issue"

# Amend last commit (if not pushed yet)
git commit --amend -m "feat: implement user authentication with JWT tokens"
```

## 4. Branch Management

### Working with Branches

```bash
# List all branches
git branch

# List remote branches
git branch -r

# List all branches (local + remote)
git branch -a

# Create new branch
git branch feature/payment-integration

# Switch to branch
git checkout feature/payment-integration

# Create and switch in one command
git checkout -b feature/order-management

# Switch to previous branch
git checkout -

# Delete local branch
git branch -d feature/completed-feature

# Force delete branch
git branch -D feature/abandoned-feature

# Delete remote branch
git push origin --delete feature/old-feature
```

### Syncing with Remote

```bash
# Fetch latest changes (doesn't merge)
git fetch origin

# Pull latest changes (fetch + merge)
git pull origin main

# Pull with rebase (cleaner history)
git pull --rebase origin main

# Push current branch
git push origin feature/user-authentication

# Push and set upstream
git push -u origin feature/user-authentication

# Push all branches
git push origin --all

# Push tags
git push origin --tags
```

## 5. Code Review Process

### Creating Pull Request (Command line prep)

```bash
# Make sure branch is up to date
git checkout feature/user-authentication
git pull origin main
git rebase main

# Push final changes
git push origin feature/user-authentication

# Create PR using GitHub CLI (if installed)
gh pr create --title "feat: implement user authentication" --body "Detailed description"
```

### Addressing Review Comments

```bash
# Make changes based on review
git add .
git commit -m "fix: address review comments

- Fix variable naming
- Add input validation
- Update error messages"

# Push changes
git push origin feature/user-authentication

# Interactive rebase to clean up commits (if needed)
git rebase -i HEAD~3  # Rebase last 3 commits
```

## 6. Merging & Integration

### Merging Feature Branch

```bash
# Switch to main branch
git checkout main

# Pull latest changes
git pull origin main

# Merge feature branch
git merge feature/user-authentication

# Merge with no fast-forward (preserves branch history)
git merge --no-ff feature/user-authentication

# Push merged changes
git push origin main

# Delete feature branch after merge
git branch -d feature/user-authentication
git push origin --delete feature/user-authentication
```

### Squash Merge (for cleaner history)

```bash
# Squash merge feature branch
git checkout main
git merge --squash feature/user-authentication
git commit -m "feat: implement user authentication

Complete implementation of JWT-based authentication system"
```

## 7. Resolving Conflicts

### Merge Conflicts

```bash
# When merge conflicts occur
git status  # Shows conflicted files

# Edit conflicted files manually, then:
git add conflicted-file.cs

# Continue merge
git commit

# Abort merge if needed
git merge --abort
```

### Rebase Conflicts

```bash
# During rebase conflicts
git status

# Edit conflicted files, then:
git add conflicted-file.cs
git rebase --continue

# Skip current commit during rebase
git rebase --skip

# Abort rebase
git rebase --abort
```

## 8. Advanced Git Operations

### Stashing Changes

```bash
# Stash current changes
git stash

# Stash with message
git stash save "WIP: working on user validation"

# List stashes
git stash list

# Apply latest stash
git stash apply

# Apply specific stash
git stash apply stash@{2}

# Pop stash (apply and remove)
git stash pop

# Drop stash
git stash drop stash@{1}

# Clear all stashes
git stash clear
```

### Cherry-picking

```bash
# Apply specific commit to current branch
git cherry-pick abc123def

# Cherry-pick multiple commits
git cherry-pick abc123def def456ghi

# Cherry-pick with new commit message
git cherry-pick -e abc123def
```

### Rebasing

```bash
# Rebase current branch onto main
git rebase main

# Interactive rebase (clean up commit history)
git rebase -i HEAD~3

# Rebase onto specific commit
git rebase abc123def

# Continue rebase after resolving conflicts
git rebase --continue

# Abort rebase
git rebase --abort
```

## 9. Release Management

### Tagging Releases

```bash
# Create annotated tag
git tag -a v1.2.0 -m "Release version 1.2.0"

# Create lightweight tag
git tag v1.2.0

# Tag specific commit
git tag -a v1.1.9 abc123def -m "Hotfix release"

# List tags
git tag

# Show tag details
git show v1.2.0

# Push tags
git push origin v1.2.0
git push origin --tags

# Delete tag
git tag -d v1.2.0
git push origin :refs/tags/v1.2.0
```

### Release Branch Workflow

```bash
# Create release branch
git checkout -b release/v1.2.0 develop

# Make final adjustments
git commit -m "chore: bump version to 1.2.0"

# Merge to main
git checkout main
git merge --no-ff release/v1.2.0

# Tag release
git tag -a v1.2.0 -m "Release version 1.2.0"

# Merge back to develop
git checkout develop
git merge --no-ff release/v1.2.0

# Clean up
git branch -d release/v1.2.0
```

## 10. Hotfix Workflow

### Creating Hotfix

```bash
# Create hotfix branch from main
git checkout main
git checkout -b hotfix/critical-security-fix

# Make fix
git add .
git commit -m "hotfix: fix critical security vulnerability

- Sanitize user input
- Add XSS protection
- Update validation rules"

# Merge to main
git checkout main
git merge --no-ff hotfix/critical-security-fix

# Tag hotfix
git tag -a v1.2.1 -m "Hotfix version 1.2.1"

# Merge to develop
git checkout develop
git merge --no-ff hotfix/critical-security-fix

# Clean up
git branch -d hotfix/critical-security-fix
git push origin main develop
git push origin v1.2.1
```

## 11. Debugging & History

### Viewing History

```bash
# View commit history
git log

# Compact log
git log --oneline

# Graphical log
git log --graph --oneline --all

# Show changes in each commit
git log -p

# Show specific number of commits
git log -5

# Show commits by author
git log --author="John Doe"

# Show commits for specific file
git log -- src/controllers/UserController.cs

# Show commits in date range
git log --since="2024-01-01" --until="2024-01-31"
```

### Finding Issues

```bash
# Show who modified each line
git blame src/controllers/UserController.cs

# Find commits that introduced specific text
git log -S "authentication" --oneline

# Find commits with specific message
git log --grep="authentication"

# Show changes between commits
git diff abc123def..def456ghi

# Show changes between branches
git diff main..feature/user-auth
```

### Undoing Changes

```bash
# Unstage file
git reset HEAD src/controllers/UserController.cs

# Discard changes in working directory
git checkout -- src/controllers/UserController.cs

# Reset to specific commit (keep changes)
git reset --soft abc123def

# Reset to specific commit (discard changes)
git reset --hard abc123def

# Revert specific commit (creates new commit)
git revert abc123def

# Reset file to specific commit
git checkout abc123def -- src/controllers/UserController.cs
```

## 12. Collaboration Commands

### Working with Team

```bash
# Add team member's fork as remote
git remote add teammate https://github.com/teammate/project.git

# Fetch their changes
git fetch teammate

# Create branch from their work
git checkout -b review-teammate-feature teammate/feature-branch

# Compare branches
git diff main..teammate/feature-branch

# Merge their changes
git merge teammate/feature-branch
```

### Submodules (for large projects)

```bash
# Add submodule
git submodule add https://github.com/company/shared-library.git lib/shared

# Initialize submodules after cloning
git submodule init
git submodule update

# Update submodules
git submodule update --remote

# Clone repository with submodules
git clone --recurse-submodules https://github.com/company/main-project.git
```

## 13. Useful Aliases

### Set up Git Aliases

```bash
# Common aliases
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
git config --global alias.pushup 'push -u origin HEAD'
git config --global alias.lg 'log --oneline --graph --all'
```

## 14. Git Hooks (Automation)

### Pre-commit Hook Example

```bash
#!/bin/sh
# .git/hooks/pre-commit

# Run tests before commit
npm test
if [ $? -ne 0 ]; then
    echo "Tests failed. Commit aborted."
    exit 1
fi

# Run linting
npm run lint
if [ $? -ne 0 ]; then
    echo "Linting failed. Commit aborted."
    exit 1
fi
```

## 15. Emergency Commands

### When Things Go Wrong

```bash
# Recover deleted branch
git reflog
git checkout -b recovered-branch abc123def

# Recover from accidental reset
git reflog
git reset --hard HEAD@{1}

# Find lost commits
git fsck --lost-found

# Remove file from Git history
git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch secrets.json' --prune-empty --tag-name-filter cat -- --all
```

## 16. Best Practices Summary

### Daily Commands Checklist

```bash
# Morning routine
git checkout main
git pull origin main
git checkout -b feature/new-feature

# During development
git add .
git commit -m "descriptive message"
git push origin feature/new-feature

# Before creating PR
git checkout main
git pull origin main
git checkout feature/new-feature
git rebase main
git push origin feature/new-feature

# After PR approval
git checkout main
git pull origin main
git branch -d feature/new-feature
```

This comprehensive guide covers the essential Git commands used in real-time enterprise projects, from basic daily workflows to advanced scenarios and emergency recovery procedures.
