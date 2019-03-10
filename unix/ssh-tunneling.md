_Written by: Reza Shams Amiri_
# SSH Tunneling

If you are behind a firewall and you want to connect to a server through a gateway you can use the following:

```
vim ~/.ssh/config
```

__~/.ssh/config__{.ct}
``` sh
HOST LNAX
   HostName <protectedhost>.example.com
   User     <youruser>
   ProxyCommand ssh <youruser>@<gateway>.example.com -W %h:%p
```

then you can easily `ssh` to the protected host by issuing:
``` sh
ssh LNAX
```

## Port forwarding while tunneling
If you want to connect to a server which is only available through `<protectedhost>`. You can do the following:

``` sh
ssh -f -N -M -S /tmp/ssh_tunnel_%h.sock -o ExitOnForwardFailure=yes -L 1357:imap.example.com:993 LNAX
```

The above code will forward any request to `localhost:1357` to `imap.example.com:993` through `LNAX` tunnel that we set up in the previous seciotn. 
1. The `-L` flag stands for: local port forwarding
1. The `-N` flag stands for: do not execute remote commmand and just forward the port
1. The `-f` flag stands for: Requests ssh to go to background just before command execution
1. The `-M` flag stands for: Places the ssh client into “master” mode for connection sharing
1. The `-S` flag stands for:  Specifies the location of a control socket for connection sharing

References:
1. [ssh tunneling - How do I know if my ssh tunnel is created successfully? - Stack Exchange][STHDIKIMSTICSULSE]
2. [An SSH tunnel via multiple hops - Super User][ASTVMHSU]



* * *
Creation date: _2019-03-09_

[STHDIKIMSTICSULSE]: https://unix.stackexchange.com/a/29949/114816
[ASTVMHSU]: https://superuser.com/a/170592/285113