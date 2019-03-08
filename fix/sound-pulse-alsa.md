_Written by: Reza Shams Amiri_
# sound pulse alsa

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
