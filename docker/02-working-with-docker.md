_Written by: Reza Shams Amiri_

# Working with Docker

Start your content here...

## Show running containers

``` sh
docker ps
```

| CONTAINER ID | IMAGE | COMMAND | CREATED | STATUS | PORTS | NAMES |
| ------------ | ----- | ------- | ------- | ------ | ----- | ----- |
| 4a8a022cfd8e | wurstmeister/zookeeper | "/bin/sh -c '/usr/sb…" | 4 hours ago | Up 4 hours | 22/tcp, 2888/tcp, 3888/tcp, 0.0.0.0:2181->2181/tcp | kafka\-docker\_zookeeper\_1 |
| 6d283af313d4 | kafka-docker_kafka | "start-kafka.sh" | 4 hours ago | Up 3 hours | 0.0.0.0:32772->9092/tcp | kafka\-docker\_kafka\_1 |

## Info

1. Display docker version and info   
    ``` sh
    docker --version
    docker version
    docker info
    ```

## Images

1. Get the list of all images   
    ``` sh
    docker image ls
    ```
1. Get the list of all containers   
    ``` sh
    docker container ls --all
    ```

## Build

1. Building the docker image:   
    ``` sh
    docker build -t <image-name> .
    docker run <image-name>
    ```
## Run
1. Just run:
   ``` sh
   docker run <image-name>
   docker start <image-name>
   ```
1. Run and accept keyboard input:
   If you want to interact with the running container you need to specify `--it`: 
   | flag | description  |
   | --- | --- |
   | -i, --interactive | Keep STDIN open even if not attached |
   | -t, --tty | Allocate a pseudo-TTY |
   ``` sh
   docker run -it <image-name>
   ```
   now for example you can break the running docker by issuing <kbd>ctrl</kbd>+<kbd>c</kbd>
3. Run and expose port:
   If the docker file exposes some ports inorder to access those ports from localhost, you need to map them.
   _An example node app which listens to port 8080 but is accessible through 3000_{.ct}
   ``` sh
   docker run -p 3000:8080 hello-node
   ```
   Now you can go to [http://localhost:3000/]() and access the app which internally runs on 8080
## Run a command on a container

1. This can be achieved either by `CONTAINER ID` or it's `NAMES`, so for the above example, you can use both of the following commands to go to the shell prompt:  
    ``` sh
    docker exec -it kafka-docker_zookeeper_1 bash

    # or

    docker exec -it 4a8a022cfd8e bash
    ```
1. For containers that doesn't stay online ([ref][LSASITDACSO]):   
    ``` sh
    docker run -it --rm gollum /bin/ash
    
    # /bin/ash is Ash (Almquist Shell) provided by BusyBox
    # --rm Automatically remove the container when it exits (docker run --help)
    # -i Interactive mode (Keep STDIN open even if not attached)
    # -t Allocate a pseudo-TTY
    ```


## Get the IP of a container

``` sh
docker exec -it kafka-docker_kafka_1 ip addr show eth0 | grep inet

# or

docker inspect 4a8a022cfd8e | grep IPAddress
```

## Cleaning
1. clean images
   ``` sh
   docker image prune
   ```
2. clean networks
   ``` sh
   docker network prune
   ```
3. clean full system
   ``` sh
   docker system prune -a
   ```

- - -
Creation date: _2019-02-09_

[LSASITDACSO]: https://stackoverflow.com/a/35689633/161312