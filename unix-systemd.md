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
1. **journalctl**:
    ``` sh
    sudo journalctl -f -u wiki-private.service
    ```



* * *
Creation date: _2018-10-29_
