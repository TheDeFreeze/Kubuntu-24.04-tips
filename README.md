# kde_tips


## Mic Echo Cancellation

To enable echo cancellation, so you can use laptop speakers with voice applications, and wacth youtube videos at the same time. I've found that the PulseAudio echo module works well.

'''
sudo apt install pulseaudio-utils

sudo apt install pavucontrol-qt

sudo pactl load-module module-echo-cancel
'''

Then in the voice application you should now have 2 additional audio devices. Input device being "Echo-Cancel Source", and output device being "Echo-Cancel Sink"
