# Git Tutorial

This tutorial provides a comprehensive guide to using Git, particularly for working with this repository.

## Table of Contents

1. [Introduction to Git](#introduction-to-git)
2. [Getting Started](#getting-started)
3. [Basic Git Workflow](#basic-git-workflow)
4. [Working with Branches](#working-with-branches)
5. [Collaborating with Others](#collaborating-with-others)
6. [Common Git Commands](#common-git-commands)
7. [Working with This Repository](#working-with-this-repository)
8. [Best Practices](#best-practices)
9. [Troubleshooting](#troubleshooting)

## Introduction to Git

Git is a distributed version control system that helps you track changes in your code, collaborate with others, and manage different versions of your project. Every Git repository contains the complete history of all changes.

### Key Concepts

- **Repository (Repo)**: A directory containing your project files and the complete version history
- **Commit**: A snapshot of your project at a specific point in time
- **Branch**: A parallel version of your repository that allows you to work on features independently
- **Remote**: A version of your repository hosted on a server (like GitHub)
- **Clone**: Creating a local copy of a remote repository
- **Pull**: Downloading changes from a remote repository
- **Push**: Uploading your local changes to a remote repository

## Getting Started

### Installing Git

**Linux (Debian/Ubuntu):**
```bash
sudo apt-get update
sudo apt-get install git
```

**macOS:**
```bash
brew install git
```

**Windows:**
Download and install from [git-scm.com](https://git-scm.com/download/win)

### Initial Configuration

Set up your identity (required before making commits):

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Check your configuration:
```bash
git config --list
```

### Cloning This Repository

To get a local copy of this repository:

```bash
git clone https://github.com/sashinogle-lgtm/mercedes-benz-com-diagnostics-1-0-swagger.git
cd mercedes-benz-com-diagnostics-1-0-swagger
```

## Basic Git Workflow

### 1. Check Repository Status

See which files have changed:
```bash
git status
```

### 2. View Changes

See what modifications you've made:
```bash
git diff
```

View changes for a specific file:
```bash
git diff swagger.yaml
```

### 3. Stage Changes

Add specific files to staging area:
```bash
git add swagger.yaml
```

Add all changes:
```bash
git add .
```

Add all YAML files:
```bash
git add *.yaml
```

### 4. Commit Changes

Commit staged changes with a message:
```bash
git commit -m "Update API endpoint documentation"
```

Commit with a detailed message (opens editor):
```bash
git commit
```

### 5. Push Changes

Push your commits to the remote repository:
```bash
git push
```

Push to a specific branch:
```bash
git push origin main
```

## Working with Branches

Branches allow you to work on features or fixes without affecting the main codebase.

### View Branches

List local branches:
```bash
git branch
```

List all branches (including remote):
```bash
git branch -a
```

### Create a Branch

Create a new branch:
```bash
git branch feature/new-endpoint
```

Create and switch to a new branch:
```bash
git checkout -b feature/new-endpoint
```

Modern Git (v2.23+):
```bash
git switch -c feature/new-endpoint
```

### Switch Branches

```bash
git checkout main
```

Modern Git (v2.23+):
```bash
git switch main
```

### Merge Branches

Merge a branch into your current branch:
```bash
git checkout main
git merge feature/new-endpoint
```

### Delete Branches

Delete a local branch:
```bash
git branch -d feature/new-endpoint
```

Force delete (if not fully merged):
```bash
git branch -D feature/new-endpoint
```

Delete a remote branch:
```bash
git push origin --delete feature/new-endpoint
```

## Collaborating with Others

### Fetching and Pulling

Fetch changes from remote (without merging):
```bash
git fetch origin
```

Pull changes from remote (fetch + merge):
```bash
git pull
```

Pull from a specific branch:
```bash
git pull origin main
```

### Handling Pull Requests

1. Create a new branch for your changes
2. Make and commit your changes
3. Push your branch to the remote
4. Create a pull request on GitHub
5. Wait for review and approval
6. Merge the pull request

### Working with Forks

Fork the repository on GitHub, then:

```bash
# Clone your fork
git clone https://github.com/YOUR-USERNAME/mercedes-benz-com-diagnostics-1-0-swagger.git
cd mercedes-benz-com-diagnostics-1-0-swagger

# Add upstream remote
git remote add upstream https://github.com/sashinogle-lgtm/mercedes-benz-com-diagnostics-1-0-swagger.git

# Fetch upstream changes
git fetch upstream

# Merge upstream changes
git merge upstream/main
```

## Common Git Commands

### Viewing History

View commit history:
```bash
git log
```

View compact history:
```bash
git log --oneline
```

View history with graph:
```bash
git log --graph --oneline --all
```

View changes in a specific commit:
```bash
git show <commit-hash>
```

### Undoing Changes

Discard changes in working directory:
```bash
git checkout -- swagger.yaml
```

Modern Git:
```bash
git restore swagger.yaml
```

Unstage a file (keep changes):
```bash
git reset HEAD swagger.yaml
```

Modern Git:
```bash
git restore --staged swagger.yaml
```

Amend the last commit:
```bash
git commit --amend
```

Revert a commit (creates new commit):
```bash
git revert <commit-hash>
```

### Stashing Changes

Save changes temporarily:
```bash
git stash
```

List stashes:
```bash
git stash list
```

Apply most recent stash:
```bash
git stash apply
```

Apply and remove most recent stash:
```bash
git stash pop
```

### Tagging

Create a tag:
```bash
git tag v1.0.0
```

Create an annotated tag:
```bash
git tag -a v1.0.0 -m "Version 1.0.0 release"
```

Push tags to remote:
```bash
git push origin --tags
```

## Working with This Repository

This repository contains the OpenAPI/Swagger specification for the Mercedes-Benz Remote Diagnostic Support API.

### Typical Workflow for Updating the API Specification

1. **Create a feature branch:**
   ```bash
   git checkout -b feature/update-diagnostics-endpoint
   ```

2. **Make changes to swagger.yaml:**
   Edit the file with your preferred editor

3. **Check your changes:**
   ```bash
   git diff swagger.yaml
   ```

4. **Validate the Swagger file:**
   Use [Swagger Editor](https://editor.swagger.io/) to validate your changes

5. **Stage and commit:**
   ```bash
   git add swagger.yaml
   git commit -m "Add new diagnostic endpoint for battery status"
   ```

6. **Push to remote:**
   ```bash
   git push origin feature/update-diagnostics-endpoint
   ```

7. **Create a Pull Request on GitHub**

### Viewing File History

See all changes to the swagger.yaml file:
```bash
git log --follow swagger.yaml
```

See who changed what in the file:
```bash
git blame swagger.yaml
```

### Comparing Versions

Compare current version with a previous commit:
```bash
git diff <commit-hash> swagger.yaml
```

Compare two commits:
```bash
git diff <commit-hash1> <commit-hash2> swagger.yaml
```

## Best Practices

### Commit Messages

Write clear, descriptive commit messages:

**Good examples:**
```
Add vehicle battery diagnostic endpoint
Fix typo in Remote Diagnostic API description
Update ECU parameter validation rules
Remove deprecated DTC snapshot endpoint
```

**Bad examples:**
```
Update
Fixed stuff
WIP
asdf
```

**Conventional Commits Format:**
```
<type>: <description>

[optional body]

[optional footer]
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

Examples:
```
feat: add battery health diagnostic endpoint
fix: correct response schema for DTC readout
docs: update API usage examples in README
```

### Branching Strategy

- `main` or `master`: Production-ready code
- `develop`: Integration branch for features
- `feature/*`: New features or enhancements
- `bugfix/*`: Bug fixes
- `hotfix/*`: Urgent production fixes
- `release/*`: Release preparation

### Commit Frequency

- Commit often, but keep commits logical
- Each commit should represent a single logical change
- Don't commit broken code
- Don't commit multiple unrelated changes together

### Before Pushing

Always check before pushing:
```bash
git status
git log --oneline -5
git diff origin/main
```

## Troubleshooting

### Merge Conflicts

When you see a merge conflict:

1. **View conflicted files:**
   ```bash
   git status
   ```

2. **Open the conflicted file** and look for conflict markers:
   ```
   <<<<<<< HEAD
   Your changes
   =======
   Their changes
   >>>>>>> branch-name
   ```

3. **Resolve the conflict** by editing the file

4. **Stage the resolved file:**
   ```bash
   git add swagger.yaml
   ```

5. **Complete the merge:**
   ```bash
   git commit
   ```

### Accidentally Committed to Wrong Branch

If you committed to `main` instead of a feature branch:

```bash
# Create a new branch with current changes
git branch feature/my-changes

# Reset main to previous commit
git reset --hard HEAD~1

# Switch to the new branch
git checkout feature/my-changes
```

### Reset to Remote State

Discard all local changes and match remote:
```bash
git fetch origin
git reset --hard origin/main
```

### View Remote URL

```bash
git remote -v
```

### Change Remote URL

```bash
git remote set-url origin <new-url>
```

### Untrack a File (Keep Locally)

```bash
git rm --cached swagger.yaml
```

### View Differences Between Branches

```bash
git diff main..feature/new-endpoint
```

### Find When a Bug Was Introduced

Use `git bisect` to binary search through commits:
```bash
git bisect start
git bisect bad                 # Current version is bad
git bisect good <commit-hash>  # Known good version
# Git will checkout commits for you to test
# Mark each as good or bad until you find the culprit
git bisect good
git bisect bad
```

### Recover Deleted Commits

View reflog:
```bash
git reflog
```

Recover a commit:
```bash
git checkout <commit-hash>
git branch recovery-branch
```

## Additional Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [Pro Git Book](https://git-scm.com/book/en/v2) (Free online)
- [GitHub Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
- [Interactive Git Branching Tutorial](https://learngitbranching.js.org/)

## Getting Help

### Git Help Command

```bash
git help
git help commit
git help branch
```

### Quick Reference

```bash
git <command> --help
git <command> -h
```

---

**Remember:** Git is a powerful tool that becomes easier with practice. Don't be afraid to experiment in a test branch, and always make sure you understand a command before running it on important code!
