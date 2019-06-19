# Python-Installation-Problems.Md                                               

## ImportError: No module named 'apt_pkg'
This problem can occur when upgrading to Ubuntu 19:

This solutions worked: 
[linux - python-dev installation error: ImportError: No module named apt_pkg - Stack Overflow][LPDIEINMNASO]

``` sh
sudo apt-get install python3-apt --reinstall
cd /usr/lib/python3/dist-packages
ll apt_pkg*
```
After reinstalling you should have at least a file simlar the following:
``` sh
-rw-r--r-- 1 root 347K Mar 11 12:49 apt_pkg.cpython-37m-x86_64-linux-gnu.so
```
python3-apt checks the highest python version, instead of the current python version in use. So I linked that file to other possible variations:
```
s ln -s apt_pkg.cpython-37m-x86_64-linux-gnu.so apt_pkg.cpython-34m-x86_64-linux-gnu.so
s ln -s apt_pkg.cpython-37m-x86_64-linux-gnu.so apt_pkg.cpython-35m-x86_64-linux-gnu.so
s ln -s apt_pkg.cpython-37m-x86_64-linux-gnu.so apt_pkg.cpython-36m-x86_64-linux-gnu.so
```
so `ls -la apt_pkg` shows:
``` sh
lrwxrwxrwx 1 root   39 May 30 00:52 apt_pkg.cpython-36m-x86_64-linux-gnu.so -> apt_pkg.cpython-37m-x86_64-linux-gnu.so
lrwxrwxrwx 1 root   39 May 30 00:51 apt_pkg.cpython-35m-x86_64-linux-gnu.so -> apt_pkg.cpython-37m-x86_64-linux-gnu.so
lrwxrwxrwx 1 root   39 May 30 00:51 apt_pkg.cpython-34m-x86_64-linux-gnu.so -> apt_pkg.cpython-37m-x86_64-linux-gnu.so
-rw-r--r-- 1 root 9.6K Mar 11 12:49 apt_pkg.pyi
-rw-r--r-- 1 root 347K Mar 11 12:49 apt_pkg.cpython-37m-x86_64-linux-gnu.so
```

##  Installing pygobject
``` bash                                                                          
sudo -H pip install pygobject --upgrade
sudo apt install libgirepository1.0-dev
sudo apt install python3-cairo-dev
```                                                                              

## Using email.Parser
``` bash
sudo -H easy_install --upgrade setuptools
sudo -H easy_install email
```
Also you should change the import from
``` python
import email.Parser
```
to
``` python
from email6.parser import Parser
```

# No module named 'apt_pkg' 
```
sudo apt install --reinstall --purge python_apt
cd /usr/lib/python3/dist-packages
ls -la apt_pkg.cpython-*


sudo ln -s apt_pkg.cpython-37m-x86_64-linux-gnu.so apt_pkg.cpython-34m-x86_64-linux-gnu.so
sudo ln -s apt_pkg.cpython-37m-x86_64-linux-gnu.so apt_pkg.cpython-36m-x86_64-linux-gnu.so
```

[LPDIEINMNASO]: https://stackoverflow.com/a/36232975/161312