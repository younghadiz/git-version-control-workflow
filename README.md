# Git Version Control Workflow

Production-style Git workflow project demonstrating structured branching strategies, collaborative development practices, merge management, conflict resolution, and repository operations commonly used in modern DevOps and software engineering teams.

---

# Project Overview

This repository demonstrates practical Git operations used for managing application and infrastructure repositories across development and production workflows.

The project focuses on:

- branch-based development workflows
- feature and bugfix isolation
- merge conflict resolution
- clean commit history management
- repository synchronization across GitHub and GitLab
- production-safe Git operations
- collaborative engineering practices

---

# Architecture Diagram

![Git Workflow Architecture](docs/arch-diagram/git-arch-diagram.png)

---

# Git Workflow Architecture

```text
Developer Workstation
        |
        | git clone
        v
Source Training Repository
        |
        | remove old remote
        v
Local Portfolio Repository
        |
        | git push
        v
GitHub Remote + GitLab Remote
        |
        | feature/* and bugfix/* branches
        v
Merge Requests / CLI Merges
        |
        | reviewed and validated changes
        v
main Branch
        |
        | git clone
        v
DigitalOcean Ubuntu Server
        |
        | validate repository and Git history
        v
Production-style Git Workflow Validation
```

---

# Branching Strategy

```text
main
  |
  └── develop
        |
        ├── feature/add-gitignore
        ├── feature/update-logging-and-homepage-image
        └── bugfix/fix-application-spelling
```

## Branch Roles

| Branch | Purpose |
|---|---|
| `main` | Stable production-ready branch |
| `develop` | Integration and testing branch |
| `feature/*` | Isolated feature development |
| `bugfix/*` | Isolated issue resolution |

---

# Key Git Operations Demonstrated

- cloning existing repositories
- reinitializing repository ownership
- configuring GitHub and GitLab remotes
- multi-remote push configuration
- feature branch workflows
- bugfix branch workflows
- descriptive commit management
- non-fast-forward merge commits
- merge conflict resolution
- revert operations
- reset operations
- branch cleanup
- repository synchronization
- Git history visualization

---

# Repository Setup

## Clone Existing Repository

```bash
git clone https://gitlab.com/twn-devops-bootcamp/latest/03-git/git-exercises.git git-version-control-workflow

cd git-version-control-workflow
```

---

## Remove Existing Remote

```bash
git remote remove origin
```

---

## Initialize Production Branch

```bash
git branch -M main
```

---

## Configure Personal Remotes

```bash
git remote add origin git@github.com:younghadiz/git-version-control-workflow.git

git remote set-url --add --push origin git@github.com:younghadiz/git-version-control-workflow.git

git remote set-url --add --push origin git@gitlab.com:devops-engineering-projects/git-workflows-version-control.git
```

---

## Push Production Branch

```bash
git push -u origin main
```

---

## Create Development Branch

```bash
git checkout -b develop

git push -u origin develop
```

---

# Feature Branch Workflow

## Create Feature Branch

```bash
git checkout develop

git checkout -b feature/add-gitignore
```

---

## Commit Changes

```bash
git add .

git commit -m "feat: add gitignore rules for generated files"
```

---

## Push Feature Branch

```bash
git push -u origin feature/add-gitignore
```

---

## Merge Feature Branch Into develop

```bash
git checkout develop

git merge --no-ff feature/add-gitignore \
-m "merge: add gitignore rules for generated files"
```

---

## Push Updated develop Branch

```bash
git push origin develop
```

---

# Production Promotion Workflow

After validation and testing:

```bash
git checkout main

git merge --no-ff develop \
-m "merge: promote tested develop branch to production"

git push origin main
```

This preserves a clean and traceable Git history.

---

# Important Git Commands

## Check Repository Status

```bash
git status
```

---

## Inspect Changes

```bash
git diff
```

---

## Stage Files

```bash
git add .
```

---

## Commit Changes

```bash
git commit -m "descriptive commit message"
```

---

## Push Branch

```bash
git push -u origin branch-name
```

---

## Revert Pushed Commit Safely

```bash
git revert HEAD
```

---

## Reset Local Commit

```bash
git reset --hard HEAD~1
```

---

## Delete Remote Branch

```bash
git push origin --delete branch-name
```

---

# Merge Conflict Resolution

A merge conflict was intentionally created by modifying the same dependency version across multiple branches.

The conflict was resolved manually by:

- reviewing conflicting sections
- preserving the correct dependency version
- removing Git conflict markers
- validating final repository state

---

# .gitignore Strategy

Generated files, IDE files, build artifacts, and local secrets should not be committed to shared repositories.

## Ignored Files

```gitignore
.idea/
.DS_Store
build/
out/
target/
.env
*.log
```

---

## Remove Previously Tracked Files

```bash
git rm -r --cached .idea

git rm -r --cached build

git rm -r --cached out

git rm --cached .DS_Store
```

---

# DigitalOcean Validation

The repository can be validated on a remote Linux server to simulate real operational workflows.

## Install Git Utilities

```bash
sudo apt update

sudo apt install -y git tree
```

---

## Clone Repository

```bash
git clone git@github.com:younghadiz/git-version-control-workflow.git
```

---

## Validate Git History

```bash
cd git-version-control-workflow

git log --oneline --graph --decorate --all
```

---

# Security Best Practices

Sensitive files and credentials should never be committed to Git repositories.

## Examples

- SSH private keys
- API tokens
- cloud credentials
- `.env` files
- personal access tokens

## Recommended Authentication

- SSH keys
- GitHub Actions Secrets
- GitLab CI/CD Variables
- Jenkins Credentials
- secure secrets managers

---

# DevOps Concepts Demonstrated

- Git branching workflows
- production branch protection concepts
- feature isolation
- merge conflict handling
- repository synchronization
- multi-remote Git operations
- clean commit history management
- collaborative engineering workflows
- Linux-based Git operations
- production-style repository management

---

# Future Improvements

- GitHub Actions CI integration
- GitLab CI/CD pipelines
- automated branch validation
- commit linting
- protected branch policies
- release tagging workflows
- semantic versioning automation

---

# Author

DevOps Engineering Portfolio Project