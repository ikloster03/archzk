---

title: "Kubernetes Replica Set"
date: 2023-03-30T23:06:05+03:00
description: ""
tags: ["k8s", "replica-set"]
ShowToc: true
ShowBreadCrumbs: true
draft: false
---

ReplicaSet - это следующее поколение Replication Controller. Единственная разница между ReplicaSet и Replication Controller - это поддержка селектора. ReplicaSet поддерживает множественный выбор в селекторе, тогда как Replication Controller поддерживает в селекторе только выбор на основе равенства.

Replica set позволяет масштабировать поды по заданной схеме

K8s обладает self-healing, то есть если удали под, или нода вышла из строя, replica-set восстановить под автоматически

Но если нужно автоматически обновить схему (образ контейнеры, обновить версию),
то для этого нужно использовать [deployment]({{< ref "202303302311-kubernetes-deployment" >}})