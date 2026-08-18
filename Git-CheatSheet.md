# Git Cheat Sheet Examples

## Getting Started

### `git init`

**Purpose:** Creates a new Git repository.

**Example:**

```bash
git init
```

I used this command to initialize my CS-101 repository.

---

### `git clone <url>`

**Purpose:** Copies an existing repository to a local machine.

**Example:**

```bash
git clone git@github.com:brinda-codes/CS-101-L01-Setup-your-first-repo-.git
```

I used this command to clone my GitHub repository.

---

## Prepare to Commit

### `git add <file>`

**Purpose:** Adds a specific file to the staging area.

**Example:**

```bash
git add README.md
```

I used this command when I added my Git notes.

---

### `git add .`

**Purpose:** Adds all modified files.

**Example:**

```bash
git add .
```

I used this command to stage all files in the repository.

---

### `git status`

**Purpose:** Displays the current status of the repository.

**Example:**

```bash
git status
```

I used this command to verify that my working tree was clean.


# Git Cheat Sheet Examples

## Getting Started

### 1. Start a New Repository

**Command**

```bash
git init
```

**Example Scenario**

I created a new directory and initialized it as a Git repository.

```bash
mkdir git-demo
cd git-demo
git init
```

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

```bash
git add <file>
```

**Example Scenario**

I modified the README file and staged only that file.

```bash
echo "Git add example" >> README.md
git add README.md
```

**Result**

Only `README.md` was added to the staging area.

---

### 4. Add All Untracked Files and Unstaged Changes

**Command**

```bash
git add .
```

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

```bash
git add -p
```

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

```bash
git mv <old> <new>
```

**Example Scenario**

I renamed a file and allowed Git to track the change.

```bash
touch notes.txt

git mv notes.txt git-notes.txt
```

**Result**

The file was renamed.

---

### 7. Delete a File

**Command**

```bash
git rm <file>
```

**Example Scenario**

I removed a file from the repository.

```bash
touch delete-me.txt

git add delete-me.txt
git commit -m "Add temporary file"

git rm delete-me.txt
```

**Result**

The file was deleted and staged for removal.

---

### 8. Stop Tracking a File Without Deleting It

**Command**

```bash
git rm --cached <file>
```

**Example Scenario**

I stopped tracking a file while keeping it on my computer.

```bash
touch temp.txt

git add temp.txt

git rm --cached temp.txt
```

**Result**

Git stopped tracking the file, but the file remained in the project directory.

---

### 9. Unstage One File

**Command**

```bash
git reset <file>
```

**Example Scenario**

I removed one file from the staging area.

```bash
git add README.md
git add Git-CheatSheet.md

git reset README.md
```

**Result**

`README.md` was unstaged.

---

### 10. Unstage Everything

**Command**

```bash
git reset
```

**Example Scenario**

I removed all files from the staging area.

```bash
git add .

git reset
```

**Result**

All staged files were unstaged.

---

### 11. Check the Repository Status

**Command**

```bash
git status
```

**Example Scenario**

I checked the current state of my repository.

```bash
git status
```

**Result**

Git displayed the current branch and listed staged, unstaged, and untracked files.

--------



# Git Cheat Sheet Examples - Commits and Branching

## Make Commits

### 1. Make a Commit and Open the Text Editor

**Command**

```bash id="q92x4v"
git commit
```

**Example Scenario**

I created a new file and committed it without using the `-m` flag.

```bash id="r7mzq3"
echo "Commit example" > examples/commit-editor.txt

git add examples/commit-editor.txt

git commit
```

**Result**

Git opened the default text editor so that I could write a commit message manually.

---

### 2. Make a Commit with a Message

**Command**

```bash id="9mctcc"
git commit -m "message"
```

**Example Scenario**

I created a new file and committed it with a message.

```bash id="4h7on9"
echo "Commit with message example" > examples/commit-message.txt

git add examples/commit-message.txt

git commit -m "Demonstrate git commit -m"
```

**Result**

The changes were committed with a message written directly in the command.

---

### 3. Commit All Unstaged Changes

**Command**

```bash id="31qjx4"
git commit -am "message"
```

**Example Scenario**

I modified an existing file and committed the changes without running `git add`.

```bash id="ow2rr1"
echo "Additional notes" >> README.md

git commit -am "Demonstrate git commit -am"
```

**Result**

Git automatically staged all modified tracked files and created a commit.

---

## Move Between Branches

### 4. Switch Branches

**Command**

```bash id="wz67hn"
git switch <name>
```

**OR**

```bash id="s7b5z5"
git checkout <name>
```

**Example Scenario**

I switched from `practice-branch` to `main`.

```bash id="06i4hi"
git switch main
```

**OR**

```bash id="d87d08"
git checkout main
```

**Result**

The active branch changed from `practice-branch` to `main`.

---

### 5. Create a Branch

**Command**

```bash id="sc16ca"
git switch -c <name>
```

**OR**

```bash id="3h4xj2"
git checkout -b <name>
```

**Example Scenario**

I created a new branch called `documentation-branch`.

```bash id="k4pvr1"
git switch -c documentation-branch
```

**OR**

```bash id="9u67ya"
git checkout -b documentation-branch
```

**Result**

A new branch was created and Git automatically switched to it.

---

### 6. List Branches

**Command**

```bash id="cll0ov"
git branch
```

**Example Scenario**

I displayed all branches in the repository.

```bash id="d2czhn"
git branch
```

**Example Output**

```text id="5djlwm"
main
practice-branch
test-branch
```

**Result**

Git displayed all local branches.

---

### 7. List Branches by Most Recent Commit

**Command**

```bash id="5j4ebh"
git branch --sort=-committerdate
```

**Example Scenario**

I sorted branches according to their most recent commit.

```bash id="9w0yag"
git branch --sort=-committerdate
```

**Result**

Git displayed the most recently updated branch first.

---

### 8. Delete a Branch

**Command**

```bash id="bdw6cf"
git branch -d <name>
```

**Example Scenario**

I deleted a branch after merging it into `main`.

```bash id="cjrqye"
git branch -d documentation-branch
```

**Result**

The merged branch was removed.

---

### 9. Force Delete a Branch

**Command**

```bash id="slnl1c"
git branch -D <name>
```

**Example Scenario**

I deleted a branch that had not been merged.

```bash id="g9j7a8"
git branch -D temporary-branch
```

**Result**

Git deleted the branch even though it had not been merged.

