_Written by: Reza Shams Amiri_

# unix systemd

## systemctl
1. **restart**:
    ``` sh
    sudo systemctl restart wiki-private.service 
    ```
1. **daemon reload**:
    ``` sh
    sudo systemctl daemon-reload
    ```
1. **List units**:
    1. List all the available units       
    ``` sh
    systemctl list-unit-files
    
    # you can use different types
    # systemctl --type=help
    systemctl list-unit-files --type=service
    systemctl list-unit-files --type=mount
    
    systemctl list-unit-files --type=socket
    systemctl list-sockets --all
    
    systemctl list-units --all --state=inactive
    
    ```
    1. **List all running units    **
    ``` sh
    systemctl list-units    
    ```
    1. List units that we have log for them 
    ``` sh
    journalctl --field _SYSTEMD_UNIT
    ```
    _Example_{.f1}
    Find teamviewer service and disable it:
    ``` 
     systemctl list-units | grep team
    teamviewerd.service
     sudo systemctl stop teamviewerd.service
     sudo systemctl disable teamviewerd.service
     sudo systemctl mask teamviewerd.service
     sudo rm /etc/systemd/system/teamviewerd.service
     sudo systemctl daemon-reload
    ```

    1. **List all failed units**
    ``` sh
    systemctl list-units --state=failed
    # Or you can use the alias
    # systemctl --failed        
    ```    
    _`systemctl --failed` doesn't work on all systems_{.note}    
    **Example results could be like this:**
    ![failed-services.png](/img/unix/failed-services.png)
1. **Display status** of the unit:
   ``` sh
   sudo systemctl status networkd-dispatcher.service      
   ```
   ![service-status.png](/img/unix/service-status.png)
