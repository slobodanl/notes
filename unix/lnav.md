_Written by: Reza Shams Amiri_

# lnav
## Support for other formats:

A git repo, as an example, provides support for different formats [https://github.com/PaulWay/lnav-formats](https://github.com/PaulWay/lnav-formats) (including log4j.)
   
If you quickly want to support `log4j` just execute the following command:
 
``` bash
curl -o ~/.lnav/formats/log4j.json https://raw.githubusercontent.com/PaulWay/lnav-formats/master/log4j.json
```

## Keyboard shortcuts

Shortcut                |   | Descrtiption 
------------------------|---|---------------------------------------------------
_Movement_{.f1}| 
<kbd>e</kbd>/<kbd>E</kbd> | ﮿﯀  | Jump to next/previous error
<kbd>w</kbd>/<kbd>W</kbd> | ﮿﯀   |Jump to next/previous warning
<kbd>n</kbd>/<kbd>N</kbd> | ﮿﯀   |Jump to next/previous search hit
<kbd>u</kbd>/<kbd>U</kbd> | ﮿﯀   |Jump to next/previous Bookmark
<kbd>1-6</kbd>/<kbd>SHIFT</kbd><kbd>1-6</kbd> | ﮿﯀  |Next/previous n’th ten minute of the hour
<kbd>8</kbd>/<kbd>7</kbd> | ﮿﯀  |Next/previous minute
<kbd>0</kbd>/<kbd>SHIGT</kbd><kbd>0</kbd> | ﮿﯀  |Next/previous day
<kbd>f</kbd>/<kbd>F</kbd> | ﮿﯀   |Goto next/previous file
<kbd>g</kbd>/<kbd>G</kbd> |祝  | Move to the top/bottom of the current view
<kbd>Home</kbd>/<kbd>End</kbd> |祝 | Move to the top/bottom of the current view
<kbd>SHIFT</kbd><kbd>/</kbd>|| Left/Right ten columns
<kbd>SHIFT</kbd><kbd>/</kbd>|| Left/Right ten columns
|_Marking_{.f1}||
<kbd>m</kbd>               || Mark/unmark the line at the top of the display.
<kbd>M</kbd>               || Mark/unmark all the lines between the top of the display and the last line marked/unmarked.
<kbd>J</kbd>               |怜  |  Mark/unmark the next line after the previously marked line.
<kbd>K</kbd>               |玲  |  Like 'J' except it toggles the mark on the previous line.
<kbd>C</kbd>               | | Clear all marked lines.
<kbd>c</kbd>               | | _Copy all selected bookmarks_{.hl}, if there are marked messages
<kbd>T</kbd>               || Toggle time
|||
|_Filters_{.f1}||
|<kbd>CTRL</kbd>+<kbd>f</kbd>| |Toggle enable/disable all filters|
|||
|_View_{.f1}||
|<kbd>P</kbd>  |  | Switch to/from the pretty-printed view|
|<kbd>p</kbd>  || enable or disable the display of the fields that the log message parser knbows about|
|<kbd>v</kbd>  |  | Switch to/from the SQL result view|
<kbd>CTRL</kbd>+<kbd>l</kbd>  |  | (Lo-fi mode) Exit screen-mode and write the displayed log lines in plain text to the terminal
<kbd>CTRL</kbd>+<kbd>w</kbd>  | 蝹 | Toggle wrap
<kbd>i</kbd>                  | | View/leave a histogram of the log messages over time
<kbd>I</kbd>                  | | Switch between the log and histogram views while keeping the time displayed at the top of each view in sync.
<kbd>?</kbd>                  || Display the help page

# User interface:
1. Errors will be colored in red
2. Earnings will be yellow
3. **Right side**:   
    has a proportionally sized ‘scrollbar’ that shows:   
   1.  your current position in the file
   2.  the locations of errors/warnings in the log files by using a red or yellow coloring
   3.  the locations of search hits by using a tick-mark pointing to the left!
    ![lnav-hits.png](/img/unix/lnav-hits.png#3dt)![lnav-search-hits.png](/img/unix/lnav-search-hits.png)

4. LNAV status bars
    ![lnav-status.png](/img/unix/lnav-status.png)

# Log formats
``` sh
 ls ~/.lnav/formats/

/home/existme/.lnav/formats/
├── default
│   ├── default-formats.json.sample
│   ├── dhclient-summary.lnav
│   ├── dump-pid.sh
│   ├── lnav-pop-view.lnav
│   ├── partition-by-boot.lnav
│   └── search-for.lnav
└── installed
```
## Installing formats
1. **Install remote repository**:   
    A standard set of repositories is maintained at [ tstack/lnav-config][GTLCOCDFL] and can be installed by passing ‘extra’ on the command line
    ``` sh
     lnav -i extra    
    ```
    It will install bunch of formats in `~/.lnav/formats` folder
1. **Install additional formats directly from a repo**:
   ``` sh
     lnav -i https://github.com/curityio/lnav.git
     lnav -i https://github.com/existme/lnav.git
   ```
  _Make sure you are using `noConsoleNoAnsi="true"` in `log4j2.xml` at `<PatternLayout noConsoleNoAnsi="true" pattern="%date ...`, otherwise pattern matching might fail_{.info .warn}

## SQL
1. Stand on a line and press <kbd>p</kbd> tos how message parser output
2. Press <kbd>;</kbd> to enter SQL run statement mode
3. Type `select * from logline;`, this will select all messages which parse the same way as this one.
4. Press <kbd>V/v</kbd> to go back and force between log viewer and sQL results
5. You can be creative with statements such as:
   ``` sql
   ;select distinct(uri) from logline order by uri;
   ```


## Run commands before showing the logs
Sometimes you want to set specific filters for certain purposes before running lnav, you can do it by having a shabang line inside a script that contains `#!lnav -f` or `#!lnav -nf` (`n` is for headless mode, so lnav will quit and doesn't show curse interface and `f` is for executing commands)

_Example 1:_{.f1}
_`~/rlnav`_{.ct}
``` sh
#!lnav -f
# This script will filter out unnecessary information from the log file

:reset-session filters
:filter-out se.curity.identityserver.web|se.curity.identityserver.util|se.curity.identityserver.controllers.AnonymousOAuthController
```
To run it, issue:
```
./rlnav /var/log/curity/server.log
```

# References
1. [lnav Documentation Release 0.8.5][TNE]
2. [GitHub - existme/lnav: Lnav add-ons for the Curity Identity Server][GELLAOFTCIS]
* * *
Creation date: _2019-01-21_

[TNE]: https://buildmedia.readthedocs.org/media/pdf/lnav/latest/lnav.pdf
[GTLCOCDFL]: https://github.com/tstack/lnav-config
[GELLAOFTCIS]: https://github.com/existme/lnav.git