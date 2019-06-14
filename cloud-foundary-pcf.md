_Written by: Reza Shams Amiri_
# Cloud Foundary PCF

## Installation
1. Install PCF CLI [Instruction page][GCCTOCLCFCF]
    _Debian/Ubuntu installation_{.ct}
    ``` sh
    # ...first add the Cloud Foundry Foundation public key and package repository to your system
    wget -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | sudo apt-key add -
    echo "deb https://packages.cloudfoundry.org/debian stable main" | sudo tee /etc/apt/sources.list.d/cloudfoundry-cli.list
    # ...then, update your local package index, then finally install the cf CLI
    sudo apt-get update
    sudo apt-get install cf-cli
    ```
1. Install **cfdev** plugin
    ``` sh
    cf install-plugin cfdev
    ```
1. Download latest version of PCF Dev from [Pivotal Network][DPDPN]
1. Start PCF Dev:
    ``` sh
    cf dev start -f <filepath/VERSION.tgz>
    ```
### ISSUES:
1. [How to Install and Configure KVM on Ubuntu 18.04 LTS Server][HTIACKOU10LS]
    1. `libvirtbin` doesn't exists anymore instead use `libvirt-daemon-system` and `libvirt-clients`
2. Proxy issues:
    ``` sh
    export no_proxy="localhost,127.0.0.1,localaddress,.domain.com,192.168.0.*"
    ```
    and in `/opt/jdk1.8.0_144/jre/lib/net.properties`
    ``` sh
    http.nonProxyHosts=localhost|127.*|[::1]|0.0.0.0|192.168.0.* 
    ```
## CF Commands
``` sh
cf plugins

cf dev start/stop

```

## Deploying a sample app:
1. Clone sample app: [spring-music][GCSSMASAFUDSOCFWSF]
1. cd ./spring-music
# References:

* * *
Creation date: _2019-06-14_

[GCCTOCLCFCF]: https://github.com/cloudfoundry/cli#downloads
[DPDPN]: https://network.pivotal.io/products/pcfdev
[GCSSMASAFUDSOCFWSF]: https://github.com/cloudfoundry-samples/spring-music
[HTIACKOU10LS]: https://www.linuxtechi.com/install-configure-kvm-ubuntu-18-04-server/