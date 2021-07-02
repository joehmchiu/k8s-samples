
## Note
#### persistent volume does not work in minikube cluster ####
#### local folder needs to be 777 ####

## Pre Task
sudo mkdir -m 777 -p /Users/data

## Deployment
kubectl apply -f deploy.yml
kubectl get po

## Port Forward
kubectl port-forward $(kubectl get po | grep mysql | tail -n1 | awk '{print $1}') 3306:3306

## Expose Pod
kubectl expose deploy mysql-server --type="LoadBalancer" --target-port=3306

## Replica Sample
kubectl scale deploy mysql-server --replicas 3

## Clean Up
kubectl delete -f deploy.yml
### delete with second thinking
sudo rm -rf /Users/data


