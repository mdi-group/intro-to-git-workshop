# GitHub and remotes

Git commits are local. A remote is another repository that can exchange commits with your local repository.

## Push and fetch

- `git push` sends local commits to a remote;
- `git fetch` downloads remote commits and updates remote-tracking names;
- `git merge` integrates another branch into the current branch;
- `git pull` fetches and then integrates.

For the class exercise, the two remotes have distinct roles:

| Remote | Points to | Used for |
| --- | --- | --- |
| `origin` | your fork | pushing your branches |
| `upstream` | `mdi-group/intro-to-git-workshop` | receiving workshop updates and opening the final pull request |

## Fork the workshop repository

Open [mdi-group/intro-to-git-workshop](https://github.com/mdi-group/intro-to-git-workshop), choose **Fork**, then create the fork under your account.

If you already have a fork, use it. GitHub may show a **Sync fork** option if it is behind the source repository.

## Clone your fork

Replace `YOUR-USERNAME` with your GitHub username:

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

Checkpoint:

- `origin` contains your username;
- `upstream` contains `mdi-group`;
- `git status` reports a clean `main` branch.

## Update local main

```console
git switch main
git fetch upstream
git merge --ff-only upstream/main
```

`--ff-only` stops instead of creating an unexpected merge commit when local and upstream histories have diverged.
