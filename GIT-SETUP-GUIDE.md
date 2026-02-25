# Git Setup Guide for Your PM Portfolio

This guide will walk you through setting up your PM portfolio on GitHub step-by-step, assuming you're completely new to Git and GitHub.

---

## Part 1: Prerequisites & Initial Setup

### Step 1: Create a GitHub Account
1. Go to https://github.com
2. Click "Sign up" in the top right
3. Follow the prompts to create your account
4. Choose a professional username (e.g., your name or initials)
5. Verify your email address

### Step 2: Install Git on Your Computer

**For Windows:**
1. Download Git from https://git-scm.com/download/win
2. Run the installer
3. Use all default settings (just keep clicking "Next")
4. When finished, open "Git Bash" from your Start menu

**For Mac:**
1. Open Terminal (press Cmd+Space, type "Terminal", press Enter)
2. Type: `git --version` and press Enter
3. If prompted, click "Install" to install developer tools
4. OR download from https://git-scm.com/download/mac

**For Linux:**
1. Open Terminal
2. Type: `sudo apt-get install git` (Ubuntu/Debian)
3. OR: `sudo yum install git` (Fedora/RedHat)

### Step 3: Configure Git with Your Information

Open your terminal (Git Bash on Windows, Terminal on Mac/Linux) and run these commands:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

**Replace "Your Name" and the email with your actual information** (use the same email you used for GitHub).

---

## Part 2: Download Your Portfolio Files

### Step 1: Get the Portfolio Files
You should have a folder called `pm-portfolio` with all your case study files. Place this folder somewhere easy to find, like your Desktop or Documents folder.

### Step 2: Navigate to Your Portfolio Folder

**Windows (Git Bash):**
```bash
cd ~/Desktop/pm-portfolio
```

**Mac/Linux:**
```bash
cd ~/Desktop/pm-portfolio
```

**Note:** If your folder is in a different location, adjust the path accordingly.

---

## Part 3: Create a GitHub Repository

### Step 1: Create a New Repository on GitHub
1. Go to https://github.com
2. Log in to your account
3. Click the green "New" button (top left, or the "+" icon in the top right → "New repository")
4. Fill in the details:
   - **Repository name:** `pm-portfolio` (or any name you prefer)
   - **Description:** "Product Management case studies and portfolio"
   - **Public or Private:** Choose Public (so employers can see it)
   - **DO NOT** check "Initialize this repository with a README"
   - **DO NOT** add .gitignore or license yet
5. Click "Create repository"

### Step 2: Copy Your Repository URL
After creating the repository, you'll see a page with setup instructions. Look for the URL that looks like:
```
https://github.com/YOUR-USERNAME/pm-portfolio.git
```
**Copy this URL** - you'll need it in the next step.

---

## Part 4: Push Your Portfolio to GitHub

Now we'll upload your portfolio files to GitHub. Run these commands one at a time in your terminal:

### Step 1: Initialize Git in Your Portfolio Folder
```bash
git init
```
**What this does:** Creates a new Git repository in your current folder.

### Step 2: Add All Your Files to Git
```bash
git add .
```
**What this does:** Stages all your files to be committed (the `.` means "everything in this folder").

### Step 3: Create Your First Commit
```bash
git commit -m "Initial commit: DoorDash nutrition tracking case study"
```
**What this does:** Saves a snapshot of your files with a message describing what's in it.

