# Conflict demonstration

Prepare the demonstration in a fork clone with `origin` pointing to that fork and `upstream` to `mdi-group/intro-to-git-workshop`. The GitHub account used for the demonstration needs permission to merge pull requests into the tutorial repository. Keep all participant files untouched.

## 1. Start both branches from the same commit

Start with a clean working tree and no existing demo branches with these names:

```console
git remote -v
git switch main
git fetch upstream
git merge --ff-only upstream/main
```

Confirm that `conflict-demo/status.txt` contains exactly:

```text
Workshop mode: open.
```

If the file does not contain this line, restore it through a normal reviewed commit on the tutorial repository, then fetch and fast-forward before continuing.

## 2. Open the first pull request

```console
git switch -c conflict-reviewing
```

Edit the file to `Workshop mode: reviewing.` and save:

```console
git add conflict-demo/status.txt
git commit -m "Set workshop mode to reviewing"
git push -u origin conflict-reviewing
```

Open a browser pull request from your fork’s `conflict-reviewing` to the tutorial repository’s `main`. Leave it open for now.

## 3. Open the competing pull request

Local `main` still contains the common starting line. Branch from it, not from `conflict-reviewing`:

```console
git switch main
git switch -c conflict-demo
```

Edit the file to `Workshop mode: merging.` and save:

```console
git add conflict-demo/status.txt
git commit -m "Set workshop mode to merging"
git push -u origin conflict-demo
```

Open the second pull request from your fork’s `conflict-demo` to the tutorial repository’s `main`.

## 4. Merge the first PR and show the conflict

In GitHub, review and merge the `conflict-reviewing` pull request. Refresh the `conflict-demo` pull request: it now conflicts with `main`.

Back in the fork clone:

```console
git switch conflict-demo
git status
git fetch upstream
git merge upstream/main
git status --short
```

The merge deliberately stops with a conflict. Short status reports `UU conflict-demo/status.txt`. The default conflict markers are:

```text
<<<<<<< HEAD
Workshop mode: merging.
=======
Workshop mode: reviewing.
>>>>>>> upstream/main
```

If your configured conflict style includes an ancestor block, explain that extra context or use a disposable clone configured with `git config merge.conflictStyle merge` before preparing the demo.

## 5. Resolve and push

Ask what the final sentence should communicate. Replace the complete marker block with:

```text
Workshop mode: reviewing and merging.
```

Save, inspect and finish:

```console
git add conflict-demo/status.txt
git diff --staged
git status
git commit -m "Resolve the tutorial conflict"
git push origin conflict-demo
```

Refresh the pull request and show the cleared conflict. Inspect the two-parent resolution commit:

```console
git log --oneline --graph --decorate --all
```

Review the final diff before merging. If you need to abandon the unresolved demonstration, `git merge --abort` is available before the resolution commit; start from a clean working tree so it can restore that state.

Finish with the fixture on the tutorial repository’s `main` set to `Workshop mode: open.` Use a normal new commit or pull request; do not rewrite history.
