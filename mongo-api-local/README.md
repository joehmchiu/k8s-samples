
# MongoDB API Local Container
MongoDB API support CRUD mode to create, update, query and delete a record by feeding a JSON data.

example:
* DT=$(date +'%F %T')
* JSON='{"name":"Fish Banana","mobile":"013333322","email":"fish.banana@mail.com","gender":"Male","created":"'$DT'"}'

## Environment
* Mac Docker Desktop
* Kubernetes

## PreTasks
* mkdir -m 777 -p /Users/k8s/api
* docker build . -t mongo-api

## Deployment
* kubectl create -f deploy.yml
<br>or 
* kubectl apply -f deploy.yml

## Check DNS
kubectl -n kube-system -l=k8s-app=kube-dns get pods

## Forward to localhost
kubectl port-forward svc/mongo-service -n mongo 8600:8600 --address='0.0.0.0'

## Test
* curl $(minikube service --url mongo-service)/api/v1/users/
* curl http://localhost:8600/api/v1/users/
* curl http://localhost:8600/api/v1/users/[id]

## Deployment
* kubectl delete -f deploy.yml
