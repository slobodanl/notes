_Written by: Reza Shams Amiri_
# rofi integeration

## Install python-rofi ([][GBPRAPMTMSGWR])

``` sh
sudo -H pip install python-rofi

# Or for the latest version installation, use: 
sudo -H pip install git+https://github.com/bcbnz/python-rofi.git --upgrade
```

## Text Entry
``` python
from rofi import Rofi
name = r.text_entry('What is your name? ')
print(name)

# With message hints
r.text_entry('What are your goals for this year? ', message='Be <b>bold</b>!')

# If you need to escape a string to avoid it being mistaken for markup, use the Rofi.escape() class method:
msg = Rofi.escape('Format: <firstname> <lastname>')
r.text_entry('Enter your name: ', message=msg)
```

## Select an option
``` python
options = ['Red', 'Green', 'Blue', 'White', 'Silver', 'Black', 'Other']
index, key = r.select('What colour car do you drive?', options)
print(index) if key == 0 else print("canceled!")
```

## Status
``` python
r.status("I'm working on that...")
```
This is the only none blocking method, to close the status message:
``` python
r.close()
```

## Themes (requires to install latest version of rofi)
To use a separate theme, supply args (themes are located in `/usr/share/rofi/themes/`):

``` python
r = Rofi(rofi_args=['-theme', '/usr/share/rofi/themes/Monokai.rasi'])
r.status('Stuff is happening, please wait...')
```
Or just:
``` python
r.status('Stuff is happening, please wait...', rofi_args=['--theme', 'Monokai'])
```
Default installed themes are:
```
Adapta-Nokto, android_notification, Arc-Dark, Arc, arthur, blue, c64, DarkBlue, dmenu, glue_pro_blue, gruvbox-common, gruvbox-dark-hard, gruvbox-dark, gruvbox-dark-soft, gruvbox-light-hard, gruvbox-light, gruvbox-light-soft, Indego, lb, Monokai, paper-float, Paper, Pop-Dark, purple, sidebar, solarized_alternate, solarized
```
* * *
Creation date: _2019-02-23_

[GBPRAPMTMSGWR]: https://github.com/bcbnz/python-rofi