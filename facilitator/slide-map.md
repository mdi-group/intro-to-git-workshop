# Slide-to-repository map

Aligned with [Intro to Git and GitHub](https://docs.google.com/presentation/d/1WVP2jXtZ6T27f7jYtcZTL6g7SZoaP3Ztb5sT68hHxsc/edit) on 11 September 2026. Numbers refer to the deck’s physical slide order. Slides 44–48 are skipped authoring assets; slide 49 is the final acknowledgement slide.

## Teaching sequence

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
| 38–40 | Two-PR conflict demonstration and resolution | [Learner explanation](../workshop/05-conflicts.md), [presenter script](conflict-demo.md) |
| 41 | Research files, data and reproducibility | [Research projects](../workshop/06-research-projects.md) |
| 42–43 | Retrieval recap and applying Git to your own work | [Recap](../workshop/07-recap.md) |
| 49 | Acknowledgements | [Acknowledgements](../workshop/acknowledgements.md) |

The graph introduction is slide 29; updating local main follows on slide 30. The repository chapter explains the graph before its update commands. All practicals are individual follow-along activities. The checkout and conflict sections are presenter demonstrations; learners can inspect the supplied explanations without making extra commits.

## The four checkpoints

| Practice | End state |
| --- | --- |
| 1 | In `aichemy-notes`, three commits: introduce notes, dataset version, analysis settings |
| 2 | Five commits after the data-source and ready-status commits; clean `main`; committed file ends with `Status: ready.` |
| 3 | In the separate `intro-to-git-workshop` clone; `origin` is the learner’s fork, `upstream` is mdi-group; clean `main` |
| 4 | One PR from the learner’s `participant/YOUR-USERNAME` branch to workshop `main`, adding only `participants/YOUR-USERNAME.md` |

## Exact local commit sequence

Use these messages in the demonstrations so the example logs and instructions agree:

1. `Introduce the research notes`
2. `Record the dataset version`
3. `Record the analysis settings`
4. `Record the dataset source`
5. `Mark the notes ready`

Hashes shown on the slides are examples. Use the current repository’s own identifiers. The history exercise selects the commit that added `and source`; checkout inspects the earlier analysis-settings commit, then returns to `main`.

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

Extra blank lines from editing do not change the learning outcome; they may change the displayed insertion counts.

## Keep the two repository contexts separate

The local notes repository is not submitted to GitHub. Leave it on clean `main`, then clone the workshop fork alongside it. The participant exercise changes only the learner’s own file. The controlled conflict uses `conflict-demo/status.txt` in a presenter fork clone.

Both PRs in the conflict demonstration begin from `Workshop mode: open.`. Merge the reviewing PR first, then on `conflict-demo` fetch and merge `upstream/main`. This produces the marker direction shown in the slides. The agreed resolution is `Workshop mode: reviewing and merging.`.

## Alignment review

The repository update fixes the command-reference link, aligns commit messages and practice numbering, adds status/log/push output, explains hashes and detached checkout, uses the same browser PR route, and adds the recap. The presenter conflict script now uses two fork-based PRs and `upstream/main`. Unrequested branch deletion has been removed from the core exercise and the corresponding slide note.

Prakriti’s existing participant file, the licence and the starting conflict fixture are preserved unchanged. Additional research guidance and troubleshooting are available for later reading; they do not add required exercises to the class.
