# Introduction to Git and GitHub

Materials for the AIChemy workshop at the University of Liverpool.

This repository accompanies the two-hour practical session. The workshop starts with a small local repository, then uses this repository for forks, branches and pull requests.


<img width="330" height="478" alt="git" src="https://github.com/user-attachments/assets/85e74292-3d8f-4222-8c81-9d78a43885b6" />


## What you will practise

- create a local Git repository;
- inspect the working tree and staging area;
- make clear, focused commits;
- read history and recover from common mistakes;
- connect local work to GitHub;
- understand commits, branches, `main` and `HEAD`;
- submit a pull request from a fork;
- resolve a merge conflict;
- apply the workflow to research projects.

## Before the workshop

You need:

- Git;
- a GitHub account;
- the GitHub CLI, written as `gh` in commands;
- a plain-text editor;
- a terminal. Use Git Bash on Windows.

Run these checks:

```console
git --version
gh --version
```

If both commands print a version, continue to [Before you begin](workshop/00-before-you-begin.md).

## Workshop route

1. [Before you begin](workshop/00-before-you-begin.md)
2. [Local version control](workshop/01-local-version-control.md)
3. [Inspect and recover](workshop/02-inspect-and-recover.md)
4. [GitHub and remotes](workshop/03-github-and-remotes.md)
5. [Branches and pull requests](workshop/04-branches-and-pull-requests.md)
6. [Conflicts](workshop/05-conflicts.md)
7. [Git for research projects](workshop/06-research-projects.md)

Keep the [command reference](workshop/command-reference.md) and [troubleshooting guide](workshop/troubleshooting.md) open during the practicals.

## Class pull-request exercise

Each participant adds one uniquely named file under [`participants/`](participants/README.md). The file name and branch name use your GitHub username, which keeps the class submissions separate.

The destination repository is:

```text
https://github.com/mdi-group/intro-to-git-workshop
```

The complete route is in [Branches and pull requests](workshop/04-branches-and-pull-requests.md).

## Slides

The workshop slides are available in [Intro to Git and GitHub](https://docs.google.com/presentation/d/1WVP2jXtZ6T27f7jYtcZTL6g7SZoaP3Ztb5sT68hHxsc/edit).

## Facilitators

Preparation notes, checkpoints and the controlled conflict demonstration are under [`facilitator/`](facilitator/README.md).

## Licence and acknowledgements

The repository is released under the [MIT licence](LICENSE).

The lesson structure is adapted from Library Carpentry's Introduction to Git. Examples and extensions were also informed by the Imperial College London introductory Git course, Learn Git Branching, k-gregor/git-workshop, Git Workshop on Read the Docs, and the official Git and GitHub documentation. Links are collected in [Acknowledgements](workshop/acknowledgements.md).
