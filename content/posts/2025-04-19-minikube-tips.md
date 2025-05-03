---
layout: post
title: "Minikube Tips"
date: 2025-04-19 08:00:00
authors:
- brucejia
tags: 
  - kubernetes
  - minikube
  - tips
description: "Minikube Tips小技巧"
categories: "kubernetes"
series:
- "Cloud Native"
---

# minikube tips


You can know api-server status by accessing the two probes.

```bash
$  minikube ssh curl https://localhost:8443/livez
```

```bash
$ minikube ssh curl https://localhost:8443/readyz
```

Proxy to API Server in Kubernetes


k proxy --port=10443 --address='0.0.0.0'

k proxy --port=10443 --address='0.0.0.0' --accept-hosts='*'
