# Tutorial slide map

This page maps [Intro to Git and GitHub](https://docs.google.com/presentation/d/1WVP2jXtZ6T27f7jYtcZTL6g7SZoaP3Ztb5sT68hHxsc/edit) to the tutorial material. Numbers refer to the deck’s physical slide order.

## Tutorial sequence

| Slides | Content | Repository material |
| --- | --- | --- |
| 1–5 | Welcome, setup, version control, Git and GitHub | [README](../README.md), [setup](../workshop/00-before-you-begin.md) |
| 6–12 | Create notes, initialise Git, identity, stage, first commit | [Local version control](../workshop/01-local-version-control.md) |
| 13 | Practice 1: two further focused commits | [Practice 1](../workshop/01-local-version-control.md#practice-1-separate-changes) |
| 14 | Commit identifiers and example log | [Commit hashes](../workshop/01-local-version-control.md#what-is-a-commit-hash) |
| 15–18 | Data-source edit, draft/ready state, Practice 2 | [Inspect and recover](../workshop/02-inspect-and-recover.md) |
| 19–21 | Read old versions, checkout, selective recovery | [Inspect and recover](../workshop/02-inspect-and-recover.md) |
| 22 | Pause | No task or timed activity |
| 23–28 | Push concept, authentication, fork, clone, remotes, Practice 3 | [GitHub and remotes](../workshop/03-github-and-remotes.md) |
| 29–34 | Update main, branch, unique file, switching, push, merge graph | [Branches and pull requests](../workshop/04-branches-and-pull-requests.md) |
| 35–37 | Browser PR, Practice 4, update local main after merging | [Branches and pull requests](../workshop/04-branches-and-pull-requests.md) |
| 38–40 | Two-PR conflict demonstration and resolution | [Conflict instructions](../workshop/05-conflicts.md), [demonstration notes](conflict-demo.md) |
| 41 | Research files, data and reproducibility | [Research projects](../workshop/06-research-projects.md) |
| 42–43 | Retrieval recap and applying Git to your own work | [Recap](../workshop/07-recap.md) |
| 49 | Acknowledgements | [Acknowledgements](../workshop/acknowledgements.md) |

The commit graph appears before the commands that update local `main`. Each practical can be followed individually. The checkout and conflict sections are demonstrations; participants can read the explanations without making extra commits.

## Tutorial checkpoints

| Practice | End state |
| --- | --- |
| 1 | In `aichemy-notes`, three commits: introduce notes, dataset version, analysis settings |
| 2 | Five commits after the data-source and ready-status commits; clean `main`; committed file ends with `Status: ready.` |
| 3 | In the separate `intro-to-git-workshop` clone; `origin` is the participant’s fork, `upstream` is mdi-group; clean `main` |
| 4 | One PR from the participant’s `participant/YOUR-USERNAME` branch to tutorial `main`, adding only `participants/YOUR-USERNAME.md` |

## Exact local commit sequence

Use these messages in the local tutorial exercise:

1. `Introduce the research notes`
2. `Record the dataset version`
3. `Record the analysis settings`
4. `Record the dataset source`
5. `Mark the notes ready`

Hashes shown on the slides are examples. Use identifiers from your own log. The history exercise selects the commit that added `and source`; checkout inspects the analysis-settings commit, then returns to `main`.

At the end of Practice 2, `git show HEAD:index.md` contains:

```markdown
# AIChemy research notes
Topic: reproducible analysis.
## Data
Record the dataset version and source.
## Method
Record the analysis settings.
Status: ready.
```

## Keep the two repository contexts separate

The local notes repository is not submitted to GitHub. Leave it on clean `main`, then clone the tutorial fork alongside it. The participant exercise changes only the participant’s own file. The controlled conflict uses `conflict-demo/status.txt` in the fork clone.

Both PRs in the conflict demonstration begin from `Workshop mode: open.`. Merge the reviewing PR first, then on `conflict-demo` fetch and merge `upstream/main`. This produces the marker direction shown in the slides. The agreed resolution is `Workshop mode: reviewing and merging.`.
