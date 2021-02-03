# This repository contains k8s manifest files for deploying a geth node on top of k8s.

## Prerequisites
- Kubernetes 1.12+

## Quickstart

```
export NETWORK=mainnet
```
or
```
export NETWORK=rinkeby
```

 - ### Install the nginx ingress
https://kubernetes.github.io/ingress-nginx/deploy/#gce-gke
 - ### Generate a basic auth user and password using htpasswd:
```bash
htpasswd -c auth geth
htpasswd auth anotherUser # Add more usernames and passwords
```

 - ### Create or update a basic auth secret:
```bash
kubectl create secret generic geth-$NETWORK --from-file=auth \
    --dry-run=client -o yaml \
    | kubectl apply -f -
```

 - ### Create the resources:
```bash
git clone https://github.com/tellor-io/eth-node
cd eth-node
kubectl apply -f $NETWORK/storage.yml
kubectl apply -f $NETWORK/deploy.yml
kubectl apply -f $NETWORK/ingress.yml
```
