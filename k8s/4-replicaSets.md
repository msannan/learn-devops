# ReplicaSets

ReplicaSets allow us to create multiple instances of the same pod, to:
1. provide high availability
1. load balancing & scaling

<blockquote>
Only apps that are fully replaceable, stateless are to be hosted as replicaSets or Deployments, for stateful application use StatefulSets
</blockquote>

## ReplicationController

<blockquote>
older tech replaced by ReplicaSet now.
</blockquote>
* selector is optional for ReplicationController

`rc-definition.yml`:

    apiVersion: v1
    kind: ReplicationController
    metadata:
        name: myapp-rc
        labels:
            app: myapp
            type: front-end
    spec:
        replicas: 3
        template:
            metadata:
                name: myapp-pod
                labels:
                    app: myapp
                    type: front-end
            spec:
                conatiners:
                    - name: nginx-container
                      image: nginx


## ReplicaSet

Monitors the pods, if anyone fails, deploys a new one.

It can also use pods created before creating replicaset. This is not supported in replication controller.
* selector is mandatory, it acts a s a filter to select which pods to monitor

`replicaset-definition.yml`:

    apiVersion: apps/v1 # different from replication controller
    kind: ReplicaSet
    metadata:
        name: myapp-replicaset
        labels:
            app: myapp
            type: front-end
    spec:
        replicas: 3
        selector: # this part different from replication controller
            matchLabels:
                type: front-end
        template:
            metadata:
                name: myapp-pod
                labels:
                    app: myapp
                    type: front-end
            spec:
                conatiners:
                    - name: nginx-container
                      image: nginx

# Scale

If we need to change the replication factor of a replicaset, there are many ways:

1. update the yaml manifest and run `kubectl replace -f replicaset-definition.yml`
1. just run the command `kubectl scale --replicas=6 -f replicaset-definition.yml` or `kubectl scale --replicas=6 replicaset myapp-replicaset`
1. There's a way to automatically scale up and down automatically based on the work-load bu that topic will be discussed later 

1st option is more preferable than 2nd, as the yaml file can be maintained by a version control system.

## ReplicationController vs ReplicaSet

It can be tricky to compare a replica controller vs replica set (ReplicalSet), because the latter is a sort of a hybrid. They are in some ways more powerful than ReplicationControllers, and in others they are less powerful. ReplicaSets are declared in essentially the same way as ReplicationControllers, except that they have more options for the selector.

The major difference difference between a replication controller and replica set is that the rolling-update command works with Replication Controllers, but won’t work with a Replica Set.  This is because Replica Sets are meant to be used as the backend for Deployments.

Deployments are actually intended to replace Replication Controllers. When comparing a Deployment vs Replica Set, the former provides  the same replication functions (through Replica Sets) and also the ability to rollout changes and roll them back if necessary.
