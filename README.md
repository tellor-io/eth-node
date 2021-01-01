# eth-node
This repository contains k8s manifest files for deploying a geth node on top of k8s.

## Prerequisites
- Kubernetes 1.12+

## Quickstart
Generate a basic auth user and password using htpasswd:
```console
$ htpasswd -c auth foo
New password: <bar>
New password:
Re-type new password:
Adding password for user foo
```
Note:  It's important the file generated is named auth (actually - that the secret has a key data.auth), otherwise the ingress-controller returns a 503.  


Create a basic auth secret:
```console
$ kubectl create secret generic geth-basic-auth --from-file=auth
secret "geth-basic-auth" created
```


Create k8s resources:
```console
$ kubectl apply -f <cloned-repo>
```