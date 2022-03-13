# helm-charts
## Install Minikube & Helm
```
brew install minikube
brew install helm
```

## Start Kubernetes Cluster
```
minikube start --mount=true --mount-string="$HOME:/host"
```

## Access Kubernetes Dashboard
```
minikube dashboard
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
```

## Install MySQL
```
kubectl apply -f mysql/pv-volume.yaml
kubectl apply -f mysql/pv-claim.yaml
helm install mysql bitnami/mysql -f mysql/values.yaml
kubectl apply -f mysql/ingress-tcp.yaml
```

## Install MongoDB
```
kubectl apply -f mongodb/pv-volume.yaml
kubectl apply -f mongodb/pv-claim.yaml
helm install mongodb bitnami/mongodb -f mongodb/values.yaml
kubectl apply -f mongodb/ingress-tcp.yaml
```

## Install Cassandra
```
kubectl apply -f cassandra/pv-volume.yaml
helm install cassandra bitnami/cassandra -f cassandra/values.yaml
kubectl apply -f cassandra/ingress-tcp.yaml
```

## Install Redis
```
helm install redis bitnami/redis -f redis/values.yaml
kubectl apply -f redis/ingress-tcp.yaml
```

## Install Elasticsearch
```
helm install elasticsearch elastic/elasticsearch -f elasticsearch/values.yaml
kubectl apply -f elasticsearch/ingress-tcp.yaml
```

## Install Kafka
```
helm install kafka bitnami/kafka -f kafka/values.yaml
kubectl apply -f kafka/ingress-tcp.yaml
```

## Install PHP
```
helm install php7 php/php7
helm install php8 php/php8
```

## Add Hosts
```
sudo -- sh -c -e  "echo 127.0.0.1 'traefik.localhost php7-localhost.k8s php8-localhost.k8s' >> /etc/hosts"
```

## Start Minikube Tunnel
```
minikube tunnel
```

## Validate Installation
Visit: [http://traefik.localhost/dashboard/](http://traefik.localhost/dashboard/)

Visit: [http://php7-localhost.k8s](http://php7-localhost.k8s)

Visit: [http://php8-localhost.k8s](http://php8-localhost.k8s)