_Written by: Reza Shams Amiri_

# Mutt

## Mutt Configuration
## Mutt smtp configuration ([REF][CPTSMUAESS])
Mutt uses postifix to send messages so for sending messages you need to configure postifix to use the correct smtp server, for example:

``` sh
sudo vim /etc/postfix/main.cf

# modify the following line
relayhost = xmail.<company>.com:25

# then restart postifix by:
sudo service postfix restart
```

Testing postifix:   

``` sh
echo "body of your email" | mail -s "This is a Subject" -a "From: you@example.com" recipient@elsewhere.com
```

## Mutt important configuration lines:

``` sh
# View
set pager_index_lines=20  # Split the view and show pager at line 20 
## Sidebar
set sidebar_width         = 30                                                   
set sidebar_visible       = yes                                                  
set sidebar_format = "%B%?F? [%F]?%* %?N?%N/?%S" 

# Sorting
set sort=threads
set sort_aux=reverse-last-date-received
set sort_browser=reverse-date
set sort_re # thread based on regex
set reply_regexp = "^(([Rr][Ee]?(\[[0-9]+\])?: *)?(\[[^]]+\] *)?)*"

# Composition config
set signature="echo Reza|"  

```
## Mutt Command Line Interface

_mutt flags_{.ct}

``` sh
-s subject
-c cc_addresses
-b bcc_addresses
```

## Mutt shortcuts

| Key | Desc |
| --- | ---- |
| <kbd>m</kbd> | new message |
| <kbd>t</kbd> | tag messages, after tagging you can use `;c` to copy or `;d` to delete tagged messages |
| <kbd>Shift+t</kbd> | ag pattern (use `.` pattern for tagging all) |
| <kbd>Ctrl+t</kbd> | untag pattern (use `.` pattern for untagging all) |
| <kbd>;</kbd> | tag operations - after pressing `;` you can press additional keys for commands<BR>`d` for delete tagged messages<BR>`c` for copy |
| <kbd>U</kbd> | Undelete messages. After the prompt write `~A` to undelete all |
| <kbd>c</kbd> | Change folder, use `=FOLDERNAME` or `?` for list ([ref][RMIOF]) |
| <kbd>ctrl+s</kbd> | Incremental search |
| <kbd>ctrl+s</kbd><kbd>ctrl+s</kbd> | Incremental search again |
| <kbd>w</kbd> | Set the flag for message |
| <kbd>Shift+w</kbd> | Remove the flag for message |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |


## Some sample configurations:
1. [ConfigList · Wiki · Mutt Project / mutt · GitLab][CWMPMG]
1. [Luc Hermitte's Cygwin configuration][LHSCC]: tunnel section is intersting

- - -

Creation date: _2018-11-11_

[CPTSMUAESS]: https://www.linode.com/docs/email/postfix/postfix-smtp-debian7/
[LHSCC]: http://hermitte.free.fr/cygwin/#Mutt
[CWMPMG]: https://gitlab.com/muttmua/mutt/wikis/ConfigList
[RMIOF]: http://therandymon.com/woodnotes/mutt/node15.html