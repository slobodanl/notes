_Written by: Reza Shams Amiri_
# Configuring k8s coredns

Determine the current cluster DNS provider. In the following example, KubeDNS is the current cluster DNS provider.
``` sh
kubectl cluster-info
```

_Deploy dnsutils_{.ct}
``` sh
kubectl apply -f https://k8s.io/examples/admin/dns/dnsutils.yaml

kubectl exec -ti dnsutils -- nslookup example.private-org.com
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

kubectl exec -n kube-system coredns-980047985-g2748 -- kill -SIGUSR1 1

for p in $(kubectl get pods --namespace=kube-system -l k8s-app=kube-dns -o name); do kubectl exec -n kube-system $p -- kill -SIGUSR1 1 ; done
```

## References
1. [Debugging DNS Resolution - Kubernetes](https://kubernetes.io/docs/tasks/administer-cluster/dns-debugging-resolution/)
2. [DNS for Services and Pods - Kubernetes][DFSAPK]

* * *
Creation date: _2020-01-22_

[DFSAPK]: https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/
