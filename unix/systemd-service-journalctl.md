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
    1. List units that we have log for them 
    ```
    journalctl --field _SYSTEMD_UNIT
    ```


* * *
Creation date: _2018-10-29_
