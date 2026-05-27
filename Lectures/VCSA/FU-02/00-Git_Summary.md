# 📘 Git Summary — FU-02 (VCSA)

> Combined revision guide from **01-Git_Basic**, **02-Git_Advanced_and_Tool**, and **03-Git_Flow**.

| # | Source file | Topic |
|---|-------------|--------|
| 1 | `01-Git_Basic.md` | VCS, Git basics, terminology, core commands |
| 2 | `02-Git_Advanced_and_Tool.md` | Advanced commands, submodules |
| 3 | `03-Git_Flow.md` | Branching workflows (Git Flow, GitHub Flow, others) |

---

## 🎯 Overall Learning Objectives

- Understand **version control** and why **Git** is used in teams  
- Use **basic Git commands** for daily work (add, commit, branch, push, pull)  
- Know when and how to use **submodules** for dependent projects  
- Choose and follow a **branching workflow** (Git Flow, GitHub Flow, trunk-based)

---

# Part 1 — Git Basics (Unit 01)

## 1.1 Version Control Systems (VCS)

**VCS** records file changes over time so you can recall any version later.

| Type | Examples | Pros | Cons |
|------|----------|------|------|
| **Local** | GNU RCS | Simple | Error-prone, no sharing |
| **Centralized** | CVS, Subversion, Perforce | Central control, team visibility | Single point of failure |
| **Distributed** | **Git**, Mercurial | No single point of failure, flexible, fast local work | More complex setup |

**Git is distributed** — every developer has a full copy of history on their machine.

---

## 1.2 Git Overview

- Created by **Linus Torvalds** (2005) for Linux kernel development  
- Goals: **speed**, **non-linear development** (branches), **large projects**

