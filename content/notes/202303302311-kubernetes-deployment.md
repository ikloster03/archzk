---

title: "Kubernetes Deployment"
date: 2023-03-30T23:11:19+03:00
description: ""
tags: ["k8s", "deployment"]
ShowToc: true
ShowBreadCrumbs: true
draft: false
---

Развёртывание (Deployment) — это абстракция Kubernetes, которая позволяют нам управлять тем, что всегда присутствует в жизненном цикле приложения

Ресурс вида Deployment позволяет автоматизировать процесс перехода от одной версии приложения к другой. Это делается без прерывания работы системы, а если в ходе этого процесса произойдёт ошибка, у нас будет возможность быстро вернуться к предыдущей, рабочей версии приложения.

В Кубере ничего не надо делать в ручную, не надо прикидывать напрямую поды или реплики сеты если есть деплойменты, тк это приведет к большим проблемам.

Деплоймент при изменение делает следующие:

1. Создает новый реплика сет
2. Затем поэтапно скейлит его до нужно количества подов, в тоже время делает даунскейл старого реплика сета

Но после завершения операции, старый реплика скейл не удаляется, у него есть 0 подов, но он оставляется для операции отката (undo)
 С помощью rollout history можно посмотреть ревизии для конкретного деплоймента

У деплоймента есть поле strategy, а у его type, принимает значения по дефолту RollingUpdate, еще есть Recreate.

RollingUpdate - постепенное обновление. Это нужно чтобы не было Даунтаймов, но нужно разрабатывать приложения с обратной совместимостью, чтобы они могли в 2 версии работать, тогда будет бесшовное обновление.

У RollingUpdate есть доп параметры maxSurge, maxUnavailable. По дефолту оба по 25%. Можно задавать в числа и в процентах.

Первая говорит сколько реплик можно поднять относительно общего количества, второе дропнуть.

Recreate - сначала удалить все старое, потом создать все новое. Не нужно думать об обратной совместимости, но будут даунтаймы 