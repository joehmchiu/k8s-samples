

# Horizontal Pod Autoscaler Walkthrough
-- https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/

## Deployment
kubectl apply -f php-apache.yml

## Create Horizontal Pod Autoscaler 
kubectl autoscale deployment php-apache --cpu-percent=50 --min=1 --max=10
or 
kubectl create -f autoscale.yml
kubectl get hpa

## Increase load 
kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- /bin/sh -c "while true; do wget -q -O- http://php-apache; done"
kubectl get hpa

## Autoscaling on multiple metrics and custom metrics
kubectl get hpa.v2beta2.autoscaling -o yaml > /tmp/hpa-v2.yaml

## Clean Up
kubectl delete -f php-apache.yml
kubectl delete hpa php-apache


