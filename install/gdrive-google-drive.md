_Written by: Reza Shams Amiri_
# gdrive google drive

## Install
``` sh
sudo add-apt-repository ppa:alessandro-strada/ppa
sudo apt-get update
sudo apt-get install google-drive-ocamlfuse
```
## [Authorize][AAGDOWG1]
``` sh
ﰲ google-drive-ocamlfuse
```
## Mount

1. [Automount][AAGDOWG2]
2. Normal mount:
    ``` sh
    ﰲ mkdir ~/gdrive
    ﰲ google-drive-ocamlfuse ~/gdrive
    ```
## [Configuration][CAGDOWG]
``` sh
ﰲ vim ~/.gdfuse/default/config
```


* * *
Creation date: _2019-06-03_

[AAGDOWG1]: https://github.com/astrada/google-drive-ocamlfuse/wiki/Authorization
[AAGDOWG2]: https://github.com/astrada/google-drive-ocamlfuse/wiki/Automounting
[CAGDOWG]: https://github.com/astrada/google-drive-ocamlfuse/wiki/Configuration