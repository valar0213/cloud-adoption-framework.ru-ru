---
title: Исправление ресурсов перед миграцией
description: Узнайте, как исправлять все активы, которые вы определили как несовместимые с выбранным поставщиком облачных служб перед началом миграции.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: f2d9250dec7a157fdee2dc908c34625e970aeef1
ms.sourcegitcommit: 9b183014c7a6faffac0a1b48fdd321d9bbe640be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2020
ms.locfileid: "85076162"
---
# <a name="remediate-assets-prior-to-migration"></a>Исправление ресурсов перед миграцией

В процессе оценки миграции команда стремится определить любые конфигурации, которые могут сделать ресурс несовместимым с выбранным поставщиком облачных служб. _Исправление_ является контрольной точкой в процессе миграции, которая гарантирует, что эти проблемы с совместимостью будут устранены. В этой статье рассматриваются несколько общих задач исправления для ознакомления. В ней также представлен стандартный процесс для принятия решения о том, является ли исправление целесообразным.

## <a name="common-remediation-tasks"></a>Общие задачи исправления

В любой корпоративной среде существует технический долг. Отчасти это нормально и ожидаемо. Архитектурные решения, которые хорошо подходили для локальной среды, могут не совсем подходить для облачной платформы. В любом случае для подготовки ресурсов к миграции могут потребоваться общие задачи исправления. Ниже приводятся несколько примеров.

- **Незначительные обновления узла.** Иногда устаревший узел необходимо обновить перед репликацией.
- **Незначительные обновления гостевой ОС.** Скорее всего, для ОС потребуется установка исправлений или обновлений перед репликацией.
- **Изменения Соглашения об уровне обслуживания.** Резервное копирование и восстановление существенно отличаются в облачной платформе. Вполне вероятно, что необходимо будет внести незначительные изменения в процессы резервного копирования ресурсов для обеспечения непрерывной работы в облаке.
- **Миграция PaaS.** В некоторых случаях для ускорения развертывания может потребоваться развертывание структуры данных или приложения по модели PaaS. Для подготовки решения к развертыванию PaaS могут потребоваться незначительные изменения.
- **Изменения кода PaaS.** Как правило, для пользовательских приложений необходимо, чтобы в код были внесены незначительные изменения для использования PaaS. Среди прочего примеры могут включать методы, которые выполняют запись на локальный диск или используют состояние сеанса в памяти.
- **Изменения конфигурации приложения.** Перенесенные приложения могут потребовать изменения переменных, таких как сетевые пути к зависимым ресурсам, изменения учетной записи службы или обновления зависимых IP-адресов.
- **Незначительные изменения сетевых путей.** Возможно, придется изменить шаблоны маршрутизации, чтобы правильно направлять трафик пользователей к новым ресурсам.
    > [!NOTE]
    > Это не производственный маршрут к новым ресурсам, а конфигурация для обеспечения правильной маршрутизации ресурсов в целом.

## <a name="large-scale-remediation-tasks"></a>Крупномасштабные задачи исправления

Скорее всего, в исправлении практически не будет необходимости, если выполняется надлежащее обслуживание, установка исправлений и обновлений центра обработки данных. Среды с необходимостью множества исправлений, как правило, распространены среди крупных предприятий, организаций, которые прошли через значительное сокращение ИТ-инфраструктуры, и организаций со средами служб с устаревшим механизмом управления и средами с расширенными возможностями для приобретения. В каждом из этих типов сред на исправление может уйти большая часть трудозатрат по миграции. Если приведенные ниже задачи исправления, которые негативно влияют на скорость или согласованность миграции, часто возникают, может быть разумным разделить исправление на параллельные команды и задачи (аналогично параллельной работе по внедрению облака и системы управления облаком).

- **Частые обновления узлов.** Если для завершения миграции рабочей нагрузки необходимо обновить большое количество узлов, у группы миграции, скорее всего, возникнут проблемы с задержками. Может быть разумно разорвать затронутые приложения и устранить действия по исправлению до включения затронутых приложений в любые запланированные выпуски.
- **Частое обновление гостевой ОС.** На крупных предприятиях обычно есть серверы, работающие на устаревших версиях Linux или Windows. Помимо очевидных угроз безопасности использования устаревшей ОС, существуют также проблемы, связанные с несовместимостью, которые препятствуют переносу необходимых рабочих нагрузок. Если для большого количества виртуальных машин требуется исправление ОС, может быть разумно разбить эти задания на параллельные итерации.
- **Значительные изменения кода.** Для более старых пользовательских приложений может потребоваться значительно большее количество модификаций, чтобы подготовить их к развертыванию PaaS. В этом случае может быть разумно полностью удалить их из невыполненных работ по миграции и управлять ими в совершенно отдельной программе.

## <a name="decision-framework"></a>Платформа принятия решений

Так как исправление для небольших рабочих нагрузок может быть простым, необходимо выбрать меньшую рабочую нагрузку для первоначальной миграции. Тем не менее, по мере того как вы приобретаете опыт в задачах по миграции и начинаете работать с большими рабочими нагрузками, исправление может стать длительным и дорогостоящим процессом. Например, трудозатраты по исправлению для миграции из Windows Server 2003, включающей более 5000 виртуальных машин, могут задержать выполнение миграции на месяцы. Если требуется такое крупномасштабное исправление, приведенные ниже вопросы помогут при принятии решений.

- Были ли все рабочие нагрузки, затронутые исправлением, определены и занесены в список невыполненных работ по миграции?
- Будет ли миграция приносить такую же рентабельность инвестиций (ROI) для рабочих нагрузок, которые не были затронуты?
- Можно ли исправить затронутые ресурсы в рамках первоначальной временной шкалы миграции? Какое влияние окажут изменения временной шкалы на рентабельность инвестиций?
- Является ли экономически целесообразным исправление ресурсов параллельно с задачами миграции?
- Достаточно ли персонала для исправления и миграции? Следует ли привлекать партнера для выполнения одной или обеих из этих задач?

Если ответы на эти вопросы неблагоприятные, возможно, стоит рассмотреть несколько альтернативных подходов, выходящих за рамки базовой стратегии повторного размещения IaaS:

- **Контейнеризация.** Некоторые ресурсы можно разместить в контейнерной среде без исправления. Это может привести к снижению производительности и не разрешит проблемы безопасности или соответствия.
- **Средствами.** В зависимости от рабочей нагрузки и требований к исправлению может оказаться более выгодным создать скрипт развертывания для новых ресурсов с использованием подхода DevOps.
- **Создать.** Если затраты на исправление очень высоки, а ценность для бизнеса одинаково велика, рабочая нагрузка может подойти в качестве кандидата для повторной сборки или перепроектирования.

## <a name="next-steps"></a>Дальнейшие действия

После завершения исправления можно приступать к [действиям репликации](./replicate.md).

> [!div class="nextstepaction"]
> [Репликация ресурсов](./replicate.md)
