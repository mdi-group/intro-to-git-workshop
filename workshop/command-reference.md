# Command reference

## Repository and identity

| Command | Purpose |
| --- | --- |
| `git init -b main` | create a repository with `main` as the first branch |
| `git status` | show the branch and file states |
| `git config --global user.name "Name"` | set the commit author name |
| `git config --global user.email "email"` | set the commit author email |

## Inspect, stage and commit

| Command | Purpose |
| --- | --- |
| `git diff` | compare saved, unstaged changes with the staging area |
| `git add FILE` | copy the saved content of a file into the staging area |
| `git diff --staged` | compare the staging area with the latest commit |
| `git commit -m "Message"` | record the staged snapshot |
| `git log --oneline` | show compact history |
| `git show HASH` | show one commit |
| `git show HEAD:FILE` | show a file from the latest commit |

## Branches

| Command | Purpose |
| --- | --- |
| `git branch --show-current` | print the current branch |
| `git switch -c NAME` | create and switch to a branch |
| `git switch NAME` | switch to an existing branch |
| `git branch -d NAME` | delete a merged local branch |
| `git log --oneline --graph --decorate --all` | draw the branch graph |

## Remotes

| Command | Purpose |
| --- | --- |
| `git clone URL` | create a local copy of a repository |
| `git remote -v` | list remote names and URLs |
| `git remote add upstream URL` | add a remote called `upstream` |
| `git fetch upstream` | download new upstream commits without changing the current branch |
| `git merge --ff-only upstream/main` | move local `main` forward when histories have not diverged |
| `git push -u origin BRANCH` | push a branch and remember its remote counterpart |
| `git pull --ff-only upstream main` | fetch and fast-forward from upstream `main` |

## Recovery

| Command | Purpose |
| --- | --- |
| `git restore --staged FILE` | unstage a file while keeping the saved edit |
| `git restore FILE` | discard unstaged edits to a file |
| `git revert HASH` | record a new commit that reverses an earlier commit |
| `git merge --abort` | stop an unresolved merge and return to the pre-merge state |
