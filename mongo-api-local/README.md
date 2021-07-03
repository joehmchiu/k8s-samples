
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
or 
* kubectl apply -f deploy.yml

## Check DNS
kubectl -n kube-system -l=k8s-app=kube-dns get pods

## Test
* curl http://localhost:8600/api/v1/users/
* curl http://localhost:8600/api/v1/users/[rec_id]
