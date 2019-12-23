_Written by: Reza Shams Amiri_
# 03 K8s file templates

Start your content here...

``` yml
apiVersion: v1
kind: Service
metadata:
  name: hello-node-service
  namespace: default
spec:
  type: NodePort
  selector:
    app: hello-node
  ports:
  - port: 8080
    targetPort: 8080
    nodePort: 30001

```

* * *
Creation date: _2019-12-24_
