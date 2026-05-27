# Unit 01: Git Basics

## 📌 Lesson Objectives
- Understand [Version Control Systems](ca://s?q=Explain_Version_Control_Systems)
- Learn about [Git](ca://s?q=What_is_Git) and its history
- Explore Git terminology and concepts
- Practice basic Git commands

---

## 🔑 Introduction to Version Control Systems (VCS)
Version Control Systems record changes to files over time, allowing recall of specific versions.

### Types of VCS
- **[Local VCS](ca://s?q=Local_Version_Control_System)**  
  - Example: GNU RCS  
  - ✅ Simple  
  - ❌ Error‑prone, cannot share

- **[Centralized VCS](ca://s?q=Centralized_Version_Control_System)**  
  - Examples: CVS, Subversion, Perforce  
  - ✅ Central control, visibility of team activity  
  - ❌ Single point of failure

- **[Distributed VCS](ca://s?q=Distributed_Version_Control_System)**  
  - Examples: Git, Mercurial  
  - ✅ No single point of failure, flexible workflows, local operations  
  - ❌ More complex setup

---

## 🐙 Git Overview
- Created by Linus Torvalds in 2005 for Linux kernel development  
- Goals:  
  - Speed  
  - Support for non‑linear development (branches)  
  - Handle large projects efficiently  

---

## ⚙️ Installing Git
- Download: [git-scm.com/download](https://git-scm.com/download)  
- Guide: [Git Book - Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

---

## 📚 Git Terminology
- **[Repository](ca://s?q=Git_repository)**: Local or remote storage of project history  
- **[Remote](ca://s?q=Git_remote)**: Online repository, default name `origin`  
- **[Commit](ca://s?q=Git_commit)**: Stores changes with a message and SHA ID  
- **[Branch](ca://s?q=Git_branch)**: Parallel versions of code; default branch is `main` (or `master`)  
- **[Checkout](ca://s?q=Git_checkout)**: Switch branches (`git checkout branch_name`)  

---

## 🧩 Git Concepts
- **File Status**  
  - Untracked, Unmodified, Modified, Staged  
  - Commands: `git add`, `git commit`

- **[Merge](ca://s?q=Git_merge)**  
  - Combines work from different branches  
  - May cause conflicts that need resolution

- **[Rebase](ca://s?q=Git_rebase)**  
  - Reapplies commits onto another branch  
  - ⚠️ Do not rebase commits already pushed to shared repositories

---

## 🌐 Working with Remotes
- `git push` – upload local commits  
- `git pull` / `git fetch` – download changes  
- `git remote add/remove` – manage remotes  
- Clone examples:  
  - `git clone ssh://user@server:project.git`  
  - `git clone http://example.com/project.git`

---

## 📝 Summary
- Learned about [VCS types](ca://s?q=Types_of_Version_Control_Systems)  
- Understood Git history and goals  
- Covered Git terminology and concepts  
- Practiced essential Git commands

---

Hope this file helpful for you!!
