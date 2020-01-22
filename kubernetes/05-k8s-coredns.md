_Written by: Reza Shams Amiri_
# Configuring k8s coredns


_Deploy dnsutils_{.ct}
``` sh
kubectl apply -f https://k8s.io/examples/admin/dns/dnsutils.yaml
```

_Get pods for coredns_{.ct}
```
kubectl get pods --namespace=kube-system -l k8s-app=kube-dns
```

_see the logs of coredns_{.ct}
```
for p in $(kubectl get pods --namespace=kube-system -l k8s-app=kube-dns -o name); do kubectl logs --namespace=kube-system $p; done
```

_edit coredns parameters_{.ct}
```
kubectl edit configmap -n kube-system coredns
```

* * *
Creation date: _2020-01-22_
