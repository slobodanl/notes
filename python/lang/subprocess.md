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
s -H pip install sh

# for python 2
sudo -H python2 -m pip install sh
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

### Showing information of the running commands
_information sample_{.ct}
``` python
#!/usr/bin/python3
import sh

rofi = sh.rofi.bake('-dmenu', '-sep', "'\\n'", _bg_exc=False)
git = sh.git.bake('--no-pager', )
res = rofi(_in=a.stdout)
print(res)
print(res.cmd)
print(res.call_args)
```
_output_{.ct}
``` python
[b'/usr/local/bin/rofi', b'-dmenu', b'-sep', b"'\\n'"]
{
	'fg': False, 
	'bg': False, 
	'bg_exc': False, 
	'with': False, 
	'in': b'989b7175 added docker images for running gollum\nd06daa2a bumped the version\nc0130d64 initial commit for Gollum custom template', 
	'out': None, 
	'err': None, 
	'err_to_out': None, 
	'in_bufsize': 0, 
	'out_bufsize': 1, 
	'err_bufsize': 1, 
	'internal_bufsize': 3145728, 
	'env': None, 
	'piped': None, 
	'iter': None, 
	'iter_noblock': None, 
	'ok_code': [
		0
	], 
	'cwd': None, 
	'long_sep': '=', 
	'long_prefix': '--', 
	'tty_in': False, 
	'tty_out': True, 
	'encoding': 'UTF-8', 
	'decode_errors': 'strict', 
	'timeout': None, 
	'timeout_signal': <Signals.SIGKILL: 9>, 
	'no_out': False, 
	'no_err': False, 
	'no_pipe': False, 
	'tee': None, 
	'done': None, 
	'tty_size': (20,80), 
	'truncate_exc': True, 
	'preexec_fn': None, 
	'uid': None, 
	'new_session': True, 
	'arg_preprocess': None, 
	'log_msg': None
}
```

### rofi piping ( also see [Rofi integeration using sh][RIUSSAS] )
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
_rofi cat_{.ct}
``` python
    from sh import rofi, find, cat, glob
    res = rofi(find('/home/existme/git/gollum/', '-name', '*.md'), "-dmenu", "-sep", '\n')
    # we should replace '\n' otherwise glob will fail to map and cat will fail too
    selected = res.replace('\n', '')
    print("[%s]" % selected)
    print("[%s]" % res.stdout)
    print(cat(glob(selected)))

```


* * *
Creation date: _2019-02-23_


[GXPEPFSW]: https://github.com/xolox/python-executor
[EPFSWE23D]: https://executor.readthedocs.io/en/latest/readme.html
[GASPPL]: https://github.com/amoffat/sh
[111S111D]: http://amoffat.github.io/sh
[RIUSSAS]: /python/lang/rofi-integeration