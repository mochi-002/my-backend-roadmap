---
Content: Git
Provider: Elzero Web School
Topics:
  - "[[#Git Workflow]]"
  - "[[#Working Directory]]"
  - "[[#Staging Area]]"
  - "[[#Local Repository]]"
  - "[[#Remote Repository]]"
  - "[[#Important Terms]]"
  - "[[#Repository (Repo)]]"
  - "[[#Branch]]"
  - "[[#Commit]]"
  - "[[#Clone]]"
  - "[[#Push]]"
  - "[[#Pull]]"
  - "[[#Fetch]]"
  - "[[#Merge]]"
  - "[[#Checkout]]"
  - "[[#Basic Commands]]"
  - "[[#Git Configuration]]"
  - "[[#SSH Authentication]]"
  - "[[#Existing Project → GitHub]]"
  - "[[#Pull Requests (PR)]]"
  - "[[#Branch Management]]"
  - "[[#Git Stash]]"
  - "[[#Git Aliases]]"
  - "[[#Restore & Clean]]"
  - "[[#Resetting HEAD]]"
  - "[[#Ignoring Files & Directories]]"
  - "[[#Tags & Releases]]"
  - "[[#GitHub Releases]]"
  - "[[#Common Daily Workflow]]"
  - "[[#Common Collaboration Workflow]]"
  - "[[#Useful Commands Cheat Sheet]]"
Resources:
  - "[Learn Git and Github - Elzero Web School](https://www.youtube.com/playlist?list=PLDoPjvoNmBAw4eOj58MZPakHjaO3frVMF)"
---
> Git is a **Version Control System (VCS)** that tracks changes in your code.
>
> GitHub is a **cloud service** that hosts Git repositories online.

---

# Git Workflow

```
Working Directory
        │
        │ git add
        ▼
 Staging Area (Index)
        │
        │ git commit
        ▼
 Local Repository
        │
        │ git push
        ▼
 Remote Repository (GitHub)
```

## Working Directory

The files you're currently editing.

Example:

```
main.py
README.md
index.html
```

Nothing is saved into Git until you stage or commit it.

---

## Staging Area

Temporary area where you choose which files will be included in the next commit.

Move files here with:

```bash
git add <file>
```

or

```bash
git add .
```

Remove a staged file:

```bash
git reset HEAD <file>
```

---

## Local Repository

The database on your computer containing every commit.

Create a snapshot using:

```bash
git commit -m "message"
```

Think of a commit as a **checkpoint** in a game.

---

## Remote Repository

A copy of your repository stored online (GitHub, GitLab, Bitbucket...).

Upload commits:

```bash
git push
```

Download changes:

```bash
git pull
```

---

# Important Terms

## Repository (Repo)

A folder tracked by Git.

Contains:

- source code
- commit history
- branches
- configuration

Initialize one:

```bash
git init
```

---

## Branch

A separate line of development.

Used for:

- adding new features
- fixing bugs
- experimenting

The default branch is usually:

```
main
```

Example:

```
main
 ├── login-feature
 ├── ui-redesign
 └── bug-fix
```

---

## Commit

A snapshot of your project.

Each commit has:

- unique ID (hash)
- author
- date
- message

Example:

```bash
git commit -m "Add login page"
```

---

## Clone

Downloads an existing repository.

```bash
git clone <repository-url>
```

Example:

```bash
git clone https://github.com/user/project.git
```

---

## Push

Uploads local commits to GitHub.

```bash
git push
```

---

## Pull

Downloads changes **and merges them**.

```bash
git pull
```

Equivalent to:

```bash
git fetch
git merge
```

---

## Fetch

Downloads changes only.

Does NOT merge them.

```bash
git fetch
```

---

## Merge

Combines two branches.

```bash
git merge branch-name
```

---

## Checkout

Moves to another branch.

```bash
git checkout branch-name
```

---

# Basic Commands

## Clone Repository

```bash
git clone <repo-link>
```

Example

```bash
git clone https://github.com/user/project.git
```

---

## Check Repository Status

```bash
git status
```

Shows:

- modified files
- staged files
- untracked files
- current branch

---

## Stage Files

Single file

```bash
git add main.py
```

Everything

```bash
git add .
```

---

## Unstage File

```bash
git reset HEAD <file>
```

---

## Commit

```bash
git commit -m "message"
```

