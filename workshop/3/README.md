## Oppgave 3

* Gratulerer! Du er flink! :smile::smile::smile:

* I denne oppgava skal du eksponere appen din for omverden, på det store nettet! Slik vill alle kunne glede seg ove den fine hello-world appen du lagde i Oppgave 1

* For dette trenger du ein Service og en Ingress-fil. (Det er forventa at dette skal kjøres fra en Github Action)

Eksempel på service.yml

```
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app.kubernetes.io/name: proxy
  ports:
  - name: name-of-service-port
    protocol: TCP
    port: 80
    targetPort: http-web-svc
```

Eksempel på ingress.yml

```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: minimal-ingress
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  ingressClassName: nginx
  rules:
  - http:
      paths:
      - path: /testpath
        pathType: Prefix
        backend:
          service:
            name: test
            port:
              number: 80
```

Prøv å eksponer appen med følgande URL: app.ostepopp.site/DITT_APP_NAVN (via Ingress)

Du vill trenge dette i ingress fila for å få det til:
```
annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /$2
```
