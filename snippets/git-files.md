# Git files
Git has a few files that are specifically recognized by Git. Some of these are hidden!

## .gitignore
This file specifies which files should be ignored by Git. `.gitignore` is generally used to hide secret files, such as `.env`, keyfiles, temporary data, certain config files (e.g. `.DS_Store` on Mac), caches (e.g. `__pycache__`), and so forth. Github provides a useful UI utility when initializing a repository, that provides a generic `.gitignore` for popular programming languages.

>__Note__: If a file was previously tracked, and is then added to the gitignore, it will continue to show in your git history.

## Uh oh! I committed a secret file
It happens to the best of us. There are two key considerations when resolving this type of error:

  1. Identify which commits were compromised.
  2. Identify if the commits have been pushed to remote.
  3. Determine if they are on a branch with multiple contributors.

### Commit was not pushed
If the mistake is not pushed, and is only on the last commit, we can easily remedy the situation with the following steps:

  1. `git rm --cached {filename}` This will move the file into staging and mark it as deleted.
  2. Add `{filename}` to `.gitignore` to ensure it is not committed again.
  3. `git commit --amend --no-edit` This will edit your previous commit's contents, removing the erroneously committed file.

If the mistake is not pushed, but occurs over a series of commits, you will need to do an interactive [rebase](./rebase.md).

### Commit was pushed
This is where things start to get problematic. Even if you've changed the contents of the remote repository, anyone who has forked the repo, or has a local copy on their machine will have access to your secrets. If you think it's possible a malicious party could have gained access to your repo at the time of the leak, your immediate next course of action should be to revoke any keys and change any passwords that were compromised. The next step is to rewrite your git history.

>__Warning__: Before you proceed, ensure your teammates who work on the branch are notified. Rewriting history disrupts your teammates, and they will get an error when trying to push to the branch. They will need to re-clone the repository, or recover with [rebase](./rebase.md).

Let's assume you've only pushed the error onto your feature branch. Luckily, GitHub has released an official [guide](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository) in their FAQ. They present the following quick steps, using the [BFG Repo Cleaner](https://rtyley.github.io/bfg-repo-cleaner/)

  1. `brew install bfg`
  2. Back up your repo `cp -r repo.git repo.git.bak`
  3. `bfg --delete-files {filename}` or `bfg --replace-text {filename}` depending on your usecase.
  4. `git push --force`

>__Warning__: This will remove stashed changes.