Example

```bash
git commit -m "Fix navbar bug"
```

---

## Push

```bash
git push
```

---

## Pull

```bash
git pull
```

Specific branch

```bash
git pull origin main
```

---

## Show Branches

```bash
git branch
```

---

## Show Remote

```bash
git remote -v
```

Example

```
origin
https://github.com/user/project.git
```

---

# Git Configuration

View all settings

```bash
git config -l
```

Global configuration

```bash
git config --global
```

Edit manually

```bash
git config --global --edit
```

Remove a value

```bash
git config --global --unset <key>
```

Example

```bash
git config --global user.name "Mohamed"
git config --global user.email "mail@example.com"
```

---

# SSH Authentication

SSH allows GitHub authentication without entering your password every time.

## Generate SSH Key

```bash
ssh-keygen -t rsa -b 4096 -C "mail@example.com"
```

Press Enter for default location.

---

## Display Public Key

```bash
cat ~/.ssh/id_rsa.pub
```

Copy its contents and add it to GitHub.

---

## Test Connection

```bash
ssh -T git@github.com
```

Expected output:

```
Hi username!
You've successfully authenticated.
```

---

# Existing Project → GitHub

Initialize Git

```bash
git init
```

Stage files

```bash
git add .
```

Commit

```bash
git commit -m "Initial commit"
```

Connect GitHub

```bash
git remote add origin <repo-link>
```

Push

```bash
git push -u origin main
```

> Older repositories may still use **master** instead of **main**.

---

# Pull Requests (PR)

A Pull Request asks someone to review and merge your changes.

## Open Source Workflow

```
Fork Repository
      │
      ▼
Clone Fork
      │
      ▼
Make Changes
      │
      ▼
Commit
      │
      ▼
Push
      │
      ▼
Open Pull Request
      │
      ▼
Maintainer Reviews
      │
      ▼
Merged
```

After merging, your fork can be deleted if no longer needed.

---

## Team Workflow

```
Create Branch
      │
      ▼
Make Changes
      │
      ▼
Commit
      │
      ▼
Push Branch
      │
      ▼
Open Pull Request
      │
      ▼
Admin Reviews
      │
      ▼
Merge into main
```

---

# Branch Management

Show branches

```bash
git branch
```

Create branch

```bash
git branch feature
```

Delete merged branch

```bash
git branch -d feature
```

Force delete

```bash
git branch -D feature
```

Rename branch

```bash
git branch -m new-name
```

Switch branch

```bash
git checkout feature
```

Create & switch

```bash
git checkout -b feature
```

Merge branch

```bash
git merge feature
```

---

# Git Stash

Temporarily saves uncommitted changes without making a commit.

Useful when you need to switch branches quickly.

Save

```bash
git stash
```

Save with message

```bash
git stash save "working on login"
```

List

```bash
git stash list
```

Restore latest

```bash
git stash pop
```

Restore specific

```bash
git stash pop stash@{2}
```

Apply without removing

```bash
git stash apply
```

Delete latest

```bash
git stash drop
```

Delete specific

```bash
git stash drop stash@{1}
```

View changes

```bash
git stash show
```

View specific stash

```bash
git stash show stash@{0}
```

Delete all stashes

```bash
git stash clear
```

---

# Git Aliases

Aliases let you create shortcuts for long commands.

Example

```bash
git config --global alias.s status
```

Now instead of

```bash
git status
```

you can type

```bash
git s
```

Another example

```bash
git config --global alias.cm "commit -m"
```

Then

```bash
git cm "Fix bug"
```

Edit aliases manually

```bash
git config --global --edit
```

---
# Restore & Clean

## Restore Staged Files

If you accidentally staged a file, you can move it back to the **Working Directory** without losing its changes.

```bash
git restore --staged <file>
```

Example:

```bash
git restore --staged main.py
```

> This only removes the file from the **Staging Area**. Your modifications remain intact.

---

## Clean Untracked Files

Git only tracks files that have been added at least once. Files that have never been tracked are called **untracked files**.

Preview what will be deleted:

```bash
git clean -n
```

Example output:

```
Would remove test.txt
Would remove temp/
```

Actually remove them:

```bash
git clean -f
```

Useful options:

```bash
git clean -fd
```

Removes untracked files **and directories**.

> ⚠️ `git clean` permanently deletes untracked files. They cannot be recovered through Git.

