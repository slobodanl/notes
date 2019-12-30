_Written by: Reza Shams Amiri_
# Open with... mime-types
## ﯦ TL/DR; Update: Easy method
``` sh
mimeopen -d ~/sample.pdf
# select zathura

xdg-open ~/sample.pdf
```

## Original method
`xdg-mime` uses `mimeapps.list` to determine the default application to use.
Separate `mimeapps.list` files exist to handle user-specific, system-specific and distribution-specific requirements. Their lookup order can be found here: [Association between MIME types and applications][ABMTAA]

``` sh
## setting
 xdg-mime default <opener-shortcut>.desktop inode/directory application

## querying
 xdg-mime query default inode/directory

## Identifying the mime type
 xdg-mime query filetype ~/Downloads/pdf/silence.epub
  application/epub+zip
 xdg-mime query default application/epub+zip
  calibre-gui.desktop
```

__The desktop files exists in `/usr/share/applications/`, when using `xdg-mime` make sure that the desktop file exists, otherwise you might get unexpected results__{.info .warn}
__In addition to the above method, you can also query the mimetype using the following commands:<br> `file --mime-type -b ~/Downloads/citation-6737405.txt`__{.info .ok}
## Example:
Changing default folder open with:

__Using thunar__{.ct}
``` sh
 xdg-mime default Thunar.desktop inode/directory application
 xdg-open .

 xdg-mime query default inode/directory
  Thunar.desktop
```
__Using nautilus__{.ct}
``` sh
 xdg-mime default org.gnome.Nautilus.desktop inode/directory application
 xdg-open .

 xdg-mime query default inode/directory
org.gnome.Nautilus.desktop
```

The changes will be written to : `~/.config/mimeapps.list`

__Some times you need to update `~/.local/share/mime` for changes to be effective in different applications (ex: calibre). To do that you need to execute:<br><br> `update-mime-database ~/.local/share/mime`__{.info .warn}

## Other examples:

### epub
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
#  locate okularApplication_md.desktop
# shows okular is not installed
#
# and
#  xdg-mime query default application/epub+zip
#   calibre-gui.desktop
#
# The issue is that since `okularApplication_md.desktop` is not present xdg-open fallsback to a
# default application for opening epubs to fix this either change
# [Default Applications]
# application/epub+zip=calibre-ebook-viewer.desktop
# or

 xdg-mime default calibre-ebook-viewer.desktop application/epub+zip
```

### pdf
__pdf__{.ct}
``` sh
 xdg-mime query filetype ~/Downloads/pdf/awk_cheatsheets.pdf
  application/pdf
 xdg-mime query default application/pdf
  wine-extension-pdf.desktop

# looking at ~/.config/mimeapps.list
# [Added Associations]
# application/pdf=org.pwmt.zathura-pdf-poppler.desktop;org.gnome.Evince.desktop;zathura-pdf-poppler.desktop;evince.desktop;okularApplication_pdf.desktop;
# [Default Applications]
# application/pdf=zathura-pdf-poppler.desktop
 xdg-mime default zathura-pdf-poppler.desktop application/pdf
 xdg-mime query default application/pdf
  wine-extension-pdf.desktop
```
This is apparantly an **ERROR**{.red}, since we manually set the default mime to `zathura-pdf-poppler.desktop`

**Investigation:**
``` sh
# To see trace logs use the following command:
 sh -x /usr/bin/xdg-mime query default application/pdf
```

1. `zathura-pdf-poppler.desktop` was not correct and trace showed that since it fails it tries to fallback to something else
2. `wine-extension-pdf.desktop` was comming from `~/.local/share/applications/mimeinfo.cache` who has maintained that file is still unknown.
3. Removing that row from that file caused a fallback to `calibre-gui.desktop` and that was comming from `/usr/local/share/applications/mimeinfo.cache`
4. These files can be updated by `update-desktop-database` command but they should be manually proned
5. Manually fixing again:
``` sh
 locate zathura-pdf-poppler.desktop
  /usr/share/app-install/desktop/zathura:zathura-pdf-poppler.desktop
  /usr/share/applications/org.pwmt.zathura-pdf-poppler.desktop

# Apparantly that desktopfile didn't exists at all

 xdg-mime default org.pwmt.zathura-pdf-poppler.desktop application/pdf
 xdg-mime query default application/pdf
  org.pwmt.zathura-pdf-poppler.desktop
```
__Apparantly there are other places that `xdg-mime` uses for fallback such as:<br>`~/.local/share/applications/mimeinfo.cache`<br>`/usr/local/share/applications/mimeinfo.cache`<br>These files are updated automatically by `sudo update-desktop-database`<br>The best way to findout about where an association is comming from is by running `sh -x /usr/bin/xdg-mime query default application/pdf`__{.note .red}

### text

__pdf__{.ct}
``` sh
 xdg-mime query filetype ~/Downloads/citation-6737405.txt
  text/plain

 xdg-mime query default text/plain
  calibre-gui.desktop

 xdg-mime default code.desktop text/plain

 xdg-mime query default text/plain
code.desktop
```
# Question:
Do we have a graphical MIME editor?



* * *
Creation date: _2019-06-02_

[ABMTAA]: https://specifications.freedesktop.org/mime-apps-spec/mime-apps-spec-1.0.1.html