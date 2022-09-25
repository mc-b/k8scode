### Erstellen der Microservices

```plain
kubectl create namespace ms-rest
kubectl apply -f https://raw.githubusercontent.com/mc-b/misegr/master/ewolff/ms-kubernetes/apache.yaml
kubectl apply -f https://raw.githubusercontent.com/mc-b/misegr/master/ewolff/ms-kubernetes/catalog.yaml
kubectl apply -f https://raw.githubusercontent.com/mc-b/misegr/master/ewolff/ms-kubernetes/customer.yaml
kubectl apply -f https://raw.githubusercontent.com/mc-b/misegr/master/ewolff/ms-kubernetes/order.yaml
kubectl apply -f https://raw.githubusercontent.com/mc-b/misegr/master/ewolff/ms-kubernetes/postgres.yaml
```{{exec}}


Exemplarisch für die YAML Dateien, schauen wir uns das Beispiel des Apache Web Servers an.


```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: apache
  namespace: ms-rest  
spec:
  replicas: 1
  selector:
    matchLabels:
      app: apache
  template:
    metadata:
      labels:
        app: apache
        group: web
        tier: frontend
    spec:
      containers:
      - name: apache
        image: registry.gitlab.com/mc-b/microservice-kubernetes/microservice-kubernetes-demo-apache:v0.0.1
        imagePullPolicy: IfNotPresent          
        ports:
        - containerPort: 80
          name: apache
```

### Port forwarden

Um auf das Menu zuzugreifen, wurde ein Service erstellt.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: apache
  namespace: ms-rest  
  labels:
    app: apache
    group: web
    tier: frontend
    service: apache
spec:
  type: NodePort
  ports:
  - port: 80
    nodePort: 32280
    name: http
  selector:
    app: apache
```

Nach einer gewissen Zeit sind die Microservices gestartet und können mittels Menu erreicht werden:

[Microservices Menu]({{TRAFFIC_HOST1_32280}})

