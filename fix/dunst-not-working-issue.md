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


* * *
Creation date: _2019-02-23_
