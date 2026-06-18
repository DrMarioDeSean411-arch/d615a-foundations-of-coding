# SETUP.md — Deploy D615A Practice Exam to GitHub Pages
## Windows Command Prompt Guide

Follow every step in order. Do not skip steps.

---

## Prerequisites

Before you start, confirm you have:
- [ ] A GitHub account at github.com (username: DrMarioDeSean411-arch)
- [ ] Git installed — download from https://git-scm.com/download/win if needed
- [ ] The three repo files downloaded to your Desktop:
  - `d615a_full_practice_exam.html`
  - `README.md`
  - `SETUP.md`

---

## Step 1 — Create the new repository on GitHub

1. Go to https://github.com/new
2. Fill in the form:
   - **Repository name:** `d615a-foundations-of-coding`
   - **Description:** `Full practice exam for WGU D615A Foundations of Coding — 80 auto-graded questions across 4 sections`
   - **Visibility:** Public
   - **Do NOT** check "Add a README file"
   - **Do NOT** check "Add .gitignore"
   - **Do NOT** check "Choose a license"
3. Click **Create repository**

You will land on an empty repo page. Leave it open.

---

## Step 2 — Open Command Prompt

Press `Windows + R`, type `cmd`, press Enter.

---

## Step 3 — Create your project folder and move files

```
mkdir %USERPROFILE%\Desktop\d615a-foundations-of-coding
cd %USERPROFILE%\Desktop\d615a-foundations-of-coding
```

Now copy your three downloaded files into this folder using File Explorer, or run:

```
copy %USERPROFILE%\Downloads\d615a_full_practice_exam.html %USERPROFILE%\Desktop\d615a-foundations-of-coding\
copy %USERPROFILE%\Downloads\README.md %USERPROFILE%\Desktop\d615a-foundations-of-coding\
copy %USERPROFILE%\Downloads\SETUP.md %USERPROFILE%\Desktop\d615a-foundations-of-coding\
```

Confirm the files are there:

```
dir
```

You should see all three files listed.

---

## Step 4 — Configure Git (first time only)

If you have used Git on this machine before, skip this step.

```
git config --global user.email "mario.booker@wgu.edu"
git config --global user.name "DrMarioDeSean411-arch"
```

---

## Step 5 — Initialize the repository and commit

```
cd %USERPROFILE%\Desktop\d615a-foundations-of-coding
git init
git add .
git commit -m "Initial commit: D615A full practice exam, README, SETUP"
```

You should see output ending with something like:
```
[main (root-commit) abc1234] Initial commit: D615A full practice exam, README, SETUP
 3 files changed, ...
```

---

## Step 6 — Connect to GitHub and push

```
git branch -M main
git remote add origin https://github.com/DrMarioDeSean411-arch/d615a-foundations-of-coding.git
git push -u origin main
```

Git will ask for your GitHub credentials:
- **Username:** `DrMarioDeSean411-arch`
- **Password:** use a **Personal Access Token**, NOT your GitHub account password

**To create a Personal Access Token (PAT):**
1. Go to https://github.com/settings/tokens
2. Click **Generate new token (classic)**
3. Name it `d615a-deploy`
4. Set expiration to 90 days
5. Check the **repo** scope (top checkbox under scopes)
6. Click **Generate token** at the bottom
7. **Copy the token immediately** — you cannot see it again after leaving the page

Paste the token when Command Prompt asks for your password. The characters will not appear on screen — that is normal. Press Enter.

---

## Step 7 — Enable GitHub Pages

1. Go to https://github.com/DrMarioDeSean411-arch/d615a-foundations-of-coding
2. Click **Settings** in the top navigation bar
3. Click **Pages** in the left sidebar (under "Code and automation")
4. Under **Source**, select **Deploy from a branch**
5. Under **Branch**, set it to `main` and folder `/` (root)
6. Click **Save**

Wait 2–3 minutes, then refresh the Settings → Pages screen. You will see:

```
Your site is live at https://DrMarioDeSean411-arch.github.io/d615a-foundations-of-coding/
```

---

## Step 8 — Verify the live exam

Open a browser and go to:

```
https://DrMarioDeSean411-arch.github.io/d615a-foundations-of-coding/d615a_full_practice_exam.html
```

The full exam should load. Test a question in each section to confirm auto-grading works.

Update the README.md link to this URL if needed, then push:

```
cd %USERPROFILE%\Desktop\d615a-foundations-of-coding
git add README.md
git commit -m "Update live exam URL in README"
git push
```

---

## Making Updates Later

When you update the exam file or README:

```
cd %USERPROFILE%\Desktop\d615a-foundations-of-coding
git add .
git commit -m "Brief description of what changed"
git push
```

GitHub Pages rebuilds automatically within 1–2 minutes.

---

## Share This Link With Students

Once live, share this direct link in your course:

```
https://DrMarioDeSean411-arch.github.io/d615a-foundations-of-coding/d615a_full_practice_exam.html
```

Students can also find instructions, the scoring guide, and the email submission requirements at the repo homepage:

```
https://github.com/DrMarioDeSean411-arch/d615a-foundations-of-coding
```

---

## Troubleshooting

**`git push` fails with "remote: Repository not found"**
```
git remote -v
```
If the URL is wrong:
```
git remote set-url origin https://github.com/DrMarioDeSean411-arch/d615a-foundations-of-coding.git
git push -u origin main
```

**"Authentication failed" or "Support for password authentication was removed"**
You need a Personal Access Token, not your GitHub password. See Step 6 above.

**GitHub Pages shows a 404 error**
- Wait 3–5 minutes and hard-refresh (Ctrl + Shift + R)
- Confirm in Settings → Pages that branch is `main` and folder is `/` (root)
- Confirm `d615a_full_practice_exam.html` is in the root of the repo (not in a subfolder)

**Exam loads but shows blank or broken**
- Open browser DevTools (F12) → Console tab
- If you see a CORS error, the file may be in a subfolder — move it to root and push again
- Hard-refresh with Ctrl + Shift + R to clear cache

---

*D615A: Foundations of Coding · Western Governors University*  
*Dr. Mario Booker · mario.booker@wgu.edu*
