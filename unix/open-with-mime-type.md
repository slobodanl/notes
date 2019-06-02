_Written by: Reza Shams Amiri_
# Open with... mime-types

`xdg-mime` uses `mimeapps.list` to determine the default application to use.
Separate `mimeapps.list` files exist to handle user-specific, system-specific and distribution-specific requirements. Their lookup order can be found here: [Association between MIME types and applications][ABMTAA]

``` sh
## setting
xdg-mime default <opener-shortcut>.desktop inode/directory application

## querying
xdg-mime query default inode/directory
```

__The desktop files exists in `/usr/share/applications/`, when using `xdg-mime` make sure that the desktop file exists, otherwise you might get unexpected results__{.info .warn}

## Example:
Changing default folder open with:

__Using thunar__{.ct}
``` sh
$ xdg-mime default Thunar.desktop inode/directory application
$ xdg-open .

$ xdg-mime query default inode/directory
  Thunar.desktop
```
__Using nautilus__{.ct}
``` sh
$ xdg-mime default org.gnome.Nautilus.desktop inode/directory application
$ xdg-open .

$ xdg-mime query default inode/directory
org.gnome.Nautilus.desktop
```

The changes will be written to : `~/.config/mimeapps.list`


* * *
Creation date: _2019-06-02_

[ABMTAA]: https://specifications.freedesktop.org/mime-apps-spec/mime-apps-spec-1.0.1.html