# Introduction
This project is part of the subject "Non traditional databases" of the [Open University of Catalonia](www.uoc.edu).

Automatically runs and sets up three instances of a MongoDB replica set.

This docker compose it's built based on four containers. Three are instances of mongodb initially set to run as a replicaSet but its configuration is not finished, as a configuration of a replicaset can be completed only at run-time. The fourth container will connect to one of the instances and it'll finish the steps to configure the replica set through a web wizard.

# Getting started

## Make sure that:

 You have Docker installed and its service is running in your computer.

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

## To access to any node

To connect to the node 1 run:
```
docker exec -it mongo1 /bin/sh
```
Next, to connect to the mongo shell run:
```
mongo
```
To connect to any other node repeat the two previous steps replacing ```mongo1``` by ```mongo2``` or ```mongo3``` depending on the instance that you want to connect.

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

To clear the state and start from the scratch, stop all containers running ```docker compose down``` and next run:

```
docker volume rm volume-mongo1
docker volume rm volume-mongo2
docker volume rm volume-mongo3
```

Finally you can run ```docker-compose up -d``` (in Windows or Mac run ```docker compose up -d```) and set up the replica again connecting to http://localhost:8080