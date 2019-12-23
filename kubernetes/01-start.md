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
    After running this command you can see what port the application will use to expose itslef in minikube by issuing:
    ```
    kubectl describe services describe ghost | grep NodePort:
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
1. Delete a deployment and its service
    ``` sh
    kubectl delete deployment hello-nginx
    kubectl delete service hello-nginx
    ```
1. Checking the logs
   ``` sh
   kubectl logs -f jenkins-7f6444449b-hdvv9
   ```
1. Login to minikube
   1. Using minikube itself:
      ``` sh
      minikube ssh
      ```
   3. Using normal ssh:
      ``` sh
      ssh -i ~/.minikube/machines/minikube/id_rsa docker@$(minikube ip)
      ```      
2. Login to a container
   1. Login as the default user:
      ``` sh
      kubectl exec -it jenkins-7f6444449b-hdvv9 -- /bin/bash
      ```
   1. Login as the root user:
      Use a script named [`shell-into-pod-as-root`][MSIPARADEMG] ([ref][STUFFDEIKEI3KKG])
      ``` sh
      ,shell-into-pod-as-root jenkins-7f6444449b-hdvv9
      ```

* * *
Creation date: _2019-12-20_

[LM]: https://minikube.sigs.k8s.io/docs/start/linux/
[HPM]: https://minikube.sigs.k8s.io/docs/reference/networking/proxy/
[IASUKK]: https://kubernetes.io/docs/tasks/tools/install-kubectl/
[STUFFDEIKEI3KKG]: https://github.com/kubernetes/kubernetes/issues/30656#issuecomment-476872519
[MSIPARADEMG]: https://github.com/existme/MyDotFiles/blob/develop/extras/bin/%2Cshell-into-pod-as-root