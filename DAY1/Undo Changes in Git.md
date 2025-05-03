Thanks for sharing the error — you're very close! The problem here is with the **remote URL format**. Let's break it down and fix it:

---

### ❌ What's Wrong:

```bash
https://github.com/<ambika-k-devops>/<https://github.com/airtel-devops-ambika/MYDEVOPS-ALL-PRACTICE>.git
```

This is **not** a valid Git URL. You accidentally included **extra angle brackets and nested another GitHub URL** inside.

---

### ✅ What It Should Be:

Assuming your GitHub repo is located here:
`https://github.com/airtel-devops-ambika/MYDEVOPS-ALL-PRACTICE.git`
Use **only that** as the remote URL:

```bash
git remote set-url origin https://github.com/airtel-devops-ambika/MYDEVOPS-ALL-PRACTICE.git
```

Then try pushing again:

```bash
git push -u origin master
```

---

### 💡 Fixing it Step-by-Step:

1. **Set correct remote URL**:

```bash
git remote set-url origin https://github.com/airtel-devops-ambika/MYDEVOPS-ALL-PRACTICE.git
```

2. **Check which branch you're on**:

```bash
git branch
```

You’ll likely see `master`. If not, create one:

```bash
git checkout -b master
```

3. **Push to GitHub**:

```bash
git push -u origin master
```

---

Would you like help confirming if your local repo is set up correctly (e.g., `.git` folder, staging, commits)?
- -----------------------------------------------------------------------------
Got it! To **undo changes in Git**, there are several ways depending on what exactly you want to undo. Here's a quick guide — choose the one that matches your situation:

---

### 🔁 **1. Undo Unstaged Local Changes (not added with `git add`)**

If you edited files but haven't staged them:

```bash
git checkout -- <filename>
```

Or to discard all:

```bash
git restore .    # Git 2.23+
```

---

### 🗑️ **2. Undo Staged Changes (you ran `git add`, but not `commit`)**

Unstage files but keep the changes in the file:

```bash
git reset <filename>
```

Or all files:

```bash
git reset
```

---

### ⏪ **3. Undo the Last Commit (but keep your code)**

If you committed but want to undo it (safe edit):

```bash
git reset --soft HEAD~1
```

To unstage and undo the commit (keep changes in working directory):

```bash
git reset --mixed HEAD~1
```

---

### 🧨 **4. Undo Last Commit and Delete All Changes**

⚠️ This is destructive — it will delete the commit and all file changes:

```bash
git reset --hard HEAD~1
```

---

### 🧹 **5. Undo Push (on remote)**

If you already pushed and want to undo:

```bash
git reset --hard HEAD~1
git push origin HEAD --force
```

> ⚠️ Use `--force` carefully — it rewrites history on the remote.

---

Can you tell me **which step you want to undo** (unstaged, staged, commit, or pushed)? I’ll give a precise command.
