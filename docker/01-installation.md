_Written by: Reza Shams Amiri_
# Install Docker CE
This is the briefed version of [Get Docker CE for Ubuntu | Docker Documentation][GDCFUDD]:
## Normal install
``` sh
# Install packages to allow apt to use a repository over HTTPS:
sudo apt-get install  apt-transport-https ca-certificates curl gnupg-agent software-properties-common

# Add Docker’s official GPG key:
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# Set up the stable repository
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
   
# Install Docker CE
sudo apt-get install docker-ce docker-ce-cli containerd.io

# Verify that Docker CE is installed
sudo docker run hello-world
```
## Convenience Install
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```
## Adding user the group
``` sh
sudo usermod -aG docker your-user
```
You should logout and logback to see the changes.

# Install Compose

Following is an example, check [GitHub][RDCG] repo for the latest version.
``` sh
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
## Uninstall compose
``` sh
sudo rm /usr/local/bin/docker-compose
```

* * *
Creation date: _2019-02-09_

[RDCG]: https://github.com/docker/compose/releases
[GDCFUDD]: https://docs.docker.com/install/linux/docker-ce/ubuntu/