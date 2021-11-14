# How to Update a Git Branch From Main

```ad-note
color: 200,200,200
That you have a branch other than main or master in your git repo, checkout [[adding_new_branch]] if you want to add a new branch. And that the main branch is ahead of the other branch i.e. you have pulled on the main branch
```

First we shoud go to main and pull from the remote repository to update the main branch.
```sh
git checkout main
git pull
```

After, the main branch has been updated then we should move to the feature branch and merge main into the feature branch.
```sh
git checkout <name of your branch>
git merge main
```
