# Branches and pull requests

## Commits, branches and HEAD

A commit records a snapshot and points to its parent commit. A branch is a movable name for one commit. `HEAD` normally names the branch that is currently checked out.

```text
HEAD -> main -> c2 -> c1 -> c0
```

Create a branch:

```console
git switch -c participant/YOUR-USERNAME
```

At first, `main` and `participant/YOUR-USERNAME` point to the same commit. A new commit moves only the checked-out branch.

```text
                     HEAD
                       |
                       v
participant/username -> c3
                         |
main ------------------> c2 -> c1 -> c0
```

Check the graph at any point:

```console
git log --oneline --graph --decorate --all
```

## Practical 3: create one unique file

Make the participant directory if it is not already present:

```console
mkdir -p participants
```

Create `participants/YOUR-USERNAME.md` in your editor. Replace the example values:

```markdown
# Your name

GitHub: @YOUR-USERNAME

One useful Git habit: Run git status before deciding what to do next.
```

Save the file, then inspect and commit it:

```console
git status
git add participants/YOUR-USERNAME.md
git diff --staged
git commit -m "Add YOUR-USERNAME workshop note"
```

An untracked file does not appear in `git diff`. `git status` identifies it before staging; `git diff --staged` shows its full content after `git add`.

Checkpoint:

```console
git status
git show --stat --oneline HEAD
```

The working tree should be clean. The latest commit should contain only your new file.

## Push the branch

```console
git push -u origin participant/YOUR-USERNAME
```

The `-u` option connects the local branch to the branch on your fork. Later pushes from the same branch can use `git push`.

## Check the proposed change

```console
git diff upstream/main...HEAD
```

The three-dot comparison shows the work introduced by your branch since it separated from upstream `main`.

## Practical 4: open the pull request

On GitHub:

1. Open your fork.
2. Choose **Contribute**, then **Open pull request**. If that option is not shown, open the Pull requests tab and choose **New pull request**.
3. Set the base repository to `mdi-group/intro-to-git-workshop` and the base branch to `main`.
4. Set the compare repository to your fork and the compare branch to `participant/YOUR-USERNAME`.
5. Use a title such as `Add YOUR-USERNAME workshop note`.
6. Open **Files changed** and confirm that only your file appears.
7. Submit the pull request.

A new commit pushed to the same branch updates the open pull request. There is no need to close it and start again.

## After the pull request is merged

```console
git switch main
git pull --ff-only upstream main
git branch -d participant/YOUR-USERNAME
```

Open your participant file locally to confirm that the merged change arrived. The `-d` option refuses to delete a branch whose commits are not present in the current history.

You may also remove the branch from your fork:

```console
git push origin --delete participant/YOUR-USERNAME
```