### Step 4: Rename the Default Branch to "main"
```bash
git branch -M main
```
**What this does:** Renames your branch to "main" (GitHub's standard).

### Step 5: Connect to Your GitHub Repository
```bash
git remote add origin https://github.com/YOUR-USERNAME/pm-portfolio.git
```
**IMPORTANT:** Replace `YOUR-USERNAME` and `pm-portfolio` with your actual GitHub username and repository name from Step 3.2 above.

**What this does:** Links your local folder to the GitHub repository you created.

### Step 6: Push Your Files to GitHub
```bash
git push -u origin main
```
**What this does:** Uploads all your files to GitHub.

**If prompted for username and password:**
- Username: Your GitHub username
- Password: You'll need to use a Personal Access Token (see instructions below)

---

## Part 5: Creating a GitHub Personal Access Token (If Needed)

If Git asks for a password, you can't use your GitHub password anymore. You need a Personal Access Token:

1. Go to https://github.com/settings/tokens
2. Click "Generate new token" → "Generate new token (classic)"
3. Give it a name like "Portfolio Upload"
4. Check the box next to "repo" (this gives it permission to access repositories)
5. Scroll down and click "Generate token"
6. **COPY THE TOKEN IMMEDIATELY** (you won't be able to see it again!)
7. Use this token as your password when Git asks

---

## Part 6: View Your Portfolio on GitHub

1. Go to https://github.com/YOUR-USERNAME/pm-portfolio
2. You should see all your files listed!
3. Click on folders and files to view them

---

## Part 7: Enable GitHub Pages (Make Your Portfolio Live!)

To make your portfolio accessible as a website:

1. Go to your repository on GitHub
2. Click "Settings" (top right)
3. Scroll down and click "Pages" in the left sidebar
4. Under "Source", select "main" branch
5. Click "Save"
6. Wait a few minutes, then refresh the page
7. You'll see a message like: "Your site is published at https://YOUR-USERNAME.github.io/pm-portfolio/"

Now anyone can view your portfolio at that URL!

---

## Part 8: Making Updates Later

When you want to add or change files in your portfolio:

### Step 1: Navigate to Your Portfolio Folder
```bash
cd ~/Desktop/pm-portfolio
```

### Step 2: Make Your Changes
Edit files, add new ones, etc.

### Step 3: Stage Your Changes
```bash
git add .
```

### Step 4: Commit Your Changes
```bash
git commit -m "Describe what you changed"
```
(Replace the message with what you actually changed, e.g., "Added case study 2")

### Step 5: Push to GitHub
```bash
git push
```

**That's it!** Your changes will appear on GitHub in a few seconds.

---

## Common Commands Reference

Here's a quick reference for common Git commands:

| Command | What It Does |
|---------|-------------|
| `git status` | Shows what files have changed |
| `git add .` | Stages all changes for commit |
| `git add filename.md` | Stages a specific file |
| `git commit -m "message"` | Saves a snapshot with a description |
| `git push` | Uploads commits to GitHub |
| `git pull` | Downloads changes from GitHub |
| `git log` | Shows history of commits |

---

## Troubleshooting

### "Permission denied" or "Authentication failed"
→ You need to set up a Personal Access Token (see Part 5 above)

### "fatal: not a git repository"
→ Make sure you're in the right folder. Run `pwd` to check your current location.

### "fatal: remote origin already exists"
→ Run `git remote remove origin` first, then try the `git remote add` command again.

### Changes not showing on GitHub Pages
→ Wait 2-5 minutes after pushing. GitHub Pages can take time to update.

### Want to start over?
→ Delete the `.git` folder in your portfolio folder (it's hidden), then start from Part 4 again.

---

## Best Practices

1. **Commit often:** Don't wait until everything is perfect. Commit after each meaningful change.

2. **Write clear commit messages:** 
   - ✅ "Added business case document with financial projections"
   - ❌ "Updates"

3. **Don't commit sensitive information:** Never push API keys, passwords, or personal information.

4. **Use .gitignore:** Create a file called `.gitignore` to exclude files you don't want tracked (like `.DS_Store` on Mac)

Example `.gitignore` file:
```
.DS_Store
*.tmp
node_modules/
```

---

## Next Steps

### Add a README
Create a file called `README.md` in your portfolio folder with information about your portfolio. Example:

```markdown
# Product Management Portfolio

## About Me
[Your brief bio]

## Case Studies
- [DoorDash Nutrition Tracking](case-study-1/) - Health-focused feature development

## Contact
- Email: your.email@example.com
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/yourprofile)
```

Then commit and push it:
```bash
git add README.md
git commit -m "Added portfolio README"
git push
```

### Share Your Portfolio
Send employers this link: `https://YOUR-USERNAME.github.io/pm-portfolio/`

---

## Getting Help

- **GitHub Docs:** https://docs.github.com
- **Git Tutorial:** https://try.github.io
- **Stack Overflow:** Search for Git questions - most have been answered!
- **GitHub Community:** https://github.community

---

## Summary: The Complete Flow

Every time you want to update your portfolio:

1. Make your changes (edit files, add files)
2. `git add .`
3. `git commit -m "Description of changes"`
4. `git push`
5. Wait a few minutes for GitHub Pages to update
6. Share your URL with the world!

**Congratulations! You now have a professional PM portfolio on GitHub!** 🎉
