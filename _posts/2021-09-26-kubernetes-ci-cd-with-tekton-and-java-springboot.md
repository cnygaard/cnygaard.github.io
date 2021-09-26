---
layout: post
title: Kubernetes CI/CD with Tekton and Java Springboot
date: 2021-09-26T07:41:17.621Z
thumbnail: https://tekton.dev/images/tekton-horizontal-color.png
---
### Install Minikube Kubernetes development environment

Today we will install Minikube development environment, install Tekton in Minikube.

<https://minikube.sigs.k8s.io/docs/start/>

Fetch Minikbe with curl and put the minikube command in path

```shell
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

### Start Minikube
```shell
minikube start
```

### Install Tekton in Kubernetes
```shell
kubectl apply -f https://storage.googleapis.com/tekton-releases/operator/latest/release.yaml
# to install pipelines, triggers and dashboard (use profile 'all')
kubectl apply -f https://raw.githubusercontent.com/tektoncd/operator/main/config/crs/kubernetes/config/all/operator_v1alpha1_config_cr.yaml
```

### Install Tekton CLI ###

Fetch tekton cli
https://github.com/tektoncd/cli/releases

```shell
sudo dpkg -i ~/Downloads/tektoncd-cli-0.20.0_Linux-64bit.deb
```

### Install Tekton Dashboard

```shell
kubectl apply --filename https://github.com/tektoncd/dashboard/releases/latest/download/tekton-dashboard-release.yaml
```

# Create example Springboot Web app in IntelliJ
File -> New Project -> Spring Initializr
Name: springboot-web-app

Next

Expand the Web cathegory and pick Spring Web

git init via IntelliJ VCS menu

Push code to your github account





