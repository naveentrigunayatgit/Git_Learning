
# 🎯 GIT MASTERCLASS - COMPLETE NOTES
## Based on Varun Joshi's 3-Part Series

---

## 📺 ANIMATED VISUAL OVERVIEW

```
╔══════════════════════════════════════════════════════════════════════╗
║                    THE GIT MASTERCLASS JOURNEY                        ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   PART 1: FOUNDATIONS          PART 2: COLLABORATION                 ║
║   ┌─────────────────┐          ┌─────────────────┐                   ║
║   │ • Why Git       │          │ • Remote Repos  │                   ║
║   │ • Architecture  │          │ • Authentication│                   ║
║   │ • Commits       │          │ • Push/Pull     │                   ║
║   │ • Branching     │          │ • Pull Requests │                   ║
║   │ • Merging       │          │ • Code Review   │                   ║
║   │ • Conflicts     │          │ • Git Stash     │                   ║
║   │ • Reset/Revert  │          │ • Production    │                   ║
║   └─────────────────┘          └─────────────────┘                   ║
║                                                                       ║
║   PART 3: ADVANCED HISTORY                                           ║
║   ┌─────────────────────────────────────────────────────────┐        ║
║   │ • Rebase          • Interactive Rebase                   │        ║
║   │ • Squash Merge    • Cherry-Pick                         │        ║
║   │ • History Rewriting • Production Integration Strategies  │        ║
║   └─────────────────────────────────────────────────────────┘        ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

# 📚 PART 1: GIT FOUNDATIONS

## 🎬 Chapter 1: Why Git Exists

### The Problem Before Git

```
╔══════════════════════════════════════════════════════════════════════╗
║                    LIFE WITHOUT GIT (FILESHARE NIGHTMARE)             ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  📁 SHARED FILESHARE (NFS/SMB)                              │    ║
║   │                                                              │    ║
║   │   👨‍💻 Dev 1 ──────┐                                         │    ║
║   │                  │                                         │    ║
║   │   👩‍💻 Dev 2 ──────┼──▶ 📄 app.js ◀── WHO EDITED LAST?      │    ║
║   │                  │                                         │    ║
║   │   👨‍💻 Dev 3 ──────┘                                         │    ║
║   │                                                              │    ║
║   │   Problems:                                                  │    ║
║   │   ❌ Overwrites each other's work                           │    ║
║   │   ❌ No reliable history                                    │    ║
║   │   ❌ Rollback is manual & error-prone                       │    ║
║   │   ❌ Collaboration is chaotic                               │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Git's Solution

```
┌─────────────────────────────────────────────────────────────────────┐
│                    GIT = DISTRIBUTED VERSION CONTROL                 │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│   ✅ Every developer has FULL repository history locally            │
│   ✅ Commits = snapshots (checkpoints)                              │
│   ✅ Branches = isolated parallel development                       │
│   ✅ Push/Pull = synchronization with remote                        │
│   ✅ Works offline (no constant network dependency)                 │
│                                                                      │
│   Created by: Linus Torvalds (2005)                                 │
│   Same legend who created Linux kernel!                             │
│   Fun fact: Git was developed WITHOUT Git!                          │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Git vs GitHub

```
╔══════════════════════════════════════════════════════════════════════╗
║                    GIT vs GITHUB                                      ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   ┌─────────────────────┐        ┌─────────────────────┐            ║
║   │       GIT           │        │      GITHUB         │            ║
║   │   (Software)        │        │   (Service)         │            ║
║   ├─────────────────────┤        ├─────────────────────┤            ║
║   │ • Installed locally │        │ • Cloud-hosted      │            ║
║   │ • Works offline     │        │ • Requires internet │            ║
║   │ • Tracks changes    │        │ • Hosts repos       │            ║
║   │ • Free & open       │        │ • Free tier + paid  │            ║
║   │ • Linus Torvalds    │        │ • Microsoft owned   │            ║
║   └─────────────────────┘        └─────────────────────┘            ║
║                                                                       ║
║   Other Remote Options:                                              ║
║   • GitLab        • Bitbucket                                       ║
║   • AWS CodeCommit • Azure Repos                                    ║
║   • Self-hosted (Gitea, Gitolite)                                   ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

## 🎬 Chapter 2: Git Installation & Initial Setup

### Windows Installation

```
┌─────────────────────────────────────────────────────────────────────┐
│                    WINDOWS INSTALLATION                              │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  1. Go to: https://git-scm.com/                                     │
│                                                                      │
│  2. Click "Download for Windows"                                    │
│                                                                      │
│  3. Run installer → Next → Next → Install → Finish                  │
│                                                                      │
│  4. ✅ Git Bash installed automatically!                            │
│                                                                      │
│  5. Verify: Open Git Bash → git --version                           │
│     Expected: git version 2.xx.x.windows.x                          │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Initial Configuration (CRITICAL)

```bash
# Set your identity (ONE TIME SETUP)
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set VS Code as default editor (Windows)
git config --global core.editor "code --wait"

# Enable VS Code command in PATH (Windows)
# Open VS Code → Ctrl+Shift+P → "Shell Command: Install 'code' command in PATH"

# View all configurations
git config --list

# View specific config
git config user.name
git config user.email
```

### Configuration Levels

```
╔══════════════════════════════════════════════════════════════════════╗
║                    GIT CONFIGURATION HIERARCHY                        ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  SYSTEM LEVEL (--system)                                     │    ║
║   │  Location: C:\Program Files\Git\etc\gitconfig               │    ║
║   │  Applies to: ALL users on machine                           │    ║
║   │  Precedence: LOWEST                                         │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                              │                                       ║
║                              ▼                                       ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  GLOBAL LEVEL (--global) ⭐ MOST COMMON                      │    ║
║   │  Location: C:\Users\YourName\.gitconfig                     │    ║
║   │  Applies to: ALL repos for YOUR user                        │    ║
║   │  Precedence: MEDIUM                                         │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                              │                                       ║
║                              ▼                                       ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  LOCAL LEVEL (--local)                                       │    ║
║   │  Location: .git/config (inside repo)                        │    ║
║   │  Applies to: ONLY that specific repository                  │    ║
║   │  Precedence: HIGHEST                                        │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   Precedence: Local > Global > System                                ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

## 🎬 Chapter 3: Git Architecture & Core Constructs

### The Three Pillars

