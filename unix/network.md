_Written by: Reza Shams Amiri_
# Network

## [ngrep – Network grep][1GOSTAO2N]
``` sh
sudo ngrep -l -q -d eth0 "^GET |^POST " tcp and port 80
```
## mtr – Traceroute+ping in a single network diagnostic tool
![mtr][TNE]

## netcat – TCP/IP swiss army knife

[Share file through port 8040][SFTH8P]
```sh
sudo nc -v -l 8040 < ~/.zshrc
```

[Broadcast your shell thru ports 5000, 5001, 5002 ...][BYSTP555UST]

```sh
script -qf | tee >(nc -kl 5000) >(nc -kl 5001) >(nc -kl 5002)
```

* * *
Creation date: _2019-02-12_

[1GOSTAO2N]: https://www.cyberciti.biz/open-source/best-terminal-applications-for-linux-unix-macosx/
[TNE]: https://www.cyberciti.biz/media/new/cms/2012/12/mtr.png
[SFTH8P]: https://www.commandlinefu.com/commands/view/870/sharing-file-through-http-80-port
[BYSTP555UST]: https://www.commandlinefu.com/commands/view/6788/broadcast-your-shell-thru-ports-5000-5001-5002-...