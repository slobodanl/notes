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
2. Current user should be a member of `libvirt`
3. Proxy issues:
    Make sure that you remove proxies otherwise you will get problems like this:
    ``` sh
    Downloading Resources...
    Progress: |====================>| 100.0%
    Setting State...
    Creating the VM...
    Starting the VM...
    Fetching VM Address...
    Waiting for the VM...
    FAILED
    ```
    So do the following before you do `cf dev start`:
    ``` sh
    http_proxy= 
    https_proxy=
    HTTP_PROXY= 
    HTTPS_PROXY=
    ```
    and you should see:
    ``` sh
    Downloading Resources...
    Progress: |====================>| 100.0%
    Setting State...
    Creating the VM...
    Starting the VM...
    Fetching VM Address...
    Waiting for the VM...
    Deploying the BOSH Director...
    Deploying CF...
      Done (10m33s)

          ██████╗███████╗██████╗ ███████╗██╗   ██╗
         ██╔════╝██╔════╝██╔══██╗██╔════╝██║   ██║
         ██║     █████╗  ██║  ██║█████╗  ██║   ██║
         ██║     ██╔══╝  ██║  ██║██╔══╝  ╚██╗ ██╔╝
         ╚██████╗██║     ██████╔╝███████╗ ╚████╔╝
          ╚═════╝╚═╝     ╚═════╝ ╚══════╝  ╚═══╝
                     is now running!

        To begin using CF Dev, please run:
            cf login -a https://api.dev.cfdev.sh --skip-ssl-validation

        Admin user => Email: admin / Password: admin
        Regular user => Email: user / Password: pass

        To deploy a particular service, please run:
            cf dev deploy-service <service-name> [Available services: mysql]
    ```
## Deploy the app
1. Login to PCF Dev:
    ``` sh
    https_proxy=
    http_proxy=
    cf login -a https://api.dev.cfdev.sh --skip-ssl-validation
    
    ```
2. Get the sample app:
    ``` sh
    git clone https://github.com/cloudfoundry-samples/spring-music
    cd ./spring-music
    ```
3. Deploy `spring-music` to the vm, for proxy stuff look at [this page][UPDBAPPD]:
    ``` sh
    export NO_PROXY=.dev.cfdev.sh,dev.cfdev.sh,$NO_PROXY
    cf set-env spring-music HTTPS_PROXY $HTTPS_PROXY

    cf push --hostname spring-music        
    ```
    You should get the following output [output.txt](/img/cloud-foundary-pcf/output.txt).
    Then just browse to: [http://spring-music-chipper-civet.dev.cfdev.sh/][HSMCCDCS]
## CF Commands
``` sh
cf plugins

cf dev start/stop

```

# References:

* * *
Creation date: _2019-06-14_

[GCCTOCLCFCF]: https://github.com/cloudfoundry/cli#downloads
[DPDPN]: https://network.pivotal.io/products/pcfdev
[GCSSMASAFUDSOCFWSF]: https://github.com/cloudfoundry-samples/spring-music
[HTIACKOU10LS]: https://www.linuxtechi.com/install-configure-kvm-ubuntu-18-04-server/
[UPDBAPPD]: https://docs.pivotal.io/pcf-dev/proxy.html
[HSMCCDCS]: http://spring-music-chipper-civet.dev.cfdev.sh/