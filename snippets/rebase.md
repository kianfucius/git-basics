# Rebase
Rebase allows us to accomplish a similar task to merging, but with a different approach. It allows us to integrate changes from one branch into another, whilst keeping a linear history unlike a merge. Rebase can be useful when:

- You want to incorporate changes while keeping a linear history.
- You want to sync your branch with a target before merging.
- You want to squash or edit a previous commit.

>__Warning__: Before you proceed, ensure your teammates who work on the branch are notified. Rewriting history disrupts your teammates, and they will get an error when trying to push to the branch. They will need to re-clone the repository, or recover with [rebase](./rebase.md).

Simple steps include:

1. Ensure your source and target branches are up to date.
2. Checkout target branch.
3. `git rebase {source-branch}`
4. Rebase will give you some instructions that should be fairly straightforward by this point.

## Interactive Rebase
The interactive rebase is an incredibly valuable tool that allows us to edit our commit history across multiple commits.
In my experience, I've mostly used rebase to target a branch, or a specific commit using either its hash or the `HEAD~n` syntax.
To start an interactive rebase, simply pass the `-i` flag to rebase (e.g. `get rebase -i HEAD~n`).
This will pull up a view that looks something like this:
```
pick 0123456 Commit message 1
pick 7890abc Commit message 2
pick defghij Commit message 3
```
From here, you can edit the first term in the list (`pick`) to trigger an action on the commit:
- pick: Keep the commit as it is.
- reword: Edit the commit message.
- edit: Pause the rebase process to make changes to the commit.
- squash: Combine the commit with the previous one.
- fixup: Like squash, but discards the commit message.
- drop: Remove the commit from the history.

Interacting with rebase:

1. Make your modifications within the interactive editor.
2. Save and exit the [editor](./vim-crash-course.md), git will step through each edit-style commit.
3. Make your change to the commit, then run `git rebase --continue` to proceed. Repeat as needed.
4. `git push --force` Keep in mind that rebase rewrites history.

> Footnote: I recommend trying this stuff out for yourself. There's a lot more to know here, and the first few times you try it may feel awkward. Read more [here](https://git-scm.com/docs/git-rebase).
