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
    
##  journalctl  
1. **Show logs for a specific unit**:
    1. to follow the logs:
    ``` sh
    sudo journalctl -f -u wiki-private.service
    ```
    1. to follow and pass it to lnav
    ``` sh
    sudo journalctl -f -u wiki-private.service | lnav
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
2. **List all units**:
    1. List all the available units       
    ``` sh
    systemctl list-unit-files
    ```
    3. List all running units    
    ``` sh
    systemctl list-units
    ```
    2. List units that we have log for them 
    ``` sh
    journalctl --field _SYSTEMD_UNIT
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

* * *
Creation date: _2018-10-29_
