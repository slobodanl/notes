_Written by: Reza Shams Amiri_
# dunst not working issue

This will be an on going investigation:

1. `ps -aux G dunst`   
    Shows:
    ``` 
    existme  19509  0.9  0.0 355436 19516 ?        Sl   14:59   0:03 /usr/bin/dunst
    ```
    After `s killall dunst; dunst -config ~/.config/dunst/dunstrc&`
    ```
    existme  22643  0.7  0.0 349824 18200 pts/5    SNl  15:05   0:00 dunst -config /home/existme/.config/dunst/dunstrc
    ```
    which shows that dunst before was loaded without the correct configuration which is strange
2. `dbus-monitor path=/org/freedesktop/Notifications` was correctly showing the received notifications
3. The file `/usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled` was changed to `/usr/share/dbus-1/services/org.freedesktop.Notifications.service`

```
/usr/share/dbus-1/services
ag dunst

org.freedesktop.Notifications.service
3:Exec=/usr/bin/dunst -config /home/existme/.config/dunst/dunstrc 

org.knopwob.dunst.service
3:Exec=/usr/local/bin/dunst
4:SystemdService=dunst.service

sudo vim org.freedesktop.Notifications.service
Edit and set:
Exec=/usr/bin/dunst -config /home/existme/.config/dunst/dunstrc 

```

**Solution**

In `i3-startup.sh` I had added a line which said `export $(dbus-launch)`
This was the source of all problems because as a result of running this the `BUS_SESSION_BUS_ADDRESS` was set to a wrong value. The correct value is:

``` sh
export BUS_SESSION_BUS_ADDRESS="unix:path=$XDG_RUNTIME_DIR/bus"
```

But that can not be set from the script and it will be empty at the end but it's better to be empty than set to a wrong value

[FAQ · Dunst][FD]
* * *
Creation date: _2019-02-23_

[FD]: https://dunst-project.org/faq/