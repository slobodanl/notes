_Written by: Reza Shams Amiri_
# crontab

## Format

## Logs
To enable separate logging:

1. Open `/etc/rsyslog.d/50-default.conf` remove `#` before `cron.*`
2. `sudo service rsyslog restart`
3. Restart cron service: service cron restart
4. `lnav /var/log/cron.log`

* * *
Creation date: _2019-06-10_
