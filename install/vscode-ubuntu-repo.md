_Written by: Reza Shams Amiri_
# VSCode Ubuntu Repo 

VSCode can be installed from Microsoft repo directly by following these instructions: ([REF][RVSCOL])

``` sh
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
sudo install -o root -g root -m 644 microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install code # or code-insiders
```

* * *
Creation date: _2019-02-25_

[RVSCOL]: https://code.visualstudio.com/docs/setup/linux#_installation