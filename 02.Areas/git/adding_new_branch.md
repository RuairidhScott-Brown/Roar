io;h# How to Add a New Branch in Git

This is quite simple, all you have to do is execute one command.

```sh
git branch <name of the new branch>
```

If you would like to make sure that you have created the correct branch, you can list all of the branches with this command.

```sh
git branch -a
```

The `-a` signals that you would like to list all of the branches i.e. the local and remote branches.

And to switch to your new branch or any branch you should use the command.

```sh
git checkout <name of the branch>
```