```
╔══════════════════════════════════════════════════════════════════════╗
║                    GIT ARCHITECTURE                                   ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐             ║
║   │  WORKING    │    │   STAGING   │    │   LOCAL     │             ║
║   │  DIRECTORY  │───▶│    AREA     │───▶│    REPO     │             ║
║   │             │    │   (Index)   │    │   (.git)    │             ║
║   └─────────────┘    └─────────────┘    └─────────────┘             ║
║         │                  │                  │                      ║
║         │    git add       │   git commit     │                      ║
║         │                  │                  │                      ║
║         ▼                  ▼                  ▼                      ║
║   ┌─────────────────────────────────────────────────────┐           ║
║   │                                                      │           ║
║   │  Create/Edit    →    Stage    →    Commit           │           ║
║   │  files               files         changes           │           ║
║   │                                                      │           ║
║   └─────────────────────────────────────────────────────┘           ║
║                              │                                       ║
║                              ▼                                       ║
║                    ┌─────────────────┐                               ║
║                    │     REMOTE      │                               ║
║                    │   (GitHub)      │                               ║
║                    └─────────────────┘                               ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### What Each Area Means

| Area | Purpose | Commands |
|------|---------|----------|
| **Working Directory** | Where you create/modify files | `touch`, `vim`, `code` |
| **Staging Area** | Precision control before commit | `git add`, `git rm --cached` |
| **Local Repository** | Permanent snapshot storage | `git commit`, `git log` |
| **Remote Repository** | Collaboration & backup | `git push`, `git pull` |

### The .git Folder (Repository Brain)

```
┌─────────────────────────────────────────────────────────────────────┐
│                    .git FOLDER STRUCTURE                             │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  📁 .git/                                                           │
│  ├── 📄 HEAD           → Points to current branch                   │
│  ├── 📄 config         → Repository configuration                   │
│  ├── 📄 description    → Repository description                     │
│  ├── 📄 index          → Staging area information                   │
│  ├── 📁 hooks/         → Scripts on Git events                      │
│  ├── 📁 info/          → Additional information                     │
│  ├── 📁 logs/          → History of all changes                     │
│  ├── 📁 objects/       → All Git objects (commits, trees, blobs)    │
│  └── 📁 refs/          → References (branches, tags)                │
│      ├── 📁 heads/     → Branch references                          │
│      └── 📁 tags/      → Tag references                             │
│                                                                      │
│  ⚠️ NEVER manually edit files in .git folder!                       │
│  💡 Delete .git = Lose all history!                                 │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 🎬 Chapter 4: Commits - The Heart of Git

### What is a Commit?

```
╔══════════════════════════════════════════════════════════════════════╗
║                    COMMIT = IMMUTABLE SNAPSHOT                        ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   Commit A ──────▶ Commit B ──────▶ Commit C                         ║
║   (parent: null)   (parent: A)     (parent: B)                       ║
║                                                                       ║
║   Each commit contains:                                              ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  • Commit Hash (SHA-1)                                      │    ║
║   │  • Parent Commit Hash                                       │    ║
║   │  • Author Name & Email                                      │    ║
║   │  • Timestamp                                                │    ║
║   │  • Commit Message                                           │    ║
║   │  • Tree Hash (snapshot of files)                            │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   🔑 KEY: Immutable = Cannot change commit hash                     ║
║   (You can change files, but not the commit itself)                 ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Commit Message Best Practices

```
┌─────────────────────────────────────────────────────────────────────┐
│                    ATOMIC COMMITS & MESSAGES                         │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ✅ DO:                                                             │
│  ├── Use imperative mood: "Add feature" not "Added feature"         │
│  ├── Give commands: "Fix bug" not "Fixed bug"                       │
│  ├── Be specific: "Add user login API"                              │
│  ├── One commit = One logical change                                │
│  └── Use prefixes: feature/, fix/, chore/, docs/                    │
│                                                                      │
│  📝 EXAMPLES:                                                       │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  feature: add ArgoCD application deployment pipeline        │    │
│  │  fix: resolve failing Terraform state lock issue            │    │
│  │  chore: upgrade Kubernetes cluster to version 1.28          │    │
│  │  docs: update README with installation steps                │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
│  ❌ DON'T:                                                          │
│  ├── "Fixed stuff"                                                  │
│  ├── "Changes"                                                      │
│  ├── "asdfghjkl"                                                    │
│  └── Multiple unrelated changes in one commit                       │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Essential Commands

```bash
# Check status
git status

# Add specific file
git add filename.txt

# Add all files
git add .

# Commit with message
git commit -m "type: description"

# Add AND commit (tracked files only)
git commit -am "type: description"

# View history
git log
git log --oneline
git log --oneline --graph
git log -n 5 --oneline

# Restore file (discard changes)
git restore filename.txt

# Unstage file
git restore --staged filename.txt
# OR
git rm --cached filename.txt
```

### Understanding Git Log

```
┌─────────────────────────────────────────────────────────────────────┐
│                    GIT LOG OUTPUT                                    │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  commit 4c8a1b2d3e4f5g6h7i8j9k0l1m2n3o4p5q6r7s8  ← Full SHA        │
│  Author: Varun Joshi <cloudwithvj@gmail.com>                        │
│  Date:   Mon Jan 15 10:30:00 2024 +0530                             │
│                                                                      │
│      feat: add file one to codebase           ← Commit message     │
│                                                                      │
│  commit 3b7a2c1d4e5f6g7h8i9j0k1l2m3n4o5p6q7r8s  ← Parent commit    │
│  Author: Varun Joshi <cloudwithvj@gmail.com>                        │
│  Date:   Sun Jan 14 09:15:00 2024 +0530                             │
│                                                                      │
│      chore: initial commit                    ← First commit        │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### HEAD Concept

```
╔══════════════════════════════════════════════════════════════════════╗
║                    HEAD POINTER                                       ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   HEAD → Currently checked out branch → Latest commit                ║
║                                                                       ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │                                                              │    ║
║   │   main:     C1 ── C2 ── C3 ── C4                            │    ║
║   │                              ▲                               │    ║
║   │                              │                               │    ║
║   │                            HEAD                              │    ║
║   │                                                              │    ║
║   │   feature:  C1 ── C2 ── F1 ── F2                            │    ║
║   │                              ▲                               │    ║
║   │                              │                               │    ║
║   │                           (not HEAD)                         │    ║
║   │                                                              │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   💡 Detached HEAD: When HEAD points directly to a commit           ║
║      (not to a branch)                                              ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

## 🎬 Chapter 5: Branching - Parallel Development

### Why Branches?

```
┌─────────────────────────────────────────────────────────────────────┐
│                    BRANCHES = ISOLATED TIMELINES                     │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Primary branch MUST always be releasable                           │
│  (Contains stable, production-ready code)                           │
│                                                                      │
│                        main/master                                   │
│  ─────●─────●─────●─────●─────●─────●─────●─────▶                   │
│        \                   /                                        │
│         \                 /                                         │
│          ●─────●─────●─────●   feature/login                        │
│                                                                      │
│  ✅ Risk Isolation: Don't break stable code                         │
│  ✅ Protected Workflows: No direct commits to main                  │
│  ✅ Parallel Work: Multiple features simultaneously                 │
│  ✅ Controlled Integration: Merge only tested changes               │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### What is a Branch?

```
╔══════════════════════════════════════════════════════════════════════╗
║                    BRANCH = LIGHTWEIGHT POINTER                       ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   A branch is just a pointer to the latest commit!                   ║
║                                                                       ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │                                                              │    ║
║   │   main ──────────────▶ C4 (branch tip)                      │    ║
║   │                                                              │    ║
║   │   feature/login ─────▶ F2 (branch tip)                      │    ║
║   │                                                              │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   🔑 KEY INSIGHTS:                                                  ║
║   • Branch creation does NOT copy files                             ║
║   • Branch creation does NOT create commits                         ║
║   • Just creates a new pointer!                                     ║
║   • New commits move the pointer forward                            ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Branch Naming Convention

