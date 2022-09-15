# Oppgave 2

* Om du har fullført oppgave 1 skal appen ligge i container-registeret registry.digitalocean.com/olsen (Sjekk med Richard)

* K8s clusteret på DO har tilgang til dette container registeret. Så lenge containeren ligger der, kan en deployment i K8S laste ned containeren derifra.

* I denne oppgava skal du deploye appen til K8S clusteret på DO.

* Du vill trenge en deployment.yml fil som definerer navn på app, navn på container, portnummer og antall "replicas" (Anbefalt 2-3).

* Namespace i yml-fila må være apps, slik:
```
  namespace: apps
```

Her er et eksempel på en deployment.yml fil for ngnix

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80

```

I Github Action må du bruke biblioteket: **matootie/dokube@v1.3.4**, her må du sette clusterName til: **k8s-miles**
og personalAccessToken til: 

```
${{ secrets.DIGITAL_OCEAN_TOKEN }}
```
