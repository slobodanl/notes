_Written by: Reza Shams Amiri_
# Open with... mime-types

`xdg-mime` uses `mimeapps.list` to determine the default application to use.
Separate `mimeapps.list` files exist to handle user-specific, system-specific and distribution-specific requirements. Their lookup order can be found here: [Association between MIME types and applications][ABMTAA]

``` sh
xdg-mime query default inode/directory
```

* * *
Creation date: _2019-06-02_

[ABMTAA]: https://specifications.freedesktop.org/mime-apps-spec/mime-apps-spec-1.0.1.html