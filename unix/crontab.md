_Written by: Reza Shams Amiri_
# crontab
Editing crontab for the current user can be achieved by:
``` sh
sudo -E crontab -u $USER -e
```
## Format

## Run complex queries
You can wrap the script as follows:
```
/bin/sh -c '<command>'
```
Examples:

__notify each minute__{.ct}
``` sh
*/1 * * * * /bin/sh -c 'export DISPLAY=:0 && /home/existme/bin/dunstify -p "Runs each minutes" "... $(date)" -i "done-38"'
```
__play a sound each minute__{.ct}
``` sh
*/1 * * * * /bin/sh -c 'export XDG_RUNTIME_DIR="/run/user/1000" && /home/existme/bin/,ding'
```

## Logs
To enable separate logging:

1. Open `/etc/rsyslog.d/50-default.conf` remove `#` before `cron.*`
2. `sudo service rsyslog restart`
3. Restart cron service: service cron restart
4. `lnav /var/log/cron.log`

* * *
Creation date: _2019-06-10_
