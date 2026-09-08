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

## Practical 2: staged and unstaged content

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

The working file says `ready`, while the staged snapshot still says `draft`. Run `git add` again to update the staged snapshot, then commit:

```console
git add index.md
git commit -m "Record the note status"
git show HEAD:index.md
```

## Read earlier versions

```console
git log --oneline
git log --oneline -- index.md
git show HASH
git show HASH^:index.md
```

Replace `HASH` with the commit that added `and source`. The caret selects its first parent.

## Choose the recovery command carefully

| Situation | Command | Effect |
| --- | --- | --- |
| staged the wrong edit | `git restore --staged index.md` | removes it from the staging area and keeps the saved edit |
| want to discard an unstaged edit | `git restore index.md` | replaces the saved file with the committed version |
| need to undo a shared commit | `git revert HASH` | creates a new commit that reverses the selected commit |

Inspect `git status` and `git diff` before using `git restore index.md`. That command discards unstaged work.

Avoid `git reset --hard` in this workshop. It can discard commits and saved work, and it is unnecessary for these exercises.
