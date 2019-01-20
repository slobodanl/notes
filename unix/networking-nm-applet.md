_Written by: Reza Shams Amiri_

# networking nm applet ([Reference][NA])

## List connections:

``` sh
nmcli device wifi list

IN-USE  SSID                  MODE   CHAN  RATE        SIGNAL  BARS  SECURITY  
*       Andreas               Infra  13    195 Mbit/s  92      ▂▄▆█  WPA2      
        Andreas               Infra  100   540 Mbit/s  82      ▂▄▆█  WPA2      
        lillobillo            Infra  1     130 Mbit/s  67      ▂▄▆_  WPA1 WPA2 
        JJ-Internet           Infra  6     195 Mbit/s  40      ▂▄__  WPA2      
        lillobillo_5G         Infra  44    540 Mbit/s  39      ▂▄__  WPA1 WPA2 
```


## Connect to a network

sudo **nmcli** device wifi connect **\<connection\>**{.hl} password **YourPa$$word**{.hl}

## Show connection
``` sh
nmcli connection show

NAME                UUID                                  TYPE      DEVICE 
PRIVATECN 3         7b377b91-a2dc-49ed-9945-c8e89ddb3c42  wifi      wls2   
hotspot             caaeb84f-63aa-6e37-e612-ef4ff3d04c68  wifi      --     
Wired connection 1  60a3b87e-7453-33c5-83b8-cf824ca36138  ethernet  --   
```
## Show current devices
``` sh
nmcli device

DEVICE  TYPE      STATE        CONNECTION 
wls2    wifi      connected    PRIVATECN 3    
eno1    ethernet  unavailable  --         
lo      loopback  unmanaged    -- 
```

## Turn wifi off
``` sh
nmcli radio wifi off
```
* * *
Creation date: _2019-01-20_

[NA]: https://wiki.archlinux.org/index.php/NetworkManager