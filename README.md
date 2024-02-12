# Git Basics
Git is an open-source version control solution that facilitates simultaneous teamwork on code. While the Git rabbit hole is deep, but not much knowledge is required to begin the journey to becoming a wizard. The goal of this doc is to cover core concepts and explain simple commands that will allow you to feel productive.

To begin, we must understand a few key terms:
- Repositories
- Branches
- Commits
- Pull Requests

__Repositories__: A repository (repo) is generally used to store a singular project.
>Note that Git repos _can_ be nested and hold multiple projects, but for our purposes, let's move forward with this understanding.

__Branches__: Branches allow us to work on different versions of a repo simultaneously. Generally, a Git repo will be instantiated with a default _main_ or _master_ branch. Branches are generally used for dedicated deployment strategies, bugfixes, or features. Git branches always stem from another branch, and can be merged into another branch to combine changes.

__Commits__: Commits are used to make changes to a branch. All commits should be accompanied by a commit message, which concisely describes the changes that were made.

__Pull Requests__: Pull requests (PR's or merge requests) are a collaborative system in GitHub which propose that changes on your branch should be merged into another branch (e.g. main). Once a PR is opened through Github's UI, other users can easily view the proposed changes, your commit history, and open a discussion regarding the PR.

## Basic Git commands
These are basic commdands for the Git CLI (Command Line Interface) that will get you off the ground. All commands here are hyperlinks to the official [`git-scm`](https://git-scm.com) docs which provide further context and CLI arguments.

[`git init`](https://git-scm.com/docs/git-init): Creates an empty git repository or re-initializes an existing repo.


[`git status`](https://git-scm.com/docs/git-status): Allows you to see the state of your current Git branch (commonly referred to as your _working tree_).

[`git add {file-name}`](https://git-scm.com/docs/git-add): Allows you to add changed code to the _staging area_. `git add` accepts bash wildcards. Useful examples include:
- `git add .` to add all changes in the current directory.
- `git add directory/*` to add a directory.
- `git add *.extension` to add all files with a given extension.

[`git reset {file-name}`](https://git-scm.com/docs/git-reset): Removes changed code from the _staging area_.

[`git commit -m "commit-message"`](https://git-scm.com/docs/git-commit): Commits all file changes in the _staging area_. By passing `-m` as an option, we can specify the commit message in a single line. If you want to provide a more in-depth commit message, you may choose to use only `git commit` which will usually take you into Vim. Read [this](snippets/vim-crash-course.md) as a "get me out of jail" card or begin your deep-dive [here](https://vim-adventures.com/).

[`git pull`](https://git-scm.com/docs/git-pull): Updates local branch from remote target.
  - Fun fact: `git pull` actually aliases two operations: `git fetch` (to retrieve references to remote) and `git merge` (to merge remote onto local).

[`git push`](https://git-scm.com/docs/git-push): Updates remote target branch from local.

[`git log`](https://git-scm.com/docs/git-log): Displays commit logs for the current branch.
  - `git log -n` Shows the `n` most recent commits only.
  - `git log -p` Shows the _diff_ (changes) for each commit.
  - `git log --oneline` View abbreviated commit messages.

[`git rm`](https://git-scm.com/docs/git-rm): Removes a file from your working directory, and stages the commit. It is a convenience function that performs identically to `rm {filename} && git add {filename}` (In this case, by adding the file we record that it was removed).

## Before you read further
This guide is only meant to serve as quick introduction to people who are new to using the Git CLI. It will by no means make you an expert, and you will likely eventually have a question that is not covered here. Linked below are some helpful links with more in-depth knowledge. This document also does not cover the Github CLI.
- [Git SCM](https://git-scm.com/docs/git): Official docs, frequently linked in this document.
- [Atlassian](https://www.atlassian.com/git): Easy to follow.
- [Visualizing Git](https://git-school.github.io/visualizing-git/): Visualizes your git changes.
- [Learn Git Branching](https://learngitbranching.js.org/): Learning gamified.
- Actually doing it. Practice makes perfect!
