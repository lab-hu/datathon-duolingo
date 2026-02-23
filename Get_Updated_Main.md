# Getting Updated Main Branch

## ⚠️ If You Have Local Uncommitted Changes

**IMPORTANT:** If you have local changes, do NOT directly pull the updated `main` as it may overwrite your work!

Follow these steps first:

```bash
# Create a new branch to save your changes
git checkout -b my-feature-branch

# Stage all your changes
git add .

# Commit your changes
git commit -m "WIP: [describe your changes]"

# Now switch to main (your changes are safely saved on my-feature-branch)
git checkout main

# Update main with the latest changes
git fetch origin
git pull origin main

# Later, you can merge your feature branch into main or create a PR
git checkout my-feature-branch
# ... continue working, or create a PR when ready
```

**What this does:**
- ✅ Saves your work on a new branch (`my-feature-branch`)
- ✅ Safely updates your local `main` without losing changes
- ✅ Keeps your changes separate for review/merging

---

## Option 1: Pull the Latest Main Branch

Use this if you already have the repository cloned and want to update your local `main` branch with the latest changes from remote. 

```bash
# Update remote references
git fetch origin

# Switch to main branch
git checkout main

# Pull latest changes
git pull origin main
```

---

## Option 2: Clone Fresh

Use this if you're starting fresh or setting up a new codespace and want to clone the repository with the `main` branch as default.

```bash
git clone https://github.com/lab-hu/datathon-duolingo.git
cd datathon-duolingo
git checkout main
```

Or with `main` as the auto-default branch:

```bash
git clone https://github.com/lab-hu/datathon-duolingo.git --branch main
cd datathon-duolingo
```

---

## Quick Verification

After using either option, verify you have the latest changes:

```bash
# Check current branch
git branch

# View latest commits on main
git log main -5 --oneline

# View the analysis notebook
git show main:analysis.ipynb
```

