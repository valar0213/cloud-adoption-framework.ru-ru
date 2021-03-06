---
title: Рекомендуемый контрольный список для миграции в облако Azure
description: Просмотрите контрольный список миграции в облако Azure, чтобы узнать, как внедрить инструменты Azure для выполнения рекомендаций по миграции в облако.
keywords: рекомендации по миграции в облако Azure, контрольный список по миграции в Azure, контрольный список по миграции в облако, рекомендации по миграции в облако
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: seo-azure-migrate
ms.openlocfilehash: 81f5fe9bf3f67031ffc35caf960009f0c3491c2c
ms.sourcegitcommit: 580a6f66a0d0f3f5b755c68d757a84b2351a432f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/31/2020
ms.locfileid: "87472797"
---
# <a name="azure-cloud-migration-best-practices-checklist"></a>Рекомендуемый контрольный список для миграции в облако Azure

Если вас интересует миграция в Azure, сначала изучите [руководство по миграции в Azure](../azure-migration-guide/index.md) в составе Cloud Adoption Framework. В этом руководстве описан ряд средств и методов для переноса виртуальных машин в облако.

В приведенных ниже контрольных списках содержатся рекомендации по миграции в облако Azure, которые выходят за рамки использования основных облачных средств. В них представлены сложные сценарии, в которых может потребоваться расширить области миграции за пределы сценария, описанного в [руководстве по миграции Azure](../azure-migration-guide/index.md).

## <a name="migration-best-practices-for-business-driven-scope-expansion"></a>Рекомендации по миграции для расширения сферы бизнеса

- **[Поддержка международных рынков](./multiple-regions.md).** Предприятие может работать в нескольких географических регионах с несогласованными требованиями к независимости данных. Чтобы соблюсти эти требования, в числе предварительных условий учитывайте дополнительные элементы, которые влияют на распределение ресурсов в ходе миграции.

## <a name="migration-best-practices-for-technology-driven-scope-expansion"></a>Рекомендации по миграции для расширения сферы технологий

- **[Перенос VMware](./vmware-host.md).** Перенос узлов VMware может ускорить общую миграцию. С каждым узлом VMware можно переносить в облако несколько рабочих нагрузок. После миграции эти виртуальные машины и рабочие нагрузки можно оставить в VMware или перенести в современные облачные решения.
- **[Перенос рабочих нагрузок SQL Server](./sql-migration.md).** Перенос экземпляров SQL Server может ускорить процесс миграции в целом. С каждым экземпляром можно переносить в облако несколько баз данных и служб, что может ускорить выполнение нескольких рабочих нагрузок.
- **[Несколько центров обработки данных](./multiple-datacenters.md).** Перенос нескольких центров обработки данных — очень непростая задача. В ходе каждого процесса в рамках перемещения (оценки, миграции, оптимизации и управления) рассматриваются дополнительные соображения для подготовки к работе в более сложных средах.
- **[Требования к данным превышают возможности сети](./network-capacity-exceeded.md).** Компании часто выбирают миграцию в облако, так как производительность, скорость и стабильность имеющегося центра обработки данных больше не соответствуют требованиям. К сожалению, эти ограничения усложняют процесс миграции и требуют отдельного планирования на этапах оценки и миграции.
- **[Стратегия реализации системы управления и соответствия требованиям](./governance-or-compliance.md).** Если системы управления и соответствие требованиям — важный аспект миграции, между ИТ-командами системы управления и командой по внедрению облачных решений потребуется дополнительное согласование.

## <a name="additional-migration-best-practices"></a>Дополнительные рекомендации по миграции

- [Настройка сетей для рабочих нагрузок, перенесенных в Azure](./migrate-best-practices-networking.md)
- [Развертывание инфраструктуры миграции](./contoso-migration-infrastructure.md)
- [Оценка затрат на рабочие нагрузки, перенесенные в Azure, и определение их размеров](./migrate-best-practices-costs.md)
- [Масштабирование миграции в Azure](./contoso-migration-scale.md)

## <a name="next-steps"></a>Дальнейшие действия

Первоначальное ознакомление с рекомендациями по миграции в Azure полезно начать с указанного ниже документа.

> [!div class="nextstepaction"]
> [несколько центров обработки данных](./multiple-datacenters.md);
