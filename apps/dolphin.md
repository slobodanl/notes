_Written by: Reza Shams Amiri_
# dolphin
KDE file manager "Dolphin" is one of the best filemanagers available on Linux.
To install it:
``` sh
sudo apt install dolphin
```

## Themes
Dolphin uses `qt5ct` for its theme. The only theme that seems to work with i3 configuration is `Breeze` but you can modify it to use `Paper` icon setes.

``` sh
sudo apt install qt5ct
```
for themes to be effective you should also have the following line executed before dolphin has started to run:

``` sh
export QT_QPA_PLATFORMTHEME=qt5ct
```

![dolphin-screenshot.png](/img/apps/dolphin-screenshot.png)
* * *
Creation date: _2019-12-30_
