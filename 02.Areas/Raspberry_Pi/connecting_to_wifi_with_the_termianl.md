# How to Connect to the Wifi Using Just the Terminal

First we have to check to see if the wifi interface is up.

```sh
iwconfig
``` 

```ad-note
color: 200,200,200
From now on I will refer the the wifi interface as wlan0. This may be differente depending on the system
```

We can also optionally turn on the wifi interface if it is off by running the command.

```sh
sudo ifconfig wlan0 up
```

Once we know that the wifi interface is on, we can scan the area to find newtorks.

```sh
sudo iw wlan0 scan | grep SSID
```
