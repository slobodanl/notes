_Written by: Reza Shams Amiri_
# xargs

## ls and replace .rasi

``` sh
ls /usr/share/rofi/themes X zsh -c 'V="{}";echo ${V//\.rasi/}'
# where X is alias for 
#   X='| xargs -I{}'
```
* * *
Creation date: _2019-02-23_
