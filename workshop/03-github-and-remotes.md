# GitHub and remotes

Git commits are local. A remote is another repository that can exchange commits with your local repository.

## Push and fetch

- `git push` sends local commits to a remote;
- `git fetch` downloads remote commits and updates remote-tracking names;
- `git merge` integrates another branch into the current branch;
- `git pull` fetches and then integrates.

For this tutorial exercise, the two remotes have distinct roles:

| Remote | Points to | Used for |
| --- | --- | --- |
| `origin` | your fork | pushing your branches |
| `upstream` | `mdi-group/intro-to-git-workshop` | fetching updates from the tutorial repository; this repository is also the PR destination on GitHub |

## Authenticate for HTTPS

```console
gh auth login
gh auth setup-git
gh auth status
```

Choose GitHub.com, HTTPS and browser sign-in. Confirm that the account shown owns your fork.

## Fork the tutorial repository

Open [mdi-group/intro-to-git-workshop](https://github.com/mdi-group/intro-to-git-workshop), choose **Fork**, then create the fork under your account.

If you already have a fork, use it. GitHub may show a **Sync fork** option if it is behind the source repository.

## Clone your fork

Start outside `aichemy-notes`. If you are inside it, `cd ..` below moves to its parent. If you are outside it, omit that line. Copy your fork’s **Code → HTTPS** URL, or replace `YOUR-USERNAME` in the example:

```console
cd ..
git clone https://github.com/YOUR-USERNAME/intro-to-git-workshop.git
cd intro-to-git-workshop
```

Cloning creates the working files and local history, configures `origin`, and checks out the default branch.

## Add the source repository

```console
git remote add upstream https://github.com/mdi-group/intro-to-git-workshop.git
git remote -v
```

## Practice 3: check your fork and clone

Run `git remote -v` and `git status`. Example remote output:

```text
origin   https://github.com/YOUR-USERNAME/intro-to-git-workshop.git (fetch)
origin   https://github.com/YOUR-USERNAME/intro-to-git-workshop.git (push)
upstream https://github.com/mdi-group/intro-to-git-workshop.git (fetch)
upstream https://github.com/mdi-group/intro-to-git-workshop.git (push)
```

These URLs have no credentials in them. Checkpoint:

- `origin` contains your username;
- `upstream` contains `mdi-group`;
- `git status` reports a clean `main` branch.

## Fork, clone and branch

| Term | What it creates | Where it lives |
| --- | --- | --- |
| Fork | a hosted repository under your account | GitHub |
| Clone | a local repository and working files | your laptop |
| Branch | a movable name pointing to a commit | a repository |

Continue to [Branches and pull requests](04-branches-and-pull-requests.md) to explore the commit graph and update local `main` before creating your branch.
