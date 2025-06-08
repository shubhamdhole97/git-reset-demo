# 🧪 Git Reset Practical Guide

Author: **Shubham**

This guide demonstrates how to use `git reset` with practical examples using a simple file.

---

## 🔧 Setup Instructions

```bash
# Step 1: Initialize a new repo
mkdir git-reset-demo && cd git-reset-demo
git init

# Step 2: Create first commit
echo "line 1" > file.txt
git add file.txt
git commit -m "Commit 1: Add line 1"

# Step 3: Add two more commits
echo "line 2" >> file.txt
git commit -am "Commit 2: Add line 2"

echo "line 3" >> file.txt
git commit -am "Commit 3: Add line 3"
```

Check Git history:
```bash
git log --oneline
```

---

## 🧠 Understanding Git Reset Types

### ✅ `git reset --soft HEAD~1`

- Moves HEAD back
- **Keeps staging area and working directory**
- Changes are still **staged**

```bash
git reset --soft HEAD~1
git status
```

You will see:
```
Changes to be committed: line 3
```

---

### ✅ `git reset --mixed HEAD~1`

- Moves HEAD back
- **Clears staging area**
- Keeps file changes in working directory

```bash
git reset --mixed HEAD~1
git status
```

You will see:
```
Changes not staged for commit: line 3
```

---

### ⚠️ `git reset --hard HEAD~1`

- Moves HEAD back
- **Deletes** changes from both staging area and working directory
- Use with caution!

```bash
git reset --hard HEAD~1
```

You will see:
```
Everything rolled back to previous commit state
```

---

## 📊 Summary Table

| Command                  | HEAD Moved | Index (Staging) | Working Dir | Safe to Use? |
|--------------------------|-------------|------------------|--------------|---------------|
| `git reset --soft`       | ✅           | ✅                | ✅            | ✅ Yes         |
| `git reset --mixed`      | ✅           | ❌                | ✅            | ✅ Yes         |
| `git reset --hard`       | ✅           | ❌                | ❌            | ⚠️ No (destructive) |

---

## 🧹 Bonus Tip: Undo a Reset

If you accidentally run a reset:
```bash
git reflog
# Find the old HEAD (e.g., abc1234)
git reset --hard abc1234
```