```
┌─────────────────────────────────────────────────────────────────────┐
│                    BRANCH NAMING CONVENTION                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Format: type/description                                           │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  feature/  → New features                                   │    │
│  │    feature/login-system                                     │    │
│  │    feature/terraform-vpc-setup                              │    │
│  │                                                              │    │
│  │  bugfix/   → Bug fixes                                      │    │
│  │    bugfix/payment-calculation-error                         │    │
│  │    bugfix/helm-values-misconfiguration                      │    │
│  │                                                              │    │
│  │  hotfix/   → Emergency production fixes                     │    │
│  │    hotfix/critical-security-patch                           │    │
│  │                                                              │    │
│  │  chore/    → Maintenance tasks                              │    │
│  │    chore/upgrade-terraform-module                           │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Branch Commands

```bash
# List branches
git branch              # Local branches
git branch -a           # All branches
git branch -r           # Remote branches
git branch -vv          # With tracking info

# Create branch
git branch branchname

# Switch branch
git checkout branchname
git switch branchname   # Modern alternative

# Create AND switch
git checkout -b branchname
git switch -c branchname  # Modern alternative

# Create from specific commit
git checkout -b branchname <commit-hash>

# Delete branch (safe)
git branch -d branchname

# Delete branch (force)
git branch -D branchname

# Rename branch
git branch -m newname
git branch -m oldname newname

# Delete remote branch
git push origin --delete branchname
```

---

## 🎬 Chapter 6: Merging - Integrating Branches

### Branch Divergence

```
╔══════════════════════════════════════════════════════════════════════╗
║                    BRANCH DIVERGENCE                                  ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   Divergence = Both branches have new commits after common ancestor  ║
║                                                                       ║
║   NO DIVERGENCE (Fast-Forward Possible):                             ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │                                                              │    ║
║   │   main:    C1 ── C2 ── C3                                   │    ║
║   │                    \                                         │    ║
║   │   feature:          F1 ── F2                                 │    ║
║   │                                                              │    ║
║   │   Common ancestor: C2                                        │    ║
║   │   Main has NO new commits after C2                          │    ║
║   │   ✅ Fast-forward merge possible                            │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   WITH DIVERGENCE (Three-Way Merge Required):                        ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │                                                              │    ║
║   │   main:    C1 ── C2 ── C3 ── C4                             │    ║
║   │                    \                                         │    ║
║   │   feature:          F1 ── F2                                 │    ║
║   │                                                              │    ║
║   │   Common ancestor: C2                                        │    ║
║   │   Both branches have new commits!                           │    ║
║   │   ✅ Three-way merge required                               │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Merge Types

```
╔══════════════════════════════════════════════════════════════════════╗
║                    MERGE TYPES                                        ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   FAST-FORWARD MERGE:                                                ║
║   ─────────────────────                                              ║
║   • No branch divergence                                             ║
║   • NO merge commit created                                          ║
║   • Branch pointer simply moves forward                              ║
║   • Linear history maintained                                        ║
║                                                                       ║
║   Before:                    After:                                  ║
║   main:    C1 ── C2          main:    C1 ── C2 ── F1 ── F2          ║
║                    \                                 ▲              ║
║   feature:          F1 ── F2                        │              ║
║                                                     │              ║
║                                                   HEAD             ║
║                                                                       ║
║   ═══════════════════════════════════════════════════════════════    ║
║                                                                       ║
║   THREE-WAY MERGE:                                                   ║
║   ────────────────                                                   ║
║   • Branch divergence exists                                         ║
║   • NEW merge commit created                                         ║
║   • Merge commit has TWO parents                                     ║
║   • Nonlinear history (branching visible)                            ║
║                                                                       ║
║   Before:                    After:                                  ║
║   main:    C1 ── C2 ── C3    main:    C1 ── C2 ── C3 ── M           ║
║                    \                      \         /               ║
║   feature:          F1 ── F2              F1 ── F2                  ║
║                                                                       ║
║   M = Merge commit (parents: C3 and F2)                              ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Merge Commands

```bash
# First, switch to TARGET branch (where you want to merge INTO)
git checkout main

# Merge SOURCE branch INTO current branch
git merge feature-login

# If conflict occurs:
# 1. Resolve conflicts in files
# 2. Stage resolved files
git add .
# 3. Complete merge
git commit -m "Merge resolved"

# Abort merge if things go wrong
git merge --abort

# View merge history
git log --oneline --graph
git reflog  # Shows merge operations
```

---

## 🎬 Chapter 7: Merge Conflicts

### Why Conflicts Occur

```
┌─────────────────────────────────────────────────────────────────────┐
│                    MERGE CONFLICT CAUSES                             │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Branch divergence does NOT cause conflicts!                        │
│  OVERLAPPING changes cause conflicts!                               │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  NO CONFLICT (Different files):                             │    │
│  │                                                              │    │
│  │  main:    app.js modified line 10                           │    │
│  │  feature: nav.html created (new file)                       │    │
│  │                                                              │    │
│  │  ✅ Git can merge automatically                             │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  CONFLICT (Same file, same line):                           │    │
│  │                                                              │    │
│  │  main:    app.js line 10 = "color: green"                   │    │
│  │  feature: app.js line 10 = "color: blue"                    │    │
│  │                                                              │    │
│  │  ❌ Git cannot decide! Needs human intervention             │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Conflict Markers

```
╔══════════════════════════════════════════════════════════════════════╗
║                    CONFLICT MARKERS                                   ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   <<<<<<< HEAD                                                       ║
║   Code from CURRENT branch (where you are)                           ║
║   =======                                                            ║
║   Code from INCOMING branch (what you're merging)                    ║
║   >>>>>>> feature-branch                                             ║
║                                                                       ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  RESOLUTION OPTIONS:                                        │    ║
║   │                                                              │    ║
║   │  1. Accept Current Change (keep HEAD version)               │    ║
║   │  2. Accept Incoming Change (keep incoming version)          │    ║
║   │  3. Accept Both Changes (keep both lines)                   │    ║
║   │  4. Manual Edit (remove markers, keep what you want)        │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   VS CODE SHORTCUTS:                                                 ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  [Accept Current Change]  ← Keep your code                  │    ║
║   │  [Accept Incoming Change] ← Keep their code                 │    ║
║   │  [Accept Both Changes]    ← Keep both                       │    ║
║   │  [Compare Changes]        ← Side-by-side view               │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Resolving Conflicts

```bash
# 1. Attempt merge
git merge feature-branch

# 2. Git reports conflict
# Auto-merging app.js
# CONFLICT (content): Merge conflict in app.js

# 3. Check status
git status
# Shows "both modified" files

# 4. Open conflicting file in VS Code
code app.js

# 5. Resolve conflicts (use VS Code buttons or manual edit)

# 6. Stage resolved files
git add app.js

# 7. Complete merge
git commit -m "Merge resolved: kept both changes"

