# Complete Tutorial: Tailoring a LaTeX Resume for Job Applications Using AI and Overleaf

## Overview

This tutorial walks through a complete workflow for maintaining a master LaTeX resume, tailoring it to specific job descriptions using an AI assistant (Claude), and keeping everything synchronized across your local machine, GitHub, and Overleaf. Claude generates and pushes updated `.tex` content directly to the remote Git repository — Overleaf then syncs the changes and handles compilation and PDF export.

---

## Prerequisites

- A LaTeX resume written in a `.tex` file (e.g., `main.tex`)
- An [Overleaf](https://www.overleaf.com) account (paid plan required for Git sync)
- A [GitHub](https://github.com) account
- [Claude](https://claude.ai) desktop app with Cowork mode
- `git` installed on your local machine
- A local folder containing your `main.tex` file that is already a Git repository

---

## Part 1: Connect Overleaf Git Repository to GitHub

### Step 1: Check Current Git Remotes

```bash
git remote -v
```

### Step 2: Add GitHub Remote Repository

```bash
git remote add github https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

### Step 3: Stage and Commit Changes

```bash
git add .
git commit -m "Your commit message"
```

### Step 4: Push to GitHub

```bash
git push github master:main
```

### Step 5: Set Up Tracking (Optional)

```bash
git branch --set-upstream-to=github/main master
```

### Step 6: Alternative — Use SSH (Recommended)

```bash
git remote set-url github git@github.com:YOUR_USERNAME/YOUR_REPOSITORY.git
```

### Step 7: Import Overleaf Project from Git Repository

- Go to [Overleaf](https://www.overleaf.com)
- Click **New Project → Import from GitHub**
- Select your repository

### Step 8: Sync Overleaf with GitHub

- In your Overleaf project, go to **Menu → Sync**
- Click **Pull latest version from GitHub** to fetch the latest changes

### Step 9: Future Sync Commands

**From local machine to GitHub:**
```bash
git add .
git commit -m "Your commit message"
git push github master:main
```

**From Overleaf to GitHub:**
- In Overleaf: **Menu → Sync → Push to GitHub**

**From GitHub to Overleaf:**
- In Overleaf: **Menu → Sync → Pull latest version from GitHub**

> **Notes:**
> - `master` is your local branch; `main` is GitHub's default branch
> - Use `master:main` to push your local master to GitHub's main
> - Always commit changes before pushing
> - The Overleaf Sync feature keeps your project synchronized with GitHub

---

## Part 2: Set Up Claude (Cowork) to Access Your Resume

### Step 10: Grant Claude Access to Your Resume Folder

- Open the Claude desktop app and switch to **Cowork mode**
- Ask Claude to access your resume folder, e.g.:
  > *"Please access my resume folder at `/path/to/your/resume/folder`"*
- Approve the folder access request when prompted

Claude now has read and write access to your `main.tex` file.

### Step 11: Save a Backup of Your Master Resume

Ask Claude:
> *"Save a backup of main.tex as main_original.tex"*

Claude will run:
```bash
cp main.tex main_original.tex
```

This preserves your master resume. For every new job application, Claude will reset from `main_original.tex` before making changes — so tailored versions never accumulate on top of each other.

---

## Part 3: Trigger the Automated Resume Tailoring Pipeline

Rather than tailoring the resume manually in chat, you can run a dedicated pipeline that handles the entire workflow in its own isolated session.

### Step 12: Run the `tailor-resume` Task

- Open the Claude desktop app
- Go to the **Scheduled** section in the sidebar
- Find the **tailor-resume** task and click **Run now**

Claude will open a fresh session and guide you through the following automatically:

1. Ask for the **company name**, **role title**, and **job description** (paste the full JD)
2. Reset from `main_original.tex` — never touches the master copy
3. Analyze the JD for key skills, tools, and framing
4. Create a new tailored file named `{Company}_{Role}_{YYYY-MM-DD}.tex`
5. Rewrite the summary, experience bullets, and skills section to match the role
6. Trim content as needed to stay on one page
7. Commit and push the new `.tex` file to both GitHub and Overleaf remotes:

```bash
git add {Company}_{Role}_{YYYY-MM-DD}.tex
git commit -m "Tailor resume for {Role} at {Company} ({date})"
git push github master:main
git push origin master
```

No PDF compilation happens locally — Overleaf handles that.

---

## Part 4: Review, Edit, and Finalize

### Step 14: Sync and Review in Overleaf

- In your Overleaf project, go to **Menu → Sync → Pull latest version from GitHub**
- Overleaf will compile the updated `main.tex` automatically
- Review the PDF preview to check that content is accurate and fits on one page

### Step 15: Make Manual Edits (if needed)

**Option A — Edit in Overleaf (recommended for visual editing):**
- Edit directly in the Overleaf editor with live preview
- When done, push back to GitHub from Overleaf: **Menu → Sync → Push to GitHub**

**Option B — Ask Claude to make specific changes:**
- Tell Claude exactly what to fix, e.g.:
  > *"Change the summary to mention X" or "Remove the third bullet in the second role"*
- Claude edits `main.tex` and pushes again — then sync in Overleaf

### Step 16: Download the Final PDF

- In Overleaf: **Menu → Download PDF**

---

## Summary of the Workflow

```
main_original.tex  (master — never modified)
       │
       ▼
Run "tailor-resume" task in Claude sidebar
       │
       ▼
Paste company, role, and job description when prompted
       │
       ▼
Claude creates {Company}_{Role}_{Date}.tex and pushes to GitHub + Overleaf
       │
       ▼
Open Overleaf → Sync → compile → review PDF preview
       │
       ├── Looks good → Download PDF from Overleaf
       │
       └── Needs edits → Edit in Overleaf or re-run task → sync again
```

---

## Key Principles

- **Always reset from the master.** Never build tailored versions on top of each other. Each job application starts from `main_original.tex`.
- **Stay on one page.** If content overflows, trim the least relevant experience or reduce bullet points rather than shrinking font size.
- **Use factual numbers.** Quantify impact where possible (e.g., "100K+ daily requests", "22 peer-reviewed papers"). Never fabricate metrics.
- **Match JD language.** Mirror the exact tools and terminology used in the job description — this helps with ATS (Applicant Tracking Systems) keyword matching.
- **Keep the master resume comprehensive.** Your `main_original.tex` should contain all experience and skills. Tailoring means selecting and emphasizing, not inventing.
