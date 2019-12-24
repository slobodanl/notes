_Written by: Reza Shams Amiri_
# 03 K8s file templates

_Deployment Sample_{.ct}
``` yml
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: hello-node-app
  name: hello-node-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: hello-node-app
  template:
    metadata:
      labels:
        app: hello-node-app
    spec:
      containers:
      - image: reza/node:latest
        name: hello-node-app
        ports:
        - containerPort: 8080
        imagePullPolicy: Never
```
_Node Service Skeleton_{.ct}
``` yml
kind: Service
apiVersion: v1
metadata:
  name: hello-node-service
  namespace: default
spec:
  ports:
    - protocol: TCP
      port: 8080
      targetPort: 8080
      nodePort: 30001
  selector:
    app: hello-node
  type: NodePort
```
## Notes:
1. **Deployment template**:
    _For using your own docker files this property is needed `imagePullPolicy: Never`_{.info .warn}
2. **Service template**:

# Generating the template ( [ref][UKTJAYFH] )
1. If you already have something running, you can extract the YAML in a way that is ready to check in by running something like: ( using `-o yaml --export` )
   ``` sh
   kubectl get deployment hello-node-app -o yaml --export > deployment.yaml
   kubectl get service hello-node-service -o yaml --export > service.yaml
   ```
2. If, instead, you want to create a YAML file from scratch, you can just run: ( using `--o yaml --dry-run` )
   ``` sh
   kubectl run hello-node-app --image=reza/node:latest -o yaml --dry-run > deployment.yaml
   
   kubectl create service nodeport hello-node-service --tcp=8080:8080 --node-port=3001 -o yaml --dry-run > service.yaml
   ```

# Imparative way of managing the cluster ( [ref][IDAAFKTBPM] )
1. **Create**:
    For example to create a namespace, a quota, a deployment and a service we can use the following four CLI commands:
    ``` sh
    kubectl create ns ghost
    kubectl create quota blog --hard=pods=1 -n ghost
    kubectl run ghost --image=ghost -n ghost
    kubectl expose deployments ghost --port 2368 --type LoadBalancer -n ghost
    ```
1. **Edit**:
    To modify any of the objects you can use the `kubectl edit` command or use any of the convenience wrappers
    ``` sh
    kubectl edit service hello-node-service
    kubectl edit replicasets.apps  hello-node-app-85b4b7fb69

    kubectl scale deployment hello-node-app --replicas 2
    ```


* * *
Creation date: _2019-12-24_

[UKTJAYFH]: https://blog.heptio.com/using-kubectl-to-jumpstart-a-yaml-file-heptioprotip-6f5b8a63a3ea
[IDAAFKTBPM]: https://medium.com/bitnami-perspectives/imperative-declarative-and-a-few-kubectl-tricks-9d6deabdde