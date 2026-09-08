# Conflicts

Git can combine changes made in different files and many changes made in different parts of one file. It stops when it cannot choose safely between competing edits.

## The workshop example

Both branches start with:

```text
Workshop mode: open.
```

`main` changes the line to:

```text
Workshop mode: reviewing.
```

`conflict-demo` changes the same line to:

```text
Workshop mode: merging.
```

The participant pull requests use unique files, so they should not create this conflict. The facilitators prepare this example separately.

## Read the conflict

After merging the latest `main` into `conflict-demo`, the file contains markers similar to these:

```text
<<<<<<< HEAD
Workshop mode: merging.
=======
Workshop mode: reviewing.
>>>>>>> upstream/main
```

The marker block shows both versions. Decide what the file should say, then replace the entire marked block. For the demonstration, use:

```text
Workshop mode: reviewing and merging.
```

Remove every marker line, save the file and finish the merge:

```console
git add conflict-demo/status.txt
git diff --staged
git status
git commit -m "Resolve the workshop conflict"
git push
```

GitHub updates the existing pull request after the push.

## Inspect the joined history

```console
git log --oneline --graph --decorate --all
```

A merge commit has two parents because it joins two lines of history.

## Abandon an in-progress merge

If the repository was clean before the merge and you want to stop:

```console
git merge --abort
```

Use `git status` before and after this command. Do not use it after the conflict has already been committed.
