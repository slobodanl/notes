_Written by: Reza Shams Amiri_

# 02 working with docker

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

## Run a command on a container

This can be achieved either by `CONTAINER ID` or it's `NAMES`, so for the above example, you can use both of the following commands to go to the shell prompt:

``` sh
docker exec -it kafka-docker_zookeeper_1 bash

# or

docker exec -it 4a8a022cfd8e bash
```

## Get the IP of a container

``` sh
docker exec -it kafka-docker_kafka_1 ip addr show eth0 | grep inet

# or

docker inspect 4a8a022cfd8e | grep IPAddress
```

- - -
Creation date: _2019-02-09_