# 8. View history
git log --oneline --graph
```

---

## 🎬 Chapter 8: Undoing Changes (Reset vs Revert)

### Reset Types

```
╔══════════════════════════════════════════════════════════════════════╗
║                    GIT RESET TYPES                                    ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   git reset --soft HEAD~1                                            ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  Commit │  Staging  │  Working Directory                    │    ║
║   │    ❌   │    ✅     │       ✅                              │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║   • Moves branch pointer back                                        ║
║   • Changes REMAIN STAGED                                            ║
║   • Use when: Correcting commit message                             ║
║                                                                       ║
║   ═══════════════════════════════════════════════════════════════    ║
║                                                                       ║
║   git reset --mixed HEAD~1 (DEFAULT)                                 ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  Commit │  Staging  │  Working Directory                    │    ║
║   │    ❌   │    ❌     │       ✅                              │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║   • Moves branch pointer back                                        ║
║   • Changes become UNSTAGED                                          ║
║   • Use when: Want to re-stage selectively                          ║
║                                                                       ║
║   ═══════════════════════════════════════════════════════════════    ║
║                                                                       ║
║   git reset --hard HEAD~1                                            ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  Commit │  Staging  │  Working Directory                    │    ║
║   │    ❌   │    ❌     │       ❌ (DANGER!)                    │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║   • Moves branch pointer back                                        ║
║   • Changes are PERMANENTLY DELETED                                  ║
║   • Use with CAUTION!                                                ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Reset vs Revert

```
┌─────────────────────────────────────────────────────────────────────┐
│                    RESET vs REVERT                                   │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  RESET (Rewrites history):                                          │
│  ─────────────────────────                                          │
│  • Moves branch pointer backward                                    │
│  • Removes commits from history                                     │
│  • Use for LOCAL commits only                                       │
│  • Changes commit hashes                                            │
│                                                                      │
│  Before:  A ── B ── C ── D (HEAD)                                  │
│  After:   A ── B (HEAD)          ← C and D gone from history       │
│                                                                      │
│  ═══════════════════════════════════════════════════════════════    │
│                                                                      │
│  REVERT (Preserves history):                                        │
│  ───────────────────────────                                        │
│  • Creates NEW commit that undoes changes                           │
│  • Original commit remains in history                               │
│  • Use for SHARED/PUSHED commits                                    │
│  • Safe for collaboration                                           │
│                                                                      │
│  Before:  A ── B ── C ── D (HEAD)                                  │
│  After:   A ── B ── C ── D ── D' (HEAD)                            │
│           (D' reverses changes of D)                                │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Commands

```bash
# RESET (Local commits only!)
git reset --soft HEAD~1     # Undo commit, keep staged
git reset --mixed HEAD~1    # Undo commit, keep unstaged (default)
git reset --hard HEAD~1     # Undo commit, DISCARD changes

# REVERT (Safe for shared branches!)
git revert <commit-hash>    # Create undo commit
git revert HEAD             # Revert latest commit
git revert HEAD~2..HEAD     # Revert range

# REFLOG (Recovery tool!)
git reflog                  # View all HEAD movements
git checkout HEAD@{5}       # Go to specific reflog entry
```

### Reflog - Your Safety Net

```
╔══════════════════════════════════════════════════════════════════════╗
║                    GIT REFLOG                                         ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   Tracks ALL HEAD movements (commits, checkouts, resets, merges)     ║
║                                                                       ║
║   HEAD@{0}: commit: Latest change                                    ║
║   HEAD@{1}: checkout: moving from feature to main                    ║
║   HEAD@{2}: reset: moving to HEAD~1                                  ║
║   HEAD@{3}: commit: Feature complete                                 ║
║   HEAD@{4}: merge feature: Merge made by ort                         ║
║                                                                       ║
║   ⏰ Expires in 90 days                                              ║
║   📍 Stored locally only (NOT pushed to remote)                     ║
║   🔑 Use to recover "lost" commits!                                  ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

# 📚 PART 2: COLLABORATION & PRODUCTION

## 🎬 Chapter 9: Remote Repositories

### Why Remote?

```
┌─────────────────────────────────────────────────────────────────────┐
│                    WHY REMOTE REPOSITORIES?                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Problem with Local-Only:                                           │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  👨‍💻 Dev 1's Laptop     👩‍💻 Dev 2's Laptop                    │    ║
│  │  ┌─────────────┐       ┌─────────────┐                       │    ║
│  │  │ App Code    │       │ App Code    │                       │    ║
│  │  │ (isolated)  │       │ (isolated)  │                       │    ║
│  │  └─────────────┘       └─────────────┘                       │    ║
│  │                                                              │    ║
│  │  ❌ No collaboration                                        │    ║
│  │  ❌ No backup                                               │    ║
│  │  ❌ No single source of truth                               │    ║
│  │  ❌ No CI/CD integration                                    │    ║
│  └─────────────────────────────────────────────────────────────┘    ║
│                                                                      │
│  Solution: Remote Repository                                        │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │                    ☁️ GITHUB                                 │    ║
│  │               (Single Source of Truth)                       │    ║
│  │                        ▲                                     │    ║
│  │         push ┌─────────┴─────────┐ push                     │    ║
│  │              │                   │                           │    ║
│  │         👨‍💻 Dev 1           👩‍💻 Dev 2                         │    ║
│  │              │                   │                           │    ║
│  │         pull └───────────────────┘ pull                     │    ║
│  │                                                              │    ║
│  │  ✅ Collaboration    ✅ Backup                              │    ║
│  │  ✅ CI/CD triggers   ✅ Access control                      │    ║
│  └─────────────────────────────────────────────────────────────┘    ║
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Remote Types

```
╔══════════════════════════════════════════════════════════════════════╗
║                    REMOTE REPOSITORY TYPES                            ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   PRIVATE REPOSITORY:                                                ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  • Access restricted to authorized users only               │    ║
║   │  • Not visible on public internet                           │    ║
║   │  • Write access: Limited to approved contributors           │    ║
║   │  • Use case: Enterprise, internal, sensitive systems        │    ║
║   │  • Examples: Company backend, infrastructure configs        │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   PUBLIC REPOSITORY:                                                 ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  • Anyone can VIEW and CLONE                                │    ║
║   │  • Openly accessible on internet                            │    ║
║   │  • Write access: Still requires explicit permission         │    ║
║   │  • Use case: Open-source, learning, community projects      │    ║
║   │  • Examples: Kubernetes, Terraform, freeCodeCamp            │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   💡 KEY: Commands are same for both! Only access differs.           ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Authentication Methods

```
╔══════════════════════════════════════════════════════════════════════╗
║                    AUTHENTICATION METHODS                             ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   GUI AUTHENTICATION:                                                ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  • Browser-based login                                       │    ║
║   │  • SSO (Google, Microsoft, etc.)                            │    ║
║   │  • Session-based (cookies + tokens under the hood)          │    ║
║   │  • Use case: Manual operations, UI workflows                │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   CLI AUTHENTICATION:                                                ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │                                                              │    ║
║   │  SSH (Typically for humans):                                │    ║
║   │  • Asymmetric key-based (public + private key pair)         │    ║
║   │  • No passwords                                              │    ║
║   │  • Private key proves identity                              │    ║
║   │  • Authorization enforced by platform                       │    ║
║   │                                                              │    ║
║   │  TOKENS (Typically for systems):                            │    ║
║   │  • Bearer tokens (possession = access)                      │    ║
║   │  • Scoped permissions                                       │    ║
║   │  • Can be short-lived, rotatable, revocable                 │    ║
║   │  • Use case: CI/CD, automation, API                         │    ║
║   │                                                              │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   💡 Modern preference: Token-based (fine-grained, auditable)        ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### SSH Key Setup (Windows)

```bash
# Step 1: Generate SSH Key
ssh-keygen -t ed25519 -C "your.email@example.com"
# Press Enter for default location
# Press Enter for no passphrase (or enter one)

