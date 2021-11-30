---
layout: post
title: Install ArgoCD Notes
date: 2021-11-30T20:44:24.815Z
thumbnail: https://argo-cd.readthedocs.io/en/stable/assets/logo.png
---
Start minikube

`minikube start`

Create ArgoCD namespace

`kubectl create namespace argocd`

Install ArgoCD

`kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`

Install ArgoCD CLI

`brew install argocd`

Port forward argocd server

`kubectl port-forward svc/argocd-server -n argocd 8080:443`

Get ArgoCD Admin password

`kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d`
