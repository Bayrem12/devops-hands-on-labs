# Git Fundamentals & Remote Repositories

## 1. Git Workflow

**What it is:** Git tracks changes through three main areas.

| Area | Purpose |
|---|---|
| Working Directory | Where files are modified |
| Staging Area | Changes prepared for the next commit |
| Local Repository | Stores committed snapshots |

**Practical example:**

```bash
git status
git add README.md
git commit -m "Update project documentation"
```

**Remember:** `git add` stages changes; `git commit` saves them in the local repository.

## 2. Essential Commands

| Command | Purpose |
|---|---|
| `git init` | Initialize a repository |
| `git clone <url>` | Copy a remote repository |
| `git status` | Show current changes |
| `git add <file>` | Stage a file |
| `git add .` | Stage changes in the current directory |
| `git commit -m "message"` | Create a commit |
| `git log --oneline` | Display compact commit history |
| `git diff` | Show unstaged changes |
| `git diff --staged` | Show staged changes |

## 3. Branch Basics

**What it is:** A branch is an independent line of development.

```bash
git branch                  # List branches
git branch feature-login    # Create a branch
git switch feature-login   # Switch branches
git switch -c feature-api   # Create and switch
git branch -d feature-login # Delete a merged branch
```

**Remember:** Branches let you work on changes without directly modifying another branch.

## 4. Remote Repositories

**What it is:** A remote is a reference to a repository hosted elsewhere, such as GitHub.

```bash
git remote -v
git remote add origin <repository-url>
git push -u origin main
git push
```

### Fetch vs Pull

| Command | What it does |
|---|---|
| `git fetch` | Downloads remote updates without integrating them into your current branch |
| `git pull` | Fetches updates and integrates them into your current branch |

**Practical example:**

```bash
git fetch origin
git log --oneline HEAD..origin/main
git pull
```

**Remember:** Fetch lets you inspect remote updates first. Pull fetches and integrates them.

## 5. Tracking Branches

A tracking branch connects a local branch to a remote branch.

```bash
git branch -vv
git push -u origin feature-login
git pull origin main
```

- `origin`: commonly the default name for a remote.
- `main`: the branch name.
- `-u`: sets the upstream branch for future push and pull commands.

**Remember:** Tracking branches make synchronization easier by connecting local and remote branches.