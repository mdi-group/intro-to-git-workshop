# Recap

## Explain the workflow from memory

1. You saved an edit. How do you review it, stage it and record it?
2. Why can one file appear under both staged and unstaged changes?
3. What do a commit hash, a branch name and `HEAD` identify?
4. Where do a fork and a clone live? Which remote receives your participant branch?
5. What are the source and destination of your workshop pull request?
6. What do you do when a merge reports a conflict?

<details>
<summary>Check your answers</summary>

1. Run `git diff`, `git add FILE`, `git diff --staged`, then `git commit -m "Describe the change"`. Check `git status` afterwards. New untracked files appear in status and can be reviewed after staging.
2. You staged one version and then saved another. `git diff` compares saved tracked content with the staged version; `git diff --staged` compares the staged version with the latest commit.
3. A hash identifies a commit. A branch name points to a commit and moves when that branch gains commits. `HEAD` normally names the current branch; in detached HEAD it points directly to a commit.
4. A fork is hosted on GitHub; a clone is local. Push to `origin`, your personal fork. Fetch workshop updates from `upstream`.
5. Source: your fork’s `participant/YOUR-USERNAME`. Destination: `mdi-group/intro-to-git-workshop`, branch `main`.
6. Inspect status and the conflicting file, choose the final content, remove markers, save, stage, commit and push. The existing PR updates.

</details>

## Match a question to a command

| Question | Command |
| --- | --- |
| What state am I in? | `git status` |
| What changed? | `git diff` and `git diff --staged` |
| What was recorded? | `git log --oneline` and `git show HASH` |
| How do I unstage while keeping my edit? | `git restore --staged FILE` |
| How do I reverse a shared commit? | `git revert HASH` |
| How do I get merged workshop changes? | on clean `main`, `git pull --ff-only upstream main` |

## Apply this to your research

Choose one project and identify the code, settings, environment specification and documentation to track. Decide where larger or sensitive data will live and how you will record the data version. Write down the first small commit you could make.
