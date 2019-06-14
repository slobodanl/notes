_Written by: Reza Shams Amiri_
# Cloud Foundary PCF

## Installation
PCF CLI [page][GCCTOCLCFCF]

_Debian/Ubuntu installation_{.ct}
``` sh
# ...first add the Cloud Foundry Foundation public key and package repository to your system
wget -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | sudo apt-key add -
echo "deb https://packages.cloudfoundry.org/debian stable main" | sudo tee /etc/apt/sources.list.d/cloudfoundry-cli.list
# ...then, update your local package index, then finally install the cf CLI
sudo apt-get update
sudo apt-get install cf-cli
```


# References:

* * *
Creation date: _2019-06-14_

[GCCTOCLCFCF]: https://github.com/cloudfoundry/cli#downloads