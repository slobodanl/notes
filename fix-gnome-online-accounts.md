# fix gnome online accounts


``` sh
sudo gedit /usr/share/applications/gnome-online-accounts-panel.desktop

```
Remove `OnlyShowIn=GNOME;Unity;`

Run `sudo gnome-control-center online-accounts`

* * *
Creation date: _2018/10/17_
