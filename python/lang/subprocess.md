_Written by: Reza Shams Amiri_
# subprocess

## Install [Executor][GXPEPFSW]

``` sh
s -H pip install executor
```
ﯙ Github page: [https://github.com/xolox/python-executor][GXPEPFSW]   
 Documentation: [https://executor.readthedocs.io/en/latest/readme.html][EPFSWE23D]   


## Example: running and piping:
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


* * *
Creation date: _2019-02-23_


[GXPEPFSW]: https://github.com/xolox/python-executor
[EPFSWE23D]: https://executor.readthedocs.io/en/latest/readme.html