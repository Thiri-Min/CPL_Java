# What Is an MD File? How to Write and Use Markdown in Your Editor

## 🎯 What you will learn
- What **`.md`** means  
- Why people use Markdown  
- How to **write** basic Markdown  
- How to **open, preview, and edit** in **Cursor** or **VS Code**  

---

## 1. What is an MD file?

| Term | Meaning |
|------|---------|
| **MD** | Short for **Markdown** |
| **`.md`** | File extension for a Markdown document (e.g. `README.md`, `03_Table_Indexes_Views.md`) |
| **Markdown** | A **plain-text** format for writing documents with simple symbols (`#`, `*`, `` ` ``) instead of clicking buttons in Word |

**In simple words:**  
An MD file is a **text file** you can open in any editor. You type normal characters. Special characters turn into **headings**, **lists**, **bold text**, **code blocks**, and **tables** when viewed in a Markdown viewer (like GitHub or Cursor preview).

**It is NOT:**
- A programming language that runs on your computer  
- Microsoft Word (`.docx`)  
- HTML (though Markdown can be converted to HTML for websites)

**It IS:**
- Easy to read **even without** preview (raw text is clean)  
- Used on **GitHub**, **documentation**, **lecture notes**, and **README** files  
- The same format as your FU-01 / FU-02 lecture files in this project  

---

## 2. Why use Markdown?

| Benefit | Explanation |
|---------|-------------|
| **Lightweight** | Small file size; works in Git |
| **Version control friendly** | Git shows clear diffs line by line |
| **Universal** | GitHub, Cursor, Notion, many tools support it |
| **Fast** | No formatting toolbar — type symbols and go |
| **Readable** | You can read the source file without preview |

**Example in this project:**  
`Lectures/DBSQL/FU-02/00_FU-02_Complete_Summary.md` is a lecture written in Markdown.

---

## 3. How to open and use MD files in Cursor / VS Code

### 3.1 Open a file
1. In the **Explorer** (left sidebar), browse to the `.md` file.  
2. **Double-click** the file — it opens in the editor tab.  

Or: **File → Open File** and choose `Something.md`.

### 3.2 Preview (see formatted result)
While the `.md` file is open:

| Action | Windows shortcut |
|--------|------------------|
| **Open Preview** | `Ctrl + Shift + V` |
| **Preview side by side** | `Ctrl + K`, then `V` (press `Ctrl+K`, release, press `V`) |

- **Left pane:** raw Markdown (what you type)  
- **Right pane:** formatted view (headings, bold, lists, etc.)

You can also right-click the tab → **Open Preview**.

### 3.3 Edit workflow (recommended)
1. Type or edit in the **source** tab.  
2. Keep **Preview** open beside it to check appearance.  
3. **Save** with `Ctrl + S`.  
4. Preview updates when you save (or as you type, depending on settings).

### 3.4 Create a new MD file
1. Right-click a folder in Explorer → **New File**.  
2. Name it with `.md` at the end, e.g. `My_Notes.md`.  
3. Start with `# My Title` and save.

---

## 4. Basic Markdown syntax (cheat sheet)

Copy these examples into a new file and try **Preview** to see the result.

### 4.1 Headings
```markdown
# Heading 1 (largest)
## Heading 2
### Heading 3
#### Heading 4
```

### 4.2 Bold, italic, strikethrough
```markdown
**bold text**
*italic text*
***bold and italic***
~~crossed out~~
```

### 4.3 Lists

**Bullet list:**
```markdown
- Item one
- Item two
  - Nested item
```

**Numbered list:**
```markdown
1. First step
2. Second step
3. Third step
```

**Task list (checkboxes on GitHub):**
```markdown
- [x] Done task
- [ ] Todo task
```

### 4.4 Links and images
```markdown
[Link text](https://www.example.com)

![Image description](path/to/image.png)
```

### 4.5 Inline code and code blocks

**Inline code** — wrap text in single backticks:

    Use `SELECT` for inline code.

**Code block** — put three backticks on a line above and below (optional language name for color):

    ```sql
    SELECT * FROM Student WHERE Age > 20;
    ```

> **Tip:** In your own `.md` file, type three backticks (not four). The indented examples above avoid broken preview in this guide.

### 4.6 Tables
```markdown
| Column A | Column B |
|----------|----------|
| Row 1    | Data     |
| Row 2    | More     |
```

### 4.7 Blockquote
```markdown
> This is a quote or important note.
```

### 4.8 Horizontal line
```markdown
---
```

### 4.9 Emojis (optional)
Many editors and GitHub show emoji shortcodes:
```markdown
:books: :white_check_mark: :rocket:
```
Or type emoji directly: 📘 ✅ 🚀

---

## 5. Example: small lecture note in Markdown

Create a new file `PK_Notes.md` and paste this content (then preview):

    # Lesson: Primary Key

    ## Objective
    - Define **primary key**
    - Write `CREATE TABLE` with PK

    ## Definition
    A **primary key** uniquely identifies each row.

    ## Example (T-SQL)
    ```sql
    CREATE TABLE Student (
        StudentID INT PRIMARY KEY,
        FullName  VARCHAR(100) NOT NULL
    );
    ```

    ## Practice
    - [ ] Create table in SSMS
    - [ ] Insert 3 rows
    - [ ] Try duplicate PK and observe error

    ## Links
    - [Microsoft Docs](https://learn.microsoft.com/en-us/sql/)

When you create the real file, **remove the 4-space indent** at the start of each line — that indent is only used here so this guide displays correctly.

Save as `PK_Notes.md` and press `Ctrl + Shift + V` to preview.

---

## 6. MD files in your project (FPT Academy demo)

| Location | Purpose |
|----------|---------|
| `Lectures/DBSQL/FU-01/*.md` | Foundation SQL / DB notes |
| `Lectures/DBSQL/FU-02/*.md` | SQL Server, ERD, DML, indexes |
| `README.md` (repo root) | Project description on GitHub |
| This file | Explains Markdown itself |

On **GitHub**, when you push `.md` files, they render automatically with headings, tables, and code highlighting.

---

## 7. Common mistakes beginners make

| Mistake | Fix |
|---------|-----|
| No space after `#` | Use `# Title` not `#Title` |
| Table columns misaligned | Header row + `|---|---|` separator required |
| Code block not closing | Add closing \`\`\` on its own line |
| Link broken | Check URL in `(https://...)` |
| Expecting `.md` to run like Java | Markdown is **documentation only** — not executed |

---

## 8. Quick practice exercise

1. Create `Lectures/My_First_Markdown.md`.  
2. Add:
   - One `#` title with your name  
   - A bullet list of 3 subjects you study  
   - One **bold** word and one `inline code` word  
   - One SQL code block with `SELECT 1;`  
   - One table with 2 columns and 2 rows  
3. Press `Ctrl + Shift + V` to preview.  
4. Save and (optional) commit to Git so it appears on GitHub.

---

## 9. Summary

| Question | Answer |
|----------|--------|
| What is `.md`? | A **Markdown** text document |
| How do I write it? | Any text editor; use `#`, lists, `**bold**`, code fences |
| How do I see pretty output? | **Preview** in Cursor: `Ctrl + Shift + V` |
| Where is it used? | GitHub, lectures, README, technical notes |
| Do I need special software? | **No** — Cursor/VS Code is enough |

---

## 🔗 Learn more

- [Markdown Guide (getting started)](https://www.markdownguide.org/getting-started/)  
- [GitHub Markdown documentation](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)  
- [CommonMark spec](https://commonmark.org/) (technical reference)  

---

**You are reading this file in Markdown right now.**  
Switch to **Preview** (`Ctrl + Shift + V`) to see the formatted version of this guide.
