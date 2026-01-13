# Git Installation and Setup on Windows

## 1. Install Git
Use **winget** (Windows Package Manager):

```bash
winget install Git.Git

Alternatively, download from the official site:
https://git-scm.com/download/win
```

## 2. Verify Installation

Check the installed version:

```bash
git --version
```

## 3. Configure Git (First-Time Setup)

Set your identity:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

```

Set default branch name to main:
```bash
git config --global init.defaultBranch main
```

##4. Line Ending Settings (Windows Best Practice)
Ensure proper handling of line endings:

```bash
git config --global core.autocrlf true
```

##5. Optional: Check Configuration

List all global settings:
```bash
git config --list
```


✅ You’re Ready!
Git is installed

Your identity is set

Default branch is main

Line endings are configured

Now you can create your first repository: