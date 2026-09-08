# Contributing

Workshop participants should follow the class pull-request exercise in [`workshop/04-branches-and-pull-requests.md`](workshop/04-branches-and-pull-requests.md).

## Participant contributions

Use one branch and one file:

- branch: `participant/YOUR-USERNAME`
- file: `participants/YOUR-USERNAME.md`

Do not edit another participant's file. Do not add personal email addresses, access tokens, passwords, private data or unpublished research data.

Before opening the pull request, run:

```console
git status
git diff upstream/main...HEAD
```

Check that the diff contains only the contribution you intended to make.

## Changes to the workshop material

For corrections or additions outside `participants/`, open an issue first. Explain the problem, the proposed change and how you checked it. Keep each pull request focused on one topic.
