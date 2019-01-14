_Written by: Reza Shams Amiri_
# Ubuntu Release Upgrade

See the following page [How To Upgrade Ubuntu To 18.10 Cosmic Cuttlefish - LinuxConfig.org][HTUUT11CCLO]

Briefly, this is what you need to do:

``` sh
sudo apt update 
sudo apt upgrade
sudo apt dist-upgrade
sudo apt autoremove


sudo vim /etc/update-manager/release-upgrades # Set "Prompt=normal" to get new upgrades
sudo do-release-upgrade 
# If upgrading before the official 18.10 release date or while the upgrade from 18.04 is still not available use -d to perform upgrade:
# sudo do-release-upgrade -d
```

* * *
Creation date: _2019-01-14_

[HTUUT11CCLO]: https://linuxconfig.org/how-to-upgrade-ubuntu-to-18-10-cosmic-cuttlefish