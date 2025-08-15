# Learn-Git-Github

This repository is part of a Git & GitHub bootcamp. It is designed to help you learn and practice essential Git and GitHub commands, including pushing, pulling, branching, and collaborating on projects.

## Table of Contents
- [Project Description](#project-description)
- [Git Basics: Add and Commit](#git-basics-add-and-commit)
- [Repository History](#repository-history)
  - [Git Log: Viewing History](#git-log-viewing-history)
  - [Undoing Changes](#undoing-changes)
- [Remote Operations](#remote-operations)
  - [Authentication Setup](#authentication-setup)
  - [Pushing Code](#pushing-code)
  - [Fetching and Pulling](#fetching-and-pulling)
- [Branch Management](#branch-management)
  - [Branch Operations](#branch-operations)
  - [Best Practices for Branch Management](#best-practices-for-branch-management)
- [Merging and Collaboration](#merging-and-collaboration)
  - [Types of Merges](#types-of-merges)
  - [Handling Merge Conflicts](#handling-merge-conflicts)
  - [Pull Request Workflow](#pull-request-workflow)
- [Advanced Git](#advanced-git)
  - [Git Stash](#git-stash)
  - [Git Rebase](#git-rebase)
  - [Git Tags](#git-tags)
  - [Git Hooks](#git-hooks)
- [Best Practices and Workflows](#best-practices-and-workflows)
  - [Commit Message Conventions](#commit-message-conventions)
  - [Git Workflow Strategies](#git-workflow-strategies)
  - [Code Review Guidelines](#code-review-guidelines)
- [Troubleshooting](#troubleshooting)
  - [Common Issues](#common-issues)
  - [Error Messages](#error-messages)


## Project Description

The goal of this bootcamp is to provide hands-on experience with Git and GitHub, enabling you to:
- Understand version control concepts.
- Work with repositories locally and remotely.
- Collaborate effectively using GitHub.

Feel free to explore the repository and practice the commands!


## Git Basics: Add and Commit

This section provides an overview of essential Git commands you'll use frequently during this bootcamp.

### Workflow Overview
1. **Create a Local Repository**:
   - Use `git init` to initialize an empty repository.
   - Verify the repository status with `git status`.

2. **Add Files to the Staging Area**:
   - Add individual files: `git add <filename>`.
   - Add multiple files: `git add <file1> <file2>`.
   - Add all changes: `git add .`.

3. **Commit Changes to the Repository**:
   - Commit staged changes with a message: `git commit -m "Your commit message"`.
   - Ensure commit messages are clear and concise to help track changes.

### Editing Files
- Modify files and check their status with `git status`.
- Stage modified files using `git add <filename>`.
- Commit changes with a descriptive message.

### Tools and Recommendations
- Use **Visual Studio Code** for editing and tracking changes.
  - It integrates well with Git and GitHub, especially for Windows users.
  - Open your terminal within VS Code for seamless workflow.

### Example Workflow
1. Create a new file (`file1.txt`) and add content.
2. Stage the file: `git add file1.txt`.
3. Commit the file: `git commit -m "Added file1.txt"`.
4. Push changes to GitHub 

### Git Log: Viewing Commit History

The `git log` command allows you to view the history of all commits made to a repository. It displays useful information such as:
- The commit hash
- The author (name and email)
- The date of the commit
- The commit message

#### Example Usage
1. Run the following command to view the commit history:
   ```bash
   git log
   ```
   This will display a list of commits, including metadata and messages.

2. Navigate through the log:
   - Press `Enter` to scroll through the log.
   - Type `q` to exit the log view.

#### Why Use Git Log?
- Understand the history of changes in your repository.
- Track who made specific changes and when.
- Review commit messages for context on past updates.

### Undoing Changes

Git provides several ways to undo changes, each serving a different purpose:

#### Discarding Uncommitted Changes
```bash
# Discard changes in working directory
git restore <file>

# Discard changes in staging area
git restore --staged <file>

# Discard all local changes
git restore .
```

#### Modifying Commits
```bash
# Modify the last commit
git commit --amend

# Modify the last commit message
git commit --amend -m "New message"

# Add files to the last commit
git add <forgotten-file>
git commit --amend --no-edit
```

#### Reverting Commits
```bash
# Create a new commit that undoes a previous commit
git revert <commit-hash>

# Revert the last commit
git revert HEAD
```

#### Reset Operations
```bash
# Soft reset - move HEAD but keep changes staged
git reset --soft HEAD~1

# Mixed reset - move HEAD and unstage changes (default)
git reset HEAD~1

# Hard reset - move HEAD and discard all changes
git reset --hard HEAD~1
```

⚠️ **Warning**: Be careful with `reset --hard` as it permanently discards changes!

#### Best Practices for Undoing Changes
1. **Before Undoing**:
   - Always ensure you have a clean working directory
   - Create a backup branch if unsure
   - Understand which changes will be affected

2. **Choosing the Right Command**:
   - Use `restore` for uncommitted changes
   - Use `revert` for committed changes that are already pushed
   - Use `reset` for local commits only
   - Use `commit --amend` only for the last commit

3. **Safety Measures**:
   - Avoid `reset --hard` on shared branches
   - Prefer `revert` over `reset` for public changes
   - Always verify the commit hash before reverting

### Pushing Code to a Remote Branch

This section explains how to push your local code to a remote branch on GitHub.

#### Workflow Overview
1. **Check for Remote Branches**:
   - Use `git remote -v` to view connected remote branches and their URLs.
   - If no remote branch is connected, you won’t see any output.

2. **Add a Remote Branch**:
   - Connect your local repository to a remote branch:
     ```bash
     git remote add origin <repository-URL>
     ```
   - By convention, the remote branch is named `origin`.

3. **Push Local Code to the Remote Branch**:
   - Push your commits to the remote branch:
     ```bash
     git push -u origin main
     ```
   - Replace `main` with `master` if your local branch is named `master`.

#### Notes on Branch Naming
- GitHub has transitioned from using `master` to `main` as the default branch name.
- You can rename your branch locally using:
  ```bash
  git branch -M main
  ```

#### Additional Commands
- **Rename a Remote Branch**:
  ```bash
  git remote rename <old-name> <new-name>
  ```
- **Remove a Remote Branch**:
  ```bash
  git remote remove <name>
  ```

#### Using Personal Access Tokens
- If you encounter permission errors, include your personal access token in the repository URL when adding the remote branch.

#### Using SSH for Authentication
- To securely connect your local repository to GitHub, use SSH instead of Personal Access Tokens.
- First, ensure your SSH key is added to your GitHub account. You can generate an SSH key using:
  ```bash
  ssh-keygen -t ed25519 -C "your_email@example.com"
  ```
- Add the SSH key to your GitHub account by copying the public key (`~/.ssh/id_ed25519.pub`) and pasting it into your GitHub SSH settings.

#### Adding a Remote Branch with SSH
- Use the following command to add a remote branch with SSH:
  ```bash
  git remote add origin git@github.com:<username>/<repository-name>.git
  ```
- Replace `<username>` and `<repository-name>` with your GitHub username and repository name.

#### Push Local Code to the Remote Branch
- Push your commits to the remote branch using SSH:
  ```bash
  git push -u origin main
  ```
- Replace `main` with `master` if your local branch is named `master`.

## Branch Management

Managing branches effectively is crucial for maintaining a clean and organized Git repository. This section covers essential branch operations including creation, renaming, and deletion.

### Branch Operations

#### Creating Branches
```bash
# Create and switch to a new branch
git switch -c <new-branch-name>

# Alternative method (legacy)
git checkout -b <new-branch-name>
```

#### Renaming Branches
1. **Switch to the branch you want to rename**:
   ```bash
   git switch <branch-to-rename>
   ```

2. **Rename the current branch**:
   ```bash
   git branch -m <new-name>
   ```

   Note: You must be checked out on the branch you wish to rename.

#### Deleting Branches

1. **Switch to a different branch first**:
   ```bash
   git switch main  # or any branch other than the one you want to delete
   ```

2. **Delete a fully merged branch**:
   ```bash
   git branch -d <branch-name>
   ```

3. **Force delete an unmerged branch**:
   ```bash
   git branch -D <branch-name>
   ```

   Warning: Using `-D` will delete the branch regardless of its merge status. Make sure you want to discard any unmerged changes.

### Best Practices for Branch Management

1. **Branch Naming Conventions**:
   - Use descriptive names that reflect the purpose
   - Use hyphens or underscores to separate words
   - Consider prefixes like:
     - `feature/` for new features
     - `bugfix/` for bug fixes
     - `hotfix/` for urgent fixes
     - `release/` for release branches

2. **Branch Lifecycle**:
   - Create branches for specific purposes
   - Keep branches short-lived when possible
   - Delete branches after merging to maintain a clean repository
   - Regularly update branches with changes from main/master

3. **Safety Measures**:
   - Never delete a branch while checked out to it
   - Always verify the merge status before deletion
   - Use `-d` instead of `-D` as a safe default
   - Keep your local branch list clean by removing merged branches

## Merging Branches

Understanding how to merge branches is crucial for collaborative development. This section covers different types of merges and how to handle merge conflicts.

### Types of Merges

#### Fast-Forward Merge
A fast-forward merge occurs when the target branch has no new commits since the feature branch was created.

```bash
# Switch to the target branch (e.g., main)
git switch main

# Merge the feature branch
git merge feature-branch
```

Example scenario:
```
Before merge:
main    A---B
             \
feature       C---D

After merge:
main    A---B---C---D
                    |
feature            D
```

#### Three-Way Merge
When both branches have diverged (have unique commits), Git creates a new merge commit.

```bash
# Switch to the target branch
git switch main

# Merge the feature branch
git merge feature-branch
```

Example scenario:
```
Before merge:
main    A---B---C
             \
feature       D---E

After merge:
main    A---B---C---F
             \     /
feature       D---E
```

### Handling Merge Conflicts

Merge conflicts occur when Git cannot automatically resolve differences between branches. Here's how to handle them:

1. **Identifying Conflicts**
   - Git marks conflicts in files using special syntax:
   ```
   <<<<<<< HEAD
   Current branch content
   =======
   Incoming branch content
   >>>>>>> feature-branch
   ```

2. **Resolving Conflicts**
   - Open the conflicted files in your editor
   - Look for the conflict markers (<<<<<<, =======, >>>>>>>)
   - Choose which changes to keep or combine them
   - Remove the conflict markers
   - Save the files

3. **Completing the Merge**
   ```bash
   # After resolving conflicts
   git add <resolved-files>
   git commit -m "Merge feature-branch: Resolve conflicts"
   ```

### Best Practices for Merging

1. **Before Merging**
   - Ensure your working directory is clean
   - Pull latest changes from the target branch
   - Test your changes thoroughly
   - Review the changes to be merged

2. **During Merge Conflicts**
   - Communicate with team members about conflicting changes
   - Take time to understand both versions
   - Consider using visual merge tools
   - Keep the final code functional and clean

3. **After Merging**
   - Verify the merged code works as expected
   - Run tests to ensure nothing broke
   - Push the merged changes
   - Delete the merged feature branch if no longer needed

### Pull Request Workflow

Pull Requests (PRs) are a key feature of collaborative development, allowing team members to review, discuss, and improve code before it's merged into the main codebase.

#### Creating a Pull Request

1. **Prepare Your Branch**:
   ```bash
   # Create and switch to a feature branch
   git switch -c feature/new-feature

   # Make your changes and commit them
   git add .
   git commit -m "Implement new feature"

   # Push to remote repository
   git push -u origin feature/new-feature
   ```

2. **Create PR on GitHub**:
   - Go to your repository on GitHub
   - Click "Pull Requests" → "New Pull Request"
   - Select your feature branch as the source
   - Select the target branch (usually `main` or `develop`)
   - Click "Create Pull Request"

#### Writing Good PR Descriptions

1. **Title**:
   - Clear and concise
   - Start with type: `feat:`, `fix:`, `docs:`, etc.
   - Example: `feat: Add user authentication system`

2. **Description Template**:
   ```markdown
   ## Changes Made
   - Implemented X feature
   - Updated Y configuration
   - Fixed Z bug

   ## Testing Done
   - Unit tests added for X
   - Manual testing performed for Y
   - Integration tests updated

   ## Screenshots/Videos
   [If applicable]

   ## Related Issues
   Closes #123
   Related to #456
   ```

#### Reviewing Pull Requests

1. **As a Reviewer**:
   - Check out the PR branch locally:
     ```bash
     git fetch origin
     git switch pull-request-branch
     ```
   - Review code changes:
     - Code quality and style
     - Test coverage
     - Documentation
     - Performance implications
   - Provide constructive feedback
   - Approve or request changes

2. **As an Author**:
   - Respond to feedback promptly
   - Make requested changes:
     ```bash
     # Make changes
     git commit -m "Address PR feedback"
     git push
     ```
   - Resolve conversations
   - Request re-review when ready

#### PR Best Practices

1. **Size and Scope**:
   - Keep PRs focused and small
   - One feature/fix per PR
   - Split large changes into multiple PRs

2. **Quality Checks**:
   - Run tests before submitting
   - Ensure CI/CD checks pass
   - Follow code style guidelines
   - Update documentation

3. **Communication**:
   - Be responsive to feedback
   - Tag relevant team members
   - Use clear and professional language
   - Link to related issues/PRs

4. **Merging Strategy**:
   - Prefer "Squash and Merge" for clean history
   - Use "Rebase and Merge" for linear history
   - Delete branch after merging

#### Common PR Workflows

1. **Feature Development**:
   ```bash
   git switch -c feature/new-feature
   # Make changes
   git commit -m "Implement feature"
   git push -u origin feature/new-feature
   # Create PR on GitHub
   ```

2. **Bugfix**:
   ```bash
   git switch -c fix/bug-description
   # Fix bug
   git commit -m "Fix: Description"
   git push -u origin fix/bug-description
   # Create PR on GitHub
   ```

3. **Updating PR After Review**:
   ```bash
   # Make requested changes
   git add .
   git commit -m "Address PR feedback"
   git push
   ```

4. **Syncing with Base Branch**:
   ```bash
   git switch feature/branch
   git fetch origin
   git rebase origin/main
   git push --force-with-lease
   ```

#### Handling PR Conflicts

1. **Local Resolution**:
   ```bash
   git fetch origin
   git switch feature-branch
   git rebase origin/main
   # Resolve conflicts
   git add .
   git rebase --continue
   git push --force-with-lease
   ```

2. **Using GitHub Interface**:
   - Click "Resolve Conflicts" button
   - Edit files in GitHub editor
   - Commit changes when done

#### Security Considerations

1. **Before Submitting**:
   - Remove sensitive data
   - Check for hardcoded credentials
   - Verify dependency updates

2. **During Review**:
   - Check for security vulnerabilities
   - Validate input handling
   - Review authentication/authorization changes