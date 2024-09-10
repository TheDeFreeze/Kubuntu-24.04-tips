## Kubuntu-24.04-tips

Currently on Kubuntu 24.04, KDE Plasma 5.27


## Mic Echo Cancellation

To enable echo cancellation, so you can use laptop speakers with voice applications, and watch youtube videos at the same time. I've found that the PulseAudio echo module works well.
https://userbase.kde.org/Simon/Tips,_Tricks_and_Best_Practices

Install Pulse Audio Utilities. This is to use the "pactl" command.
```
sudo apt install pulseaudio-utils
```

Install the Pulse Audio Control panel.
```
sudo apt install pavucontrol-qt
```

Start module. (Note: do not use sudo)
```
pactl load-module module-echo-cancel
```

Make module load on boot by appending load module to the .profile file. (This is not perfect, google results make you add stuff to /etc/pulse/default.pa, but this simply does not work, and there's an open 3 year old bug tracker on it. This is just the easiest way I've found that I've tested, that works.) (Note: do not use sudo)
```
echo "pactl load-module module-echo-cancel" >> ./home/$USER/.profile
```



Then in the voice application you should now have 2 additional audio devices. Input device being "Echo-Cancel Source", and output device being "Echo-Cancel Sink"


Some thought: This works by default in Windows. In Kubuntu, it maybe kind of works before doing this? Sometimes? Or maybe it was just the Discord Krisp doings it's best. I dunno, but if you do this it's fantastic. Dissappointed this isn't better integrated, since laptops are common for throwing Linux on.



## Enable Flatpak in the Discover app
I prefer flatpaks, the Discover app will list them if you install the Flatpak dicover backend,and in some cases let you select source between Ubuntu, snap and flatpak.

```
sudo apt install plasma-discover-backend-flatpak
```


## Tap to click touchpad option grayed out
I don't know why this is not on by default, but to have it on, add this line to /usr/share/X11/xorg.conf.d/40-libinput.conf

```
Section "InputClass"
        Identifier "libinput touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Option "Tapping" "True" # ADD THIS LINE
        Driver "libinput"
EndSection
```