**Install:** [git-scm.com/download](https://git-scm.com/download)

---

## 1.3 Git Terminology

| Term | Meaning |
|------|---------|
| **Repository (repo)** | Project history (local or remote) |
| **Remote** | Online repo; default name is `origin` |
| **Commit** | Saved snapshot with message + unique **SHA** ID |
| **Branch** | Parallel line of development; default often `main` |
| **Checkout** | Switch to another branch (`git checkout branch_name` or `git switch`) |

---

## 1.4 File Status & Basic Workflow

```
Untracked → (git add) → Staged → (git commit) → Committed
                ↑
           Modified (edit files)
```

| Status | Meaning |
|--------|---------|
| **Untracked** | New file, Git not tracking yet |
| **Unmodified** | No changes since last commit |
| **Modified** | Changed, not staged |
| **Staged** | Ready for next commit |

### Essential commands

```bash
git init                    # start repo
git clone <url>             # copy remote repo
git status                  # see file states
git add <file>              # stage changes
git commit -m "message"     # save snapshot
git log                     # view history

git branch                  # list branches
git branch feature-x        # create branch
git checkout feature-x      # switch branch (or: git switch feature-x)

git push origin main        # upload commits
git pull origin main        # fetch + merge from remote
git fetch origin            # download without merge

git remote -v               # list remotes
git remote add origin <url>
```

---

## 1.5 Merge vs Rebase

| | **Merge** | **Rebase** |
|---|-----------|------------|
| **Action** | Combines branch histories with a merge commit | Replays commits on top of another branch |
| **History** | Preserves branching structure | Linear history |
| **Risk** | Merge conflicts | ⚠️ Do **not** rebase commits already pushed to shared remote |

---

## 1.6 Working with Remotes

```bash
git clone ssh://user@server:project.git
git clone https://github.com/user/project.git

git push      # send local commits to remote
git pull      # get remote changes and merge
git fetch     # get remote changes only
```

---

# Part 2 — Git Advanced & Tools (Unit 02)

## 2.1 Advanced Command Practice

- Builds on Unit 01 basics  
- Hands-on demo of core commands in real project scenarios  
- Focus: confident daily use (status, diff, branch, merge, remote)

**Useful extra commands:**

```bash
git diff                    # unstaged changes
git diff --staged           # staged changes
git merge <branch>          # merge branch into current
git stash                   # temporarily save work
git stash pop               # restore stashed work
```

---

## 2.2 Git Submodules

### When to use submodules

- External library or subproject changes **often** (iOS/Android/Java dependency)  
- Third-party project integrated at a **fixed release point**  
- Vendor code tracked at a **specific snapshot**, not copied manually

### What is a submodule?

- A **Git repo inside another Git repo**  
- Parent repo stores **which commit** of the child repo to use

### Basic workflow

```bash
# 1. Clone parent repo
git clone <parent_repo_url>
cd parent-repo

# 2. Add submodule
git submodule add <child_repo_url> path/to/submodule

# 3. Commit submodule reference in parent
git add .
git commit -m "Add submodule"

# 4. Clone parent with submodules (for teammates)
git clone --recurse-submodules <parent_repo_url>
# or after clone:
git submodule update --init --recursive
```

| Command | Purpose |
|---------|---------|
| `git submodule add <url>` | Add submodule |
| `git submodule update --init` | Fetch submodule content |
| `git submodule status` | Check submodule state |

---

# Part 3 — Git Flow & Workflows (Unit 03)

## 3.1 Why workflows matter

Daily Git work = **branching** + **merging** + **releasing** in a team.  
A **workflow** defines which branches exist and how code moves to production.

---

## 3.2 Git Flow (classic)

| Branch | Purpose |
|--------|---------|
| **main / master** | Production-ready code only |
| **develop** | Integration of completed features |
| **feature/** | New functionality (branch from `develop`) |
| **release/** | Prepare and stabilize a production release |
| **hotfix/** | Urgent fix on production (branch from `main`) |

### Flow (simplified)

```
feature → develop → release → main
                ↑
hotfix ─────────┴──→ main (and back to develop)
```

**Benefits:**
- Clear rules for features, releases, and emergencies  
- Production stays stable on `main`

**Merge:** Feature and hotfix branches merge back into `develop` and/or `main` when done.

---

## 3.3 GitHub Flow (simpler)

1. Branch from `main`  
2. Commit and push changes  
3. Open **Pull Request (PR)**  
4. Review and merge to `main`  
5. Deploy from `main`

| Pros | Cons |
|------|------|
| Simple, good for CI/CD | Less structure for multiple environments/releases |
| Works well with PR reviews | Not ideal for complex multi-release setups |

**Tip:** Teams often use **rebase** on feature branches before merge for cleaner history.

---

## 3.4 Other Branching Models

| Model | Idea |
|-------|------|
| **Environment branches** | Separate branches per environment (`staging`, `test`, `prod`) |
| **Release branches** | Long-lived branch to stabilize each release |
| **Trunk-based** | Everyone commits small changes frequently to `main` (trunk); strong CI required |

---

## 3.5 Choosing a workflow

| Situation | Suggested approach |
|-----------|------------------|
| Small team, web app, continuous deploy | **GitHub Flow** |
| Scheduled releases, many features in parallel | **Git Flow** |
| Strong CI, experienced team | **Trunk-based** |
| Multiple environments (dev/stage/prod) | **Environment branches** |

---

# ✅ Master Checklist

| Skill | Can you…? |
|-------|-----------|
| VCS | Explain local vs centralized vs distributed VCS? |
| Basics | `add`, `commit`, `push`, `pull`, `clone`? |
| Branches | Create, switch, and merge branches? |
| Remotes | Connect repo to `origin` on GitHub? |
| Merge/Rebase | Know when **not** to rebase shared commits? |
| Submodules | Explain why and run `submodule add`? |
| Git Flow | Name `main`, `develop`, `feature`, `hotfix` roles? |
| GitHub Flow | Describe PR-based workflow? |

---

## 📝 Review Questions

1. What are the three types of VCS? Which type is Git?  
2. What is the difference between **staged** and **modified**?  
3. What is the difference between `git fetch` and `git pull`?  
4. When should you **not** use `git rebase`?  
5. What problem do **submodules** solve?  
6. In **Git Flow**, which branch is for production?  
7. How is **GitHub Flow** different from **Git Flow**?  
8. What is **trunk-based development**?

---

## 🔗 Quick Reference Links

- [Git Downloads](https://git-scm.com/download)  
- [Pro Git Book](https://git-scm.com/book/en/v2)  
- [GitHub Docs — Flow](https://docs.github.com/en/get-started/using-github/github-flow)  
- [Atlassian — Git Flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

---

*Sources: `01-Git_Basic.md`, `02-Git_Advanced_and_Tool.md`, `03-Git_Flow.md` — FU-02 VCSA*
