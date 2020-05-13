_Written by: Reza Shams Amiri_
# shutter

How to Install Shutter Screenshot Tool in Ubuntu 19.04

_updated ppa which has the latest shutter package and libgoo-canvas-perl_{.ct}
``` sh
sudo add-apt-repository ppa:linuxuprising/shutter
sudo apt install --install-recommends --install-suggests shutter
```

In some distros you need to install the following packages for edit button to be enabled in shutter:

_libraries needed for enabling edit button inside the app_{.ct}
``` sh
sudo apt libgoocanvas3 libgoocanvas-common libgoo-canvas-perl
sudo apt install gnome-web-photo 
sudo apt install libimage-exif-perl libimage-exiftool-perl 
```

_if you are behind a proxy use `sudo add-apt-repository -E ppa:...` instead_{.info .warn}

_shutter is a simple perl program, you can view the source by just editing the file with `vim /usr/bin/shutter`_{.info}

References:
1. [New Shutter PPA For Ubuntu 20.04, 19.10, 19.04 And 18.04 | Linux Mint 19.x - Linux Uprising Blog][NSPFU201110A10LM1XLUB]

* * *
Creation date: _2019-06-14_


[NSPFU201110A10LM1XLUB]: https://www.linuxuprising.com/2018/10/shutter-removed-from-ubuntu-1810-and.html