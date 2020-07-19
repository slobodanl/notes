_Written by: Reza Shams Amiri_
# Install Persian font for telegram


1. [[Install Persian font][IPF]]
2. Add/edit the following file `~/.local/share/TelegramDesktop/tdata/fc-custom-1.conf`:
    _`~/.local/share/TelegramDesktop/tdata/fc-custom-1.conf`_{.ct}
    ``` xml
    <?xml version='1.0'?>
    <!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
    <fontconfig>
       <dir>/usr/share/fonts</dir>
       <dir>/usr/local/share/fonts</dir>
       <dir>~/.fonts</dir>
       <dir prefix="xdg">fonts</dir>
       <match target="pattern">
              <test qual="any" name="family">
                <string>sans serif</string>
              </test>
              <edit name="family" mode="assign" binding="same">
                <string>Vazir</string>
              </edit>
       </match>
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
1. Restart Telegram
1. If the above didn't work, use:
   ``` sh
   FONTCONFIG_FILE=~/.local/share/TelegramDesktop/tdata/fc-custom-1.conf /usr/bin/telegram-desktop
   ```
   and modify `/usr/share/applications/telegramdesktop.desktop`
   _/usr/share/applications/telegramdesktop.desktop_{.ct}
   ``` sh
   Exec=env FONTCONFIG_FILE=/home/existme/.local/share/TelegramDesktop/tdata/fc-custom-1.conf telegram-desktop -- %u
   ```
* * *
Creation date: _2020-01-03_

[IPF]: /fix/install-Persian-or-Farsi-font