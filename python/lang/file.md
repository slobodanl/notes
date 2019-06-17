_Written by: Reza Shams Amiri_

# python files

## [open][BIFP373D]

| Character | Meaning |
| --------- | ------- |
| `'r'` | open for reading (default) |
| `'w'` | open for writing, truncating the file first |
| `'x'` | open for exclusive creation, failing if the file already exists |
| `'a'` | open for writing, appending to the end of the file if it exists |
| `'b'` | binary mode |
| `'t'` | text mode (default) |
| `'+'` | open a disk file for updating (reading and writing) |

For binary read-write access, the mode `w+b` opens and truncates the file to 0 bytes. `r+b` opens the file without truncation.
## file - if exists
``` python
agenda_path = os.path.expanduser('~/agenda.dat')
if not os.path.exists(agenda_path):
   print("file doesn't exists")
```
## file - create
_open/create file if doesn't exists_{.ct}
``` sh
file = open('myfile.dat', 'w+')
```
## file - read

_Read the content of a file_{.ct}
``` python
f = open("demofile.txt", "r")
print(f.read())
```

_Read first 5 bytes_{.ct}
``` python
f = open("demofile.txt", "r")
print(f.read(5))
```

## [expanduser][OPCPMP373D]
If you want to use `~` in the file name you need to use `expanduser`:
``` python
import  os

# with will automatically close your file
with open(os.path.expanduser("~/.boto"),"w") as f:
    f.write("test") # write to f
```

## [glob][GUSPPEP373D]
``` python
import glob
>>> glob.glob('~/.zshrc')
>>> glob.glob('**/*.txt', recursive=True)
['2.txt', 'sub/3.txt']
>>> glob.glob('./**/', recursive=True)
['./', './sub/']
```

- - -

Creation date: _2019-06-17_

[GUSPPEP373D]: https://docs.python.org/3/library/glob.html#glob.glob
[BIFP373D]: https://docs.python.org/3/library/functions.html#open
[OPCPMP373D]: https://docs.python.org/3/library/os.path.html#os.path.expanduser