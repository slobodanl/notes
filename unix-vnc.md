# Linux VNC using tigervnc
# Linux VNC using tigervnc

For refernce about tiger vnc see [arch-wiki | TigerVnc][HWAOIPT]

## Installation on server
Install tiger vnc on server

``` sh
sudo apt install tigervnc-standalone-server tigervnc-xorg-extension
```

set the vnc password by running `vncpasswd`

create the config file: `~/.vnc/config`
``` sh
securitytypes=tlsvnc
desktop=sandbox
geometry=1200x700
dpi=96
localhost
alwaysshared
```

Run the server by issuing the following command:

``` sh
vncserver :1 -geometry 1280x800 -depth 24 -alwaysshared -fg  
```

The server should start at port `5901`, since `-fg` is specified it will run in foreground.

## Client connection
On client machine, install remmina:
``` sh
sudo apt install remmina
```
In remmina create a vnc connection and use `<yourserver>:5901` as server address, then enable SSH Tunnel (required!.) For authentication use the Identity File and use your `id_rsa` file.



* * *
Creation date: _2018/09/23_

[HWAOIPT]: https://wiki.archlinux.org/index.php/TigerVNC