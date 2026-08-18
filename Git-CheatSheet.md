# Git Cheat Sheet Examples

## Getting Started

### `git init`

**Purpose:** Creates a new Git repository.

**Example:**


git init


I used this command to initialize my CS-101 repository.

---

### `git clone <url>`

**Purpose:** Copies an existing repository to a local machine.

**Example:**


git clone git@github.com:brinda-codes/CS-101-L01-Setup-your-first-repo-.git


I used this command to clone my GitHub repository.

---

## Prepare to Commit

### `git add <file>`

**Purpose:** Adds a specific file to the staging area.

**Example:**


git add README.md


I used this command when I added my Git notes.

---

### `git add .`

**Purpose:** Adds all modified files.

**Example:**


git add .


I used this command to stage all files in the repository.

---

### `git status`

**Purpose:** Displays the current status of the repository.

**Example:**


git status


I used this command to verify that my working tree was clean.
---


# Git Cheat Sheet Examples

## Getting Started

### 1. Start a New Repository

**Command**


git init


**Example Scenario**

I created a new directory and initialized it as a Git repository.


mkdir git-demo
cd git-demo
git init


**Result**

An empty Git repository was created.

---

### 2. Clone an Existing Repository

**Command**

```bash
git clone <url>
```

**Example Scenario**

I cloned my GitHub repository to my local machine.

```bash
git clone git@github.com:brinda-codes/CS-101-L01-Setup-your-first-repo-.git
```

**Result**

A local copy of the repository was created.

---

## Prepare to Commit

### 3. Add an Untracked File or Unstaged Changes

**Command**


git add <file>


**Example Scenario**

I modified the README file and staged only that file.


echo "Git add example" >> README.md
git add README.md


**Result**

Only `README.md` was added to the staging area.

---

### 4. Add All Untracked Files and Unstaged Changes

**Command**


git add .


**Example Scenario**

I modified two files and staged all changes at once.

```bash
echo "Example" >> README.md
echo "Example" >> Git-CheatSheet.md

git add .
```

**Result**

All modified files were added to the staging area.

---

### 5. Choose Which Parts of a File to Stage

**Command**


git add -p


**Example Scenario**

I edited a file and selected specific changes to add to the next commit.

```bash
echo "Line 1" >> README.md
echo "Line 2" >> README.md

git add -p README.md
```

**Result**

Only the selected changes were staged.

---

### 6. Move a File

**Command**


git mv <old> <new>


**Example Scenario**

I renamed a file and allowed Git to track the change.


touch notes.txt

git mv notes.txt git-notes.txt


**Result**

The file was renamed.

---

### 7. Delete a File

**Command**


git rm <file>


**Example Scenario**

I removed a file from the repository.


touch delete-me.txt

git add delete-me.txt
git commit -m "Add temporary file"

git rm delete-me.txt


**Result**

The file was deleted and staged for removal.

---

### 8. Stop Tracking a File Without Deleting It

**Command**


git rm --cached <file>


**Example Scenario**

I stopped tracking a file while keeping it on my computer.


touch temp.txt

git add temp.txt

git rm --cached temp.txt


**Result**

Git stopped tracking the file, but the file remained in the project directory.

---

### 9. Unstage One File

**Command**


git reset <file>


**Example Scenario**

I removed one file from the staging area.


git add README.md
git add Git-CheatSheet.md

git reset README.md


**Result**

`README.md` was unstaged.

---

### 10. Unstage Everything

**Command**


git reset


**Example Scenario**

I removed all files from the staging area.


git add .

git reset


**Result**

All staged files were unstaged.

---

### 11. Check the Repository Status

**Command**


git status


**Example Scenario**

I checked the current state of my repository.


git status


**Result**

Git displayed the current branch and listed staged, unstaged, and untracked files.
----

---

## Make Commits

### 12. Make a Commit (Open the Editor)

**Command**

```bash
git commit
```

**Example Scenario**

I created a commit and wrote the commit message in the editor.

```bash
git commit
```

**Result**

Git opened the default editor and created a new commit after I saved the message.

---

### 13. Make a Commit with a Message

**Command**

```bash
git commit -m "message"
```

**Example Scenario**

I committed my changes with an inline message.

```bash
git commit -m "Demonstrate git commit -m"
```

**Result**

Git created a new commit with the specified message.

---

### 14. Commit All Modified Files

**Command**

```bash
git commit -am "message"
```

**Example Scenario**

I modified an existing tracked file and committed it without using `git add`.

```bash
echo "Additional notes" >> README.md

git commit -am "Demonstrate git commit -am"
```

**Result**

Git automatically staged the modified tracked files and created a commit.

---

## Move Between Branches

### 15. Switch Branches

**Command**

```bash
git switch <name>
```

**OR**

```bash
git checkout <name>
```

**Example Scenario**

I switched from `practice-branch` to `main`.

```bash
git switch main
```

**Result**

Git changed the active branch to `main`.

---

### 16. Create a Branch

**Command**

```bash
git switch -c <name>
```

**OR**

```bash
git checkout -b <name>
```

**Example Scenario**

I created a new branch called `documentation-branch`.

```bash
git switch -c documentation-branch
```

**Result**

Git created a new branch and switched to it automatically.

---

### 17. List Branches

**Command**

```bash
git branch
```

**Example Scenario**

I displayed all local branches.

```bash
git branch
```

**Result**

Git displayed all branches in the repository.

---

### 18. List Branches by Most Recent Commit

**Command**

```bash
git branch --sort=-committerdate
```

**Example Scenario**

I sorted branches according to their latest commits.

```bash
git branch --sort=-committerdate
```

**Result**

Git displayed the most recently updated branch first.

---

### 19. Delete a Branch

**Command**

```bash
git branch -d <name>
```

**Example Scenario**

I deleted a branch after merging it into `main`.

```bash
git branch -d documentation-branch
```

**Result**

The merged branch was removed.

---

### 20. Force Delete a Branch

**Command**

```bash
git branch -D <name>
```

**Example Scenario**

I deleted a branch that had not been merged.

```bash
git branch -D temporary-branch
```

**Result**

Git deleted the branch even though it had not been merged.
