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

---
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

---
# Git Cheat Sheet Add-On: Diff Commands

## Compare Changes

### 21. Show All Staged and Unstaged Changes

**Command**

```bash
git diff HEAD
```

**Example Scenario**

I modified `README.md` and `Git-CheatSheet.md`. I staged one file and left the other unstaged.

```bash
echo "Updated README" >> README.md
echo "Added diff notes" >> Git-CheatSheet.md

git add Git-CheatSheet.md

git diff HEAD
```

**Result**

Git displayed all changes in the repository, including both staged and unstaged modifications.

---

### 22. Show Only Staged Changes

**Command**

```bash
git diff --staged
```

**Example Scenario**

I modified `README.md` and staged the file.

```bash
echo "Staged example" >> README.md

git add README.md

git diff --staged
```

**Result**

Git displayed only the changes that had been added to the staging area.

---

### 23. Show Only Unstaged Changes

**Command**

```bash
git diff
```

**Example Scenario**

I modified `README.md` but did not stage the changes.

```bash
echo "Unstaged example" >> README.md

git diff
```

**Result**

Git displayed only the changes that had not yet been staged.

---

## Compare Commits

### 24. Show the Difference Between a Commit and Its Parent

**Command**

```bash
git show <commit>
```

**Example Scenario**

I displayed the changes introduced by the most recent commit.

```bash
git show HEAD
```

**Result**

Git displayed the commit information and the changes included in that commit.

---

### 25. Compare Two Commits

**Command**

```bash
git diff <commit> <commit>
```

**Example Scenario**

I compared the current commit with the previous commit.

```bash
git diff HEAD~1 HEAD
```

**Result**

Git displayed the differences between the two commits.

---

### 26. Compare One File Since a Specific Commit

**Command**

```bash
git diff <commit> <file>
```

**Example Scenario**

I compared `README.md` with the version stored in the previous commit.

```bash
git diff HEAD~1 README.md
```

**Result**

Git displayed only the changes made to `README.md`.

---

### 27. Show a Summary of a Diff

**Command**

```bash
git diff <commit> --stat
```

**Example Scenario**

I displayed a summary of all changes since the latest commit.

```bash
git diff HEAD --stat
```

**Result**

Git displayed the modified files and the number of insertions and deletions.

---

### 28. Show a Summary of Changes in a Commit

**Command**

```bash
git show <commit> --stat
```

**Example Scenario**

I displayed a summary of the latest commit.

```bash
git show HEAD --stat
```

**Result**

Git displayed the commit details and a statistical summary of the changes.

---

## Ways to Refer to a Commit

### 29. Use a Branch Name

**Example**

```bash
git diff main
```

**Result**

Git compared the current working tree with the `main` branch.

---

### 30. Use a Tag

**Example**

```bash
git diff v0.1
```

**Result**

Git compared the current working tree with the `v0.1` tag.

---

### 31. Use a Commit ID

**Example**

```bash
git diff 3e887ab
```

**Result**

Git compared the current working tree with the specified commit.

---

### 32. Use a Remote Branch

**Example**

```bash
git diff origin/main
```

**Result**

Git compared the current working tree with the remote `main` branch.

---

### 33. Use `HEAD`

**Example**

```bash
git diff HEAD
```

**Result**

Git compared the current working tree with the latest commit.

---

### 34. Refer to Earlier Commits

**Example**

```bash
git diff HEAD~3
```

**OR**

```bash
git diff HEAD^^^
```

**Result**

Git compared the current working tree with the commit from three revisions earlier.


# Git Cheat Sheet Add-On: Discard Changes and Edit History

## Discard Your Changes

### 35. Delete Unstaged Changes to One File

**Command**

```bash
git restore <file>
```

**OR**

```bash
git checkout <file>
```

**Example Scenario**

I modified `practice.txt` and then decided that I did not want to keep the changes.

```bash
echo "Temporary change" >> practice.txt

git status

git restore practice.txt

git status
```

**Result**

Before running `git restore`, Git showed `practice.txt` as modified. After running the command, the working tree was clean.

---

### 36. Delete All Staged and Unstaged Changes to One File

**Command**

```bash
git restore --staged --worktree <file>
```

**OR**

```bash
git checkout HEAD <file>
```

**Example Scenario**

I modified `practice.txt`, added it to the staging area, and then restored it to the previous version.

```bash
echo "Another change" >> practice.txt

git add practice.txt

git restore --staged --worktree practice.txt
```

**Result**

The changes were removed from both the staging area and the working directory.

---

### 37. Delete All Staged and Unstaged Changes

**Command**

```bash
git reset --hard
```

**Example Scenario**

I made several temporary changes to `practice.txt` and then removed them.

```bash
echo "Reset example" >> practice.txt
echo "Another line" >> practice.txt

git reset --hard
```

**Result**

All tracked files were restored to the state of the most recent commit.

---

### 38. Delete Untracked Files

**Command**

```bash
git clean -f
```

**Example Scenario**

I created a temporary file that was not being tracked by Git.

```bash
touch temporary.txt

git clean -f
```

**Result**

The untracked file was removed from the repository.

---

### 39. Stash All Staged and Unstaged Changes

**Command**

```bash
git stash
```

**Example Scenario**

I needed to save my work temporarily before continuing.

```bash
echo "Stash example" >> practice.txt

git stash

git stash pop
```

**Result**

The changes were temporarily stored and then restored to the working directory.

---

## Edit History

### 40. Undo the Most Recent Commit While Keeping the Working Directory the Same

**Command**

```bash
git reset HEAD^
```

**Example Scenario**

I created a temporary commit and then removed it while keeping the file changes.

```bash
echo "Reset commit example" >> practice.txt

git add .

git commit -m "Temporary commit"

git reset HEAD^
```

**Result**

The commit was removed, but the changes remained in the working directory.

---

### 41. Squash the Last Five Commits Into One

**Command**

```bash
git rebase -i HEAD~5
```

**Example Scenario**

I combined the previous five commits into a single commit.

```bash
git rebase -i HEAD~5
```

I changed the rebase instructions from:

```text
pick 11ab701 Add diff command examples to Git cheat sheet
pick c8d6172 Add practice file for discard and history examples
pick 4613980 Document git reset hard example
pick 038ade5 Document git stash example
pick cc14e9a Document git reset HEAD example
```

to:

```text
pick 11ab701 Add diff command examples to Git cheat sheet
fixup c8d6172 Add practice file for discard and history examples
fixup 4613980 Document git reset hard example
fixup 038ade5 Document git stash example
fixup cc14e9a Document git reset HEAD example
```

**Result**

The five commits were combined into a single commit.

---

### 42. Undo a Failed Rebase

**Command**

```bash
git reflog BRANCHNAME
```

Then:

```bash
git reset --hard <commit>
```

**Example Scenario**

I displayed the commit history stored in the reflog and restored the repository to an earlier state.

```bash
git reflog main

git reset --hard <commit-id>
```

**Result**

The repository was restored to the selected commit.

---

### 43. Change a Commit Message or Add a File You Forgot

**Command**

```bash
git commit --amend
```

**Example Scenario**

I added a file that I forgot to include in the previous commit.

```bash
echo "Amend example" >> practice.txt

git add practice.txt

git commit --amend
```

**Result**

The most recent commit was updated with the new changes.
