# Vim Crash Course
Vim is an old text-editor which uses keyboard shortcuts/commands. It is also the default editor in most Linux systems, so it's handy to know a little bit. As the focus of this document is Git, we will not do a deep-dive into Vim.

  1. To edit text in Vim, press the `I` key to enter _insert mode_ and write your commit message.
  2. Once you are done, you must exit _insert mode_. This can be accomplished in your terminal by hitting `Esc` or if you use the embedded terminal in VSCode, you can hit `Ctrl-C`.
  3. Once you are done writing your changes, enter command mode by hitting `:`.
  4. To save your commit, submit `wq⏎` to complete the commit.
  5. To abort the commit, submit `q!⏎` in command mode. Your code changes will still be in the _staging area_.
