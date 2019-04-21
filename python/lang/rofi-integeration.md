_Written by: Reza Shams Amiri_
# Rofi integeration using `sh` (See also [subprocess][S])

## Installation
``` python
s -H pip install sh
# for python 2
sudo -H python2 -m pip install sh
```
## Important considerations:
``` python
#!/usr/bin/python3
import sh
rofi = sh.rofi.bake('-dmenu', '-sep', '\n')
git = sh.git.bake('--no-pager')

revs = git.log('--no-color', "--format=format:%h %s", "build.sh")
print(rofi(_in=revs.stdout))
# Either the above or the following
# print(rofi(revs))
```
**Please make note that if you use **`stdout`** or a `String` for input, it's mandatory to use `_in=`. If you are using the instance of `RunningCommand` you can use both (in this case revs)**{.note .red}

### Dealing with deadlocks
If you are encountering deadlocks for no-reason one way to findout what's wrong is using `_timeout=<seconds>` within the `bake` or when running the command.
``` python
rofi = sh.rofi.bake('-dmenu', '-sep', "'\\n'", _timeout=1)
```
This will make sure if the process hanged your system after 1 second it will break and you are out of deadlock!

# Rofi integeration using python-rofi

## Install python-rofi ([][GBPRAPMTMSGWR])

``` sh
sudo -H pip install python-rofi

# Or for the latest version installation, use: 
sudo -H pip install git+https://github.com/bcbnz/python-rofi.git --upgrade

# for python 2
sudo -H /usr/bin/python2 -m pip install -U python-rofi
sudo -H /usr/bin/python2 -m pip install git+https://github.com/bcbnz/python-rofi.git --upgrade
```
**Use the github version (although they look like they are the same version), if you don't you can't use the `rofi_args`**{.note .red}
## Text Entry
``` python
from rofi import Rofi
r = Rofi()
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
``` sh
Adapta-Nokto, android_notification, Arc-Dark, Arc, arthur, blue, c64, DarkBlue, dmenu, glue_pro_blue, gruvbox-common, gruvbox-dark-hard, gruvbox-dark, gruvbox-dark-soft, gruvbox-light-hard, gruvbox-light, gruvbox-light-soft, Indego, lb, Monokai, paper-float, Paper, Pop-Dark, purple, sidebar, solarized_alternate, solarized
```
* * *
Creation date: _2019-02-23_

[GBPRAPMTMSGWR]: https://github.com/bcbnz/python-rofi
[S]: /python/lang/subprocess