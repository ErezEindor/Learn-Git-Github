# Git & GitHub Exercises

These exercises will help you understand Git basics and how to work with Pull Requests on GitHub. Each exercise builds on the previous one, helping you learn essential Git concepts.

## Exercise 1: Basic Git Commands

**Goal**: Learn the basic Git workflow and essential commands.

**Tasks**:
1. Create a new branch
   ```bash
   # Create and switch to a new branch
   git switch -c feature/my-first-branch
   ```

2. Make changes
   - Create a new file called `hello.txt`
   - Add some text to it: "Hello, this is my first Git exercise!"

3. Stage and commit your changes
   ```bash
   # Check status to see your changes
   git status

   # Add your file to staging
   git add hello.txt

   # Commit your changes with a message
   git commit -m "Add hello.txt file"
   ```

4. Push your changes
   ```bash
   # Push your branch to GitHub
   git push -u origin feature/my-first-branch
   ```

## Exercise 2: Creating Your First Pull Request

**Goal**: Learn how to create and manage a Pull Request on GitHub.

**Tasks**:
1. Go to your repository on GitHub
   - Click on "Pull Requests"
   - Click "New Pull Request"

2. Set up your PR
   - Select your branch (`feature/my-first-branch`) as the source
   - Select `main` as the target branch
   - Click "Create Pull Request"

3. Fill in PR details
   ```markdown
   Title: Add hello.txt file
   
   Description:
   - Created new hello.txt file
   - Added welcome message
   ```

4. Submit and review your PR
   - Look at the "Files changed" tab to see your changes
   - Wait for review or merge if you have permission

## Exercise 3: Collaborative Work with Git

**Goal**: Practice working with others' code and handling updates.

**Tasks**:
1. Update your local main branch
   ```bash
   # Switch to main branch
   git switch main

   # Get latest changes
   git pull origin main
   ```

2. Create a new feature branch
   ```bash
   # Create new branch from updated main
   git switch -c feature/add-readme
   ```

3. Make changes
   - Create a README.md file with:
   ```markdown
   # My Project
   This is a practice repository for learning Git and GitHub.
   ```

4. Create a PR with multiple commits
   ```bash
   # Add and commit README
   git add README.md
   git commit -m "Add basic README"

   # Update README and make another commit
   # (Add more content to README.md first)
   git add README.md
   git commit -m "Update README with more details"

   # Push changes
   git push -u origin feature/add-readme
   ```

5. Create PR on GitHub following same steps as Exercise 2

**Tips for Success**:
- Always check your current branch with `git status`
- Write clear commit messages
- Review your changes before committing
- Keep PRs focused on one task
- Respond to review comments if you get any

**Common Commands Reference**:
```bash
# Check status
git status

# Create new branch
git switch -c branch-name

# Switch branches
git switch branch-name

# Stage changes
git add filename

# Commit changes
git commit -m "message"

# Push changes
git push -u origin branch-name

# Get latest changes
git pull origin branch-name

# See commit history
git log
```

Remember:
1. Keep your commits small and focused
2. Write descriptive commit messages
3. Review your PR before submitting
4. Ask for help if you get stuck!

## Oh My Zsh Git Cheatsheet

Oh My Zsh provides many helpful aliases for Git commands. Here are the most commonly used ones:

### Basic Commands
```bash
g       = git
gst     = git status
gl      = git pull
gup     = git pull --rebase
gp      = git push
gd      = git diff
gdc     = git diff --cached
gdca    = git diff --cached
gdcw    = git diff --cached --word-diff
```

### Branches
```bash
gb      = git branch
gba     = git branch -a
gbd     = git branch -d
gbD     = git branch -D
gco     = git checkout
gcb     = git checkout -b
gsw     = git switch
gswc    = git switch -c
```

### Adding Files
```bash
ga      = git add
gaa     = git add --all
gapa    = git add --patch
```

### Committing
```bash
gc      = git commit -v
gc!     = git commit -v --amend
gcn!    = git commit -v --no-edit --amend
gca     = git commit -v -a
gcam    = git commit -a -m
gcmsg   = git commit -m
```

### Fetching & Merging
```bash
gf      = git fetch
gfa     = git fetch --all --prune
gfo     = git fetch origin
gm      = git merge
gmom    = git merge origin/main
gmum    = git merge upstream/main
```

### Stashing
```bash
gsta    = git stash push
gstaa   = git stash apply
gstd    = git stash drop
gstl    = git stash list
gstp    = git stash pop
```

### Logs & History
```bash
glg     = git log --stat
glgg    = git log --graph
glgga   = git log --graph --decorate --all
glgm    = git log --graph --max-count=10
glod    = git log --graph --pretty='%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%ad) %C(bold blue)<%an>%Creset'
glog    = git log --oneline --decorate --graph
```

### Remote Repositories
```bash
gr      = git remote
gra     = git remote add
grmv    = git remote rename
grset   = git remote set-url
grup    = git remote update
grv     = git remote -v
```

### Common Workflows
```bash
# Create and switch to new branch
gswc feature/new-branch

# Stage all changes and commit
gaa && gcmsg "Your commit message"

# Push new branch to remote
gp -u origin feature/new-branch

# Update branch with main
gco main && gl && gco - && gm main

# Quick status check and add
gst && gaa

# View branch history
glod
```

### Tips for Using Oh My Zsh Git Aliases
1. Use `gst` frequently to check your status
2. `gaa && gcmsg "message"` for quick commits
3. `gco -` to switch to previous branch
4. `glod` for a nice graphical log view
5. `gp -u origin $(current_branch)` to push new branch

These aliases can significantly speed up your Git workflow once you're comfortable with them. Start with a few common ones and gradually incorporate more as you get comfortable.