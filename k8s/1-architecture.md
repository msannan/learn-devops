# Node is machine where containers will be launched
also called minions

cluster is a set of nodes grouped together

Master / Control Plane Node is watched over the nodes in cluster and is resposible for actual orchestration of containers on worker nodes

# Components

![k8s-architecture][k8s-architecture]

[k8s-architecture]: images/1-architecture.png

## API server

acts as front-end for k8s

users, devices, cmds all talk to server to interact with k8s cluster

## etcd

is a distributed key-value store for all data to manage the cluster

info of all nodes

implementsmanages locks - avoids conflicts between masters

## scheduler

distributes work loads or containers across multiple nodes

## Controller

brain behind orchestration

continuously try to match the desired state of cluster

## container runtime

underlying software used to run containers

mostly its docker, other options are also available

## kubelet

agent that runs on each node in the cluster

makes sure conatiners are running on nodes as expected


# Master vs Worker Nodes

![mastervsworkers][mastervsworkers]

[mastervsworkers]: images/2-mastervsworkers.png
