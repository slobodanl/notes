_Written by: Reza Shams Amiri_
# Install Persian font for telegram


1. [Install Persian font][IPF]
2. Add/edit the following file `~/.local/share/TelegramDesktop/tdata/fc-custom-1.conf`:
    ``` xml
    <?xml version='1.0'?>
    <!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
    <fontconfig>
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

* * *
Creation date: _2020-01-03_

[IPF]: /fix/install-farsi-font