_Written by: Reza Shams Amiri_
# Getting started

1. Install from [Linux | minikube][LM]
2. check kvm2 is supported: `egrep -q 'vmx|svm' /proc/cpuinfo && echo yes || echo no`
3. validate kvm: `virt-host-validate`
4. `minikube start --vm-driver=kvm2`
    1. Make sure the `NO_PROXY` (captial is important) include minikube IP (refer to [HTTP Proxies | minikube][HPM])

* * *
Creation date: _2019-12-20_

[LM]: https://minikube.sigs.k8s.io/docs/start/linux/
[HPM]: https://minikube.sigs.k8s.io/docs/reference/networking/proxy/