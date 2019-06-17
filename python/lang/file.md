_Written by: Reza Shams Amiri_

# python files

## [open](https://docs.python.org/3/library/functions.html#open)

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

_open/create file if doesn't exists_{.ct}
``` sh
file = open('myfile.dat', 'w+')
```

- - -

Creation date: _2019-06-17_