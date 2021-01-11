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
NETWORK with either mainnet or rinkeby.
```bash
git clone https://github.com/tellor-io/eth-node
cd eth-node
export NETWORK=mainnet
kubectl apply -f $NETWORK/storage.yml
kubectl apply -f $NETWORK/deploy.yml
kubectl apply -f $NETWORK/ingress.yml
```
