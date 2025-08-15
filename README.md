# Learn-Git-Github

This repository is part of a Git & GitHub bootcamp. It is designed to help you learn and practice essential Git and GitHub commands, including pushing, pulling, branching, and collaborating on projects.

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

### Understanding HEAD and Branches in Git

#### What is HEAD?
- **HEAD** is a reference to the current commit or branch you are working on.
- It points to the latest commit in the branch you have checked out.
- Example: When working on the `master` branch, HEAD points to the most recent commit in `master`.

#### How HEAD Works with Branches
- Branches are references to specific commits in the repository.
- HEAD tells you which branch you are currently working on.
- When you switch branches, HEAD updates to point to the new branch.

#### Key Commands for HEAD and Branches
1. **Check the Current HEAD**:
   - Use `git log` to see the current HEAD and its associated branch:
     ```bash
     git log
     ```

2. **Switch HEAD to Another Branch**:
   - Use `git checkout` or `git switch` to move HEAD to a different branch:
     ```bash
     git checkout <branch-name>
     ```
     Or:
     ```bash
     git switch <branch-name>
     ```

3. **Create a New Branch and Update HEAD**:
   - Create a new branch and switch HEAD to it:
     ```bash
     git branch <new-branch-name>
     git switch <new-branch-name>
     ```

4. **Return HEAD to the Master/Main Branch**:
   - Switch back to the `master` or `main` branch:
     ```bash
     git switch master
     ```

#### Why HEAD Matters
- HEAD helps you understand which branch you are currently working on.
- It ensures that new commits are added to the correct branch.
- You can easily switch between branches to work on different features or versions of the codebase.
