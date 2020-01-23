_Written by: Reza Shams Amiri_
# Docker and AWS

1. `aws configure`
    1. AWS Access Key ID [None]: XXXXXX
    1. AWS Secret Access Key [None]: XXXXXXXXXXXXXXXXXX
    1. Default region name [None]: eu-west-1
    1. Default output format [None]: json

2. `eval $(aws ecr get-login --region eu-west-1 --no-include-email)`
3. ![push_commands.png](/img/docker/push_commands.png)
    ``` sh
    docker build -t curity-docker-repo .
    docker tag curity-docker-repo:latest xxx.yyyy.zzz.eu-west-1.amazonaws.com/curity-docker-repo:latest
    docker push xxx.yyyy.zzz.eu-west-1.amazonaws.com/curity-docker-repo:latest
    ```
4. In the deployment yaml:
   ``` yaml
   spec:
      template:
         spec:
            containers:
               - image: xxx.yyyy.zzz.eu-west-1.amazonaws.com/curity-docker-repo:latest
   
   # comment the following line
   #          imagePullPolicy: Never
   ```
* * *
Creation date: _2020-01-23_
