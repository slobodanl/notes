# X-Theme.Md

----------------------------------------- 
## Theme manager

The best theme manager so far is, `mate-appearance-properties`, which
can be installed using:

```bash
sudo apt install mate-control-center
```

Others are:
1. lxappearance
2. gtk-theme-config
3. gtk-chtheme
4. qtconfig-qt4
5. xfce4-appearance-settings
6. gnome-tweak-tool:
    ``` sh
    sudo apt install gnome-tweak-tool
    ```
7. gnome-tweaks

## Changing cursor
All the programs should be restarted for cursor to be effective

## Icon theme

Use:
``` bash
gsettings list-recursively | grep icon-theme
```
To list all themes in use.
To change theme use:

```
gsettings set org.gnome.desktop.interface gtk-theme "custom-desktop-theme"
```

## Control Center

To trick gnome and bring control center up in i3:
``` bash
env XDG_CURRENT_DESKTOP=GNOME gnome-control-center
```

### Folders:

System wide: `/usr/share/icons`
User: `~/.icons`

# Enable dark mode in Chrome

Set `gtk-application-prefer-dark-theme` to `true` in `~/.config/gtk-3.0/settings.ini`:   

_~/.config/gtk-3.0/settings.ini_{.ct}
``` sh
gtk-application-prefer-dark-theme=true
```

-----------------------------------------
2017-12-26 09:53:49
