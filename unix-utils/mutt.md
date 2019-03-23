_Written by: Reza Shams Amiri_

# Mutt
## Good references:
1. [Configuration - NeoMutt](https://neomutt.org/guide/configuration.html)
1. [Mutt - ArchWiki][MA]
1. [Mutt and HTML email - jasonwryan.com][MAHEJC]
2. [Tim Hentenaar's Blog][THSB]

## Mutt Configuration
Install the following packages:

``` sh
sudo apt install urlview 
```
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

## Finding escape sequence for bindings in terminal
Inside mutt run `:exec what-key` and you get the equivalent sequence

## Using markdown for email composition

1. [Pandoc Tricks · jgm/pandoc Wiki · GitHub][PTJPWG]

## Mutt shortcuts

| Key | Desc |
| --- | ---- |
| <kbd>m</kbd> | new message |
| <kbd>t</kbd> | tag messages, after tagging you can use `;c` to copy or `;d` to delete tagged messages |
| <kbd>Shift+t</kbd> | ag pattern (use `.` pattern for tagging all) |
| <kbd>Ctrl+t</kbd> | untag pattern (use `.` pattern for untagging all) |
| <kbd>;</kbd> | tag operations - after pressing `;` you can press additional keys for commands<BR>`d` for delete tagged messages<BR>`c` for copy |
| <kbd>shift+U</kbd> | Undelete messages. After the prompt write `~A` or `.` to undelete all |
| <kbd>c</kbd> | Change folder, use `=FOLDERNAME` or `?` for list ([ref][RMIOF])<BR>Also if you press <kbd>tab</kbd> you can switch to subscribed folder view |
| <kbd>ctrl+s</kbd> | Incremental search |
| <kbd>ctrl+s</kbd><kbd>ctrl+s</kbd> | Incremental search again |
| <kbd>w</kbd> | Set the flag for message |
| <kbd>Shift+w</kbd> | Remove the flag for message |
| **Operations** |  |
| <kbd>N</kbd> | ~~Go to next new message~~ not working! |
| <kbd>h</kbd> | Show headers |
| <kbd>v</kbd> | View attachments |
| <kbd>i</kbd> | Mark as read |
| <kbd>I</kbd> | Mark as unread |
| <kbd>Esc</kbd><kbd>e</kbd> | Resend the message |
| **View** |  |
| <kbd>b</kbd> or <kbd>Ctrl + </kbd> | Toggle sidebar visibility |
| <kbd>Ctrl + </kbd> | Previous item in sidebar |
| <kbd>Ctrl + </kbd> | Next item in sidebar |
| <kbd>Ctrl + </kbd> | Open mailbox in sidebar |
| <kbd></kbd> | View message in surf |
| <kbd>Ctrl+l</kbd> | Refresh the view |
| | |
| <kbd>Shift + </kbd> | Tag/untag upward|
| <kbd>Shift + </kbd> | Tag/untag downward |
| <kbd>Shift + </kbd> | untag all |
| **Mailbox Navigation** |  |
| <kbd>g</kbd><kbd>i</kbd> | Goto inbox |
| <kbd>g</kbd><kbd>s</kbd> | Goto sent messages |
| <kbd>g</kbd><kbd>d</kbd> | Goto draft messages |
| <kbd>g</kbd><kbd>t</kbd> | Goto trashed messages |
| <kbd>g</kbd><kbd>a</kbd> | Goto starred messages (only gmail)|
|  |  |
| <kbd>F1</kbd> | gmail |
| <kbd>F2</kbd> | axis |
|  |  |


## Some sample configurations:
1. [ConfigList · Wiki · Mutt Project / mutt · GitLab][CWMPMG]
1. [Luc Hermitte's Cygwin configuration][LHSCC]: tunnel section is intersting
1. [Dave's mutt config [/home/davep/.muttrc]][DSMCHDM]
1. [Some handy mutt macros for this and that · GitHub][SHMMFTATG]
1. [PissedOffAdmins  » more mutt goodness][PMMG]
1. [dotfiles/muttrc.bindings at master · gregf/dotfiles · GitHub][DMBAMGDG]: Good commands
1. [wincent/wincent][WRDFMAMWWG]: The VimCast guy
1. [mutt-wizard/muttrc][MWMAMLMWG]: LukeSmithxyz/mutt-wizard
1. [mutt + Gmailを使ってCUIでのメール環境を作る - Qiita][MGQ]

## Cheet sheets
1. [Mutt Cheat Sheet - Kapeli][MCSK]
- - -

Creation date: _2018-11-11_

[CPTSMUAESS]: https://www.linode.com/docs/email/postfix/postfix-smtp-debian7/
[LHSCC]: http://hermitte.free.fr/cygwin/#Mutt
[CWMPMG]: https://gitlab.com/muttmua/mutt/wikis/ConfigList
[RMIOF]: http://therandymon.com/woodnotes/mutt/node15.html
[MA]: https://wiki.archlinux.org/index.php/mutt
[MAHEJC]: http://jasonwryan.com/blog/2012/05/12/mutt/
[DSMCHDM]: http://www.davep.org/mutt/muttrc/
[SHMMFTATG]: https://gist.github.com/pdxmph/cfc4dd675184c06e405e
[THSB]: http://hentenaar.com/keeping-track-of-meetings-with-mutt-calcurse
[PMMG]: http://pissedoffadmins.com/general/more-mutt-goodness.html
[DMBAMGDG]: https://github.com/gregf/dotfiles/blob/master/mutt/muttrc.bindings
[PTJPWG]: https://github.com/jgm/pandoc/wiki/Pandoc-Tricks
[MCSK]: https://kapeli.com/cheat_sheets/Mutt.docset/Contents/Resources/Documents/index
[WRDFMAMWWG]: https://github.com/wincent/wincent/tree/master/roles/dotfiles/files/.mutt
[MWMAMLMWG]: https://github.com/LukeSmithxyz/mutt-wizard/blob/master/muttrc
[MGQ]: https://qiita.com/iorionda/items/c48355770ae689ca1896