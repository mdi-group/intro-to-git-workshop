# Local version control

This practical builds a small repository called `aichemy-notes`.

## 1. Create the repository

```console
mkdir aichemy-notes
cd aichemy-notes
git init -b main
git status
```

Git stores repository history and configuration inside the hidden `.git/` directory. Do not edit files inside `.git/` during the workshop.

Expected state:

```text
On branch main
No commits yet
```

## 2. Create the first file

Create `index.md` in your editor:

```markdown
# AIChemy research notes

Topic: reproducible analysis.
```

Save the file, then run:

```console
git status
```

`index.md` is untracked. Git can see the file but has not been asked to include it in a commit.

## 3. Stage the file

```console
git add index.md
git status
```

The staging area contains the snapshot that the next commit will record.

```mermaid
flowchart LR
    W[Working file] -->|git add| S[Staged snapshot]
    S -->|git commit| H[Commit history]
```

## 4. Make the first commit

```console
git commit -m "Introduce the research notes"
git status
```

A useful commit message completes this sentence: "If applied, this commit will..."

## Practical 1: separate changes

Add this section to `index.md`:

```markdown
## Data

Record the dataset version.
```

Save, stage and commit it:

```console
git add index.md
git commit -m "Record the dataset version"
```

Now add:

```markdown
## Method

Record the analysis settings.
```

Make a second commit:

```console
git add index.md
git commit -m "Document the analysis settings"
git log --oneline
```

Checkpoint: the history contains three commits, each with one clear purpose. Press `q` if Git opened the log in a pager.

## Working tree, staging area and history

These three states explain most everyday Git commands:

| State | Contains | Useful command |
| --- | --- | --- |
| working tree | files currently saved on disk | `git diff` |
| staging area | content selected for the next commit | `git diff --staged` |
| commit history | recorded snapshots | `git log`, `git show` |
