---
title: "Kubernetes Config"
date: 2023-04-01T22:42:35+03:00
description: "О конфигах в k8s"
tags: ["k8s", "configmap"]
ShowToc: true
ShowBreadCrumbs: true
draft: false
---

В spec конкретного контейнера с помощью env можно прокидывать переменные окружения
Но это не оптимальное решение

Лучше использовать [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/)

Представляет собой yml конфиг, где в data, можно прописывать переменные окружения.
Не рекомендуется хранить секреты.
