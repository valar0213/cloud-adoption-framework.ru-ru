---
title: Защита и восстановление в облачном управлении
description: Узнайте о важности подготовки к невозможности сбоя рабочей нагрузки. Эта подготовка позволяет команде выявлять сбои быстрее и быстро восстанавливаться.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 7b924c02fa1028d7df6206a021c2c7e4a6bb8a4f
ms.sourcegitcommit: af521583b98153f7157895b7ba9de71183d437b0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176469"
---
# <a name="protect-and-recover-in-cloud-management"></a>Защита и восстановление в облачном управлении

После соблюдения требований к [инвентаризации и видимости](./inventory.md) и [эксплуатационному соответствию](./operational-compliance.md), команды управления облачными средами могут предвидеть и подготавливать потенциальный сбой рабочей нагрузки. При планировании управления облаком группы должны начать с предположения, что что-то не удастся.

Ни одно техническое решение не может обеспечить согласованное соглашение об уровне обслуживания в 100% времени. Решения с наиболее избыточными архитектурами выставляются с "шестью 9S" или 99,9999% времени работы. Но даже решение "шесть 9S" выходит за 31,6 секунд в любой конкретный год. К сожалению, в решении возникает ситуация, когда решение потребует больших, непрерывных эксплуатационных инвестиций, которые необходимы для достижения "шести 9S" времени работы.

Подготовка к сбою позволяет команде быстро обнаруживать сбои и выполнять восстановление быстрее. Основное внимание уделяется действиям, происходящим сразу после сбоя системы. Как защитить рабочие нагрузки, чтобы их можно было быстро восстановить при возникновении сбоя?

## <a name="translate-protection-and-recovery-conversations"></a>Миграция для защиты и восстановления

Рабочие нагрузки, включающие операции Power Business, состоят из приложений, данных, виртуальных машин и других ресурсов. Для каждого из этих ресурсов может потребоваться другой подход к защите и восстановлению. Важным аспектом этой дисциплины является обеспечение согласованного обязательства в рамках базового плана управления, которое может предоставить отправную точку во время бизнес-обсуждений.

Как минимум, каждый ресурс, поддерживающий любую заданную рабочую нагрузку, должен иметь базовый подход с четким обязательством по скорости восстановления (целевые значения времени восстановления или RTO) и риску потери данных (целевые точки восстановления или RPO).

### <a name="recovery-time-objectives-rto"></a>Целевые показатели времени восстановления (RTO)

При аварийном восстановлении целевое время восстановления — это время, необходимое для восстановления системы до ее состояния до аварии. Для каждой рабочей нагрузки это может включать время, необходимое для восстановления минимально необходимых функций для виртуальных машин и приложений. Он также включает время, необходимое для восстановления данных, необходимых для приложений.

В бизнес-условиях RTO представляет собой период времени, в течение которого бизнес-процесс не будет обслуживаться. Для критически важных рабочих нагрузок эта переменная должна быть относительно низкой, что позволяет бизнес-процессам быстро возобновляться. Для рабочих нагрузок с более низким приоритетом Стандартный уровень RTO может не оказать заметного влияния на производительность компании.

Базовый план управления должен устанавливать стандартное значение RTO для некритически важных рабочих нагрузок. Затем бизнес может использовать этот базовый план как способ выровнять дополнительные инвестиции во время восстановления.

### <a name="recovery-point-objectives-rpo"></a>Целевые точки восстановления (RPO)

В большинстве систем управления облачными системами данные периодически фиксируются и сохраняются с помощью какой-либо формы защиты данных. Время последнего захвата данных называется точкой восстановления. При сбое системы его можно восстановить только до последней точки восстановления.

Если в системе есть Целевая точка восстановления, измеряемая в часах или днях, то сбой системы приведет к утрате данных за часы или дни между последней точкой восстановления и сбоем. Однодневная RPO теоретически будет приводить к утрате всех транзакций в день, ведущих к сбою.

Для критически важных систем целевой объект RPO, измеряемый в минутах или секундах, может быть более подходящим для использования во избежание потери дохода. Но более короткое значение RPO обычно приводит к увеличению общей стоимости управления.

