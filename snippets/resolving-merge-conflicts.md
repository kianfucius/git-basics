# Resolving merge conflicts
Occasionally when one goes to merge their approved PR, they will see the dreaded "_This branch has conflicts that must be resolved_". This happens when your PR branch stems from an older version of your target branch (e.g. merging `feature` into `dev`), and new changes have been applied to `dev` on lines that conflict with your PR changes. Although you may be tempted to resolve this in Github's built-in merge editor, you will struggle with large merge conflicts, and lose the advantage of IDE syntax highlighting or linting to double-check your work. Thus, we have rebasing.

## Rebase vs Merge
`git rebase` and `git merge` are designed to resolve the same problem: integrating changes from one branch into another. Put simply, merge preserves the history of your tree, and creates a "merge commit" in your `feature` branch. Alternatively, rebase moves the tip of the feature branch onto the tip of the `target` branch, directly incorporating the changes in `feature` into the `target` and thus rewriting history. You can read a more detailed explanation [here](https://www.atlassian.com/git/tutorials/merging-vs-rebasing).

## Simple steps to resolve merge conflicts
This procedure should only be used in cases where you are the sole developer on your feature branch. For this example, we are merging `feature` into `dev`. Generally, when we are working on projects with other developers, we prefer resolving merge conflicts with `git merge` because it is non-destructive (i.e. rewriting and force-pushing history can cause problems for developers in the future).

  1. `git checkout dev && git pull origin dev` Ensures your local version of `dev` is updated with all latest changes from remote.
  2. `git checkout feature && git pull origin feature` Ensures your local version of `feature` is updated with all latest changes from remote.
  3. `git merge dev` Git will attempt to merge all changes from `dev` into `feature`. If there are merge conflicts, we will see something like this:
  ```
  Auto-merging somefile.txt
  CONFLICT (content): Merge conflict in somefile.txt
  Automatic merge failed; fix conflicts and then commit the result.
  ```
  4. `git status` Will let you revise the conflicts, in case you've cleared your terminal's full buffer.
  5. Resolve merge conflicts. They will look something like this:
  ```
  <<<<<<< HEAD
  # Changes from the current branch (e.g., dev)
  =======
  # Changes from the branch you are merging in (e.g., feature)
  >>>>>>> feature
  ```
  6. `git add {filename}` for any resolved file. You will need to repeat Step 5 and 6 until all conflicts are resolved.
  7. `git commit -m "Resolved merge conflicts from dev`
  8. `git push` to push your merge conflict resolution to remote. Your changes should now be visible in Github and it will not show you any further conflicts.

Congratulations! Your merge conflicts are now resolved. In Github UI, you will be allowed 3 options to close the PR: `Create a merge commit`, `Squash and merge`, and `Rebase and merge`. By using `Squash and merge`, we can squash all of our commits into a singular commit. However, keep in mind that code commit comments are a form of code documentation. Github will preserve previous commit messages, but we will lose the history of the commits themselves. If we choose to use this route, it is important to re-read the auto-generated commit message, and ensure that it provides a strong explanation of the merge, so that the resulting commit message thoroughly explains the purpose of the PR which will be visible in `dev`.
