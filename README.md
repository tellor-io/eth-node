# This repository contains k8s manifest files for deploying a geth node on top of k8s.

## Prerequisites
- Kubernetes 1.12+

## Quickstart

 - ### Install the nginx ingress
https://kubernetes.github.io/ingress-nginx/deploy/#gce-gke
 - ### Generate a basic auth user and password using htpasswd:
```bash
htpasswd -c auth geth
```

 - ### Create a basic auth secret:
```bash
kubectl create secret generic geth --from-file=auth
```


 - ### Create the resources:
```bash
kubectl apply -f https://raw.githubusercontent.com/tellor-io/eth-node/main/storage.yml
kubectl apply -f https://raw.githubusercontent.com/tellor-io/eth-node/main/deploy.yml
kubectl apply -f https://raw.githubusercontent.com/tellor-io/eth-node/main/ingress.yml
```
or from a cloned repository
```
kubectl apply -f storage.yml
kubectl apply -f deploy.yml
kubectl apply -f ingress.yml
```