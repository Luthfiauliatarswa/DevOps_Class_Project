---
title: First Kubernetes Deployment
subtitle: First application on Kubernetes using Kubernetes deployments
date: 2019-02-01
tags: ["kubernetes", "code"]
---

Pada tulisan ini kita membuat aplikasi pertama di Kubernetes menggunakan resource **Deployment**.

## Membuat Deployment

Simpan manifest berikut sebagai `deployment.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hello-nginx
spec:
  replicas: 2
  selector:
    matchLabels:
      app: hello-nginx
  template:
    metadata:
      labels:
        app: hello-nginx
    spec:
      containers:
        - name: nginx
          image: nginx:stable
          ports:
            - containerPort: 80
```

## Menjalankan di cluster

```bash
kubectl apply -f deployment.yaml
kubectl get deployments
kubectl get pods
```

Deployment akan menjaga agar jumlah Pod selalu sesuai dengan nilai `replicas`.
