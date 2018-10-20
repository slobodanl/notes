# I3-Misc.Md

## Keyboard:
See the available keysyms:
```bash
xmodmap -pke
```
Or use `xev` to see the keysyms.

## Misc new stuff

### subscribe message type:

``` sh
i3-msg -t subscribe '[ "workspace" ]' | jshon -e current -e num

# Like inotifywait, the -m flag allows to wait indefinitely for events
# For example, continuously monitor the names of focused windows with:
i3-msg -t subscribe -m '[ "window" ]' | jq .container.name
```

-----------------------------------------
2017-12-22 22:54:56
