_Written by: Reza Shams Amiri_
# Getting started

1. Install from [Linux | minikube][LM]
2. Check kvm2 is supported: `egrep -q 'vmx|svm' /proc/cpuinfo && echo yes || echo no`
3. Validate kvm: `virt-host-validate`
4. `minikube start --vm-driver=kvm2`
    1. Make sure the `NO_PROXY` (captial is important) include minikube IP (refer to [HTTP Proxies | minikube][HPM])
5. `minikube config set vm-driver kvm2`
6. Install `kubectl` from [Install and Set Up kubectl - Kubernetes][IASUKK]

# Deploying app using minikube

1. deploy the image
    ``` sh
    kubectl create deployment ghost --image=ghost:latest
    ```
2. expose
    ``` sh
    kubectl expose deployments ghost --port=2368 --type=NodePort
    ```
3. run
    ``` sh
    minikube service ghost

    |-----------|-------|-------------|----------------------------|
    | NAMESPACE | NAME  | TARGET PORT |            URL             |
    |-----------|-------|-------------|----------------------------|
    | default   | ghost |             | http://192.168.39.44:32468 |
    |-----------|-------|-------------|----------------------------|
    ```
    Then manually open the url in browser to access the service.


* * *
Creation date: _2019-12-20_

[LM]: https://minikube.sigs.k8s.io/docs/start/linux/
[HPM]: https://minikube.sigs.k8s.io/docs/reference/networking/proxy/
[IASUKK]: https://kubernetes.io/docs/tasks/tools/install-kubectl/