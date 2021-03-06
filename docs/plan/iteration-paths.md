---
title: Установка итераций и разработка планов выпусков
description: Используйте платформу внедрения облачных технологий для Azure, чтобы узнать, как определить итерации и планы выпуска для упрощения управления реализацией.
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: f49d96af36176b08e4de93ab81439b4cd17d8fc2
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "80428124"
---
# <a name="establish-iterations-and-release-plans"></a>Установка итераций и разработка планов выпусков

Гибкие и другие итеративные методологии основаны на концепциях итераций и выпусков. В этой статье описывается назначение итераций и выпусков во время планирования. Эти назначения применяют видимость временной шкалы для упрощения общения между членами группы стратегии облака. Назначения также выделяют технические задачи таким образом, чтобы группа внедрения в облако могла управлять во время реализации.

## <a name="establish-iterations"></a>Создание итераций

В итеративном подходе к технической реализации вы планируете технические усилия по повторяющимся временным блокам. Итерации, как правило, составляют одну неделю до шести недель. Консенсус предполагает, что две недели — это средняя продолжительность итерации для большинства групп по внедрению в облако. Но выбор длительности итерации зависит от типа технических усилий, административных издержек и предпочтений группы.

Чтобы приступить к согласованию усилий с временной шкалой, мы рекомендуем определить набор итераций за последние 6 – 12 месяцев.

## <a name="understand-velocity"></a>Понимать скорость

Для согласования усилий с итерациями и выпусками требуется понимание скорости. Скорость — это объем работы, который может быть выполнен в любой заданной итерации. Во время раннего планирования скорость является оценкой. После нескольких итераций скорость станет очень ценным показателем обязательств, которые команда может уверенно сделать.

Можно измерять скорость в абстрактных терминах, таких как баллы истории. Вы также можете измерять его в более ощутимых условиях, например в часах. Для большинства итеративных платформ рекомендуется использовать абстрактные измерения, чтобы избежать проблем с точностью и восприятием. Примеры в этой статье представляют скорость в часах для каждого спринта. Это представление делает раздел более универсальным для понимания.

**Пример:** Группа по проведению облачного внедрения из пяти человек зафиксирована в течение двух недель. Учитывая текущие обязательства, такие как собрания и поддержка других процессов, каждый участник группы может постоянно участвовать в течение 20 часов в неделю. Для этой команды Оценка начальной скорости составляет 100 часов на спринте.

## <a name="iteration-planning"></a>Планирование итераций

Изначально вы планируете итерации, оценивая технические задачи на основе приоритетной невыполненной работы. Специалисты по внедрению в облако оценивают усилия, необходимые для выполнения различных задач. Затем эти задачи назначаются первой доступной итерации.

Во время планирования итерации группы внедрения в облако проверяют и уточняют оценки. Они делают это до тех пор, пока все доступные скорости не будут согласованы с конкретными задачами. Этот процесс выполняется для каждой рабочей нагрузки с приоритетностью до тех пор, пока все усилия не будут согласованы с прогнозируемой итерацией.

В этом процессе команда проверяет задачи, назначенные следующему спринту. Группа обновляет свои оценки, исходя из диалогового окна группы о каждой задаче. Затем команда добавляет каждую оценочную задачу в следующий спринт, пока не будет достигнута доступная скорость. Наконец, команда оценивает дополнительные задачи и добавляет их к следующей итерации. Команда выполняет эти действия до тех пор, пока не будет исчерпана скорость этой итерации.

Предыдущий процесс продолжится до тех пор, пока все задачи не будут назначены итерации.

**Пример:** Давайте выполним сборку на предыдущем примере. Предположим, что для каждой миграции рабочей нагрузки требуется 40 задач. Также предположим, что вы оцениваете каждую задачу в среднем на один час. Общая оценка составляет приблизительно 40 часов на миграцию рабочей нагрузки. Если эти оценки остаются постоянными для всех 10 приоритетных рабочих нагрузок, эти рабочие нагрузки будут занимать 400 часов.

Скорость, определенная в предыдущем примере, предполагает, что миграция первых 10 рабочих нагрузок займет четыре итерации, что составляет два месяца календарного времени. Первая итерация будет состоять из 100 задач, которые приводят к миграции двух рабочих нагрузок. В следующей итерации аналогичная коллекция задач 100 приведет к переносу трех рабочих нагрузок.

> [!WARNING]
> Предыдущее число задач и оценок строго используется в качестве примера. Технические задачи редко являются постоянными. Этот пример не должен отображаться в виде отражения времени, необходимого для миграции рабочей нагрузки.

## <a name="release-planning"></a>Планирование выпуска

В рамках внедрения в облаке выпуск определяется как коллекция конечных результатов, которые создают достаточно бизнес-ценности, чтобы вычислить риск нарушения работы бизнес-процессов.

Освобождение изменений, связанных с рабочей нагрузкой, в рабочей среде приводит к внесению некоторых изменений в бизнес-процессы. В идеале эти изменения легко, и бизнес видит ценность изменений без существенных перерывов в обслуживании. Но риск нарушения бизнес-процессов представлен любыми изменениями, и его не следует делать нелегко.

Чтобы обеспечить выравнивание изменений по возможному возврату, Группа облачной стратегии должна принять участие в планировании выпуска. После согласования задач с спринтами группа может определить приблизительную временную шкалу, когда каждая рабочая нагрузка будет готова к рабочей версии. Группа облачных стратегий просмотрела время каждого выпуска. Затем команда определит точку перегиба между риском и ценностью бизнеса.

**Пример:** Продолжим предыдущий пример, специалисты по облачной стратегии проверили план итерации. Проверка определила две точки выпуска. Во время второй итерации будет подготовлено пять рабочих нагрузок для миграции. Эти пять рабочих нагрузок обеспечит значительную ценность для бизнеса и активируют первый выпуск. Следующий выпуск получит две итерации позже, когда следующие пять рабочих нагрузок будут готовы к выпуску.

## <a name="assign-iteration-paths-and-tags"></a>Назначение путей итерации и тегов

Для клиентов, которые управляют планами внедрения в облако в Azure DevOps, предыдущие процессы отражаются путем назначения пути итерации каждой задаче и пользовательской истории. Мы также советуем добавлять теги каждой рабочей нагрузки в конкретный выпуск. Это автоматическое заполнение отчетов временной шкалы с помощью тегов и веб-канала назначения.

## <a name="next-steps"></a>Следующие шаги

[Оцените временные шкалы](./timelines.md) для правильной связи ожидания.

> [!div class="nextstepaction"]
> [Оценка временных шкал](./timelines.md)
