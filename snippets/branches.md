# Branches
Branches allow us to work on different versions of a repo simultaneously. Generally, a Git repo will be instantiated with a default _main_ or _master_ branch. Branches are generally used for dedicated deployment strategies, bugfixes, or features. Git branches always stem from another branch, and can be merged into another branch to combine changes.

## Naming conventions
Branch names should concisely indicate the purpose of the branch, and many organizations mandate that your branch names are prefixed by either `feature/` or `bugfix/` as necessary. It is also common for organizations to require that branch names include ticket numbers from 3rd party project management solutions such as _Jira_ or _Asana_.

## Deployment strategies
Generally, organizations will also dedicate a branch to `development` or `dev`. This branch serves as the main area for dev work, and when we seek to create a feature or bugfix branch, we should almost always create our new branches from `dev`. A major exception is when hotfixing a bug in production, in which case we would stem our branch off the production branch (usually `main`), and then merge the hotfix into both `main` and `dev`. You can read more about Git workflows in this [famous blogpost](https://nvie.com/posts/a-successful-git-branching-model/). It's important to remember that the power of Git is in its customizability, and workflows may vary between organizations.

## Useful Commands
These are basic commdands for the Git CLI (Command Line Interface) that will get you off the ground. You can read more about `git branch` on `git-scm`'s [official docs](https://git-scm.com/docs/git-branch).

`git branch`: Lists all _local_ branches.
  - `git branch -r`: Lists all remote branches.
  - `git branch -a`: Lists all local and remote branches.
  - `git branch -v`: Lists all local branches with latest commit.

`git switch {branch-name}`: Switches to the specified branch.

`git checkout {branch-name}`: Switches to the specified branch.
  - `git checkout -B {branch-name}`: Creates and switches to a new branch from the current branch.
  - A word of caution:
    - `git checkout {filename}`: Discards uncommitted changes to a file. It may be wiser to use `git switch` to switch branches, in case a file has the same name as a branch. However, this situation should only be caused by poor branch names or file names.
