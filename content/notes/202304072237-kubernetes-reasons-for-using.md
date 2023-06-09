---

title: "Должен ли я использовать K8s?"
date: 2023-04-07T22:37:40+03:00
description: "Критерии, преимущества и недостатки k8s и docker swarm"
tags: ["k8s"]
ShowToc: true
ShowBreadCrumbs: true
draft: false
---

На основе статьей от VK [Self-Hosted, или Kubernetes для богатых: почему самостоятельное развертывание кластера — не всегда способ сэкономить](https://habr.com/ru/company/vk/blog/559370/) и [Как жили до Kubernetes: сравниваем самый популярный оркестратор с другими решениями](https://habr.com/ru/company/vk/blog/543232/).

## Критерии

1. Типы рабочих нагрузок: предназначен ли оркестратор для управления Docker-контейнерами, иными контейнерами и неконтейнерными приложениями.
2. Легкость управления: насколько оркестратор прост в установке и настройке.
3. Требования к платформе для развертывания: является ли решение платформонезависимым или есть определенные требования к ОС и иные ограничения.
4. Производительность: среднее время обработки API-вызовов, запуска контейнеров и других важных операций.
5. Ограничения на количество узлов и контейнеров в кластере: какие существуют ограничения на число управляемых компонентов.
6. Конфигурация как код: есть ли возможность загрузки схем приложений из YAML- или JSON-файлов.
7. Шаблоны: доступна ли настройка пользовательских шаблонов.
8. Сети: как строится сеть, есть ли собственное сетевое решение или необходимо использовать сторонние сетевые плагины.
9. Возможность обнаружения сервисов: поддерживается ли динамическое обнаружение сервисов путем использования DNS, Proxy и так далее.
10. Автомасштабирование: есть ли возможность автомасштабирования в зависимости от изменений нагрузки.
11. Выполнение обновлений и отката: какие стратегии обновлений поддерживаются. Существует ли возможность последовательных обновлений (Rolling Update), когда старые инстансы приложения постепенно заменяются на новые. Насколько просто проводится откат.
12. Отказоустойчивость: как выполняется обработка сбоев, что происходит при выходе из строя одного из узлов.
13. Мониторинг: есть ли встроенные механизмы или необходимо использовать внешние инструменты и какие.
14. Безопасность: есть ли встроенное решение для управления конфиденциальной информацией (логины и пароли).

## Преимущества и недостатки систем оркестрации

### Docker Swarm

Преимущества:

1. Ниже порог входа: быстро устанавливается, легок в изучении, интегрирован с Docker Compose и Docker CLI.
2. Позволяет быстрее разворачивать контейнеры.

Недостатки:

1. Уступает Kubernetes в плане администрирования, особенно в Production-среде.
2. Отсутствует автомасштабирование.
3. Проигрывает в плане поддержки сообществом: инструментарий намного меньше, чем у Kubernetes, что приводит к отсутствию готовых решений и необходимости многое настраивать самостоятельно.

*Для каких задач подходит:* в небольших проектах, где предпочтение отдается простоте и быстрой разработке.

### Kubernetes

Преимущества:

1. Самодостаточный инструмент оркестровки, в который встроено множество сервисов. Kubernetes предоставляет все функции, необходимые для запуска приложений на основе контейнеров, включая: управление кластером, планирование, обнаружение служб, мониторинг, управление безопасностью и многое другое.
2. Поддерживается фондом CNCF (Cloud Native Computing Foundation). У Kubernetes самое впечатляющее по числу участников сообщество среди всех оркестраторов, что обеспечивает богатый инструментарий и большое число готовых решений.
3. Это бесплатный инструмент с открытым исходным кодом, который работает в любой ОС.

Недостатки:

1. Сложнее настроить вручную, хотя это можно решить с помощью использования Kubernetes aaS.
2. Предназначен только для контейнерных приложений.
3. Меньшее количество поддерживаемых узлов по сравнению с Nomad и Mesos.

Переход с Docker Swarm наиболее прост. Можно либо самостоятельно переписать все манифесты, либо использовать доступные инструменты преобразования из файлов Docker Compose в YAML Kubernetes, например Kompose. Первый способ представляется более правильным, так как позволит учесть все преимущества Kubernetes, связанные с deployments, labels, tolerations и так далее. Второй способ позволит избежать переписывания, но менее нативен.

## K8s cloud vs self-hosted

У кубера много плюсов но есть проблемы в использовании.

1. Если использовать облачные решения нужно считать стоимость, но можно сэкономить на развертывании и специалистах
2. Если делать  Self-Hosted решение, тот тут все сложнее

Проблемы Self-Hosted:

1. Нужны специалисты, чтобы развивать кластер. Минимум 1 на фуллтайм.
2. Время для развертывание кластера эти половина задачи, нужна поддержка и развитие кластера
3. Нужно 3 ноды (сервера)
4. Резерв в зависимости от целей (например: 10%, для 10 нод это 1 нода, то есть 1 сервер должен простаивать, ожидая своего часа)
5. Autoscaling - непростая задача, тоже нужен запас серверов
6. Нужно настраивать мониторинг, сбор логов и балансировку нагрузки
7. Интегрировать систему хранения данных

![Диаграмма быстро/дешево/качественно](/img/k8s/diagram-fast-cheap-quality.jpg)