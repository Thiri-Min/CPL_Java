# Unit 02: Git Advanced & Tools

## 📌 Lesson Objectives
- Demonstrate [Git commands](ca://s?q=Git_command_demo)  
- Understand and implement [Git submodules](ca://s?q=Git_submodule)

---

## 🖥️ Git Command Demo
- Review of previous session’s basics  
- Hands‑on demonstration of core Git commands

---

## 🔑 Git Submodules

### Situations for Using Submodules
- External component or subproject changes too frequently (e.g., iOS framework, Android submodule, Java dependency)  
- Component updated rarely, tracked as vendor dependency  
- Third‑party delegated project integrated at specific release points  

### What Are Submodules?
- Keep a Git repository as a subdirectory of another repository  
- Reference another repository at a particular snapshot in time  

---

## ⚙️ Implementing Submodules
1. Clone parent repository  
2. Add submodule:  
   ```bash
   git submodule add <repo_url>
