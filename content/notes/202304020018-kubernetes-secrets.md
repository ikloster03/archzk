---

title: "Kubernetes Secrets"
date: 2023-04-02T00:18:17+03:00
description: "О том как работают секреты в кубере"
tags: ["k8s", "secrets"]
ShowToc: true
ShowBreadCrumbs: true
draft: false
---

[Секрет (Secret)](https://kubernetes.io/docs/concepts/configuration/secret/) - это объект кубера, который содержит чувствительную информацию, типа ключа, токена. (лимит 1 MiB)

Есть разные виды секретов, но основные:

1. generic (пароли/токены)
2. docker-registry (данные авторизации docker registry)
3. tls (tls сертификаты для Ingress)

Generic:

(kind) секрета - (type) Opaque (так повелось, что используется слово "непрозрачный")

```yml
apiVersion: v1
kind: Secret
metadata:
  name: mysecret
type: Opaque
data:
  username: c2x1cm0=
  password: U29tZVN0cm9uZ1Bhc3M=
```

При этом Opaque - не шифрование секрета, а кодирование с помощью base64
