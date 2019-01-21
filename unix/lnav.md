_Written by: Reza Shams Amiri_

# lnav

## Support for other formats:

A git repo, as an example, provides support for different formats [https://github.com/PaulWay/lnav-formats](https://github.com/PaulWay/lnav-formats) (including log4j.)

If you quickly want to support `log4j` just execute the following command:
 
``` bash
curl -o ~/.lnav/formats/log4j.json https://raw.githubusercontent.com/PaulWay/lnav-formats/master/log4j.json
```

## Keyboard shortcuts

Shortcut                   | Descrtiption 
---------------------------|---------------------------------------------------
<kbd>m</kbd>               | Mark/unmark the line at the top of the display.
<kbd>M</kbd>               | Mark/unmark all the lines between the top of the display and the last line marked/unmarked.
<kbd>J</kbd>               | Mark/unmark the next line after the previously marked line.
<kbd>K</kbd>               | Like 'J' except it toggles the mark on the previous line.
<kbd>C</kbd>               | Clear all marked lines.
<kbd>T</kbd>               | Toggle time
<kbd>CTRL</kbd>+<kbd>l</kbd>  | (Lo-fi mode) Exit screen-mode and write the displayed log lines in plain text to the terminal
<kbd>CTRL</kbd>+<kbd>w</kbd>  | Toggle wrap
<kbd>i</kbd>                  | View/leave a histogram of the log messages over time
<kbd>I</kbd>                  | Switch between the log and histogram views while keeping the time displayed at the top of each view in sync.
<kbd>?</kbd>                  | Display the help page

* * *
Creation date: _2019-01-21_
