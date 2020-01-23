_Written by: Reza Shams Amiri_
# Cheat sheet

## Quickly installing example pods
All example pods could be found here: 
[https://github.com/kubernetes/website/tree/master/content/en/examples][WCEEAMKWG]and you can install them for example by issuing:
``` sh
kubectl apply -f https://k8s.io/examples/application/shell-demo.yaml
```` 
and login-in to it using 
``` sh
kubectl exec -it shell-demo -- /bin/bash
```
### Usefull pods
1. [shell-demo][shell-demo]: A bash prompt based on nginx
2. [dnsutils][TNE]: dnsutils including nslookup, dig, etc.
2. [busybox][busybox]: busybox

### Usefull debian installation scripts
``` sh
apt-cache search mysql-client

apt install default-mysql-client    # mysql client
apt install inetutils-ping          # ping

```

* * *
Creation date: _2020-01-23_

[WCEEAMKWG]: https://github.com/kubernetes/website/tree/master/content/en/examples
[shell-demo]: https://k8s.io/examples/application/shell-demo.yaml
[dnsutils]: https://k8s.io/examples/admin/dns/dnsutils.yaml
[busybox]: https://k8s.io/examples/admin/dns/busybox.yaml
[TNE]: https://k8s.io/examples/admin/dns/busybox.yaml