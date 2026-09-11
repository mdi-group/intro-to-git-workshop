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

## Choose the recovery command carefully

Choose the command that matches your situation. Use one option at a time and finish this section on a clean `main`.

| Situation | Command | Effect |
| --- | --- | --- |
| staged the wrong edit | `git restore --staged index.md` | removes it from the staging area and keeps the saved edit |
| want to discard an unstaged edit | `git restore index.md` | replaces the saved file with the staged version; when nothing is staged, this matches the latest commit |
| need to undo a shared commit | `git revert HASH` | creates a new commit that reverses the selected commit |

Inspect `git status` and `git diff` before using `git restore index.md`. That command discards unstaged work.

Avoid `git reset --hard` in this tutorial. It can discard commits and saved work, and it is unnecessary for these exercises.
