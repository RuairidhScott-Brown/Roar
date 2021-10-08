# How to Change the Default Account Username and Password on a Pi
==tis is not complete and at this point I can't get it to work.==

```ad-note
color: 200,200,200

This was done with the operating system noobs. It shouldn't make a difference because all linux system act in the same way.
```

First we have to activate the root user and log into it:
```shell
sudo passwd root
```

Then we can logout of the pi user by switching to the new user:
```shell
su - root
```

Then we can change the name of the pi user:
```shell
 usermod -l <new name> pi
 ```
 
