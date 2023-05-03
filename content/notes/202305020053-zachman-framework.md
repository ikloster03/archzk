---
title: "Zachman Framework"
date: 2023-05-02T00:53:27+03:00
description: "Заметка о модели (фреймворке) Захмана"
tags: ["arch", "framework", "zachman"]
ShowToc: true
ShowBreadCrumbs: true
draft: false
---

По посту Максима Смирнова: [Объясняем матрицу Захмана](https://mxsmirnov.com/2018/03/23/zachman/)

> Матрица Захмана, пожалуй, является наиболее ранним и наиболее показательным примером того, когда большая и сложная картинка скрывает суть вещей, которые она, по идее, должна пояснять. Помню своё первое знакомство с этим творением человеческой мысли. Если что-то и привлекает внимание при беглом взгляде на эту картинку, то это карта США в третьем верхнем квадрате, которая в более поздних версиях уступит вое место карте мира.

Полная поздняя версия модели Захмана:
![zachman-framework-full](/img/zachman-framework/zachman-framework-full.jpg)

В первоначальной версии не было, 3 правых столбцов: Who, When и Why. Давайте их уберем и посмотрим, что получилось:
![zachman-framework-short](/img/zachman-framework/zachman-framework-short.jpg)

Рассмотрим пояснения к модели Захмана:
![zachman-framework-concept](/img/zachman-framework/zachman-framework-concept.jpg)

> Не продолжая дальнейший детальный разбор строк и не объясняя отброшенные в начале три правых столбца, хочу обратить ваше внимание на несколько моментов. Последовательность работ, приведенные в матрице в строках, в последующих реинкарнациях архитектурного фреймворка, таких как [TAFIM](https://en.wikipedia.org/wiki/TAFIM) и [TOGAF]({{< ref "202304301855-togaf" >}}) свернется в известное нам кольцо этапов architecture development method. Три столбца первоначальной модели еще встретятся нам в виде столбцов нотации [ArchiMate]({{< ref "202304301856-archimate" >}}), как впрочем и идея связи между элементами моделей из разных клеточек, о которой мы сегодня не поговорили. Ну а другие идеи статьи прямиком попадут в [IEEE-1471](https://en.wikipedia.org/wiki/IEEE_1471), который преобразуется уже в 2000-ые годы в [ISO-42010](https://en.wikipedia.org/wiki/ISO/IEC_42010), а в наши времена и подвергнется переводу на русский язык в виде [ГОСТ Р 57100-2016](https://mxsmirnov.com/2017/06/10/gost-r-57100/).
