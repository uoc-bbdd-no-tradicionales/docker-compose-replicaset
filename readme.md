# Introduction
This project is part of the subject "Non traditional databases" of the [Open University of Catalonia](www.uoc.edu).

Automatically runs and sets up three instances of a MongoDB replica set.

This docker compose it's built based on four containers. Three are instances of mongodb initially set to run as a replicaSet but its configuration is not finished, as a configuration of a replicaset can be completed only at run-time. The fourth container will connect to one of the instances and it'll finish the steps to configure the replica set through a web wizard.

# Getting started

## Make sure that:

You have [Docker installed](https://docs.docker.com/get-docker/) and its service is running in your computer.

## Download the repo

Download the repo and unzip it clicking in Code > Download ZIP as it is shown below:

![Clone the repo screenshot](https://github.com/MarkCBB/docker-compose-replicaset/blob/master/docs/screenshot.png?raw=true)

## Go to the root folder of the project

Open a command line shell and go to the path where you unziped the file. For example in windows:

```
cd C:\Users\Marc\Documents\docker-compose-replicaset\
```

This path may not work in your PC, make sure to identify the root path of yours.

## To run the stack in Mac and Windows
 
```
docker compose up -d
```

## To run the stack in Linux

```
docker-compose up -d
```

## Setting up the replica set

Once the stack is running, connect to http://localhost:8080 and follow the instructions.

## Accessing nodes individually

To connect to the node 1 run:
```
docker exec -it mongo1 /bin/sh
```
Next, to connect to the mongo shell run:
```
mongo mongo1:27018
```
To connect to the node 2 run:
```
docker exec -it mongo2 /bin/sh
```
Next, to connect to the mongo shell run:
```
mongo mongo2:27019
```

To connect to the node 3 run:
```
docker exec -it mongo3 /bin/sh
```
Next, to connect to the mongo shell run:
```
mongo mongo3:27020
```

## To stop all containers in Windows
After exiting the mongo and the container shell, run:

```
docker compose down
```
## To stop all containers in Linux
After exiting the mongo and the container shell, run:

```
docker-compose down
```

This will **not** clear the replica set configuration. Running again ```docker-compose up -d``` all the containers will start in the same state as they were when were stopped.

## Clear/reset all configuration and data
To clear the state and start from the scratch, stop all containers running ```docker compose down``` and next run:

```
docker volume rm volume-mongo1
docker volume rm volume-mongo2
docker volume rm volume-mongo3
```

Finally you can run ```docker-compose up -d``` (in Windows or Mac run ```docker compose up -d```) and set up the replica again connecting to http://localhost:8080