# helm-charts
## Install Minikube & Helm
```
brew install minikube
brew install helm
```

## Start Kubernetes Cluster
```
minikube start --cpus=4 --memory=5120 --mount=true --mount-string="$HOME:/host"
```

## Access Kubernetes Dashboard
```
minikube dashboard
```

## Add Helm Repository
```
helm repo add stable https://charts.helm.sh/stable
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo add traefik https://helm.traefik.io/traefik
helm repo add elastic https://helm.elastic.co
helm repo add liwenhe https://liwenhe1993.github.io/charts
helm repo add beeinventor https://beeinventor.github.io/charts
helm repo add aliyun https://apphub.aliyuncs.com/stable
```

## Install Traefik
```
helm install traefik traefik/traefik -f traefik/values.yaml
kubectl apply -f traefik/ingress.yaml
```

## Install MySQL
```
kubectl apply -f mysql/pv-volume.yaml,mysql/pv-claim.yaml,mysql/ingress-tcp.yaml
helm install mysql bitnami/mysql -f mysql/values.yaml
```

## Install MongoDB
```
kubectl apply -f mongodb/pv-volume.yaml,mongodb/pv-claim.yaml,mongodb/ingress-tcp.yaml
helm install mongodb bitnami/mongodb -f mongodb/values.yaml
```

## Install Cassandra
```
kubectl apply -f cassandra/pv-volume.yaml,cassandra/pv-claim.yaml,cassandra/ingress-tcp.yaml
helm install cassandra bitnami/cassandra -f cassandra/values.yaml
```

## Install ClickHouse
```
kubectl apply -f clickhouse/pv-volume.yaml,clickhouse/pv-volume-replica.yaml,clickhouse/pv-claim.yaml,clickhouse/pv-claim-replica.yaml,clickhouse/ingress-tcp.yaml
helm install clickhouse liwenhe/clickhouse -f clickhouse/values.yaml
```

## Install Redis
```
kubectl apply -f redis/pv-volume.yaml,redis/pv-volume-replica.yaml,redis/pv-claim.yaml,redis/pv-claim-replica.yaml,redis/ingress-tcp.yaml
helm install redis bitnami/redis -f redis/values.yaml
```

## Install Etcd
```
kubectl apply -f etcd/pv-volume.yaml,etcd/pv-claim.yaml,etcd/ingress-tcp.yaml
helm install etcd bitnami/etcd -f etcd/values.yaml
```

## Install Elasticsearch
```
kubectl apply -f elasticsearch/pv-volume.yaml,elasticsearch/pv-claim.yaml,elasticsearch/ingress-tcp.yaml
helm install elasticsearch elastic/elasticsearch -f elasticsearch/values.yaml
```

## Install Nsq
```
kubectl apply -f nsq/pv-volume.yaml,nsq/pv-claim.yaml,nsq/ingress-tcp.yaml
helm install nsq beeinventor/nsq -f nsq/values.yaml
```

## Install Kafka
```
kubectl apply -f kafka/ingress-tcp.yaml
helm install kafka bitnami/kafka -f kafka/values.yaml
```

## Install RabbitMQ
```
kubectl apply -f rabbitmq/pv-volume.yaml,rabbitmq/pv-claim.yaml,rabbitmq/ingress-tcp.yaml
helm install rabbitmq aliyun/rabbitmq -f rabbitmq/values.yaml
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
