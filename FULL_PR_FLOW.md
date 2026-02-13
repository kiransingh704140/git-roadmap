# 🚀 Complete Guide: Fork → Open Source Contribution → Pull Request (With Fetch, Merge, Pull & Rebase Explained)

This guide explains the **entire open-source workflow** in a simple but detailed way so beginners can clearly understand how everything works.

---

# 🌍 1. What is Forking?

Forking means creating **your own copy** of someone else's repository under your GitHub account.

Example:

Original repository:

```
https://github.com/original-user/cool-project
```

After forking:

```
https://github.com/your-username/cool-project
```

Now you can safely make changes without affecting the original project.

---

# 📥 2. Step-by-Step: Fork → Clone → Setup

## ✅ Step 1: Fork the Repository

1. Open the repository on GitHub.
2. Click the **Fork** button (top right).
3. Select your account.
4. GitHub creates a copy in your profile.

---

## ✅ Step 2: Clone Your Fork Locally

Clone your fork to your computer:

```bash
git clone https://github.com/your-username/cool-project.git
```

Move into the project folder:

```bash
cd cool-project
```

---

## ✅ Step 3: Add Original Repo as Upstream

This step connects your local project to the original repository.

```bash
git remote add upstream https://github.com/original-user/cool-project.git
```

Check remotes:

```bash
git remote -v
```

You should see:

```
origin    https://github.com/your-username/cool-project.git
upstream  https://github.com/original-user/cool-project.git
```

* `origin` → Your fork
* `upstream` → Original repository

---

# 🌱 3. Create a Feature Branch (Never Work on main)

Always create a new branch for changes.

```bash
git checkout -b fix-navbar-bug
```

Now you're working on a separate branch.

---

# 💾 4. Make Changes and Commit

After editing files:

```bash
git add .
git commit -m "Fix navbar alignment issue"
```

Good commit messages should clearly describe what you changed.

---

# ⬆️ 5. Push Changes to Your Fork

```bash
git push origin fix-navbar-bug
```

Your branch is now uploaded to GitHub.

---

# 🔥 6. Open a Pull Request (PR)

1. Go to your fork on GitHub.
2. Click **Compare & Pull Request**.
3. Ensure:

   * Base repository = Original repo
   * Base branch = main
   * Compare branch = fix-navbar-bug
4. Add description.
5. Click **Create Pull Request**.

Now maintainers will review your code.

---

# 🔄 7. Understanding Important Git Commands

---

# 📥 What is `git fetch`?

Downloads changes from a remote repository.

It does NOT change your working files.

```bash
git fetch upstream
```

This updates remote tracking branches only.

---

# 📥 What is `git pull`?

`git pull` = `git fetch` + `git merge`

It downloads changes and immediately merges them into your current branch.

```bash
git pull upstream main
```

---

# 🔀 What is `git merge`?

Merge combines two branches.

Example:

```bash
git checkout main
git merge fix-navbar-bug
```

Merge creates a new "merge commit".

Before merge:

```
A---B---C main
      \
       D---E fix-navbar-bug
```

After merge:

```
A---B---C------M
      \        /
       D---E----
```

---

# 🔁 What is `git rebase`?

Rebase moves your branch on top of another branch.

```bash
git checkout fix-navbar-bug
git fetch upstream
git rebase upstream/main
```

Before rebase:

```
A---B---C main
      \
       D---E fix-navbar-bug
```

After rebase:

```
A---B---C---D'---E'
```

No merge commit. Cleaner history.

---

# ⚔️ Merge vs Rebase

| Merge                    | Rebase                   |
| ------------------------ | ------------------------ |
| Keeps original history   | Rewrites history         |
| Creates merge commit     | No merge commit          |
| Safe for shared branches | Avoid on shared branches |

---

# 🔄 8. Keeping Your Fork Updated

Original projects keep changing. You must sync your fork.

### Step 1: Fetch updates

```bash
git fetch upstream
```

### Step 2: Update local main

Using merge:

```bash
git checkout main
git merge upstream/main
```

Or using rebase (cleaner):

```bash
git checkout main
git rebase upstream/main
```

### Step 3: Push updated main to your fork

```bash
git push origin main
```

---

# 🚨 Handling Merge Conflicts

If Git shows:

```
CONFLICT (content): Merge conflict in index.js
```

Steps:

1. Open the conflicted file.
2. Fix the conflict manually.
3. Then:

For merge:

```bash
git add .
git commit
```

For rebase:

```bash
git add .
git rebase --continue
```

---

# 🎯 Full Open Source Workflow Summary

```
Fork
↓
Clone
↓
Add upstream
↓
Create branch
↓
Make changes
↓
Commit
↓
Push
↓
Open PR
↓
Fetch & Rebase if needed
↓
PR Merged 🎉
```

---

# 💡 Best Practices

* Never work directly on `main`
* Always create feature branches
* Write meaningful commit messages
* Keep commits small and focused
* Sync with upstream before opening PR
* Read CONTRIBUTING.md before contributing

---

# 🏁 Final Understanding

* `fetch` → Download only
* `pull` → Download + merge
* `merge` → Combine branches
* `rebase` → Move branch for clean history
* `PR` → Request to merge changes into original repo

---
