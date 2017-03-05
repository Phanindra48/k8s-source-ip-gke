# k8s-source-ip-gke
Minimalistic kubernetes cluster to see source ip in google container engine

1. Create a cluster in [google cloud engine](https://cloud.google.com/container-engine/) and leave the defaults
2. Connect to the cluster (You can use either cloud console or your own terminal)


## Create namespace

```
kubectl apply -f namespace.yaml
```

## Create default backend

```
kubectl apply -f default-backend.yaml
```

## create nginx-ingress

```
kubectl apply -f configmap.yaml
kubectl apply -f nginx-controller.yaml
```
Map your External IP that you have got from below command to some domain name.
```
kubectl get svc --namespace=nginx-ingress nginx-ingress
```
## Create source ip app

```
kubectl apply -f source-ip-deploy.yaml
kubectl apply -f source-ip-svc.yaml

```
## Create ingress
Replace `host` in rules section of `ingress.yaml` with your domain that you mapped earlier

```
kubectl apply -f ingress.yaml
```

For more information checkout kubernetes [page](https://kubernetes.io/docs/tutorials/services/source-ip/)
