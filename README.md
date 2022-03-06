# helm-charts

## Start Cluster
```
minikube start --mount=true --mount-string="$HOME:/host"
```

## Install Helm Chart
```
helm install php7 php/php7
```