# Step 2: Start SSH Agent
eval "$(ssh-agent -s)"
# Output: Agent pid 12345

# Step 3: Add Key to Agent
ssh-add ~/.ssh/id_ed25519
# Output: Identity added

# Step 4: Copy Public Key
cat ~/.ssh/id_ed25519.pub | clip
# This copies to clipboard

# Step 5: Add to GitHub
# Go to: GitHub → Settings → SSH and GPG keys → New SSH key
# Title: "My Windows PC"
# Paste the key → Add SSH key

# Step 6: Test Connection
ssh -T git@github.com
# Expected: Hi username! You've successfully authenticated...
```

### Personal Access Token Setup

```
┌─────────────────────────────────────────────────────────────────────┐
│                    CREATING PERSONAL ACCESS TOKEN                    │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  1. GitHub → Settings → Developer settings                          │
│                                                                      │
│  2. Personal access tokens → Fine-grained tokens                    │
│                                                                      │
│  3. Generate new token:                                             │
│     ┌─────────────────────────────────────────────────────────────┐ │
│     │  Token name: my-token                                       │ │
│     │  Expiration: 7 days / 30 days / 90 days / Custom           │ │
│     │  Repository access: Only select repositories               │ │
│     │  Permissions: Contents (Read and Write)                    │ │
│     └─────────────────────────────────────────────────────────────┘ │
│                                                                      │
│  4. Generate token → COPY IMMEDIATELY (shown only once!)            │
│                                                                      │
│  5. Use in Git operations:                                          │
│     git push origin main                                            │
│     Username: your-username                                         │
│     Password: <paste-token-here>                                    │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Remote Commands

```bash
# View remotes
git remote -v

# Add remote
git remote add origin <url>

# Change remote URL
git remote set-url origin <new-url>

# Rename remote
git remote rename origin upstream

# Remove remote
git remote remove origin

# Push to remote
git push origin main

# Push and set upstream (first time)
git push -u origin main
git push --set-upstream origin main

# Push all branches
git push --all origin

# Delete remote branch
git push origin --delete branchname

# Prune deleted remote branches
git remote prune origin

# Fetch from remote
git fetch origin
git fetch --all

# Pull (fetch + merge)
git pull origin main
git pull  # If upstream is set
```

---

## 🎬 Chapter 10: Fetch vs Pull

### The Difference

```
╔══════════════════════════════════════════════════════════════════════╗
║                    FETCH vs PULL                                      ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   GIT FETCH:                                                          ║
║   ─────────                                                          ║
║   Remote ──────▶ Local Remote Tracking ──────▶ (NO merge)            ║
║                                                                       ║
║   • Downloads changes                                                ║
║   • Does NOT modify working files                                   ║
║   • Lets you review before merging                                  ║
║   • Safe operation                                                   ║
║   • Updates ALL remote tracking branches                            ║
║                                                                       ║
║   ═══════════════════════════════════════════════════════════════    ║
║                                                                       ║
║   GIT PULL:                                                           ║
║   ─────────                                                           ║
║   Remote ──────▶ Local Remote Tracking ──────▶ MERGE to Local        ║
║                                                                       ║
║   • Downloads changes (fetch)                                        ║
║   • Automatically merges into current branch                         ║
║   • Can cause conflicts                                              ║
║   • = git fetch + git merge                                          ║
║   • Only works on CURRENT checked out branch                         ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Typical Workflow

```bash
# Scenario: Developer 2 pushed changes while you were away

# Option 1: Safe approach (recommended)
git fetch origin              # Download changes
git log main..origin/main     # Review what changed
git diff main origin/main     # See actual file changes
git merge origin/main         # Merge when ready

# Option 2: Quick sync
git pull origin main          # Fetch + merge in one command

# Check status
git status
# Output: Your branch is behind 'origin/main' by 1 commit
#         (use "git pull" to update your local branch)

# After fetch (before pull)
git status
# Output: Your branch is behind 'origin/main' by 1 commit
#         and can be fast-forwarded
```

---

## 🎬 Chapter 11: Pull Requests & Code Review

### Why Pull Requests?

```
┌─────────────────────────────────────────────────────────────────────┐
│                    PULL REQUEST PURPOSE                              │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Problem with Direct Push:                                          │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  Developer ────push────▶ main (PROTECTED) ❌                 │    │
│  │                                                              │    │
│  │  ❌ Untested changes enter production branch                │    │
│  │  ❌ No code review                                          │    │
│  │  ❌ No CI/CD validation                                     │    │
│  │  ❌ Stability issues surface late                           │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
│  Solution: Pull Request Workflow                                    │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │                                                              │    │
│  │  1. Create feature branch                                   │    │
│  │  2. Make changes & commit                                   │    │
│  │  3. Push to remote feature branch                           │    │
│  │  4. Create Pull Request                                     │    │
│  │  5. CI runs automatically                                   │    │
│  │  6. Code review by team lead                                │    │
│  │  7. Approved → Merge to main                                │    │
│  │                                                              │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Production PR Workflow

```
╔══════════════════════════════════════════════════════════════════════╗
║                    PRODUCTION PULL REQUEST FLOW                       ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   Step 1: Create Working Branch                                      ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  git checkout -b feature/search                             │    ║
║   │  Branch from stable main                                    │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                              │                                       ║
║                              ▼                                       ║
║   Step 2: Implement Changes (Local)                                  ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  Develop, commit, iterate                                   │    ║
║   │  Work remains private and isolated                          │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                              │                                       ║
║                              ▼                                       ║
║   Step 3: Push Branch to Remote                                      ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  git push -u origin feature/search                          │    ║
║   │  Enables collaboration & PR creation                        │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                              │                                       ║
║                              ▼                                       ║
║   Step 4: Create Pull Request                                        ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  • Propose changes into protected branch                    │    ║
║   │  • Initiates validation & approval workflow                 │    ║
║   │  • CI/CD triggers automatically                             │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                              │                                       ║
║                              ▼                                       ║
║   Step 5: Review & Validation                                        ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  • Automated checks (build, test, lint)                     │    ║
║   │  • Manual review by team lead                               │    ║
║   │  • Address feedback, push fixes                             │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                              │                                       ║
║                              ▼                                       ║
║   Step 6: Merge to Main                                              ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  • Approved PR merged                                       │    ║
║   │  • Triggers downstream pipelines                            │    ║
║   │  • Deploy to staging → production                           │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                              │                                       ║
║                              ▼                                       ║
║   Step 7: Cleanup                                                    ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  git branch -d feature/search                               │    ║
║   │  Delete local and remote feature branches                   │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Branch Protection Rules

```
┌─────────────────────────────────────────────────────────────────────┐
│                    BRANCH PROTECTION RULES                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Configure in: GitHub → Settings → Rules → Rulesets                 │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  ✅ Require pull request before merging                     │    │
│  │     └── Required approvals: 1                               │    │
│  │                                                              │    │
│  │  ✅ Dismiss stale pull request approvals                    │    │
│  │                                                              │    │
│  │  ✅ Require status checks to pass                           │    │
│  │     └── CI must pass before merge                           │    │
│  │                                                              │    │
│  │  ✅ Require conversation resolution                         │    │
│  │                                                              │    │
│  │  ✅ Restrict deletions                                      │    │
│  │                                                              │    │
│  │  ✅ Block force pushes                                      │    │
│  │                                                              │    │
│  │  ✅ Allowed merge methods:                                  │    │
│  │     ☑ Merge commit                                          │    │
│  │     ☑ Squash and merge                                      │    │
│  │     ☐ Rebase and merge                                      │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Creating a Pull Request

