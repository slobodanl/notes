_Written by: Reza Shams Amiri_
# mutt setup config

## Offline IMAP

for offline imap we will use `mbsync` as suggested by [LukeSmithxyz][GLMWASFACMAIWASIASP]

``` sh
sudo apt install isync
```
The files needed to be configured for `isync/mbsync` are:
1. `~/.mbsyncrc`
2. `~/.msmtprc`
3. The mail-dir is configured to be in `~/mail`

Checking the settings:
_list all gmail mailboxes_{.ct}
``` sh
mbsync -l Gmail
```

* * *
Creation date: _2019-07-11_

[GLMWASFACMAIWASIASP]: https://github.com/LukeSmithxyz/mutt-wizard