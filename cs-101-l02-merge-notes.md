# CS-101 L02 — Working with a Team on Git

## Task 1: Isolated branch work

Created a new branch cs-101-l02 off of main.

git checkout -b cs-101-l02
git push -u origin cs-101-l02

Added cs-101-l02-task-01-file-01.md on this branch, committed, and pushed:

git add cs-101-l02-task-01-file-01.md
git commit -m "Add cs-101-l02-task-01-file-01.md"
git push origin cs-101-l02

Switched back to main, verified with git branch, and created a second file directly on main:

git checkout main
git branch
git add cs-101-l02-task-01-file-02.md
git commit -m "Add cs-101-l02-task-01-file-02.md"
git push origin main

At this point main and cs-101-l02 had diverged independently, each with a commit the other branch did not have.

Diagram of the divergence (commit hashes and branch names are from the actual repository):
See screenshots/branch-divergence-diagram.png

A: 3cec4a1 (git push commands here)
B: 1af9883 (git config,pull) — the commit where cs-101-l02 branched off
C: 2856a2b (main) — Add cs-101-l02-task-01-file-02.md
D: a44e44f (cs-101-l02) — Add cs-101-l02-task-01-file-01.md

## Task 2: Merging a feature branch into main

Switched to main and merged cs-101-l02 into it:

git checkout main
git merge cs-101-l02
git push origin main

This merge required no conflict resolution, since the two branches had touched different files.

## Task 3: Same file, different lines — testing automatic merge

Created shared-file.md on main as a common base, then created two branches (branch-a and branch-b) off of it, each appending a different new line to the file in a different location.

Merged branch-a into main (fast-forward, no conflict).
Merged branch-b into main:

git merge branch-b

Result: Git auto-merged successfully. Auto-merging shared-file.md completed with no CONFLICT message, because the two additions landed in different, non-overlapping parts of the file. This showed that Git can often combine independent changes automatically even when they touch the same file, as long as the changes do not overlap on the same lines.

## Task 4: Same line, different content — forcing a real conflict

To reliably trigger a conflict, created two more branches (branch-c and branch-d) off of main, both editing the exact same line (the file's heading) to different text.

Merged branch-c into main (fast-forward, no conflict, since main had not moved).
Attempted to merge branch-d into main:

git merge branch-d

Result:
Auto-merging shared-file.md
CONFLICT (content): Merge conflict in shared-file.md
Automatic merge failed; fix conflicts and then commit the result.

This time Git could not decide which version of the line to keep, since both branches modified the identical line differently. Git left conflict markers in the file for manual resolution.

## Resolving the conflict in VS Code

Opened the repository in VS Code with `code .` and clicked on the conflicted file. VS Code highlighted the conflicting section directly in the editor with color-coded blocks and inline action buttons: Accept Current Change, Accept Incoming Change, Accept Both Changes, Compare Changes.

Interpretation of the labels:
- "Current" (marked HEAD) is the version already on the branch being merged into — in this case, main, which already contained branch-c's edit to the heading.
- "Incoming" is the version being brought in from the branch being merged — branch-d's edit to the same heading.

Since both edits were meaningful and neither should be discarded, clicked "Accept Both Changes." This removed the <<<<<<<, =======, and >>>>>>> conflict markers automatically and kept both versions of the heading, one after the other, in the file.

After clicking, a small amount of leftover text (the words HEAD and branch-d, remnants of the marker lines) had to be manually deleted, since VS Code's Accept Both Changes only strips the marker symbols themselves, not any stray text that had been attached to those marker lines by earlier edits.

Saved the file, then verified in the terminal:

git status
git add shared-file.md
git commit -m "Merge branch-d into main, resolving conflict on shared heading"
git push origin main

Screenshots: see screenshots/conflict-markers-in-vscode.png and screenshots/resolved-file-in-vscode.png

## Summary

- A merge without any overlapping line changes (branch-a and branch-b) can be resolved automatically by Git with no manual intervention.
- A merge where two branches change the exact same line (branch-c and branch-d) always produces a conflict that requires manual resolution.
- VS Code's merge conflict interface labels the branch being merged into as "Current"/"HEAD" and the branch being merged from as "Incoming," and provides one-click options to accept one side, the other, or both.
