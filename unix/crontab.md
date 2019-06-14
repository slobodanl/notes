_Written by: Reza Shams Amiri_

# CRONTAB

Editing crontab for the current user can be achieved by:

``` sh
sudo -E crontab -u $USER -e
```
**If `crontab -e` doesn't work for your user and you need to use sudo to access your crontab file (which is located in `/var/spool/cron/crontabs/`), you probably are not part of the `crontab` group.<br>Use:<br> `sudo sudo usermod -a -G crontab $USER` to add yourself to the `crontab` group.<br>If you don't want to logoff and logon for the group to be effective use [this hack][SRALUSGAWLOSU]**{.info .warn}

### Use `-l` flag to Display the current crontab:
_System wide cron jobs_{.ct}
``` sh
 sudo crontab -l

#Ansible: Update certificates
25 * * * * /opt/MyApp/scripts/refresh-cert.sh
```
_Current user's cron jobs_{.ct}
``` sh
 sudo crontab -l -u $USER

# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# BEWARE: % signs should be escaped in crontab they have special meaning here (newline)
#
# m h  dom mon dow   command
*/5 * * * * /bin/sh -c 'export DISPLAY=:0 && /home/existme/bin/dunstify -p "Run each five minutes" "$(date +\%H:\%M)" -i "done-38"' >/tmp/crontab.log 2>&1
*/5 * * * * /bin/sh -c 'export XDG_RUNTIME_DIR="/run/user/1000" && /home/existme/bin/,ding' > /tmp/crontab.log 2>&1
```
_BEWARE: `%` signs should be escaped in crontab they have special meaning there (newline).<br>The best way is to have a script running not writing complex bash commands_{.info .warn}
# Format
**Syntax:**
``` sh
*  *  *  *  *  /path/to/script *
1  2  3  4  5        6         7
|  |  |  |  |        |         |+- Year
|  |  |  |  |        +-- Command to run
|  |  |  |  +---- Day of the Week   (Allowed Value: 0-6, 1 for Monday and so on)
|  |  |  +------ Month of the Year (Allowed Value: 1-12, 1 for January and so on)
|  |  +-------- Day of the Month  (Allowed Value: 1-31)
|  +---------- Hour              (Allowed Value: 0-23)
+------------ Minute            (Allowed Value: 0-59)
```
The following picture is referenced from [https://www.markus-gattol.name/ws/time.html#cron][TCRSM] 
![cron_schedule_a_command_format.png](/img/unix/cron_schedule_a_command_format.png)

You can use different services for **generating crontab**{.hl} jobs:
1. [Crontab Generator][CGGCS]  - Generate crontab syntax
2. [crontab.guru][CGTCSEE]  - the cron schedule expression editor
3. [CRON tester][CTTYCD] - Test your CRON definition

## Some examples (see [ref][2UCETSCILBWHO])
| Syntax | Meaning |
| ------ | ------- |
| `*/1 * * * *` | At every minute |
| `  0 * * * *` | At minute 0 (**every hour**) |
| `0 */6 * * *` | At minute 0 past every 6th hour (every 6 hour) |
| `30 16 * * *` | At 16:30 every day |
| `30-50/5 14 * * *` | At every 5 minutes starting at 2:30 pm and ending at 2:50 pm daily |
| `0 22 * * 1-5` | At 22:00 on every day-of-week from Monday through Friday |
| `45 18 * 1-4,8 5` | At 6:45 PM every Friday(5) in <br> January(1) through March(4) and August(8) |

`crontab` also allows the following formats:

| Keyword | Equivalent | Describe |
| ------- | ---------- | -------- |
| @yearly  | `0 0 1 1 *` | 0th minute of every year |
| @monthly | `0 0 1 * *` | 00:00 on 1st of every month |
| @daily   | `0 0 * * *` | 00:00 Every single day |
| @hourly  | `0 * * * *` | Every hour |
| @reboot  | `Run at startup` ||

Run process after reboot can look like this:
``` sh
@reboot /home/ondrej/run_process.sh
```
## More about Crontab
An example of ENV variables inside of Crontab job
``` sh
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root
HOME=/
```
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

# Logs

To enable separate logging:

1. Open `/etc/rsyslog.d/50-default.conf` remove `#` before `cron.*`
2. `sudo service rsyslog restart`
3. Restart cron service: service cron restart
4. `lnav /var/log/cron.log`

# Disable sending emails (See [ref][DTMABCCOALOULSN]):

Either send the results to `>/dev/null 2>&1` or `> /tmp/mylog.log`

``` sh
*/1 * * * * /bin/sh -c 'export DISPLAY=:0 && /home/existme/bin/dunstify -p "Run each five minutes" "... $(date)" -i "done-38"' >/dev/null 2>&1

*/1 * * * * /bin/sh -c 'export XDG_RUNTIME_DIR="/run/user/1000" && /home/existme/bin/,ding' > /tmp/crontab.log
```
# Running jobs if they are missed because computer is turned off (See [ref][LJSUCWWHWCISDTTSF])
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
[SRALUSGAWLOSU]: https://superuser.com/a/345051/285113
[2UCETSCILBWHO]: https://best-web-hosting.org/linux-crontab-examples/
[TCRSM]: https://www.markus-gattol.name/ws/time.html#cron