---

# Resetting HEAD

Sometimes you create commits that you no longer need.

Git keeps a special pointer called **HEAD**, which points to the **current (latest checked-out) commit**.

Example:

```
A ── B ── C ── D (HEAD)
```

If you reset to commit **B**, Git moves `HEAD` back:

```
A ── B (HEAD)
```

Commits `C` and `D` become unreachable (unless referenced elsewhere).

---

## View Commit History

```bash
git log
```

Example:

```
8af92de  Fix login
74ac211  Update README
14e97fd  Initial commit
```

Each commit has a unique **hash**.

---

## Hard Reset

Move `HEAD` to a previous commit and discard all changes after it.

```bash
git reset --hard <commit-hash>
```

Example:

```bash
git reset --hard 74ac211
```

> ⚠️ This permanently removes all commits and working directory changes after the selected commit.

---

## Update the Remote Repository

If you've already pushed the removed commits to GitHub, you'll need to overwrite the remote history.

```bash
git push --force origin main
```

or

```bash
git push -f origin main
```

> ⚠️ Force pushing rewrites Git history. Avoid using it on shared branches unless everyone agrees.

---

# Ignoring Files & Directories

Git ignores files listed in a `.gitignore` file.

Example:

```gitignore
# Ignore log files
*.log

# Ignore build folder
build/

# Ignore node modules
node_modules/

# Ignore environment files
.env
```

---

## Common Patterns

Ignore every file with a specific extension:

```gitignore
*.type
```

Example:

```gitignore
*.log
```

Ignore a directory:

```gitignore
folder/
```

Example:

```gitignore
build/
```

Ignore every file except one:

```gitignore
!important.txt
```

---

## Force Add an Ignored File

Sometimes you want to track an ignored file.

```bash
git add -f <file>
```

Example:

```bash
git add -f .env
```

---

# Tags & Releases

Tags mark important commits, usually versions.

Example timeline:

```
Commit ── Commit ── Commit(v1.0) ── Commit ── Commit(v1.1)
```

Unlike branches, tags do **not** move.

---

## Lightweight Tag

Simply points to a commit.

```bash
git tag v1.0
```

---

## Annotated Tag

Stores extra information such as:

- author
- date
- message

```bash
git tag -a v1.0 -m "First stable release"
```

---

## View Tags

```bash
git tag
```

---

## Push a Tag

```bash
git push origin v1.0
```

Push every local tag:

```bash
git push origin --tags
```

---

## Delete a Local Tag

```bash
git tag -d v1.0
```

---

## Delete a Remote Tag

```bash
git push origin --delete v1.0
```

---
# GitHub Releases

A **Release** is a GitHub feature built on top of Git tags.

A release can include:

- Version number
- Release notes
- Changelog
- Downloadable source code
- Compiled binaries or assets
---
## Creating a Release

1. Push a tag to GitHub.
2. Open the repository on GitHub.
3. Go to **Releases**.
4. Click **Create a new release**.
5. Select or create a tag.
6. Add a title and release notes.
7. Click **Publish release**.

> A release is intended for end users, while a tag is mainly for Git itself.
---

# Common Daily Workflow

```text
Edit files
    │
    ▼
git status
    │
    ▼
git add .
    │
    ▼
git commit -m "Describe changes"
    │
    ▼
git push
```

---

# Common Collaboration Workflow

```text
git pull
      │
      ▼
Make changes
      │
      ▼
git add .
      │
      ▼
git commit
      │
      ▼
git push
```

---
# Useful Commands Cheat Sheet

| Command                 | Description            |
| ----------------------- | ---------------------- |
| `git status`            | Show repository status |
| `git add .`             | Stage everything       |
| `git add <file>`        | Stage one file         |
| `git reset HEAD <file>` | Unstage file           |
| `git commit -m ""`      | Create commit          |
| `git push`              | Upload commits         |
| `git pull`              | Download & merge       |
| `git fetch`             | Download only          |
| `git branch`            | List branches          |
| `git checkout`          | Switch branch          |
| `git checkout -b`       | Create & switch        |
| `git merge`             | Merge branches         |
| `git stash`             | Save temporary work    |
| `git stash pop`         | Restore stash          |
| `git remote -v`         | Show remotes           |
| `git clone`             | Download repository    |
| `git config -l`         | Show Git configuration |
