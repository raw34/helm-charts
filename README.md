# helm-charts
## Install Helm
```
brew install helm
```

## Start Kubernetes Cluster
```
minikube start --mount=true --mount-string="$HOME:/host"
```

## Add Helm Repository
```
helm repo add stable https://kubernetes-charts.storage.googleapis.com/
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo add traefik https://helm.traefik.io/traefik
helm repo add elastic https://helm.elastic.co
```

## Install Traefik
```
helm install traefik traefik/traefik -f traefik/values.yaml
kubectl apply -f traefik/dashboard.yaml
minikube tunnel
```

## Install MySQL
```
kubectl apply -f mysql/pv-volume.yaml
kubectl apply -f mysql/pv-claim.yaml
helm install mysql bitnami/mysql -f mysql/values.yaml
kubectl apply -f mysql/ingressroute.yaml
```

## Install MongoDB
```
kubectl apply -f mongodb/pv-volume.yaml
kubectl apply -f mongodb/pv-claim.yaml
helm install mongodb bitnami/mongodb -f mongodb/values.yaml
kubectl apply -f mongodb/ingressroute.yaml
```

## Install Cassandra
```
kubectl apply -f cassandra/pv-volume.yaml
helm install cassandra bitnami/cassandra -f cassandra/values.yaml
kubectl apply -f cassandra/ingressroute.yaml
```

## Install Redis
```
helm install redis bitnami/redis -f redis/values.yaml
kubectl apply -f redis/ingressroute.yaml
```

## Install Elasticsearch
```
helm install elasticsearch elastic/elasticsearch -f elasticsearch/values.yaml
kubectl apply -f elasticsearch/ingressroute.yaml
```

## Install Kafka
```
helm install kafka bitnami/kafka -f kafka/values.yaml
kubectl apply -f kafka/ingressroute.yaml
```

## Install PHP
```
helm install php7 php/php7
```

## Access Kubernetes Dashboard
```
minikube dashboard
```

## Host Config
```
sudo -- sh -c -e  "echo 127.0.0.1 'traefik.localhost php7-localhost.k8s php8-localhost.k8s' >> /etc/hosts"
```