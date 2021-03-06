---
title: Оценка готовности рабочей нагрузки
description: Узнайте, что нужно для того, чтобы оценить готовность рабочей нагрузки к переходу в облако. Вы узнаете, как проверить все активы и связанные с ними зависимости.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 83859b5687c8342c8b09ccab36aaefb53a169cd6
ms.sourcegitcommit: 011525720bd9e2d9bcf03a76f371c4fc68092c45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/18/2020
ms.locfileid: "88570187"
---
# <a name="evaluate-workload-readiness"></a>Оценка готовности рабочей нагрузки

Здесь описывается оценка готовности рабочей нагрузки к переносу в облако. Во время этого действия команда по внедрению в облако проверяет, все ли ресурсы и связанные зависимости совместимы с выбранной моделью развертывания и поставщиком облачных служб. В ходе этого процесса команда документирует все трудозатраты, необходимые для [устранения](../migrate/remediate.md) проблем совместимости.

## <a name="evaluation-assumptions"></a>Предположения относительно оценки

Большая часть содержимого, обсуждающая принципы в облачной инфраструктуре внедрения, зависит от облака. Однако процесс оценки готовности должен быть в значительной степени адаптирован к конкретной облачной платформе. В приведенных ниже рекомендациях предполагается, что вы выполняете миграцию в Azure. Здесь также предполагается, что для [действий репликации](../migrate/replicate.md) используется служба "Миграция Azure" (также известная как Azure Site Recovery). Альтернативные инструменты см. в разделе [Параметры репликации](../migrate/replicate-options.md).

В этой статье не записываются все возможные действия по оценке. Здесь предполагается, что каждая среда и желаемый бизнес-результат будут диктовать определенные требования. Чтобы ускорить формирование этих требований, в оставшейся части этой статьи приведено несколько общих действий по оценке, связанных с оценкой [инфраструктуры](#common-infrastructure-evaluation-activities), [базы данных](#common-database-evaluation-activities) и [сети](#common-network-evaluation-activities).

## <a name="common-infrastructure-evaluation-activities"></a>Общие действия по оценке инфраструктуры

- Требования к VMware. [Ознакомьтесь с требованиями к Azure Site Recovery для VMware](/azure/site-recovery/vmware-physical-azure-support-matrix).
- Требования к Hyper-V. [Ознакомьтесь с требованиями к Azure Site Recovery для Hyper-v](/azure/site-recovery/hyper-v-azure-support-matrix).

Не забудьте задокументировать все несоответствия в конфигурации узлов, реплицируемых виртуальных машин, требованиях хранилища и конфигурации сети.

## <a name="common-database-evaluation-activities"></a>Общие действия по оценке базы данных

- Задокументируйте целевые показатели точки восстановления (RPO) и целевое время восстановления (RTO) текущего развертывания базы данных. Они используются во время выполнения [действий архитектуры](./architect.md) , чтобы помочь в принятии решений.
- Задокументируйте все требования к конфигурации высокого уровня доступности. Дополнительные сведения о требованиях к SQL Server см. в статье [SQL Server рекомендации по решениям высокого уровня доступности](/sql/sql-server/failover-clusters/high-availability-solutions-sql-server).
- Оцените совместимость PaaS. С [помощью руководств по миграции данных Azure](https://datamigration.microsoft.com) локальные базы данных сопоставляются с совместимыми решениями Azure PaaS, такими как [Azure Cosmos DB](/azure/cosmos-db), база данных [SQL Azure](/azure/sql-database) [для MySQL](/azure/mysql), база [данных Azure для PostgreSQL](/azure/postgresql)или [база данных Azure для MariaDB](/azure/mariadb).
- Если миграция PaaS является вариантом без необходимости каких-либо исправлений для обеспечения совместимости, то следует обратиться к команде, ответственной за [действия, связанные с архитектурой](./architect.md). Миграция PaaS может значительно сократить время перемещения и снизить совокупную стоимость владения большинства облачных решений.
- Если миграция PaaS является вариантом, но требуется исправление для обеспечения совместимости, обратитесь к командам, ответственным за [действия по архитектуре](./architect.md) и [действия по исправлению](../migrate/remediate.md). Во многих сценариях преимущества миграции PaaS для решений баз данных могут перевешивать увеличение времени исправления.
- Задокументируйте размер и скорость изменения для каждой переносимой базы данных.
- По возможности задокументируйте все приложения или другие ресурсы, которые выполняют вызовы к каждой базе данных.

> [!NOTE]
> Синхронизация любого ресурса потребляет пропускную способность во время процесса репликации. Игнорирование потребления пропускной способности, необходимого для синхронизации ресурсов между точкой репликации и выпуска, является очень распространенной ошибкой. Базы данных в значительной степени потребляют пропускную способность во время циклов выпуска, а базы данных с большим объемом хранилища или высокой частотой изменений особенно проблематичны. Рассмотрим подход репликации структуры данных с контролируемыми обновлениями перед пользовательским приемочным тестированием (UAT) и выпуском. В таких случаях вместо службы Azure Site Recovery может быть целесообразно использовать альтернативные средства. Дополнительные сведения см. в статье Руководство по [миграции базы данных Azure](https://datamigration.microsoft.com).

## <a name="common-network-evaluation-activities"></a>Обычные действия для оценки сети

- Вычислите общий объем хранилища для всех виртуальных машин, реплицируемых во время итераций, ведущих к выпуску.
- Вычислите смещение или частоту изменений хранилища для всех виртуальных машин, реплицируемых во время итераций, ведущих к выпуску.
- Вычислите потребности в пропускной способности, необходимые для каждой итерации, суммируя общий объем хранилища и объем смещения.
- Рассчитайте неиспользуемую пропускную способность, доступную в текущей сети, для проверки согласованности итераций.
- Задокументируйте пропускную способность, необходимую для достижения ожидаемой скорости миграции. Если для обеспечения необходимой пропускной способности требуется какое-либо исправление, следует уведомить команду, ответственную за [действия по исправлению](../migrate/remediate.md).

> [!NOTE]
> Общий объем хранилища напрямую влияет на потребности в пропускной способности во время начальной репликации. Однако смещение хранилища продолжится от точки репликации до выпуска. Это означает, что смещение имеет общее воздействие на доступную пропускную способность.

## <a name="next-steps"></a>Дальнейшие действия

После завершения оценки системы на основе полученных результатов выполняется разработка новой [облачной архитектуры](./architect.md).

> [!div class="nextstepaction"]
> [Проектирование рабочих нагрузок до миграции](./architect.md)
