_Written by: Reza Shams Amiri_

# Integration with docker ([ref][LHTULDIWMSO])
To enable integeration do the following:
1. Set the environment variables with:
   ``` sh
   eval $(minikube docker-env)
   ```
1. Build the image with the Docker daemon of Minikube:
   ``` sh
   docker build -t my-image .
   ```
1. Set the image in the pod spec like the build tag to `my-image`
   ``` yaml
   spec:
     template:
       spec:
         containers:
           - name: example
             image: my-image
           ports:
           - containerPort: 8080
           imagePullPolicy: Never
   ```
1. Set the imagePullPolicy to Never (as above example), otherwise Kubernetes will try to download the image.


* * *
Creation date: _2019-12-23_

[LHTULDIWMSO]: https://stackoverflow.com/a/42564211/161312