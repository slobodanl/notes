_Written by: Reza Shams Amiri_
# Install Persian font

1. Download Vazir font from here: [Releases · rastikerdar/vazir-font · GitHub][RRVFG]
1. Extract it into `~/.fonts/Vazir`
1. Add/or edit the file `~/.fonts.conf` with the following content:
    _`~/.fonts.conf`_{.ct}
    ``` xml
    <?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
    <fontconfig>
       <match target="pattern">
          <test name="family" qual="any">
             <string>sans serif</string>
          </test>
          <edit mode="assign" binding="same" name="family">
             <string>Vazir</string>
          </edit>
       </match>
       <dir>/usr/share/fonts</dir>
       <dir>/usr/local/share/fonts</dir>
       <dir>~/.fonts</dir>
       <match target="font">
          <edit mode="assign" name="antialias">
              <bool>true</bool>
          </edit>
          <edit mode="assign" name="embeddedbitmap">
              <bool>false</bool>
          </edit>
          <edit mode="assign" name="hinting">
              <bool>true</bool>
          </edit>
          <edit mode="assign" name="hintstyle">
              <const>hintslight</const>
          </edit>
          <edit mode="assign" name="lcdfilter">
              <const>lcddefault</const>
          </edit>
          <edit mode="assign" name="rgba">
              <const>rgb</const>
          </edit>
       </match>
    </fontconfig>
    ```
1. Run `fc-cache -frv`

* * *
Creation date: _2020-01-03_

[RRVFG]: https://github.com/rastikerdar/vazir-font/releases