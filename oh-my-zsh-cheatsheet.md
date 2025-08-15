# Oh My Zsh Cheatsheet

## Table of Contents
- [Git Commands](#git-commands)
  - [Essential Git Commands](#essential-git-commands)
  - [Branch Operations](#branch-operations)
  - [Staging and Committing](#staging-and-committing)
  - [Fetching and Merging](#fetching-and-merging)
  - [Stashing](#stashing)
  - [History and Logs](#history-and-logs)
  - [Remote Operations](#remote-operations)
  - [Common Git Workflows](#common-workflows)
  - [Git Tips and Tricks](#git-tips-and-tricks)
- [Shell Navigation](#shell-navigation)
  - [Directory Movement](#directory-movement)
  - [Directory Stack](#directory-stack)
  - [Directory Shortcuts](#directory-shortcuts)
- [File Operations](#file-operations)
  - [Listing Files](#listing-files)
  - [File Management](#file-management)
- [Shell Features](#shell-features)
  - [History Commands](#history-commands)
  - [Auto-Completion](#auto-completion)
  - [Process Management](#process-management)
- [Oh My Zsh Management](#oh-my-zsh-management)
  - [Plugin Management](#plugin-management)
  - [Theme Management](#theme-management)
  - [Configuration](#configuration)
  - [Troubleshooting](#troubleshooting)

## Git Commands

### Essential Git Commands
```bash
# Most Frequently Used Commands
gst     = git status              # Check repository status
ga      = git add                 # Stage a file
gaa     = git add --all          # Stage all changes
gcmsg   = git commit -m          # Commit with message
gp      = git push               # Push changes
gl      = git pull               # Pull changes
gd      = git diff               # View changes
gdc     = git diff --cached      # View staged changes

# Quick Combinations
gaa && gcmsg "message"           # Stage all and commit
gst && gaa && gcmsg "message"    # Check, stage all, and commit
```

### Branch Operations
```bash
# Viewing Branches
gb      = git branch             # List local branches
gba     = git branch -a          # List all branches (including remote)

# Branch Management
gsw     = git switch             # Switch branches (new syntax)
gswc    = git switch -c          # Create and switch to new branch
gco     = git checkout           # Switch branches (old syntax)
gcb     = git checkout -b        # Create and checkout branch
gbd     = git branch -d          # Delete branch (safe)
gbD     = git branch -D          # Force delete branch
```

### Staging and Committing
```bash
# Basic Staging
ga      = git add                # Stage specific files
gaa     = git add --all          # Stage all changes
gapa    = git add --patch        # Interactive staging

# Committing
gcmsg   = git commit -m          # Commit with message
gc      = git commit -v          # Commit with verbose diff
gc!     = git commit --amend     # Amend last commit
gcn!    = git commit --no-edit --amend  # Amend without editing
```

### Fetching and Merging
```bash
# Fetching Updates
gf      = git fetch              # Fetch changes
gfa     = git fetch --all        # Fetch from all remotes
gfo     = git fetch origin       # Fetch from origin

# Merging
gm      = git merge              # Merge branch
gmom    = git merge origin/main  # Merge origin/main
gm -    = git merge -            # Merge previous branch
```

### Common Workflows

1. **Start New Feature**
   ```bash
   gco main          # Switch to main branch
   gl                # Pull latest changes
   gswc feature/xyz  # Create and switch to feature branch
   ```

2. **Regular Development Cycle**
   ```bash
   gst               # Check status
   gd                # Review changes
   gaa               # Stage all changes
   gcmsg "feat: X"   # Commit with message
   ```

3. **Update Feature Branch**
   ```bash
   gco main          # Switch to main
   gl                # Pull changes
   gco -             # Return to feature branch
   gm main           # Merge main into feature
   ```

4. **Publish Changes**
   ```bash
   # First time pushing branch
   gp -u origin $(current_branch)
   
   # Subsequent pushes
   gp
   ```

### Git Tips and Tricks

1. **Safety First**
   - Always `gst` before any major operation
   - Use `gd` to review changes before staging
   - Prefer `gbd` (safe delete) over `gbD` (force delete)

2. **Quick Operations**
   - `gco -` to switch to previous branch
   - `gaa && gcmsg` for quick commit
   - `gm -` to merge from previous branch

3. **History Review**
   - `glod` for pretty graph view
   - `glg` for detailed stats
   - `glog` for compact graph

[Rest of the document continues with Shell Navigation, etc...]