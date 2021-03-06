---
title: Руководство по принудительному применению политик
description: Используя Cloud Adoption Framework для Azure, узнайте о подписках с принудительным применением политик в качестве основного приоритета при миграции в Azure.
author: rotycenh
ms.author: abuck
ms.date: 02/11/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: e90acc824745f947972593ea97c59cf8c8c77a86
ms.sourcegitcommit: 07d56209d56ee199dd148dbac59671cbb57880c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/26/2020
ms.locfileid: "88881654"
---
# <a name="policy-enforcement-decision-guide"></a>Руководство по принудительному применению политик

Определение корпоративной политики — это неэффективный процесс, если вы не можете применить ее в организации. При планировании любой миграции в облако крайне важно определить оптимальное сочетание средств, предоставляемых облачной платформой, и существующих ИТ-процессов для обеспечения максимального соответствия политике во всем облаке.

![Схема вариантов принудительного использования политик, отсортированных в порядке увеличения сложности, со ссылками для быстрого перехода](../../_images/decision-guides/decision-guide-policy-enforcement.png)

Перейти к разделу: [Рекомендуемая практика по базовым показателям](#baseline-best-practices) | [Мониторинг соблюдения политики](#policy-compliance-monitoring) | [Применение политик](#policy-enforcement) | [Политика для совместной работы между организациями](#cross-organization-policy) | [Автоматическое применение](#automated-enforcement)

По мере роста облачных ресурсов возникает необходимость поддерживать и применять политику в отношении большего числа ресурсов и подписок. Увеличение числа активов и усложнение требований в организации требует расширять область действия процессов применения политик, чтобы гарантировать согласованное применение политики и быстрое обнаружение нарушений.

Предоставленных платформой механизмов применения политик на уровне ресурсов или подписок обычно хватает для небольших облачных активов. Для более крупных развертываний с более широкой областью применения могут потребоваться более сложные механизмы, включающие стандарты развертывания, группировку и организацию ресурсов, а также интеграцию применения политик с системами ведения журналов и отчетности.

Основные факторы при определении области действия для процессов применения политики — это действующие для организации [нормативные требования к облаку](../../govern/index.md), размер и характер облачных активов, а также зависимость [схемы подписок](../subscriptions/index.md) от структуры организации. Увеличение размера активов или повышение необходимости в централизованном управлении применением политик могут стать основанием для увеличения области применения.

## <a name="baseline-best-practices"></a>Рекомендуемая практика по базовым показателям

Для одиночной подписки и простых облачных развертываний многие корпоративные политики можно реализовать на основе встроенных возможностей ресурсов и подписок Azure. Единообразное использование шаблонов, которые обсуждаются в [руководствах по принятию решений](../index.md) Cloud Adoption Framework, поможет создать базовый уровень соответствия политикам без определенных инвестиций. Эти функции включают в себя следующие:

- [Шаблоны развертывания](../resource-consistency/index.md) могут предоставлять ресурсы со стандартизированной структурой и конфигурацией.
- [Стандарты присвоения тегов и имен](../resource-tagging/index.md) могут помочь организовать операции и поддерживать требования к бухгалтерскому учету и бизнесу.
- Управление трафиком и сетевые ограничения могут быть реализованы через [программно-определяемую сеть](../software-defined-network/index.md).
- [Управление доступом на основе ролей](../identity/index.md) позволяет защитить и изолировать облачные ресурсы.

Начните планирование применения облачной политики, изучив, как применение стандартных шаблонов, описанных в этих руководствах, может помочь удовлетворить требования организации.

## <a name="policy-compliance-monitoring"></a>Отслеживание соответствия нормативным требованиям

Первым шагом, выходящим за пределы стандартных возможностей платформы Azure по применению политик, будет возможность проверки соблюдения политики организации для облачных приложений и служб. Сюда входят возможности уведомления ответственных лиц о нарушении политик для некоторого ресурса. Эффективное [ведение журнала и отчетность](../logging-and-reporting/index.md) о состоянии соответствия облачных рабочих нагрузок является важной частью стратегии применения корпоративной политики.

По мере роста облачных ресурсов дополнительные средства, такие как [Центр безопасности Azure](/azure/security-center), могут обеспечивать интегрированную безопасность и обнаружение угроз, а также применять централизованное управление политиками и оповещения для локальных и облачных ресурсов.

## <a name="policy-enforcement"></a>Принудительное применение политики

Чтобы обеспечить соблюдение политики, в Azure можно применить параметры конфигурации и правила создания ресурсов на уровне группы управления, подписки или группы ресурсов.

[Политика Azure](/azure/governance/policy/overview) — это служба Azure для создания, назначения политик и управления ими. Эти политики гарантируют соблюдение различных правил и действий с ресурсами, что обеспечивает соответствие этих ресурсов корпоративным стандартам и соглашениям об уровне обслуживания. Служба "Политика Azure" оценивает ресурсы на предмет несоответствия назначенным политикам. Например, может потребоваться ограничить размер SKU виртуальных машин в среде. После реализации этой политики новые и имеющиеся ресурсы будут оцениваться на предмет соответствия. При правильном типе политики имеющиеся ресурсы могут быть приведены в соответствие.

## <a name="cross-organization-policy"></a>Политики между организациями

Когда для облачных активов потребуется большое число подписок, для применения политик ко всем этим подпискам потребуется единая стратегия в масштабе всей облачной системы.

[Схема подписок](../subscriptions/index.md) должна учитывать политику в отношении структуры организации. Помимо поддержки сложной организации в рамках проекта подписки [группы управления Azure](../../ready/azure-best-practices/organize-subscriptions.md) можно использовать для назначения правил политики Azure нескольким подпискам.

## <a name="automated-enforcement"></a>Автоматизированное принудительное выполнение

Хотя стандартизированные шаблоны развертывания эффективны в меньших масштабах, [Azure Blueprints](/azure/governance/blueprints/overview) позволяет выполнять крупномасштабную стандартизированную подготовку и оркестрацию развертывания решений Azure. Рабочие нагрузки в нескольких подписках можно развертывать с согласованными параметрами политики для любых созданных ресурсов.

Для ИТ-сред, интегрирующих облачные и локальные ресурсы, может потребоваться использование систем ведения журналов и создания отчетов, чтобы обеспечить гибридные возможности мониторинга. Ваши сторонние или пользовательские системы оперативного мониторинга могут предложить дополнительные возможности применения политик. Для более крупных и развитых облачных систем рассмотрите возможности интегрировать эти системы с облачными ресурсами.

## <a name="next-steps"></a>Дальнейшие действия

Применение политики — один из базовых компонентов инфраструктуры, решение о котором необходимо принять на этапе внедрения облачных решений. См. обзор руководств по принятию решений об архитектуре, чтобы узнать об альтернативных шаблонах или моделях, используемых с другими типами инфраструктуры.

> [!div class="nextstepaction"]
> [Руководства по принятию решений об архитектуре](../index.md)
