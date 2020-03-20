# Dunst
## Pango
For information about `Pango` syntax look at [Markup: Pango Reference Manual][MPRM]

_Pango example_{.ct}
``` sh
<span font='Balcony Angels Regular 32' underline='low'>Current Agendas</span>
- <span color="#ff0000" weight='heavy'>check</span> <big>state</big> in target
- Emphasize on the <span weight='heavy'>important</span> parts
- <span color="#ff0000"><span weight='heavy'>bold</span>notbold </span>
<span bgcolor="#00FF0044" style='italic' color='#00FF00FF' weight='bold' stretch='expanded'>
This section has different background and foreground color
</span>
<span stretch='ultracondensed'>
You <b>can</b> also <i>see</i> variable<sub>sub</sub>/variable<sup>sup</sup> 
and <small>also it can be small</small> or <big>big</big> or <u>underlined</u>
or <s>strikethrough</s>
</span>
<span background='#f8f8f8' color='#181818'><tt>
#!/bin/sh
exec ~/bini3/,o 9 $@
</tt></span>
- <span underline='double' underline_color='yellow'>pango in notification for agenda</span>

<span font='False Positive Round BRK Normal 32'>This font is good?</span>
<span font='Dephunked BRK Regular 32'>Or this?</span>
```
![agenda.png](/img/agenda.png)
## Actions
You can have some actions and when the notification is displayed use :
<kbd>ctrl</kbd>+<kbd>shift</kbd>+<kbd>.</kbd> which is definded in `dunstrc` (shortcut  context) to display the result in `rofi` or `dmenu`

``` sh
dunstify "new mail" "text" -i "mail-6-128" --action="c,cancel" --action="r,reply"
```

## Problems
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
_Also make sure to run `sudo dunst -/.config/dunst/dunstrc -print` because `sudo` user might already have acquired the same app although it's not obviouse and even though you have already uninstalled the extra notification service!_{.note .red}

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

Some of the notification services that are safe to be removed are:
1. `notify-osd`
2. `mate-notification-daemon`
3. ...

-----------------------------------------
2017-11-30 00:35:23

[MPRM]: https://developer.gnome.org/pango/unstable/pango-Markup.html