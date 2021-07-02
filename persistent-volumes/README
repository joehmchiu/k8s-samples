
## Create PV
sudo mkdir -m 777 -p /Users/task
sudo sh -c "echo 'Hello from Kubernetes storage' > /Users/task/index.html"
cat /Users/task/index.html

## Deployment
kubectl apply -f deploy.yml
kubectl get pod task-pv-pod
kubectl describe svc task-pv-service

## Access Pod
kubectl exec -it task-pv-pod -- /bin/bash
apt update
apt install curl
curl http://localhost/

## Port Forward 
kubectl port-forward $(kubectl get po | grep task | tail -n1 | awk '{print $1}') 8888:80

## Expose Port 80
### this is a way to expose pod to localhost
kubectl expose pod task-pv-pod --type="LoadBalancer" --target-port=80
kubectl exec -it task-pv-pod -- curl http://10.1.0.21

## Not Working
x kubectl expose pod task-pv-pod --type="NodePort" --target-port=80
kubectl delete svc task-pv-pod

## Clean Up
kubectl delete -f deploy.yml
sudo rm /Users/task/index.html
sudo rm -rf /Users/task

## Useful Tools 
apt install iputils-ping
apt install mariadb-client
apt install net-tools
apt install netcat