```bash
# 1. Create and switch to feature branch
git checkout -b feature/search

# 2. Make changes and commit
git add .
git commit -m "feat: enhance search functionality with filters"

# 3. Push to remote
git push -u origin feature/search

# 4. Go to GitHub → Compare & pull request
# 5. Add title and description
# 6. Create pull request
# 7. Wait for CI and review
# 8. Merge (options: Merge / Squash / Rebase)
# 9. Delete branch

# After merge, update local
git checkout main
git pull origin main
```

---

## 🎬 Chapter 12: Git Stash

### Why Stash?

```
╔══════════════════════════════════════════════════════════════════════╗
║                    GIT STASH - TEMPORARY STORAGE                      ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   SCENARIO:                                                           ║
║   ─────────                                                           ║
║   1. You're working on feature branch (uncommitted changes)          ║
║   2. Urgent bug fix needed on another branch!                        ║
║   3. Git blocks branch switch (would overwrite changes)              ║
║   4. Solution: STASH your changes!                                   ║
║                                                                       ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │                                                              │    ║
║   │   Working Dir     →  git stash  →  Stash Area               │    ║
║   │   (changes)                        (temporary shelf)        │    ║
║   │                                                              │    ║
║   │   Working Dir     ←  git stash pop  ←  Stash Area            │    ║
║   │   (changes back)                    (retrieved)             │    ║
║   │                                                              │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   🔑 KEY RULE: Git blocks branch switch ONLY when uncommitted        ║
║      changes would be overwritten, modified, or lost.                ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Stash Commands

```bash
# Save changes to stash
git stash
git stash save "work in progress"

# List all stashes
git stash list
# stash@{0}: WIP on feature: abc123 Add login UI
# stash@{1}: WIP on main: def456 Fix header

# Apply latest stash (keeps in list)
git stash apply

# Apply and remove from list
git stash pop

# Apply specific stash
git stash apply stash@{2}
git stash pop stash@{1}

# Drop specific stash
git stash drop stash@{0}

# Clear all stashes
git stash clear

# View stash contents
git stash show -p
git stash show -p stash@{1}
```

---

# 📚 PART 3: ADVANCED HISTORY MANAGEMENT

## 🎬 Chapter 13: Git Rebase

### Rebase vs Merge

```
╔══════════════════════════════════════════════════════════════════════╗
║                    REBASE vs MERGE                                    ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   BEFORE REBASE:                                                      ║
║   ─────────────                                                       ║
║   main:     C1 ── C2 ── C3 ── C4                                     ║
║                     \                                                 ║
║   feature:           F1 ── F2                                        ║
║                                                                       ║
║   ═══════════════════════════════════════════════════════════════    ║
║                                                                       ║
║   AFTER MERGE:                    AFTER REBASE:                       ║
║   ─────────────                   ─────────────                       ║
║   main: C1─C2─C3─C4─M             main: C1─C2─C3─C4                  ║
║              \   /                              \                    ║
║   feature:    F1─F2              feature:        F1'─F2'             ║
║                                                                       ║
║   (M = merge commit)              (Linear history!)                  ║
║                                                                       ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  MERGE: Preserves history, creates merge commit             │    ║
║   │  REBASE: Rewrites history, linear timeline                  │    ║
║   │  Same code outcome, different history representation!       │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### How Rebase Works

```
┌─────────────────────────────────────────────────────────────────────┐
│                    REBASE - UNDER THE HOOD                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  1. Identify unique commits in feature branch (D, E)                │
│                                                                      │
│  2. Temporarily remove them from feature branch                     │
│                                                                      │
│  3. Move base from C to F (rebase!)                                 │
│                                                                      │
│  4. Replay commits D and E as D' and E'                             │
│     (Commit hashes CHANGE!)                                         │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │                                                              │    │
│  │   Before:  main:    C1 ── C2 ── C3 ── C4                    │    │
│  │                         \                                    │    │
│  │            feature:      D ── E                              │    │
│  │                                                              │    │
│  │   After:   main:    C1 ── C2 ── C3 ── C4                    │    │
│  │                                          \                   │    │
│  │            feature:                        D' ── E'           │    │
│  │                                                              │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
│  ⚠️ NEVER rebase shared branches! (Others' history will diverge)    │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Rebase Commands

```bash
# First, switch to YOUR branch (not main!)
git checkout feature

# Rebase onto main
git rebase main

# If conflict occurs:
# 1. Resolve conflicts in files
# 2. Stage resolved files
git add .
# 3. Continue rebase
git rebase --continue

# Abort rebase (go back to before)
git rebase --abort

# Skip current commit
git rebase --skip
```

### When to Use Rebase vs Merge

```
╔══════════════════════════════════════════════════════════════════════╗
║                    WHEN TO USE WHAT                                   ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   USE REBASE:                                                        ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  ✅ Local feature branches (not shared)                     │    ║
║   │  ✅ Before pushing to remote                                │    ║
║   │  ✅ When you want linear history                            │    ║
║   │  ✅ Single developer working on branch                      │    ║
║   │  ✅ Cleaning up local commits                               │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   USE MERGE:                                                         ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  ✅ Shared branches (multiple developers)                   │    ║
║   │  ✅ Main/master branch                                      │    ║
║   │  ✅ When preserving history matters                         │    ║
║   │  ✅ After pushing to remote (shared)                        │    ║
║   │  ✅ When you want to see actual development timeline        │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   🔥 GOLDEN RULE:                                                    ║
║   Never rebase commits that exist outside your repository!           ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

## 🎬 Chapter 14: Interactive Rebase

### Why Interactive Rebase?

```
┌─────────────────────────────────────────────────────────────────────┐
│                    INTERACTIVE REBASE PURPOSE                        │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Problem: You have noisy commits in your feature branch             │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  Commit 1: "add login UI"                                   │    │
│  │  Commit 2: "fix login UI"                                   │    │
│  │  Commit 3: "fix login UI again"                             │    │
│  │  Commit 4: "cleanup login UI"                               │    │
│  │  Commit 5: "final login UI fix"                             │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
│  Solution: Combine into one meaningful commit!                      │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  Single Commit: "feat: implement login UI"                  │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
│  Interactive rebase allows you to:                                  │
│  • Combine related commits (squash)                                 │
│  • Reorder commits                                                  │
│  • Edit commit messages                                             │
│  • Remove noisy commits                                             │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Interactive Rebase Options

```
╔══════════════════════════════════════════════════════════════════════╗
║                    INTERACTIVE REBASE COMMANDS                        ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   Command: git rebase -i HEAD~3                                      ║
║                                                                       ║
║   Opens editor with:                                                 ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  pick abc123 Add login UI                                   │    ║
║   │  pick def456 Fix login UI                                   │    ║
║   │  pick ghi789 Cleanup login UI                               │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   CHANGE "pick" TO:                                                  ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  pick   = Keep commit as is                                 │    ║
║   │  reword = Change commit message                             │    ║
║   │  edit   = Stop to amend commit                              │    ║
║   │  squash = Combine with previous commit                      │    ║
║   │  fixup  = Combine, discard message                          │    ║
║   │  drop   = Remove commit entirely                            │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   EXAMPLE: Squash 3 commits into 1                                   ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  pick abc123 Add login UI                                   │    ║
║   │  squash def456 Fix login UI      ──▶ Combined!              │    ║
║   │  squash ghi789 Cleanup login UI                              │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Interactive Rebase Commands