1. **Mask**/**Unmask** (imposible to start)
    ``` sh
    systemctl mask httpd.service
    # ln -s '/dev/null' '/etc/systemd/system/httpd.service'    

    systemctl unmask httpd.service
    # rm '/etc/systemd/system/httpd.service'
    
    $ systemctl list-unit-files    
    httpd.service                          masked
    ```
1. **Enable/disable**:
    ``` sh
    # systemctl is-active tmp.mount
    # systemctl enable tmp.mount
    # systemctl disable  tmp.mount
    ```
1. Display a unit file:
    ``` sh
    systemctl cat atd.service
    ```
1. Checking Unit Properties   
    ``` sh
    systemctl show sshd.service
    ```
1. Editing a unit file
    ``` sh
    sudo systemctl edit wiki-notes.service --full
    ```
1. Displaying Dependencies   
    ``` sh
    systemctl list-dependencies sshd.service
    ```
    
##  journalctl  
1. **Show logs for a specific unit** (`<service-name>.service`):
   1. to follow the logs:
   ``` sh
   sudo journalctl -f -u wiki-private.service
   # OR: sudo journalctl -f -u wiki-private
   ```
   1. to follow and pass it to lnav
   ``` sh
   sudo journalctl -f -u wiki-private.service | lnav
   # OR: sudo journalctl -f -u wiki-private | lnav
   ```
   1. to show logs since boot(`-b`) and not truncating the logs(`-l`) 
   ``` 
   sudo journalctl -u networkd-dispatcher -b -l
   ```
   1. Show logs since(`--since`) a specific date
   ``` 
   sudo journalctl --since "2015-01-10 17:15:00" -u wiki-notes.service --no-pager | lnav
   ```
   1. Show logs since last boot
   ``` 
   journalctl --list-boots
   
   -12 456fa857417c4253b71fb798cf457e11 Mon 2019-06-03 19:02:40 CEST—Tue 2019-06-04 00:27:51 CEST
   -11 e9cc9d10b9304cc4b23ac55ee73fc917 Tue 2019-06-04 19:12:45 CEST—Mon 2019-06-10 05:23:56 CEST   
   -10 88c37209120142f390f2b5a4fdbc9a52 Mon 2019-06-10 21:12:10 CEST—Wed 2019-06-12 00:56:54 CEST
   
   journalctl -b -1 -u private-wiki
   ```
1. **Rotate logs**:
    1. for all units:
    ``` sh
    sudo journalctl --rotate
    ```
    1. for a specific unit:
    ``` sh
    sudo journalctl --rotate -u wiki-notes.service
    ```
1. **Bruteforce flush**
    ``` sh
    sudo journalctl --flush
    sudo journalctl --vacuum-time=1seconds
    ```
1. **Show errors since boot**
   * `-x` Augment log lines with explanation texts from the message catalog
   * `-b` Show messages from a specific boot. If the boot ID is omitted, a positive offset will look up the boots starting from the beginning of the journal
   * `-p` Filter output by message priorities or priority ranges. i.e: "emerg" (0), "alert" (1),"crit" (2), "err" (3), "warning" (4), "notice" (5), "info" (6), "debug" (7)
   ``` sh
   journalctl -xb -p err
   ```

## Analyse

1.  Analyze systemd boot process     
    ``` sh
    systemd-analyze
    
    Startup finished in 26.510s (firmware) + 9.187s (loader) + 5.150s (kernel) + 1min 1.908s (userspace) = 1min 42.756s
    graphical.target reached after 22.610s in userspace
    ```
1.  Analyze time taken by each process at boot   
    ``` sh
    systemd-analyze blame
    
         23.612s apt-daily-upgrade.service
         16.206s apt-daily.service
          7.681s NetworkManager-wait-online.service
          1.949s mnt-mybook\x2d2t.mount
           525ms docker.service
           340ms dev-nvme0n1p2.device
           322ms logrotate.service
           249ms systemd-resolved.service
           212ms systemd-logind.service
           187ms networkd-dispatcher.service
           183ms systemd-timesyncd.service
    ...
    ```
1.  Analyze critical chain at boot   
    ``` sh
    systemd-analyze critical-chain
    
    The time after the unit is active or started is printed after the "@" character.
    The time the unit takes to start is printed after the "+" character.

    graphical.target @22.610s
    └─multi-user.target @22.610s
      └─docker.service @22.085s +525ms
        └─network-online.target @22.084s
          └─NetworkManager-wait-online.service @14.402s +7.681s
            └─NetworkManager.service @14.333s +57ms
              └─dbus.service @14.320s
                └─basic.target @14.287s
                  └─sockets.target @14.287s
                    └─snapd.socket @14.280s +6ms
                      └─sysinit.target @14.271s
                        └─systemd-timesyncd.service @14.087s +183ms
                          └─systemd-tmpfiles-setup.service @14.057s +24ms
                            └─local-fs.target @14.044s
                              └─tmp-.mount_jetbraiXTxxu.mount @27.961s
                                └─local-fs-pre.target @278ms
                                  └─keyboard-setup.service @208ms +69ms
                                    └─systemd-journald.socket @193ms
                                      └─system.slice @175ms
                                        └─-.slice @175ms

    ```
## Default target
To view the default target that systemd tries to reach at boot (which in turn starts all of the unit files that make up the dependency tree of that target), type:
``` sh
 systemctl get-default
graphical.target

 sudo systemctl list-dependencies graphical.target
graphical.target
● ├─accounts-daemon.service
● ├─apport.service
● ├─dictd.service
● ├─grub-common.service
● ├─hddtemp.service
● ├─switcheroo-control.service
● ├─systemd-update-utmp-runlevel.service
● ├─udisks2.service
● ├─xdm.service
● └─multi-user.target
●   ├─anacron.service
●   ├─apache2.service
●   ├─apport.service
●   ├─autofs.service
●   ├─avahi-daemon.service
●   ├─binfmt-support.service
●   ├─cfengine3.service
●   ├─containerd.service
●   ├─cron.service
●   ├─cups-browsed.service
●   ├─cups.path
●   ├─dbus.service
●   ├─dictd.service
●   ├─dmesg.service

```
Here we can see that `xdm.service` is started at boot

References:
1. [How to Manage 'Systemd' Services and Units Using 'Systemctl' in Linux][HTMSSAUUSIL]
2. [How To Use Systemctl to Manage Systemd Services and Units | DigitalOcean][HTUSTMSSAUD]
3. [How To Use Journalctl to View and Manipulate Systemd Logs | DigitalOcean][HTUJTVAMSLD]

* * *
Creation date: _2018-10-29_

[HTMSSAUUSIL]: https://www.tecmint.com/manage-services-using-systemd-and-systemctl-in-linux/
[HTUSTMSSAUD]: https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units
[HTUJTVAMSLD]: https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs