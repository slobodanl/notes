_Written by: Reza Shams Amiri_
# xsession startup

`.xinitrc` is exectued when you explicitly run `xinit` (startx ultimately calls xinit) to start an X-server. Mostly this doesn't happen as current Linuxes use desktop managers, which diretly start a X-Server and then run `/etc/X11/Xsession <desktopenvironment>`, where `<desktopenvironment>` is the value of any line `Exec=` from a file in `/usr/share/xsessions`,

![user-share-xsessions.png](/img/unix/x/user-share-xsessions.png)

* * *
Creation date: _2020-01-01_
