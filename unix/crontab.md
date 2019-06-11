_Written by: Reza Shams Amiri_

# CRONTAB

Editing crontab for the current user can be achieved by:

``` sh
sudo -E crontab -u $USER -e
```

## Format

You can use different services for generating crontab jobs:
1. [Crontab Generator][CGGCS]  - Generate crontab syntax
2. [crontab.guru][CGTCSEE]  - the cron schedule expression editor
3. [CRON tester][CTTYCD] - Test your CRON definition


| Format | Meaning |
| ------ | ------- |
| `*/1 * * * *` | At every minute |
| `  0 * * * *` | At minute 0 (**every hour**) |
| `0 */6 * * *` | At minute 0 past every 6th hour (every 6 hour) |
| `30 16 * * *` | At 16:30 every day |
| `0 22 * * 1-5` | At 22:00 on every day-of-week from Monday through Friday |

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
## Running jobs if they are missed because computer is turned off (See [ref][LJSUCWWHWCISDTTSF])
To do that you need to use **`anacron`**, the file is located at `/etc/anacrontab`. Viewing `anacrontab` shows that it has:
``` sh
# format: period delay job-identifier command
1	        5	cron.daily	run-parts --report /etc/cron.daily
7	        10	cron.weekly	run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly	run-parts --report /etc/cron.monthly
```
The `5`, `10`, and `15` numbers shows that anacron will wait `5`, `10`, and `15` minutes after system startup to execute the symlink scripts in each of these folders:
1. `/etc/cron.daily/`
1. `/etc/cron.weekly/`
1. `/etc/cron.monthly/`

To read more about `anacron` just `vim /usr/share/doc/anacron/README.gz`
- - -

Creation date: _2019-06-10_

[CGGCS]: https://crontab-generator.org/
[DTMABCCOALOULSN]: https://www.cyberciti.biz/faq/disable-the-mail-alert-by-crontab-command/
[CGTCSEE]: https://crontab.guru
[CTTYCD]: http://cron.schlitt.info/index.php
[LJSUCWWHWCISDTTSF]: https://serverfault.com/a/52338/447489