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
   ```

* * *
Creation date: _2019-12-24_

[UKTJAYFH]: https://blog.heptio.com/using-kubectl-to-jumpstart-a-yaml-file-heptioprotip-6f5b8a63a3ea