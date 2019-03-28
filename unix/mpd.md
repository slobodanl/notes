_Written by: Reza Shams Amiri_
# mpd

## Installation
``` sh
sudo apt install mpd mpc ncmpcpp
```
## Config
``` sh
sudo gpasswd -a mpd $USER
sudo gpasswd -a mpd audio
```
## Service
``` sh
sudo service mpd restart
```
## ncmpcpp shortcuts [ [ref1][NCS] ]

|Key|Action|
|---|------|
| <kbd>p</kbd> | Pause/Play |
| <kbd>s</kbd> | Stop |
| <kbd>f</kbd> | Seek forward |
| <kbd>b</kbd> | Seek backward |
* * *
Creation date: _2019-03-28_

[NCS]: https://pkgbuild.com/~jelle/ncmpcpp/