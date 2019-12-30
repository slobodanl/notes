_Written by: Reza Shams Amiri_
# K8s Getting started

1. Install from [Linux | minikube][LM]
2. Check kvm2 is supported: `egrep -q 'vmx|svm' /proc/cpuinfo && echo yes || echo no`
3. Validate kvm: `virt-host-validate`
4. `minikube start --vm-driver=kvm2`
    1. Make sure the `NO_PROXY` (captial is important) include minikube IP (refer to [HTTP Proxies | minikube][HPM])
5. `minikube config set vm-driver kvm2`
6. Install `kubectl` from [Install and Set Up kubectl - Kubernetes][IASUKK]

# Minikube config
1. kubectl config:
   ``` sh
   kubectl config use-context minikube
   ```
1. docker config:
   ``` sh
   eval $(minikube docker-env)
   # build docker images afterwards
   ```
   If `docker ps` fails with `proxy: unknown scheme: socks` makesure to run:
   ``` sh
   unset ALL_PROXY
   unset all_proxy
   ```

1. Minikube memory config:
   ``` sh
   minikube config set memory 8192     # in megabytes
   minikube delete
   minikube start                      # The ip of minikube might change
   ```
# Stoping all the services

``` sh
 minikube stop
```
Sometimes stopping minikube is not enough and there might be residual clusters remaining which could consume a lot of resources. To kill them, the `virsh` command can be used:

_Going into `virsh` and killing the cluster intractively_{.ct}
``` sh
 virsh -c qemu:///system

virsh # list
Id   Name       State
--------------------------
 4    cluster2   running

virsh # destroy cluster2  
```
or
_killing domains directly_{.ct}
``` sh
 virsh -c qemu:///system list
 virsh -c qemu:///system virsh -c qemu:///system list
``` 
# Deploying app using minikube

_Always make sure to run `eval $(minikube docker-env)` and subsequently a `docker ps` which should return lots of runnning containers. Otherwise your custom build docker images will never be pulled._{.note .red}
1. deploy the image
    ``` sh
    kubectl create deployment ghost --image=ghost:latest
    ```
2. expose
    ``` sh
    kubectl expose deployments ghost --port=2368 --type=NodePort
    ```
    After running this command you can see what port the application will use to expose itslef in minikube by issuing:
    ```
    kubectl describe services ghost | grep NodePort:
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

Then run:
``` sh
kubectl get pods,rs,deployments,services
```
The port(32468) is comming from `kubectl describe services ghost`  `NodePort`
The ip(192.168.39.44) is comming from `minikube ip`

## Manage the minikube
1. **Delete** a deployment and its service
    ``` sh
    kubectl delete deployment hello-nginx
    kubectl delete service hello-nginx
    ```
1. Checking the **logs**
   ``` sh
   kubectl logs -f jenkins-7f6444449b-hdvv9
   kubectl logs -f curity-master-app-5d799b59df-86x9g
   ```
1. **Login** to minikube
   1. Using minikube itself:
      ``` sh
      minikube ssh
      ```
   3. Using normal ssh:
      ``` sh
      ssh -i ~/.minikube/machines/minikube/id_rsa docker@$(minikube ip)
      ```      
1. **Login** to a container
   1. Login as the default user:
      ``` sh
      kubectl exec -it jenkins-7f6444449b-hdvv9 -- /bin/bash
      ```
   1. Login as the root user:
      Use a script named [`shell-into-pod-as-root`][MSIPARADEMG] ([ref][STUFFDEIKEI3KKG])
      ``` sh
      ,shell-into-pod-as-root jenkins-7f6444449b-hdvv9
      ```
## Networking
1. **Local Tunnel**
    In minikube there is a magic command:
    ``` sh
    minikube tunnel
    ```
    when you run this commmand the cluster IPs like the ones you get through `kubectl get service` are reachable locally:
    ``` sh
    kubectl get service --watch

    NAME                          TYPE           CLUSTER-IP      EXTERNAL-IP     PORT(S)                         AGE
    curity-admin-service          LoadBalancer   10.96.102.211   192.168.39.48   6749:30614/TCP,6789:30575/TCP   31h
    curity-runtime-loadbalancer   LoadBalancer   10.96.120.19    192.168.39.44   8445:32153/TCP                  81m
    curity-runtime-service        NodePort       10.96.242.99    <none>          6789:32240/TCP,2024:31809/TCP   22m
    hello-minikube                NodePort       10.96.237.62    <none>          8080:30219/TCP                  5d15h
    kubernetes                    ClusterIP      10.96.0.1       <none>          443/TCP                         5d15h
    curity-admin-service          LoadBalancer   10.96.102.211   10.96.102.211,192.168.39.48   6749:30614/TCP,6789:30575/TCP   31h
    curity-runtime-loadbalancer   LoadBalancer   10.96.120.19    10.96.120.19,192.168.39.44    8445:32153/TCP                  85m
    ```
    Which means that now you can browse `10.96.102.211`!

References:
1. [kubectl for Docker Users - Kubernetes][KFDUK]
2. [Configure Access to Multiple Clusters - Kubernetes][CATMCK]
3. [Getting Started with Kubernetes Ingress-Nginx on Minikube][GSWKINOM]
4. [kubectl Cheat Sheet - Kubernetes][KCSK]
5. [Docker & Kubernetes : NodePort vs LoadBalancer vs Ingress - 2019][DKNVLVI2]

* * *
Creation date: _2019-12-20_

[LM]: https://minikube.sigs.k8s.io/docs/start/linux/
[HPM]: https://minikube.sigs.k8s.io/docs/reference/networking/proxy/
[IASUKK]: https://kubernetes.io/docs/tasks/tools/install-kubectl/
[STUFFDEIKEI3KKG]: https://github.com/kubernetes/kubernetes/issues/30656#issuecomment-476872519
[MSIPARADEMG]: https://github.com/existme/MyDotFiles/blob/develop/extras/bin/%2Cshell-into-pod-as-root
[KFDUK]: https://kubernetes.io/docs/reference/kubectl/docker-cli-to-kubectl/
[CATMCK]: https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/
[GSWKINOM]: https://medium.com/@awkwardferny/getting-started-with-kubernetes-ingress-nginx-on-minikube-d75e58f52b6c
[KCSK]: https://kubernetes.io/docs/reference/kubectl/cheatsheet/
[DKNVLVI2]: https://www.bogotobogo.com/DevOps/Docker/Docker_Kubernetes_NodePort_vs_LoadBalancer_vs_Ingress.php