_Written by: Reza Shams Amiri_

# Mutt

## Mutt Configuration
## Mutt smtp configuration
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
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |
|  |  |

- - -

Creation date: _2018-11-11_