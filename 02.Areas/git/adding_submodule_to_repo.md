# How to Add a Git Submodule to a Repository

This is quite simple. All you do is go to your repo and then find where you want to put the submodule repo and exectue the command.

```sh
git submodule add <address of the submodule>
```

```ad-note
color: 200,200,200

When you run the above command the `<address of the submodule>` string will be copied into a file called .gitmodules in the repository. Therefore, if you have used a personel access token in the address this will also be saved into the repository.
```
