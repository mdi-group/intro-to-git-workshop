# Inspect and recover

## Review a saved edit

Change the Data sentence in `index.md`:

```diff
- Record the dataset version.
+ Record the dataset version and source.
```

Before staging it, run:

```console
git diff
```

Stage the file and compare the staged snapshot with the latest commit:

```console
git add index.md
git diff --staged
git commit -m "Record the dataset source"
```

## Practice 2: staged and unstaged content

Add this line to `index.md`, save it and stage it:

```text
Status: draft.
```

```console
git add index.md
```

Now change the saved line to `Status: ready.` without staging it again.

Inspect both comparisons:

```console
git status
git diff
git diff --staged
```

Relevant `git status` output:

```text
On branch main
Changes to be committed:
  modified:   index.md

Changes not staged for commit:
  modified:   index.md
```

The file appears twice because the saved and staged versions differ. `Status:` is text inside the file; it is separate from the `git status` command.

The changed lines in `git diff` are:

```diff
-Status: draft.
+Status: ready.
```

`git diff --staged` includes `+Status: draft.` because the latest commit contains no Status line yet.

The working file says `ready`, while the staged snapshot still says `draft`. Run `git add` again to update the staged snapshot, then commit:

```console
git add index.md
git commit -m "Mark the notes ready"
git show HEAD:index.md
```

Run `git status` again: the working tree should be clean, and `git show HEAD:index.md` should end with `Status: ready.`.

## Read earlier versions

```console
git log --oneline
git log --oneline -- index.md
git show HASH
git show HASH^:index.md
```

Replace `HASH` with the commit that added `and source`. The caret selects its first parent.

## Inspect an older snapshot with checkout

Start on `main` with a clean working tree. Choose the hash of the analysis-settings commit from your own log:

```console
git status
git checkout --detach HASH
```

Example output:

```text
HEAD is now at 3480b70 Record the analysis settings
```

Open `index.md`: the source and Status edits are absent at this point in history. `HEAD` now points directly to the selected commit. No branch is checked out; this is called detached HEAD. Inspect only during this demonstration, then return:

```console
git checkout main
git status
```

Your latest committed file is back. The modern equivalents are `git switch --detach HASH` and `git switch main`. `git show` reads an older version without switching the working files.

## Restore or revert changes

Use `git restore` for uncommitted file changes. Use `git revert` for a commit that is already in the repository history.

These are alternative examples, not one sequence to run. Start each example with a clean working tree.

### Unstage an edit without losing it

Make a small edit to `index.md` and stage it:

```console
git add index.md
git status
```

If you decide not to include the edit in the next commit, unstage it:

```console
git restore --staged index.md
git status
git diff
```

The edit remains in the working file, but it is no longer in the staging area. With `--staged`, Git restores the index to match `HEAD`.

### Discard an unstaged edit

Make another edit to `index.md`, but do not stage it. Inspect it first:

```console
git status
git diff
```

If you do not want to keep the edit, restore the file from the staging area:

```console
git restore index.md
git status
```

When nothing is staged, this restores the file to the version in the latest commit. This command discards the unstaged edit, so check `git diff` before running it.

### Restore a file from a selected commit

To bring a file from another commit into your working tree without changing branches, use `--source`:

```console
git restore --source HASH -- index.md
git diff
```

Replace `HASH` with a commit from `git log --oneline`. The restored content is an unstaged edit. Review it, then either commit it or discard it with `git restore index.md`.

### Revert a committed change

To reverse a commit that is already part of the shared history:

```console
git status
git log --oneline
git revert HASH
git log --oneline -2
```

Replace `HASH` with the commit to reverse. Save and close the commit-message editor when Git opens it. Git creates a new commit with the inverse change; it does not erase the original commit. A clean working tree is required before starting `git revert`. If the revert has conflicts, resolve the files, stage them and run `git revert --continue`. Use `git revert --abort` to cancel an unresolved revert.

| Situation | Command | Effect |
| --- | --- | --- |
| staged the wrong edit | `git restore --staged index.md` | removes it from the staging area and keeps the saved edit |
| want to discard an unstaged edit | `git restore index.md` | restores the saved file from the staging area |
| want a file from another commit | `git restore --source HASH -- index.md` | copies that commit’s file into the working tree as an unstaged edit |
| need to undo a shared commit | `git revert HASH` | creates a new commit that reverses the selected commit |

Avoid `git reset --hard` in this tutorial. It can discard commits and saved work, and it is unnecessary for these exercises.
