# Node CRUD API with K8s Manifest

## Overview
This repo is contains a CRUD API using node and also kubernetes manifest for deployment, service, hpa, secret, configmap and Mongo Helm Chart.

## Kubernetes Manifest
### App Manifest
To apply an app manifest, just using
```
kubectl apply -f <manifest>
```
we can combine into one yaml but this time is splitted for easily maintenance.

### Mongo Helm Chart
To install an helm chart, usually you want to make the mogo HA as possible and also keep in mind the Persistent Storage, and maybe Toleration.
But for install this chart, just use :
```
helm install mongo-db . -f custom-values.yaml
```

## Source Code
The app source code are cloned from https://github.com/bezkoder/node-express-mongodb but I do some tweak :
- Created a Dockerfile app for this app,so it can run in kubernetes cluster.
- Move variable to Envar by using ```process.env``` object for configmaps & secrets.

To build an app you could use a Gitlab CI or Github Action, using kaniko or docker in docker image.