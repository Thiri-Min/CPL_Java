# 🚀 GitHub Portfolio Upload Guide (Beginner Friendly)

This guide explains step-by-step how to upload your frontend portfolio project to GitHub and optionally deploy it as a live website.

---

## 📌 Requirements

- GitHub account
- Git installed
- Portfolio project (HTML, CSS, JS)
- VS Code or Terminal

---

## 🧱 Step 1: Create a Repository on GitHub

1. Go to https://github.com
2. Click **New Repository**
3. Repository name: `Portfolio`
4. Select **Public**
5. Do NOT add README
6. Click **Create Repository**

Example repository URL:
https://github.com/Thiri-Min/Portfolio.git


---

## 📂 Step 2: Open Project Folder

### Using VS Code
- Open project folder
- Go to View
- Open Terminal

### Using Terminal
type `pwd` and enter

```python
pwd
```

You can see this view 

```python
PS D:\FPT Academy\2026 Internship Program\Lectures> pwd

Path
----
D:\FPT Academy\2026 Internship Program\Lectures
```

## 🔧 Step 3: Initialize Git

```python
git init
```

## 🔗 Step 4: Connect GitHub Repository

Replace USERNAME with your GitHub username:

git remote add origin https://github.com/USERNAME/Portfolio.git

```python
git remote -v
```

## 📦 Step 5: Add Files

```python
git add .
```

## 📝 Step 6: Commit Files

```python
git commit -m "Initial portfolio upload"

```

## ⬆️ Step 7: Push Code to GitHub

```python
git branch -M main
git push -u origin main
```

## 🔍 Step 8: Verify on GitHub

- Open your repository
- Refresh the page
- Confirm files are uploaded

---

## 🌐 Optional: Deploy Using GitHub Pages

1. Repository → **Settings**
2. Click **Pages**
3. Source:
   - Branch: `main`
   - Folder: `/root`
4. Click **Save**

you can see your username in this link.
Live URL: https://username.github.io/Portfolio

Exception:
If you updated code, you can update using these commits

```python
git status
git add .
git commit -m "your message"
git push
```