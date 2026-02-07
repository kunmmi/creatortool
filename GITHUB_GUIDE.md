# 📚 GitHub Version Control Guide

This guide will help you understand and use GitHub for version control as we build this project.

## 🤔 What is Version Control?

Version control (Git) is like a time machine for your code:
- **Saves snapshots** of your project at different points
- **Tracks changes** - see what you changed and when
- **Allows collaboration** - multiple people can work on the same project
- **Safety net** - you can go back to previous versions if something breaks
- **Professional standard** - all real projects use version control

## 🎯 Basic Concepts

### Repository (Repo)
Your project folder that Git tracks. This entire `creatortool` folder will become a repository.

### Commit
A saved snapshot of your project at a specific point in time. Like saving a game - you can return to it later.

### Branch
A separate line of development. Think of it as an alternate timeline.

### Push
Uploading your commits to GitHub (the cloud backup).

### Pull
Downloading changes from GitHub to your computer.

## 📋 Step-by-Step Setup

### Step 1: Create GitHub Account
1. Go to [github.com](https://github.com)
2. Sign up for a free account
3. Verify your email

### Step 2: Create Repository on GitHub
1. Click the **+** icon in top right → **New repository**
2. Name it: `creatortool` (or `creator-publisher`)
3. Description: "Mobile app for cross-platform content creator caption management"
4. Choose **Private** (recommended for now)
5. **DO NOT** check "Initialize with README" (we already have files)
6. Click **Create repository**

### Step 3: Connect Local Project to GitHub

After creating the repo, GitHub will show you commands. We'll run these:

```bash
# Initialize Git in your project (if not done)
git init

# Add all files to Git
git add .

# Create first commit (save snapshot)
git commit -m "Initial commit: Project setup and documentation"

# Connect to GitHub (replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/creatortool.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## 🔄 Daily Workflow

### When You Start Working
```bash
# Pull latest changes (if working on multiple computers)
git pull
```

### When You Finish a Feature/Task
```bash
# 1. See what changed
git status

# 2. Add changed files
git add .

# 3. Commit with descriptive message
git commit -m "Add: User authentication screen"

# 4. Push to GitHub
git push
```

## 📝 Good Commit Messages

Write clear, descriptive commit messages:

✅ **Good:**
- `"Add: User sign-up screen with email validation"`
- `"Fix: Video upload error handling"`
- `"Update: Caption generation rules for TikTok"`

❌ **Bad:**
- `"changes"`
- `"fix stuff"`
- `"update"`

## 🌿 Branch Strategy (For Later)

For now, we'll work on the `main` branch. Later, you can create branches for features:

```bash
# Create a new branch for a feature
git checkout -b feature/draft-management

# Work on your feature...

# When done, merge back to main
git checkout main
git merge feature/draft-management
```

## 🚨 Common Situations

### "I made a mistake, how do I undo?"
```bash
# Undo changes to a file (before committing)
git checkout -- filename.ts

# Undo last commit (keep changes)
git reset --soft HEAD~1
```

### "I want to see what changed"
```bash
# See all changes
git status

# See detailed changes
git diff
```

### "I forgot to pull and now there's a conflict"
```bash
# Pull changes
git pull

# If conflicts occur, Git will mark them
# Fix conflicts, then:
git add .
git commit -m "Resolve merge conflicts"
git push
```

## 📊 Viewing History

```bash
# See commit history
git log

# See a visual graph
git log --oneline --graph
```

## 🔐 Authentication

GitHub requires authentication. Options:

1. **Personal Access Token** (Recommended)
   - GitHub → Settings → Developer settings → Personal access tokens
   - Generate token with `repo` permissions
   - Use token as password when pushing

2. **GitHub CLI** (Advanced)
   ```bash
   gh auth login
   ```

## ✅ Best Practices

1. **Commit often** - Small, frequent commits are better than huge ones
2. **Commit before major changes** - Save your work before big refactors
3. **Write clear messages** - Future you will thank you
4. **Pull before push** - Always get latest changes first
5. **Don't commit secrets** - `.env` files are in `.gitignore` for a reason

## 🎓 Learning Resources

- [GitHub Docs](https://docs.github.com)
- [Git Basics](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics)
- [Visual Git Guide](https://learngitbranching.js.org)

## 💡 Pro Tips

- Use GitHub Desktop app if you prefer a GUI
- GitHub Actions can automate testing (we'll add this later)
- Issues and Projects help track tasks
- Pull Requests are great for code review (even solo projects)

---

**Remember**: Git is a tool, not a burden. It will save you time and stress in the long run!

