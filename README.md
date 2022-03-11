# helm-charts

## Start Kubernetes Cluster
```
minikube start --mount=true --mount-string="$HOME:/host"
```

## Install Helm
```
brew install helm
helm repo add stable  https://kubernetes-charts.storage.googleapis.com/
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo add traefik https://helm.traefik.io/traefik
helm repo add elastic https://helm.elastic.co
```

## Install Traefik
```
helm install traefik traefik/traefik -f traefik/values.yaml
kubectl apply -f traefik/dashboard.yaml
```

## Install MySQL
```
helm install mysql stable/mysql -f mysql/values.yaml
kubectl apply -f mysql/ingressroute.yaml
```

## Install Redis
```
helm install redis stable/redis -f redis/values.yaml
kubectl apply -f redis/ingressroute.yaml
```

## Install MongoDB
```
helm install mongodb bitnami/mongodb -f mongodb/values.yaml
kubectl apply -f mongodb/ingressroute.yaml
```

## Install Cassandra
```
helm install cassandra bitnami/cassandra -f cassandra/values.yaml
kubectl apply -f cassandra/ingressroute.yaml
```

## Install Elasticsearch
```
helm install elasticsearch elastic/elasticsearch -f elasticsearch/values.yaml
kubectl apply -f elasticsearch/ingressroute.yaml
```

## Install PHP
```
helm install php7 php/php7
```
