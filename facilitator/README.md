# Facilitator notes

## Repository preparation

Before the workshop:

1. Add these materials to `mdi-group/intro-to-git-workshop`.
2. Check every internal link from the root README.
3. Confirm that repository forking and pull requests are enabled.
4. Confirm that `main` is the default branch.
5. Decide whether participant pull requests can be merged during the session.
6. Prepare the controlled conflict using [conflict-demo.md](conflict-demo.md).
7. Keep a clean presenter clone available for demonstrations.

Do not give every participant direct write access. The fork workflow works with the repository's normal public permissions and makes the source and destination clear.

## Learner checkpoints

### Local Git

- `git status` reports `main`;
- `git log --oneline` contains three focused commits after Practice 1;
- learners can distinguish `git diff` from `git diff --staged`;
- `git show HEAD:index.md` displays committed content.

### GitHub setup

- `origin` contains the learner's username;
- `upstream` contains `mdi-group`;
- local `main` is clean before creating the participant branch.

### Pull request

- branch is `participant/YOUR-USERNAME`;
- exactly one uniquely named participant file was added;
- the pull-request base is `mdi-group:main`;
- Files changed contains the intended contribution only.

## Review demonstration

Open several pull requests and inspect:

- the title and description;
- the commit message;
- Files changed;
- whether the change matches the exercise;
- how a new pushed commit updates an open pull request.

Use **Create a merge commit**, if enabled, when explaining the two-parent diagram. If the repository requires squash or rebase, explain that the diagram shows a different merge strategy.

Merge a selection, then let those learners update local `main` and inspect their merged file. Keep branches during class; deletion is optional afterwards and can be refused after a squash merge.

Use the [slide-to-repo map](slide-map.md) to keep the four practice checkpoints aligned. The conflicts section is a presenter demonstration; learners do not edit the shared conflict file.

## Fallbacks

- If a learner cannot authenticate, let them complete the local branch and commit steps.
- If GitHub is unavailable, demonstrate the remote and pull-request steps from the presenter account.
- If a learner's history has diverged, preserve the branch and inspect it after the main demonstration. Do not solve it with a force-push in front of the class.
