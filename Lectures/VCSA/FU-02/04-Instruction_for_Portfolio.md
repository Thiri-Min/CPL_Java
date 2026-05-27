## 04: Instruction for Portfolio (AI + GitHub)

This guide helps you create a frontend portfolio using an AI chat bot (in VS Code or any editor), then upload it to GitHub using Git.

> **Important — read before you start**  
> The prompt examples in Section 3 are **samples only**. They show what a good prompt *looks like* (structure, sections, deliverables).  
> **Do not copy and paste a sample prompt as-is.** Change the content so it matches **your** name, skills, projects, colors, layout, and tech choices.  
> **Each student’s portfolio must be unique.** Submissions that look identical (same layout, same projects, same wording) may not be accepted.

---

## 1) Requirements

- GitHub account
- Git installed
- VS Code (or any code editor) + internet access for AI chat
- A frontend portfolio project (HTML/CSS/JavaScript or any frontend framework you learned)
- **Profile photo:** Use **your own picture** on the portfolio (About/Home section). Do **not** use an avatar icon, cartoon image, AI-generated face, or stock placeholder photo.

---

## 2) Use an AI chat bot to generate your portfolio

### 2.1 Choose an editor + AI tool

You can use:

- **VS Code + Copilot Chat** (or Copilot)
- **ChatGPT** (web) and then paste code into your editor
- **Any AI chatbot** that can generate code (browser or IDE extension)

### 2.2 What to include in your prompt

To get a good portfolio, your prompt should clearly describe:

- Your **portfolio sections** (example: Home, About, Projects, Skills, Contact)
- Your **frontend technologies** (example: HTML/CSS/JavaScript, React, etc.)
- **Design rules** (responsive, clean UI, consistent colors, simple animations)
- **Features** (example: project cards, filter/search, modal details, contact form UI)
- **Output format** (request file-by-file code so it’s easy to copy)

Tip: Ask the AI to generate a **simple** version first, then improve it.

---

## 3) Sample prompt templates (front-end portfolio)

> **Exception / rule for prompts below**  
> Templates A, B, and C are **reference samples only** — not ready-to-submit prompts.  
> - **Do not** submit a portfolio built by pasting a sample prompt unchanged into an AI tool.  
> - **Do** write your own prompt: use the sample as a guide, then customize sections, features, design, and project list for **your** work.  
> - Your final site should reflect **your** identity (about text, real or practice projects you chose, your color theme, your skills).

### Template A (HTML + CSS + JavaScript, single-page portfolio)

**Sample structure only.** Adapt every `[ ]` field and change requirements (sections, features, number of projects) so your prompt is original:

```text
I need a responsive frontend portfolio website (no backend).

Requirements:
- Style: modern, clean, beginner-friendly
- Sections: Home, About, Projects, Skills, Contact
- Include a projects grid with 6 example projects
- Add simple interactivity using vanilla JavaScript:
  - filter projects by category
  - when clicking a project card, show details in a modal
- Accessibility: semantic HTML, proper headings, keyboard-friendly modal

Tech stack: HTML, CSS, vanilla JavaScript

Deliverables:
1) index.html
2) styles.css
3) app.js

Important:
- Provide code file-by-file with clear headings: "index.html", "styles.css", "app.js".
- Keep code well structured and easy to edit.

Project details:
- Name: [Your Name]
- Theme color: [e.g. #2563eb]
- Projects categories: [e.g. Web, Data, Tools]
- Contact: [your email placeholder]
```

### Template B (If you want a small multi-page site)

**Sample only** — adjust pages, project count, and layout to match your plan; do not use this text verbatim.

```text
Create a responsive portfolio website using HTML/CSS/JS with multiple pages.

Pages:
- index.html (Home)
- projects.html (Projects list)
- contact.html (Contact form UI)
- about.html (About me)

Tech stack: HTML, CSS, vanilla JavaScript

Requirements:
- Consistent navbar across pages
- Projects page shows at least 8 projects
- Use a simple CSS grid layout
- Contact page includes a form UI (no backend needed)

Deliver code file-by-file:
- index.html, projects.html, contact.html, about.html, styles.css, app.js
```

### Template C (Improve an existing AI result)

**Sample only** — use after you have **your own** draft code (from your customized prompt), not as a shortcut to copy someone else’s portfolio.

If you already have generated code, ask the AI to improve it:

```text
Review my portfolio code and improve:
- responsiveness (mobile first)
- UI consistency (spacing, font sizes)
- accessibility issues (headings, alt text, keyboard navigation)

Here is my code:
[paste files]

Return only the updated parts and explain what you changed briefly.
```

---

## 4) Build / finalize in your editor

1. Paste the generated code into your editor (create files like `index.html`, `styles.css`, `app.js`).
2. Run your project in a browser:
   - If you only use HTML/CSS/JS, you can open `index.html` directly.
   - If you use a framework (React/Vue/etc.), follow the framework run instructions.
3. Make sure:
   - No big layout breaks on mobile
   - All interactive features work (filter + modal, etc.)
   - Your file names match what the AI generated

---

## 5) Upload your portfolio to GitHub

### Option 1: Upload using Terminal (recommended)

#### Step 1: Create a GitHub repository

1. Go to https://github.com
2. Click **New repository**
3. Name it something like: `Portfolio` or `[YourName]-portfolio`
4. Select **Public**
5. Choose **Do NOT add README** (so you start clean)
6. Click **Create repository**

#### Step 2: Open your project folder in VS Code

- Open the folder
- Open Terminal in VS Code (or use your normal terminal)

#### Step 3: Initialize Git

```bash
git init
```

#### Step 4: Connect to GitHub (set your remote)

Replace `USERNAME` and repo name:

```bash
git remote add origin https://github.com/USERNAME/Portfolio.git
```

Check:

```bash
git remote -v
```

#### Step 5: Add files + commit

```bash
git add .
git commit -m "Initial portfolio upload"
```

#### Step 6: Push to GitHub

```bash
git branch -M main
git push -u origin main
```

#### Step 7: Verify

- Refresh your GitHub repo page
- Confirm files are uploaded

---

### Option 2: Upload using VS Code Source Control

1. Open your project folder in VS Code
2. Go to **Source Control** panel (left sidebar)
3. Click **Initialize Repository**
4. Stage changed files
5. Write a commit message (example: `Upload portfolio`)
6. Click **Commit**
7. Click **Sync / Push**

---

## 6) Optional: Deploy using GitHub Pages (if your portfolio is static)

If your portfolio is simple HTML/CSS/JS, you can host it online:

1. Go to your repository **Settings**
2. Find **Pages**
3. Choose:
   - Branch: `main`
4. Save

Wait a moment, then open your site URL like:
- `https://USERNAME.github.io/Portfolio/`

Note: If you use React/Vue build output, the Pages setup may differ.

---

## ✅ Final checklist before submitting

- GitHub repo created and pushed successfully
- Your `index.html` (or entry file) exists at repo root (if using static site)
- Projects + interactions work
- Commit message included (example: `Initial portfolio upload`)
- **Uniqueness:** You wrote or heavily customized your AI prompt (not a copy of Template A/B/C as-is)
- **Uniqueness:** About section, project list, colors, and layout are **yours** — not identical to classmates’ portfolios

