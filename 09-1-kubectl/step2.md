### Pod erstellen

Erzeugen eines Pod's, hier der Apache Web Server.

Die Option `--restart=Never` erzeugt nur einen Pod. Ansonsten wird ein Deployment erzeugt.

```plain
kubectl run apache --image=registry.gitlab.com/mc-b/misegr/httpd --restart=Never --namespace test
```{{exec}}

