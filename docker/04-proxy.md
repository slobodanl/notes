_Written by: Reza Shams Amiri_

# 04 proxy

1. Add following configuration in **/etc/sysconfig/docker** file:
    ```
    export HTTP_PROXY="http://USERNAME:PASSWORD@[your.proxy.server]:[port]"
    export HTTPS_PROXY="https://USERNAME:PASSWORD@[your.proxy.server]:[port]"
    ```
1. Restart the Docker daemon after setting up the proxy.</span>
    ```
    service docker restart
    ```

***
Creation date: _2019-12-12_