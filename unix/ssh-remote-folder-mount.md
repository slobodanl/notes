_Written by: Reza Shams Amiri_
# Mounting a remote folder into a local folder

Mount a remote folder into the local host:

_Mount a remote folder into a local folder_{.ct}
``` sh
sudo apt install sshfs

mkdir -p ~/git/remote-example-kube

sshfs rezasa@LNAX:~/git/example-kube ~/git/remote-example-kube
```

* * *
Creation date: _2019-12-23_
