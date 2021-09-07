# KUBECTL

a cmd line interface to create configurations, get current status, or get detailed information
about the services

    kubectl create -f pod-definition.yml
    kubectl get nodes
    kubectl get pods
    kubectl get services
    kubectl get replicationcontroller
    kubectl get replicaset
    kubectl describe pods
    kubectl delete -f .
    kubectl delete -f pod-definition.yml
    kubectl run hello-minikube
    kubectl cluster-info
    kubectl apply -f pod-definition.yml
    kubectl run nginx --image=nginx
    kubectl edit pod <pod-name>
    kubectl replace -f replicaset-definition.yml
    kubectl edit replicaset new-replica-set