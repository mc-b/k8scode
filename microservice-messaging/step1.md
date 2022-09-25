### Erstellen der Microservices

```plain
kubectl create namespace ms-kafka
kubectl apply -f https://raw.githubusercontent.com/mc-b/misegr/master/ewolff/ms-kafka/apache.yaml
kubectl apply -f https://raw.githubusercontent.com/mc-b/misegr/master/ewolff/ms-kafka/invoicing.yaml
kubectl apply -f https://raw.githubusercontent.com/mc-b/misegr/master/ewolff/ms-kafka/kafka.yaml
kubectl apply -f https://raw.githubusercontent.com/mc-b/misegr/master/ewolff/ms-kafka/order.yaml
kubectl apply -f https://raw.githubusercontent.com/mc-b/misegr/master/ewolff/ms-kafka/postgres.yaml
kubectl apply -f https://raw.githubusercontent.com/mc-b/misegr/master/ewolff/ms-kafka/shipping.yaml
kubectl apply -f https://raw.githubusercontent.com/mc-b/misegr/master/ewolff/ms-kafka/zookeeper.yaml
```{{exec}}


### Port forwarden

Nach einer gewissen Zeit sind die Microservices gestartet und können mittels Menu erreicht werden:

[Microservices Menu]({{TRAFFIC_HOST1_32180}})

