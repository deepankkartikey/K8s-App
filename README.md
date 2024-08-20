### Repository for a demo app with K8s using MongoDB and a Webapp

![DB0E934A-5586-4A3F-ABFD-FA4A014D5BB9](https://github.com/user-attachments/assets/ca0d0397-5435-43ba-b4b8-2058398ae476)

#### K8s manifest files 
* mongo-config.yaml - contains configuration for mongo db url
* mongo-secret.yaml - contains username and password for mongo db service
* mongo.yaml - deployment and service for mongo db
* webapp.yaml - deployment and service for node js app exposed at port 3000 inside container

#### K8s commands

##### start Minikube and check status
    minikube start docker 
    minikube status

##### to apply all services and deployments and start the pods
    kubectl apply -f mongo-secret.yaml
    kubectl apply -f mongo-config.yaml
    kubectl apply -f mongo.yaml
    kubectl apply -f webapp.yaml
 * following the order of commands is necessary
 * first configurations and secrets are setup
 * then only services and deployments can start

##### get minikube node's ip address
    minikube ip

##### get basic info about k8s components
    kubectl get node
    kubectl get pod
    kubectl get svc
    kubectl get all

##### get extended info about components
    kubectl get pod -o wide
    kubectl get node -o wide

##### get detailed info about a specific component
    kubectl describe svc {svc-name}
    kubectl describe pod {pod-name}

##### get application logs
    kubectl logs {pod-name}
    
##### stop your Minikube cluster
    minikube stop

<br />

> :warning: **Known issue - Minikube IP not accessible** 

If you can't access the NodePort service webapp with `MinikubeIP:NodePort`, execute the following command:
    
    minikube service webapp-service

<br />

#### Links
* mongodb image on Docker Hub: https://hub.docker.com/_/mongo
