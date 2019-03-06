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
| <kbd>U</kbd> | Undelete messages. After the prompt write `~A` to undelete all |
| <kbd>c</kbd> | Change folder, use `=FOLDERNAME` or `?` for list ([ref][RMIOF]) |
| <kbd>s</kbd> | Incremental search |
| <kbd>s</kbd><kbd>s</kbd> | Incremental search again |
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