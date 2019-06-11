_Written by: Reza Shams Amiri_

# crontab

Editing crontab for the current user can be achieved by:

``` sh
sudo -E crontab -u $USER -e
```

## Format

You can use different services for generating crontab jobs:
1. [Crontab Generator - Generate crontab syntax][CGGCS]
2. [crontab.guru - the cron schedule expression editor][CGTCSEE]
3. [CRON tester - Test your CRON definition][CTTYCD]


| Format | Meaning |
| ------ | ------- |
| `*/1 * * * *` | At every minute |
| `  0 * * * *` | At minute 0 (every hour) |
| `0 */6 * * *` | At minute 0 past every 6th hour (every 6 hour) |

## Run complex queries

You can wrap the script as follows:

```
/bin/sh -c '<command>'
```

Examples:

**notify each minute**{.ct}

``` sh
*/1 * * * * /bin/sh -c 'export DISPLAY=:0 && /home/existme/bin/dunstify -p "Runs each minutes" "... $(date)" -i "done-38"'
```

To be able to use graphical UI `export DISPLAY=:0` should be preceded.

**play a sound each minute**{.ct}

``` sh
*/1 * * * * /bin/sh -c 'export XDG_RUNTIME_DIR="/run/user/1000" && /home/existme/bin/,ding'
```

To have sound `export XDG_RUNTIME_DIR="/run/user/1000"` should be preceded.

## Logs

To enable separate logging:

1. Open `/etc/rsyslog.d/50-default.conf` remove `#` before `cron.*`
2. `sudo service rsyslog restart`
3. Restart cron service: service cron restart
4. `lnav /var/log/cron.log`

## Disable sending emails (See [ref][DTMABCCOALOULSN]):

Either send the results to `>/dev/null 2>&1` or `> /tmp/mylog.log`

``` sh
*/1 * * * * /bin/sh -c 'export DISPLAY=:0 && /home/existme/bin/dunstify -p "Run each five minutes" "... $(date)" -i "done-38"' >/dev/null 2>&1

*/1 * * * * /bin/sh -c 'export XDG_RUNTIME_DIR="/run/user/1000" && /home/existme/bin/,ding' > /tmp/crontab.log
```

- - -

Creation date: _2019-06-10_

[CGGCS]: https://crontab-generator.org/
[DTMABCCOALOULSN]: https://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/
[CGTCSEE]: https://crontab.guru
[CTTYCD]: http://cron.schlitt.info/index.php?cron=*%2F10+*+*+*+*&iterations=10&test=Test