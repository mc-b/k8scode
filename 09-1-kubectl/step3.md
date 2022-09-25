### Service erstellen

Zu dem Pod `apache` Erzeugen wir einen Service. Dadurch wird der Web Server von aussen sichtbar.

Der Port 80 wird von Kubernetes automatisch auf den nächsten freien Port gemappt.

```plain
kubectl expose pod/apache --type="LoadBalancer" --port 80 --namespace test
```{{exec}}

