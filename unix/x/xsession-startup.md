_Written by: Reza Shams Amiri_
# xsession startup

`.xinitrc` is exectued when you explicitly run `xinit` (startx ultimately calls xinit) to start an X-server. Mostly this doesn't happen as current Linuxes use desktop managers, which diretly start a X-Server and then run `/etc/X11/Xsession <desktopenvironment>`, where `<desktopenvironment>` is the value of any line `Exec=` from a file in `/usr/share/xsessions`, for instance

``` sh
Exec=startxfce4
```
if you selected XFCE as sessiontype.

![user-share-xsessions.png](/img/unix/x/user-share-xsessions.png)

On at least Debian based systems the scripts in `/etc/X11/Xsession.d/` are sourced (!) in order. Mostly all these scripts set stuff up and/or modify a variable `STARTUP` which is eventually used in the line
_99x11-common_start_{.ct}
``` sh
exec $STARTUP
```
![etc-x11-xsession.d.png](/img/unix/x/etc-x11-xsession.d.png)


`/etc/X11/Xsession` sets the following variables before sourcing files in `/etc/X11/Xsession.d/`:
``` sh
OPTIONFILE=/etc/X11/Xsession.options

SYSRESOURCES=/etc/X11/Xresources
USRRESOURCES=$HOME/.Xresources

SYSSESSIONDIR=/etc/X11/Xsession.d
USERXSESSION=$HOME/.xsession
USERXSESSIONRC=$HOME/.xsessionrc
ALTUSERXSESSION=$HOME/.Xsession
ERRFILE=$HOME/.xsession-errors
```





References:
1. [xorg - Is xinitrc executed when logging in? - Unix & Linux Stack Exchange][XIXEWLIULSE]
2. 

* * *
Creation date: _2020-01-01_

[XIXEWLIULSE]: https://unix.stackexchange.com/a/77495/114816