```bash
# Interactive rebase (last 3 commits)
git rebase -i HEAD~3

# Interactive rebase (specific commit)
git rebase -i <commit-hash>

# After editing the todo list:
# 1. Save and close editor
# 2. If squash: Editor opens for combined message
# 3. Edit message, save, close
# 4. If conflict: Resolve, add, continue
git add .
git rebase --continue

# Abort
git rebase --abort
```

---

## 🎬 Chapter 15: Squash Merge (Platform Level)

### Platform Integration Strategies

```
╔══════════════════════════════════════════════════════════════════════╗
║                    GITHUB MERGE STRATEGIES                            ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   1. CREATE A MERGE COMMIT                                           ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  • Preserves full history                                   │    ║
║   │  • Adds merge commit                                        │    ║
║   │  • Shows branch divergence                                  │    ║
║   │  • Default GitHub behavior                                  │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   2. SQUASH AND MERGE                                                ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  • Combines ALL feature commits into ONE                    │    ║
║   │  • NO merge commit created                                  │    ║
║   │  • Clean, minimal main history                              │    ║
║   │  • Main branch gets single commit                           │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   3. REBASE AND MERGE                                                ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │  • Commits replayed individually                            │    ║
║   │  • Linear history                                           │    ║
║   │  • Commit hashes change                                     │    ║
║   │  • Rarely used on main branch                               │    ║
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Squash Merge Flow

```
┌─────────────────────────────────────────────────────────────────────┐
│                    SQUASH AND MERGE WORKFLOW                         │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Before Squash:                                                     │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  main:     A ── B                                           │    │
│  │                   \                                          │    │
│  │  feature:          C ── D ── E                              │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
│  Squash and Merge:                                                  │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  main:     A ── B ── X                                      │    │
│  │                                                              │    │
│  │  (X = combined commit of C + D + E)                         │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
│  ✅ Feature branch remains unchanged                                │
│  ✅ Only main branch affected                                       │
│  ✅ Clean, linear history on main                                   │
│  ✅ No merge commit                                                 │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### GitHub Squash Merge Steps

