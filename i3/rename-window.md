_Written by: Reza Shams Amiri_
# rename window

i3 gets the window title from the application. Using `xdotool` you can modify the current window title but some applications constantly set the window title automatically such as terminal emulators like `tilix`.

In order to change that you need to modify the application behaviour first for the change to be effective.

## Change tilix behaviour
Go to **tilix** settings (<kbd>ctrl</kbd>+<kbd>alt</kbd>+<kbd>S</kbd>).

![tilix-settings.png](/img/i3/tilix-settings.png)

Then you can use an script such as the one provided here [github/existme:i3-renamewindow.sh][DIRAMEDG] and bind it to a shortcut for example <kbd>mode</kbd>+<kbd>shift</kbd>+<kbd>w</kbd> using the following config:
``` sh
bindsym $mod+Shift+w exec /home/$USER/bini3/i3-renamewindow `zenity --entry --text "Rename window to:"`
```


* * *
Creation date: _2019-12-22_

[DIRAMEDG]: https://github.com/existme/doti3/blob/master/bini3/i3-renamewindow