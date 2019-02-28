# Unix-Disable-Service.Md

----------------------------------------- 

``` bash
s update-rc.d wildfly disable
sudo apt-get install sysv-rc-conf
sudo apt-get install jobs-admin
```

1. **systemd-manager**:
    ``` sh
    git clone https://github.com/mmstick/systemd-manager && cd systemd-manager && make && sudo make install
    ```
1. **kcm_systemd**:
    ``` sh
    sudo apt install kde-config-systemd kde-cli-tools
    
    kcmshell5 kcm_systemd
    ```
    ![][TNE]

-----------------------------------------
2018-08-06 17:13:37

[TNE]: https://i.stack.imgur.com/uqrSV.png