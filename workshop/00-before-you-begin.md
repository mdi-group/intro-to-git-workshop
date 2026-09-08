# Before you begin

## Check the tools

Open a terminal and run:

```console
git --version
gh --version
```

Open a plain-text editor and sign in to your GitHub account in a browser.

## Configure your commit identity

Use your own name and email address:

```console
git config --global user.name "Your Name"
git config --global user.email "you@example.org"
```

These details are stored in each commit. They are separate from GitHub authentication.

Check the values:

```console
git config --global --get user.name
git config --global --get user.email
```

If you want GitHub to associate commits with your account without publishing your email address, use the no-reply address shown in your GitHub email settings.

## Authenticate with GitHub

```console
gh auth login
gh auth setup-git
gh auth status
```

Choose GitHub.com, HTTPS and browser sign-in when prompted. Check the account shown by `gh auth status`.

Never paste an access token, password or authentication code into a workshop chat, issue or shared document.

## A useful habit

Run `git status` whenever you are unsure what Git will do next. It reports the current branch and the state of tracked, staged and untracked files.
