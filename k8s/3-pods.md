# Pods

k8s does not deploy conatiners directly

conatiners are encapsulated in pods

pod is the smallest deployable unit in k8s

usually there's only one container per pods, but in case we need helper conatiners that support the main application. the helper container can have tasks such as logging, processing a file, etc. Note that these helper containers' usecase is dependent on the main container and they do not have any purpose as a stand-alone application. These conatiners can access eachother using the localhost as they share the same network. They also share the same stoarage space.

## YAML file as input

    apiVersion: (pods: v1, service: v1, ReplicaSet: apps/v1, Deployment: apps/v1)
    kind: Pod / Service / ReplicaSet / Deployment
    metadata: # data about the object
        name: myapp-pod
        labels: # its a dictionary
            app: myapp
            type: front-end
    spec: # specification - different for different object types
        conatiners: # list / array
            - name: nginx-container
              image: nginx

Run this command to create the pod:

    kubectl create -f pod-definition.yml

Run these commands to see the pod details:

    kubectl get pods
    kubectl describe pod myapp-pod