Чтобы снизить затраты, базовый план управления должен сосредоточиться на самой длинной целевой точке восстановления. Затем группа управления облаком может увеличить целевую точку восстановления для конкретных платформ или рабочих нагрузок, что потребует больше инвестиций.

## <a name="protect-and-recover-workloads"></a>Защита и восстановление рабочих нагрузок

Большинство рабочих нагрузок в ИТ-среде поддерживают конкретный деловой или технический процесс. Системы, не имеющие системного влияния на бизнес-операции, часто не гарантируют повышенных инвестиций, необходимых для быстрого восстановления или снижения потери данных. Устанавливая базовые показатели, бизнес может ясно понять, какой уровень поддержки восстановления может быть предложен по постоянно управляемой ценовой точке. Это понимание помогает заинтересованным сторонам предприятия оценить ценность инвестиций в восстановление.

Для большинства групп управления облаком Улучшенная Базовая оценка с конкретными обязательствами RPO/RTO для различных активов дает наиболее приемлемый путь к деловым обязательствам. В следующих разделах описаны некоторые стандартные улучшенные базовые показатели, позволяющие бизнесу легко добавлять функции защиты и восстановления с помощью повторяемого процесса.

### <a name="protect-and-recover-data"></a>Защита и восстановление данных

Данные являются наиболее ценным активом в цифровой экономике. Возможность более эффективной защиты и восстановления данных является наиболее распространенной улучшенной базовой конфигурацией. Для данных, которые заключаются в рабочей нагрузке, потери данных могут быть напрямую нарушены из-за потери прибыли или потери рентабельности. Специалисты по управлению облачными системами, как правило, расширяют возможности базового управления, поддерживающего общие платформы данных.

Перед тем, как группы управления облачными службами реализуют операции с платформой, они часто поддерживают улучшенные операции для платформы данных платформы как услуги (PaaS). Например, Группа управления облачными системами легко применяет более высокую частоту резервного копирования или многорегионовой репликации для базы данных SQL Azure или решений Azure Cosmos DB. Это позволяет команде разработчиков легко улучшить RPO, модернизации их платформы данных.

Дополнительные сведения об этом процессе обработки идей см. в разделе [Platform Operations дисциплина](./platform.md).

### <a name="protect-and-recover-vms"></a>Защита и восстановление виртуальных машин

Большинство рабочих нагрузок имеют некоторую зависимость от виртуальных машин, где размещаются различные аспекты решения. Чтобы Рабочая нагрузка поддерживала бизнес-процесс после сбоя системы, некоторые виртуальные машины необходимо быстро восстановить.

Каждая минута простоя на этих виртуальных машинах может привести к потере дохода или снижению рентабельности. Когда время простоя виртуальной машины напрямую влияет на финансовую производительность бизнеса, RTO очень важен. Виртуальные машины можно быстро восстановить, используя репликацию на дополнительный сайт и автоматическое восстановление — модель, которая называется моделью восстановления с горячим горячим подключением. При наивысшем состоянии восстановления виртуальные машины можно реплицировать на полностью функциональный вторичный сайт. Этот более ресурсоемкий подход называется моделью высокого уровня доступности или горячей интенсивности восстановления.

Каждая из предыдущих моделей сокращает RTO, что приводит к более быстрому восстановлению возможностей бизнес-процесса. Однако каждая модель также приводит к значительному увеличению затрат на управление облаком.

Кроме того, обратите внимание, что помимо репликации для обеспечения высокого уровня доступности, резервное копирование должно быть включено для таких сценариев, как случайное удаление, повреждение данных и атаки злоумышленников.

Дополнительные сведения об этом процессе обработки идей см. в разделе [операции рабочей нагрузки дисциплина](./workload.md).

## <a name="next-steps"></a>Дальнейшие действия

После выполнения этого компонента базового плана управления группа может взглянуть на то, чтобы избежать простоев в [работе платформы](./platform.md) и [операций рабочей нагрузки](./workload.md).

> [!div class="nextstepaction"]
> Операции с платформой [Platform operations](./platform.md) 
>  [Операции рабочей нагрузки](./workload.md)
