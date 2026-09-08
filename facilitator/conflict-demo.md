# Controlled conflict demonstration

Prepare this in a presenter clone after the workshop materials are on `main`.

## 1. Record the common starting line

Confirm that `conflict-demo/status.txt` contains:

```text
Workshop mode: open.
```

Commit and push it on `main` if it is not already present.

## 2. Create the demonstration branch

```console
git switch main
git pull --ff-only origin main
git switch -c conflict-demo
```

Change `conflict-demo/status.txt` to:

```text
Workshop mode: merging.
```

```console
git add conflict-demo/status.txt
git commit -m "Set workshop mode to merging"
git push -u origin conflict-demo
```

Open a pull request from `conflict-demo` to `main`, but do not merge it.

## 3. Make the competing change on main

```console
git switch main
```

Change the same line to:

```text
Workshop mode: reviewing.
```

```console
git add conflict-demo/status.txt
git commit -m "Set workshop mode to reviewing"
git push origin main
```

Refresh the open pull request. GitHub should now report that the branch conflicts with `main`.

## 4. Resolve the conflict locally

```console
git switch conflict-demo
git fetch origin
git merge origin/main
```

Open `conflict-demo/status.txt`. Explain the `HEAD`, separator and incoming-branch marker lines. Replace the complete marker block with:

```text
Workshop mode: reviewing and merging.
```

Finish and push:

```console
git add conflict-demo/status.txt
git diff --staged
git status
git commit -m "Resolve the workshop conflict"
git push
```

Refresh the pull request and show that the conflict has cleared. Inspect the joined history:

```console
git log --oneline --graph --decorate --all
```

After the demonstration, merge or close the pull request and restore `conflict-demo/status.txt` to a sensible state for future sessions.
