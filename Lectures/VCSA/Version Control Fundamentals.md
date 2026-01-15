# Version Control Fundamentals

## Why VCS?
- **Collaboration**: Enables multiple developers to work on the same project without overwriting each other’s changes.
- **History Tracking**: Maintains a record of all changes, allowing you to revert to previous versions if needed.
- **Backup & Recovery**: Acts as a safeguard against accidental data loss.
- **Experimentation**: Developers can create branches to test new features without affecting the main codebase.

---

## Centralized vs Distributed

### Centralized Version Control (CVCS)
- **Single server** stores the codebase.
- Developers check out and commit changes directly to this central repository.
- **Pros**: Simple model, easy to understand.
- **Cons**: Single point of failure; limited offline capabilities.

### Distributed Version Control (DVCS)
- Each developer has a **full copy** of the repository, including history.
- Changes are committed locally and later pushed/pulled to synchronize with others.
- **Pros**: Offline work possible, faster operations, redundancy.
- **Cons**: Slightly more complex to learn.

---

## Git Mental Model

### Commit
- A **snapshot** of the project at a given point in time.
- Each commit has a unique identifier (hash).

### Branch
- A **pointer** to a series of commits.
- Allows parallel development (e.g., feature branches, bugfix branches).

### HEAD
- A **reference** to the current commit or branch you’re working on.
- Moves as you make new commits.

---

## Working Tree vs Staging 

### 🔧 Working Tree 

- The actual files and directories you are editing on your machine. 
- Reflects the current state of your project. 
- Think of it like your desk: papers are spread out, and you’re making changes. 

### 📦 Staging Area (Index) 

- A **preparation zone** where changes are collected before committing. 
- Allows selective inclusion of changes in a commit.

-----
