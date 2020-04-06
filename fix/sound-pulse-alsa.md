_Written by: Reza Shams Amiri_
# sound pulse alsa

## Microphome problem

See this [linux - Headset microphone not detected by Pulse und Alsa - Super User][LHMNDBPUASU]

Just add `options snd-hda-intel model=dell-headset-multi` to `/etc/modprobe.d/alsa-base.conf` and restart the machine

## Restart alsa

``` sh
sudo alsa force-reload
```

## Restart pulse

``` sh
systemctl --user restart pulseaudio.service
systemctl --user restart pulseaudio.socket
```

## Gnome sound settings
``` sh
gnome-control-center sound

# more settings
pavucontrol
alsamixer

```

* * *
Creation date: _2019-03-07_

[LHMNDBPUASU]: https://superuser.com/a/1423564/285113