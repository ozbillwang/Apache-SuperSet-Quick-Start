# Apache Superset Guick Start

This repo is set for my blog

https://medium.com/@ozbillwang/quick-start-with-apache-superset-3bf055263ed3

## prerequsite

* kubernetes cluster is ready
* cert manager with letsencrypt is ready

## Getting started

```
$ helm repo add superset https://apache.github.io/superset

"superset" has been added to your repositories

$ helm search repo superset

NAME                    CHART VERSION   APP VERSION     DESCRIPTION
superset/superset       0.1.1           1.0             Apache Superset is a modern, enterprise-ready b...

# create namespace
$ kubectl create ns apache-superset-dev
$ kubens apache-superset-dev

# install superset helm chat

$ helm -n apache-superset-dev upgrade --install --values values-dev.yaml superset superset/superset
$ kubectl get pods
NAME                                    READY   STATUS      RESTARTS   AGE
superset-celerybeat-7cdcc9575f-k6xmc    1/1     Running     0          119s
superset-f5c9c667-dw9lp                 1/1     Running     0          4m7s
superset-f5c9c667-fk8bk                 1/1     Running     0          4m11s
superset-init-db-zlm9z                  0/1     Completed   0          111s
superset-postgresql-0                   1/1     Running     0          6d20h
superset-redis-master-0                 1/1     Running     0          6d20h
superset-worker-75b48bbcc-jmmjr         1/1     Running     0          4m8s
superset-worker-75b48bbcc-qrq49         1/1     Running     0          4m12s

# access 
kubectl port-forward service/superset 8088:8088 --namespace apache-superset-dev
```
