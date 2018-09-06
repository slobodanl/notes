# android bootloop
# android bootloop

## Connect to the device
Boot to the custom recovery, wait a few seconds until `adb devices` shows your device, then:
``` sh
$ adb devices
List of devices attached
db81b8b68cee40e9	recovery

$ adb shell
~ # 
```

## mount system folder

``` sh
mount -a
touch /system/reza
```

## ADB operations
1. **Push** files to device:
``` sh
adb push /home/user/Downloads/Magisk-v17.1.zip /sdcard/data
```
2. Pull files from the device
``` sh
adb pull /sdcard/data/mydoc.txt ~/Downloads/
```
3. **Reboot**:
    1. Reboot to **recovery**: `adb reboot recovery`
    2. Normal **Reboot**: `adb reboot
    3. Reboot to **BootLoader**: `adb reboot bootloader`
    4. Reboot to **FastBoot**: `adb reboot fastboot`
4. Install an app on the system:
The app should first be pushed to the device:
``` sh
adb install /sdcard/data/app.apk
```

## Root related

### Magisk
Download related files from this [thread][HFXDCAMOMVUST]

1. Installation:  
    1. Download latest [installer][HGCTMRDV1MV1Z]
    2. Push the zip file to the device (assuming you have a folder called `data` inside yout `/sdcard` folder:
    ``` sh
    adb push ~/Downloads/Magisk-v17.1.zip /sdcard/data/
    ```
    3. Goto `twrp` and install the pushed zip file (ref):  
       In this case you will browse to `/sdcard/data` and select `Magisk-v17.1.zip` and swipe to install it.  
![Install-Magisk-Module.png](/img/Install-Magisk-Module.png)
    4. Reboot! Done!
2. Uninstallation:  
    1. Download latest [uninstaller][HGCTMRDV1MU2Z]
    2. Goto `twrp` and install the pushed zip file ([ref][HMNUMMT]):  
       In this case you will browse to `/sdcard/data` and select `Magisk-uninstaller-20180901.zip` and swipe to install it.  
    4. Reboot! Done!

* * *
Creation date: _2018/09/06_

[HFXDCAMOMVUST]: https://forum.xda-developers.com/apps/magisk/official-magisk-v7-universal-systemless-t3473445
[HGCTMRDV1MV1Z]: https://github.com/topjohnwu/Magisk/releases/download/v17.1/Magisk-v17.1.zip
[HGCTMRDV1MU2Z]: https://github.com/topjohnwu/Magisk/releases/download/v17.1/Magisk-uninstaller-20180901.zip
[HMNUMMT]: https://magiskroot.net/uninstall-magisk-module-twrp/