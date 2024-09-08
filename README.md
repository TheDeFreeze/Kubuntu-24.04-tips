# kde_tips

Currently on KDE Kubuntu 24.04 Plasma 5.27


## Mic Echo Cancellation

To enable echo cancellation, so you can use laptop speakers with voice applications, and watch youtube videos at the same time. I've found that the PulseAudio echo module works well.
https://userbase.kde.org/Simon/Tips,_Tricks_and_Best_Practices


```
sudo apt install pulseaudio-utils
```
```
sudo apt install pavucontrol-qt
```
```
sudo pactl load-module module-echo-cancel
```

Then in the voice application you should now have 2 additional audio devices. Input device being "Echo-Cancel Source", and output device being "Echo-Cancel Sink"



## Enable Flatpak in the Discover app
I prefer flatpaks, the Discover app will list them if you install the Flatpak dicover backend,and in some cases let you select source between Ubuntu, snap and flatpak.

```
sudo apt install plasma-discover-backend-flatpak
```
