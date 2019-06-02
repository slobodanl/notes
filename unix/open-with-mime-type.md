_Written by: Reza Shams Amiri_
# Open with... mime-types

`xdg-mime` uses `mimeapps.list` to determine the default application to use.
Separate `mimeapps.list` files exist to handle user-specific, system-specific and distribution-specific requirements. Their lookup order can be found here: [Association between MIME types and applications][ABMTAA]

``` sh
xdg-mime query default inode/directory
```

Changing default folder open with:

__Using thunar__{.ct}
``` sh
xdg-mime default Thunar.desktop inode/directory application
xdg-open .
```
__Using nautil__{.ct}
``` sh
xdg-mime default nautilus.desktop inode/directory application
xdg-open .
```

The changes will be written to : `~/.config/mimeapps.list`


* * *
Creation date: _2019-06-02_

[ABMTAA]: https://specifications.freedesktop.org/mime-apps-spec/mime-apps-spec-1.0.1.html