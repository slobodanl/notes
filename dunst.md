# Dunst

----------------------------------------- 
Either remove the following service or change it to use `dunst`

```bash
/usr/share/dbus-1/services/org.freedesktop.Notifications.service
```

As an example you change it to this:

```bash
[D-BUS Service]
Name=org.freedesktop.Notifications
#Exec=/usr/lib/x86_64-linux-gnu/notify-osd
Exec=/usr/bin/dunst
```

Or the better way is to disable the service by renaming it to
`/usr/share/dbus-1/services/org.freedesktop.Notifications.service.disable`
Also notice that there already exists a service called:
`org.knopwob.dunst.service`

containing the following:

```bash
[D-BUS Service]
Name=org.freedesktop.Notifications
Exec=/usr/bin/dunst
```

## If another notification daemon is replacing dunst
Try running dunst:
``` sh
dunst -config ~/.config/dunst/dunstrc -print
```
You might get something like this:
```
CRITICAL: Cannot acquire 'org.freedesktop.Notifications': Name is acquired by 'Notification Daemon' with PID '19731'.
```
See what process has that PID:
``` sh
ps -aux G 19731
existme  19731  0.7  0.2 439940 70020 ?        Sl   23:29   0:00 /usr/lib/mate-notification-daemon/mate-notification-daemon
existme  22605  0.0  0.0   8992  2528 pts/1    SN+  23:30   0:00 grep --color=always --exclude-dir=.bzr --exclude-dir=CVS --exclude-dir=.git --exclude-dir=.hg --exclude-dir=.svn 19731
```
We can see that `/usr/lib/mate-notification-daemon/mate-notification-daemon` is the one that takes over dunst. Uninstall it:
``` sh
sudo apt remove mate-notification-daemon
```

-----------------------------------------
2017-11-30 00:35:23
