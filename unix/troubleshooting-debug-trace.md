_Written by: Reza Shams Amiri_
# troubleshooting debug trace


``` sh
journalctl -xb -p err
```
``` sh
loginctl session-status
```
``` sh
dbus-update-activation-environment --systemd DBUS_SESSION_BUS_ADDRESS DISPLAY XAUTHORITY
```

* * *
Creation date: _2019-06-03_
