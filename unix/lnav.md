_Written by: Reza Shams Amiri_

# lnav

## Keyboard shortcuts

Shortcut                |  Iconinc Desc | Descrtiption 
------------------------|---|---------------------------------------------------
_Spatial Navigation_{.f1}| |
<kbd>g</kbd>/<kbd>G</kbd> |祝  | Move to the top/bottom of the current view
<kbd>Home</kbd>/<kbd>End</kbd> |祝 | Move to the top/bottom of the current view
<kbd>e</kbd>/<kbd>E</kbd> | ﮿﯀  | Jump to next/previous error
<kbd>w</kbd>/<kbd>W</kbd> | ﮿﯀   |Jump to next/previous warning
<kbd>n</kbd>/<kbd>N</kbd> | ﮿﯀   |Jump to next/previous search hit
<kbd>u</kbd>/<kbd>U</kbd> | ﮿﯀   |Jump to next/previous Bookmark
<kbd>s</kbd>/<kbd>S</kbd> | ﮿﯀  省 |A slow down is detected by measuring how quickly the message rate has changed over the previous several messages.
<kbd>f</kbd>/<kbd>F</kbd> | ﮿﯀   |Goto next/previous log file
<kbd>X</kbd> |   |Close current log file
<kbd>SHIFT</kbd><kbd>/</kbd>|| Left/Right ten columns
<kbd>SHIFT</kbd><kbd>/</kbd>|| Left/Right ten columns
|||
|_Chronological Navigation_{.f1}||
<kbd>1-6</kbd>/<kbd>SHIFT</kbd><kbd>1-6</kbd> | ﮿﯀  |Next/previous n’th ten minute of the hour
<kbd>8</kbd>/<kbd>7</kbd> | ﮿﯀  |Next/previous minute
<kbd>0</kbd>/<kbd>SHIFT</kbd><kbd>0</kbd> | ﮿﯀  |_Next/previous day_{.hl}
|||
|_Bookmarks_{.f1}||
<kbd>m</kbd>               || Mark/unmark the line at the top of the display.
<kbd>M</kbd>               || Mark/unmark all the lines between the top of the display and the last line marked/unmarked.
<kbd>J</kbd>               |怜  |  Mark/unmark the next line after the previously marked line.
<kbd>K</kbd>               |玲  |  Like 'J' except it toggles the mark on the previous line.
<kbd>C</kbd>               | | Clear all marked lines.
<kbd>c</kbd>               | | _Copy the marked text_{.hl} to the X11 selection buffer or OS X clipboard.
<kbd>T</kbd>               || Toggle time
|||
|_Filters_{.f1}||
|<kbd>TAB</kbd> | |Toggle focusing on the Filter Editor or to the main window<br>_(only available in lnav 0.8.5+)_{.red}|
|<kbd>CTRL</kbd>+<kbd>f</kbd>| |Toggle enable/disable all filters|
||| **Only when Filter Editor is active**<br>|
|<kbd>SPACE</kbd> || **Toggle** a filter|
|<kbd>o</kbd> |ﱻ| Create a new "**out**" filter |
|<kbd>i</kbd> |ﱷ| Create a new "**in**" filter |
|<kbd>t</kbd> |﴾| **Toggle** the type of filter between "**in**" and "**out**"|
|<kbd>Enter</kbd> || Edit the selected filter |
|<kbd>D</kbd> |﫧| Delete the selected filter |
|||
|_Display options_{.f1}||
|<kbd>P</kbd>  |  | Switch to/from the pretty-printed view|
|<kbd>p</kbd>  |ﬥ| enable or disable the display of the fields that the log message parser knbows about|
|<kbd>v</kbd>  |  | Switch to/from the SQL result view|
|<kbd>Shift</kbd>+<kbd>v</kbd>  | 難 | Switch to/from the SQL result view and move to the corresponding in the log_line column
<kbd>CTRL</kbd>+<kbd>l</kbd>  |  | (_Lo-fi mode_{.hl}) Exit screen-mode and write the displayed log lines in plain text to the terminal
<kbd>CTRL</kbd>+<kbd>R</kbd>  |  | _Reset the session state_{.hl}.  This will save the current session state (filters, highlights) and then reset the state to the factory default.
<kbd>z</kbd>/<kbd>Z</kbd>  |  | Zoom in or out one step in the histogram view
<kbd>CTRL</kbd>+<kbd>w</kbd>  | 蝹 | _Toggle wrap_{.hl}
<kbd>SHIFT</kbd>+<kbd>t</kbd> |神 | Display elapsed time between lines
<kbd>i</kbd>/<kbd>I</kbd>                  | | View/leave a histogram of the log messages over time
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
See more about log formats here: [Debugging lnav config][LCD]
## Installing formats:
- **Install remote repository**:   
  A standard set of repositories is maintained at [ tstack/lnav-config][GTLCOCDFL] and can be installed by passing ‘extra’ on the command line
  ``` sh
   lnav -i extra    
  ```
  It will install bunch of formats in `~/.lnav/formats` folder
- **Install additional formats directly from a repo**:
  ``` sh
    lnav -i https://github.com/curityio/lnav.git
    lnav -i https://github.com/existme/lnav.git
  ```