```
┌─────────────────────────────────────────────────────────────────────┐
│                    HOW TO SQUASH MERGE ON GITHUB                     │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  1. Create PR from feature → main                                   │
│                                                                      │
│  2. Click dropdown arrow next to "Merge pull request"               │
│                                                                      │
│  3. Select "Squash and merge"                                       │
│                                                                      │
│  4. Edit commit message (combined message)                          │
│                                                                      │
│  5. Click "Confirm squash and merge"                                │
│                                                                      │
│  6. Delete feature branch (optional)                                │
│                                                                      │
│  Result:                                                            │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  main:     A ── B ── X                                      │    │
│  │                                                              │    │
│  │  X = Single commit containing all feature changes            │    │
│  └─────────────────────────────────────────────────────────────┘    │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 🎬 Chapter 16: Git Cherry-Pick

### What is Cherry-Pick?

```
╔══════════════════════════════════════════════════════════════════════╗
║                    GIT CHERRY-PICK                                    ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║   Problem:                                                            ║
║   Merge/Rebase integrate ENTIRE branch (all commits)                 ║
║   What if you only want ONE specific commit?                         ║
║                                                                       ║
║   Solution: Cherry-pick!                                             ║
║   Pick a specific commit from another branch                         ║
║                                                                       ║
║   ┌─────────────────────────────────────────────────────────────┐    ║
║   │                                                              │    │
║   │   main:    A ── B ── C ── D                                 │    │
║   │                       \                                      │    │
║   │   feature:             E ── F ── G                          │    │
║   │                                                              │    │
║   │   I want commit C only!                                      │    │
║   │                                                              │    │
║   │   git cherry-pick C                                          │    │
║   │                                                              │    │
║   │   feature:  E ── F ── G ── C'                               │    │
║   │                                                              │    │
║   │   (C' = new commit with same changes, different hash)        │    │
║   └─────────────────────────────────────────────────────────────┘    ║
║                                                                       ║
║   Use Cases:                                                         ║
║   • Hot fixes to multiple branches                                   ║
║   • Backporting changes                                              ║
║   • Selective integration                                            ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

### Cherry-Pick Commands

```bash
# Cherry-pick a specific commit
git cherry-pick <commit-hash>

# Cherry-pick multiple commits
git cherry-pick <hash1> <hash2>

# Cherry-pick a range
git cherry-pick <start-hash>..<end-hash>

# If conflict occurs:
# 1. Resolve conflicts
# 2. Stage resolved files
git add .
# 3. Continue
git cherry-pick --continue

# Abort
git cherry-pick --abort
```

---

## 📊 COMPLETE COMMAND REFERENCE

```
╔══════════════════════════════════════════════════════════════════════╗
║                    GIT MASTER COMMAND REFERENCE                       ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  SETUP & CONFIG                                                       ║
║  ──────────────                                                       ║
║  git --version                    Check Git version                  ║
║  git config --global user.name    Set your name                      ║
║  git config --global user.email   Set your email                     ║
║  git config --global core.editor  Set default editor                 ║
║  git config --list                View all configs                   ║
║                                                                       ║
║  STARTING A PROJECT                                                   ║
║  ──────────────────                                                   ║
║  git init                         Initialize new repo                ║
║  git clone <url>                  Clone existing repo                ║
║                                                                       ║
║  BASIC SNAPSHOT                                                       ║
║  ──────────────                                                       ║
║  git status                       Check current state                ║
║  git add <file>                   Stage specific file                ║
║  git add .                        Stage all changes                  ║
║  git commit -m "msg"              Commit with message                ║
║  git commit -am "msg"             Add & commit (tracked files)       ║
║  git restore <file>               Discard changes                    ║
║  git restore --staged <file>      Unstage file                       ║
║                                                                       ║
║  BRANCHING                                                            ║
║  ─────────                                                            ║
║  git branch                       List branches                      ║
║  git branch <name>                Create branch                      ║
║  git checkout <name>              Switch branch                      ║
║  git checkout -b <name>           Create & switch                    ║
║  git switch <name>                Switch (modern)                    ║
║  git switch -c <name>             Create & switch (modern)           ║
║  git branch -d <name>             Delete branch                      ║
║  git branch -D <name>             Force delete branch                ║
║  git branch -m <new>              Rename branch                      ║
║                                                                       ║
║  MERGING                                                              ║
║  ───────                                                              ║
║  git merge <branch>               Merge branch into current          ║
║  git merge --abort                Abort merge                        ║
║  git merge --continue             Continue after conflict            ║
║                                                                       ║
║  REMOTE                                                               ║
║  ──────                                                               ║
║  git remote -v                    List remotes                       ║
║  git remote add origin <url>      Add remote                         ║
║  git remote remove origin         Remove remote                      ║
║  git remote prune origin          Clean stale branches               ║
║  git push origin <branch>         Push to remote                     ║
║  git push -u origin <branch>      Push & set upstream                ║
║  git push origin --delete <branch> Delete remote branch              ║
║  git fetch                        Fetch only                         ║
║  git fetch --all                  Fetch all remotes                  ║
║  git pull                         Fetch & merge                      ║
║  git pull origin <branch>         Pull specific branch               ║
║                                                                       ║
║  UNDOING                                                              ║
║  ───────                                                              ║
║  git reset --soft HEAD~1          Undo commit, keep staged           ║
║  git reset --mixed HEAD~1         Undo commit, keep unstaged         ║
║  git reset --hard HEAD~1          Undo commit, discard all           ║
║  git revert <commit>              Create undo commit                 ║
║  git reflog                       View all HEAD movements            ║
║                                                                       ║
║  STASHING                                                             ║
║  ────────                                                             ║
║  git stash                        Save changes temporarily           ║
║  git stash list                   List stashes                       ║
║  git stash pop                    Apply & remove                     ║
║  git stash apply                  Apply & keep                       ║
║  git stash drop                   Delete stash                       ║
║  git stash clear                  Clear all stashes                  ║
║                                                                       ║
║  HISTORY                                                              ║
║  ───────                                                              ║
║  git log                          Full history                       ║
║  git log --oneline                Compact history                    ║
║  git log --graph                  Graph view                         ║
║  git log -n 5                     Last 5 commits                     ║
║  git log --all                    All branches                       ║
║  git show <commit>                Show commit details                ║
║  git diff                         Compare working vs staged          ║
║  git diff --staged                Compare staged vs last commit      ║
║  git diff branch1..branch2        Compare branches                   ║
║                                                                       ║
║  REBASING                                                             ║
║  ────────                                                             ║
║  git rebase <branch>              Rebase onto branch                 ║
║  git rebase -i HEAD~n             Interactive rebase                 ║
║  git rebase --continue            Continue after conflict            ║
║  git rebase --abort               Abort rebase                       ║
║  git rebase --skip                Skip current commit                ║
║                                                                       ║
║  CHERRY-PICK                                                          ║
║  ───────────                                                          ║
║  git cherry-pick <hash>           Apply specific commit              ║
║  git cherry-pick --continue       Continue after conflict            ║
║  git cherry-pick --abort          Abort cherry-pick                  ║
║                                                                       ║
║  TAGS                                                                 ║
║  ────                                                                 ║
║  git tag                          List tags                          ║
║  git tag v1.0.0                   Create lightweight tag            ║
║  git tag -a v1.0.0 -m "msg"       Create annotated tag               ║
║  git push origin --tags           Push all tags                      ║
║  git push origin v1.0.0           Push specific tag                  ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

## 🎯 KEY TAKEAWAYS

```
╔══════════════════════════════════════════════════════════════════════╗
║                    GOLDEN RULES OF GIT                                ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                       ║
║  1. COMMIT OFTEN, COMMIT EARLY                                       ║
║     └── Small commits are easier to understand and revert            ║
║                                                                       ║
║  2. WRITE MEANINGFUL COMMIT MESSAGES                                 ║
║     └── Use imperative mood: "Add feature" not "Added feature"       ║
║                                                                       ║
║  3. ONE COMMIT = ONE TASK                                            ║
║     └── Atomic commits are the way                                   ║
║                                                                       ║
║  4. ALWAYS CHECK git status                                          ║
║     └── Know what you're about to commit                             ║
║                                                                       ║
║  5. USE BRANCHES FOR EVERYTHING                                      ║
║     └── Never work directly on main                                  ║
║                                                                       ║
║  6. NEVER REBASE SHARED BRANCHES                                     ║
║     └── Rewriting history causes chaos                               ║
║                                                                       ║
║  7. PULL BEFORE YOU PUSH                                             ║
║     └── Stay updated with remote changes                             ║
║                                                                       ║
║  8. USE .gitignore                                                   ║
║     └── Keep sensitive files out of repo                             ║
║                                                                       ║
║  9. NEVER COMMIT SECRETS                                             ║
║     └── Even in private repos!                                       ║
║                                                                       ║
║  10. PREFER SSH OR TOKENS OVER PASSWORDS                             ║
║      └── More secure, more auditable                                 ║
║                                                                       ║
║  11. USE git fetch BEFORE git pull                                   ║
║      └── Review changes before merging                               ║
║                                                                       ║
║  12. PRACTICE DAILY                                                   ║
║      └── Git is a skill, not knowledge                               ║
║                                                                       ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

## 📝 INTERVIEW PREPARATION NOTES

### Common Git Interview Questions

```
┌─────────────────────────────────────────────────────────────────────┐
│                    TOP GIT INTERVIEW QUESTIONS                       │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Q1: What is the difference between Git and GitHub?                 │
│  A: Git = software (local), GitHub = service (cloud)                │
│                                                                      │
│  Q2: What is the difference between merge and rebase?               │
│  A: Merge preserves history (merge commit), rebase rewrites         │
│     history (linear). Same code, different history.                 │
│                                                                      │
│  Q3: What is the difference between fetch and pull?                 │
│  A: Fetch downloads only. Pull = fetch + merge.                     │
│                                                                      │
│  Q4: What is the difference between reset and revert?               │
│  A: Reset rewrites history (local). Revert creates new commit       │
│     (safe for shared).                                              │
│                                                                      │
│  Q5: What is cherry-pick?                                           │
│  A: Apply specific commit from one branch to another.               │
│                                                                      │
│  Q6: What is the difference between soft, mixed, hard reset?        │
│  A: Soft = keep staged, Mixed = keep unstaged, Hard = discard all   │
│                                                                      │
│  Q7: What is the difference between merge and squash merge?         │
│  A: Merge creates merge commit, squash combines all into one        │
│                                                                      │
│  Q8: What is the difference between git stash and git commit?       │
│  A: Stash = temporary, uncommitted. Commit = permanent, tracked.    │
│                                                                      │
│  Q9: What is the difference between SSH and HTTPS authentication?   │
│  A: SSH = key-based, no passwords. HTTPS = token-based,            │
│     interactive.                                                    │
│                                                                      │
│  Q10: What is the difference between rebase and interactive rebase? │
│  A: Rebase = automatic replay. Interactive = user control           │
│     (squash, reorder, edit).                                        │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

*Notes compiled from Varun Joshi's Git Masterclass (3-Part Series)*
*Optimized for Windows Users*
*Total Duration: ~6 hours 44 minutes*
*Topics Covered: Fundamentals, Architecture, Commits, Branching, Merging, Conflicts, Reset/Revert, Remote Repos, Authentication, Fetch/Pull, Pull Requests, Stash, Rebase, Interactive Rebase, Squash Merge, Cherry-Pick*