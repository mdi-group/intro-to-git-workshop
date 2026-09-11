# Tutorial notes

## Prepare the tutorial

Before the tutorial:

1. Add these materials to `mdi-group/intro-to-git-workshop`.
2. Check every internal link from the root README.
3. Confirm that repository forking and pull requests are enabled.
4. Confirm that `main` is the default branch.
5. Decide whether participant pull requests can be merged during the tutorial.
6. Prepare the controlled conflict using [conflict-demo.md](conflict-demo.md).
7. Keep a clean clone available for demonstrations.

Do not give every participant direct write access. The fork workflow works with the repository's normal public permissions and makes the source and destination clear.

## Tutorial checkpoints

### Local Git

- `git status` reports `main`;
- `git log --oneline` contains three focused commits after Practice 1;
- participants can distinguish `git diff` from `git diff --staged`;
- `git show HEAD:index.md` displays committed content.

### GitHub setup

- `origin` contains the participant's username;
- `upstream` contains `mdi-group`;
- local `main` is clean before creating the participant branch.

### Pull request

- branch is `participant/YOUR-USERNAME`;
- exactly one uniquely named participant file was added;
- the pull-request base is `mdi-group:main`;
- Files changed contains the intended contribution only.

## Review pull requests

Open several pull requests and inspect:

- the title and description;
- the commit message;
- Files changed;
- whether the change matches the exercise;
- how a new pushed commit updates an open pull request.

If enabled, **Create a merge commit** produces the two-parent diagram. Squash and rebase produce different history.

After selected pull requests are merged, participants update local `main` and inspect their merged file. Keep branches during the tutorial; deletion is optional and can be refused after a squash merge.

The [slide-to-repo map](slide-map.md) connects the four practice checkpoints with the tutorial material. The conflicts section is a demonstration; participants do not edit the shared conflict file.

## If something goes wrong

- If a participant cannot authenticate, let them complete the local branch and commit steps.
- If GitHub is unavailable, demonstrate the remote and pull-request steps from the tutorial account.
- If a participant's history has diverged, preserve the branch and inspect it after the main demonstration. Do not solve it with a force-push during the tutorial.