- **Downloading one format from internet and installing it directly**
  A git repo, as an example, provides support for different formats [https://github.com/PaulWay/lnav-formats](https://github.com/PaulWay/lnav-formats) (including log4j.)  
  If you quickly want to support `log4j` just execute the following command: 
  ``` sh
  curl -o ~/.lnav/formats/installed/log4j.json https://raw.githubusercontent.com/PaulWay/lnav-formats/master/log4j.json
  ```
  _Make sure you are using `noConsoleNoAnsi="true"` in `log4j2.xml` at `<PatternLayout noConsoleNoAnsi="true" pattern="%date ...`, otherwise pattern matching might fail_{.info .warn}
# Command line interface
|Optional arguments|Description|
|------|-----------|
| `-I` path | Add the given configuration directory to the search path|
| `-i` | **Install the given format** files in the `$HOME/.lnav/formats/installed` directory|
| `-c` | **A command, query**, or file to execute.  The first characterdetermines the type of operation: a `colon` is used for the built-in commands; a `semi-colon` for SQL queries; and a pipe symbol (`|`) for executing a file containing other commands. |
| `-C` | Check the configuration and exit.  The log format files will be loaded and checked|
| `-d` file | **Write debug messages** to the given file|
| `-f` file | A file that contains commands, queries, or **files to execute**. This option is a shortcut for `-c '|file'`.  You can use a dash (`-`) to execute commands from the standard input.|
| `-V` | Print version information|
| `-r` | **Load older rotated log** files as well|
| `-t` | **Prepend timestamps** to the lines of data being read in on the standard input|
| `-w` file | **Write** the contents of the **standard input** to this file.|

## _Examples:_{.f3}

1. `-c`:
   _goto a line_{.ct}
   ``` sh
   # Goto line number 10 after loading the file
   lnav -c ':goto 10' /var/log/curity/server.log
   ```
   This option **can be given multiple times** to execute multiple operations in sequence.
1. `-f`:
   _Using `-f` to execute commands from stdin_{.ct}
   ``` sh   
   echo ":goto 10"|lnav /var/log/curity/server.log -f -
   ```
1. `-r`:
   _Using `-r` to load older rotated logs_{.ct}
   ``` sh
   # The following command only loads /var/log/apache2/error.log
   sudo lnav /var/log/apache2/error.log
   
   # How ever supplying -r will cause lnav to load all the following files:
   # /var/log/apache2/error.log
   # /var/log/apache2/error.log.1
   # /var/log/apache2/error.log.2.gz
   # ....
   # /var/log/apache2/error.log.14.gz   
   sudo lnav -r /var/log/apache2/error.log
   ```
   ![lnav-loaded-files.png](/img/unix/lnav-loaded-files.png)
   
   _Using `-r` to load older syslog rotated logs_{.ct}
   ``` sh
   # The following command only loads /var/log/apache2/error.log
   sudo lnav -r
   ```   
   
1. `-d`: 
   _Using `-d` to write debug logs to a file_{.ct}
   ``` sh
   lnav /var/log/curity/server.log -d /tmp/lnav.out
   ```
1. `-t`:
   _Using `-t` to prepend timestamp_{.ct}
   ``` sh
   ,build i3 | lnav -t
   
   ## Slightly better version will use `|&` which will not mess with lnav display
   ,build i3 |& lnav -t
   ```
   _Pay attention to the usage of `|&` (pipe ampersand) to avoid messing lnav display when piping!_{.note .red}
1. `-w`:
   _Using `-w` to write stdin to a file_{.ct}
   ``` sh
   ,build i3 |& lnav -t -w /tmp/lnav.out
   ```
   `/tmp/lnav.out` will contain the output of make

# SQL queries

## Performing queries
1. Stand on a line and press <kbd>p</kbd> tos how message parser output
2. Press <kbd>;</kbd> to enter SQL run statement mode
3. Type `select * from logline;`, this will select all messages which parse the same way as this one.
4. Press <kbd>V/v</kbd> to go back and force between log viewer and sQL results
5. You can be creative with statements such as:
   ``` sql
   ;select distinct(uri) from logline order by uri;
   ```
   or
   ``` sql 
   ;SELECT distinct(class) from logline order by class;
   ```

## Tables
`lnav` will create tables that can be queried using the subset of SQL that is supported by Sqlite3.
  Note that only the log messages that match a particular format can be queried by a particular table. 
  _You can get a dump of the schema for the internal tables, and any attached databases, by running the `.schema` SQL command_{.note}

Some commonly used format tables are:
1. `generic_log`
2. `access_log`
3. `syslog_log`
4. `strace_log`
5. **Curity Logs:**
    1. `curity_server_log`
    1. `curity_audit_log`
    1. `curity_cluster_log`
    1. `curity_conf_service_log`
    1. `curity_request_log`    

_Examples:_{.f1}
``` sql
select count(class) as _count, class from curity_server_log group by class order by _count
```
Example output and the histogram of the query is showed below:
![lnav-select-output.png](/img/unix/lnav-select-output.png)
# Running commands before showing the log
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
[LCD]: /unix/lnav-config-debug