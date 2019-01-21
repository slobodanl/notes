_Written by: Reza Shams Amiri_

# Install npm as another user

Assuming that your service user (you can't login with it) is 'svcids':

``` sh
export USER=svcids
export HOME=/home/$USER
export PROXY=http://yourproxy.com:3128
sudo npm config set proxy $PROXY
sudo npm config set https-proxy $PROXY
sudo ln -s /usr/bin/nodejs /usr/bin/node

sudo -u svcids sh -c 'npm config set proxy $PROXY'
sudo -u svcids sh -c 'npm config set https-proxy $PROXY'
sudo -u svcids sh -c 'npm config set registry "https://registry.npmjs.org"'

sudo -u svcids sh -c 'npm install'
```

* * *
Creation date: _2019-01-21_
