# Python-Installation-Problems.Md                                               

##  `s pip install pygobject --upgrade`                                          
``` bash                                                                          
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

