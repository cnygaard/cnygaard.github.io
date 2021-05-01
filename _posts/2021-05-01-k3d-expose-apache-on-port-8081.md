---
layout: post
title: k3d expose Apache on port 8081
date: 2021-05-01T11:30:28.762Z
thumbnail: https://upload.wikimedia.org/wikipedia/commons/thumb/6/67/Kubernetes_logo.svg/798px-Kubernetes_logo.svg.png
---
Create a K3d cluster with a loadbalancer

`k3d cluster create --api-port 6550 -p "8081:80@loadbalancer" --agents 2`

Create an deployment of Apache httpd

`kubectl create deployment httpd --image=httpd`

Create a Kubernetes service for httpd on port 80

`kubectl create service clusterip httpd --tcp=80:80`

Create an Kubernetes that exposes the service ingress.yaml
```yaml
# apiVersion: networking.k8s.io/v1beta1 # for k3s < v1.19
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: httpd
  annotations:
    ingress.kubernetes.io/ssl-redirect: "false"
spec:
  rules:
  - http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: httpd
            port:
              number: 80
```

kubectl apply -f ingress.yaml

Curl Traefik 

`curl localhost:8081`

Traefik on port 8081 should display
"It works!".
