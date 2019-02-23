_Written by: Reza Shams Amiri_
# subprocess

## Executor

### Install [Executor][GXPEPFSW]
``` sh
s -H pip install executor
```
ﯙ Github page: [https://github.com/xolox/python-executor][GXPEPFSW]   
 Documentation: [https://executor.readthedocs.io/en/latest/readme.html][EPFSWE23D]   


### Example: running and piping:
This examples reads files using `ls` and pipes the markdown files to `rofi`

_subprocess with executor ex01_{.ct}
``` python
import re
from executor import execute

cmd = execute('cd ~/notes;ls', capture=True)

rfiles = re.finditer(r'(.*)\n', cmd)
files = []
for file in rfiles:
    filename = file.group(1)
    if filename.endswith('.md'):
        files.append(filename)

pipeIn = "|".join(files)
res = execute("rofi -dmenu -sep '|' -p 'how are you' -theme Paper", input=pipeIn, check=False, capture=True)
print(res)
```

## More examples

_Providing input_{.ct}
``` python
execute('tr a-z A-Z', input='Hello world from Python!\n')
```

_Getting the output_{.ct}
``` python
execute('hostname', capture=True)
```

_Run command as sudo_{.ct}
``` python
execute('echo test > /etc/hostname', sudo=True)
```

## sh
### Install [sh][GASPPL]
``` sh
s -H pip install executor
```
ﯙ Github page: [https://github.com/amoffat/sh][GASPPL]
 Documentation: [http://amoffat.github.io/sh][111S111D]

### Example: running and piping:
_tail `/var/log/syslog` and pass it to tr_{.ct}
``` python
import sh
with sh.contrib.sudo:
    for line in sh.tr(sh.tail("-f", "/var/log/syslog", _piped=True, ), "[:upper:]", "[:lower:]", _iter=True):
        print(line)
```
### rofi piping
_rofi piping_{.ct}
``` python
import logging
from sh import rofi, find, ErrorReturnCode
logging.basicConfig(level=logging.INFO)

try:
    # note that -sep and '\n' are separated that's because it's too sensitive
    res = rofi(find("/home/existme/git/gollum", ".", _piped=True), "-dmenu", "-sep", '\n')
    print(res)
    print(res.exit_code)
except ErrorReturnCode:
    print("unknown error/canceled")
```


* * *
Creation date: _2019-02-23_


[GXPEPFSW]: https://github.com/xolox/python-executor
[EPFSWE23D]: https://executor.readthedocs.io/en/latest/readme.html
[GASPPL]: https://github.com/amoffat/sh
[111S111D]: http://amoffat.github.io/sh