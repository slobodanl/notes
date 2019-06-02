_Written by: Reza Shams Amiri_
# Open with... mime-types

`xdg-mime` uses `mimeapps.list` to determine the default application to use.
Separate `mimeapps.list` files exist to handle user-specific, system-specific and distribution-specific requirements. Their lookup order can be found here: [Association between MIME types and applications][ABMTAA]

``` sh
## setting
ﰲ xdg-mime default <opener-shortcut>.desktop inode/directory application

## querying
ﰲ xdg-mime query default inode/directory

## Identifying the mime type
ﰲ xdg-mime query filetype ~/Downloads/pdf/silence.epub
  application/epub+zip
ﰲ xdg-mime query default application/epub+zip
  calibre-gui.desktop
```

__The desktop files exists in `/usr/share/applications/`, when using `xdg-mime` make sure that the desktop file exists, otherwise you might get unexpected results__{.info .warn}

## Example:
Changing default folder open with:

__Using thunar__{.ct}
``` sh
ﰲ xdg-mime default Thunar.desktop inode/directory application
ﰲ xdg-open .

ﰲ xdg-mime query default inode/directory
  Thunar.desktop
```
__Using nautilus__{.ct}
``` sh
ﰲ xdg-mime default org.gnome.Nautilus.desktop inode/directory application
ﰲ xdg-open .

ﰲ xdg-mime query default inode/directory
org.gnome.Nautilus.desktop
```

The changes will be written to : `~/.config/mimeapps.list`

__Some times you need to update `~/.local/share/mime` for changes to be effective in different applications (ex: calibre). To do that you need to execute:<br><br>ﰲ `update-mime-database ~/.local/share/mime`__{.info .warn}

## Other examples:

__epub__{.ct}
``` sh
# Looking at ~/.config/mimeapps.list , shows:
#
# [Added Associations]
# application/epub+zip=atril.desktop;okularApplication_md.desktop;calibre-ebook-edit.desktop;calibre-ebook-viewer.desktop;
# [Default Applications]                                                           
# application/epub+zip=okularApplication_md.desktop
# 
# but :
# ﰲ locate okularApplication_md.desktop
# shows okular is not installed
#
# and 
# ﰲ xdg-mime query default application/epub+zip
#   calibre-gui.desktop
#
# 

```

* * *
Creation date: _2019-06-02_

[ABMTAA]: https://specifications.freedesktop.org/mime-apps-spec/mime-apps-spec-1.0.1.html