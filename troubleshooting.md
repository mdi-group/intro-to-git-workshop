# Git for research projects

Git works best with source material that can be inspected as text.

## Good candidates for version control

- analysis and simulation code;
- configuration and parameter files;
- environment specifications;
- documentation and lab notes written in text formats;
- small example or test data;
- scripts that generate figures and tables;
- manuscript source files.

## Usually keep elsewhere

- passwords, access tokens and private keys;
- sensitive or identifiable data;
- large raw datasets;
- generated binaries and caches;
- large model checkpoints;
- files whose licence does not permit redistribution.

Record where external data and models are stored, which version was used, and how derived outputs can be regenerated.

## Use .gitignore deliberately

`.gitignore` prevents matching untracked files from being added by routine commands. It does not remove a file that is already tracked and it does not erase a secret from history.

Before committing:

```console
git status
git diff
git diff --staged
```

Check generated notebooks and figures carefully. Notebook outputs can create large or noisy diffs, so agree as a group whether outputs are committed.

## A practical repository structure

| Path | Purpose |
| --- | --- |
| `README.md` | purpose, setup and a small runnable example |
| `environment.yml` | software environment |
| `.gitignore` | generated or local files to exclude |
| `src/` | source code |
| `tests/` | checks on the code |
| `scripts/` | repeatable analysis and figure generation |
| `notebooks/` | exploratory work |
| `config/` | analysis settings |
| `docs/` | supporting documentation |

The README should tell a new contributor what the project does, what it needs, how to run a small example, and where larger data live.

## Before sharing a repository

1. Search the tracked files and history for secrets or private data.
2. Check that the licence permits sharing.
3. Run the smallest useful test or example.
4. Confirm that the environment can be reconstructed.
5. Tag or record the commit used for an important result.
