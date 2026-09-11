# Troubleshooting

Start with:

```console
git status
git branch --show-current
git remote -v
```

Do not force-push or delete `.git/` while diagnosing a tutorial problem.

## `not a git repository`

Check the current directory:

```console
pwd
ls
```

On Windows Git Bash, use the same commands. Enter the repository directory with `cd`.

## `destination path ... already exists`

Do not clone over an existing directory. Inspect it first. If it is a clone for this tutorial, enter it and run `git status`. Otherwise choose a new destination name:

```console
git clone URL intro-to-git-workshop-fresh
```

## `remote origin already exists`

A clone already has an `origin`. Inspect it:

```console
git remote -v
```

For the tutorial workflow, add the source repository as `upstream`, not as another `origin`.

## Authentication failed

```console
gh auth status
gh auth login
gh auth setup-git
```

Confirm that the account is the one that owns your fork. Never put credentials in a remote URL, issue or screenshot.

## Push rejected

Check the current branch and remote:

```console
git branch --show-current
git remote -v
git status
```

For the tutorial exercise, push the participant branch to your fork:

```console
git push -u origin participant/YOUR-USERNAME
```

Do not force-push to `main`.

## Detached HEAD after inspecting history

If you only inspected the selected snapshot and made no edits, run `git checkout main`. If you started new work there, create a branch with `git switch -c saved-work` before leaving and ask for help preserving it.

## Participant branch or file already exists

If a participant branch or file is present, inspect `git branch`, `git status` and the file before creating anything. Continue on your own branch when it contains your work; do not overwrite another participant’s work.

## Fast-forward update refused

Local `main` and `upstream/main` may have different commits. Keep both histories and ask for help inspecting them. Do not force-push or reset to make the message disappear.

## Git opened a pager

Press `q` to return to the terminal.

## Git opened an editor for a merge commit

Keep the proposed message, save and close the editor. Common exits:

- Vim: press `Esc`, type `:wq`, then press Enter;
- Nano: press `Ctrl+O`, Enter, then `Ctrl+X`;
- VS Code: save and close the commit-message tab.

## Line-ending warnings

Warnings about LF and CRLF are common when repositories move between Windows, macOS and Linux. Stop and ask if a file appears to have every line changed. Do not commit a whole-file line-ending rewrite during the participant exercise.

## The pull request shows unrelated files

Return to the terminal and inspect:

```console
git diff upstream/main...HEAD
git log --oneline upstream/main..HEAD
```

Ask for help before rewriting or deleting commits. Preserve the branch until the cause is understood.
