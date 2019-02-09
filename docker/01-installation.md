_Written by: Reza Shams Amiri_
# 01 installation


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

* * *
Creation date: _2019-02-09_
