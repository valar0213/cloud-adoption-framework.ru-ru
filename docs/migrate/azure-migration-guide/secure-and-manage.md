---
title: Защита и управление
description: Узнайте больше о методах безопасности и управления, которые можно использовать для управления своей средой после миграции в Azure.
author: matticusau
ms.author: mlavery
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 92d625da9da3e6953cf5502f4d7e5e7adb055d41
ms.sourcegitcommit: 07d56209d56ee199dd148dbac59671cbb57880c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/26/2020
ms.locfileid: "88884782"
---
<!-- markdownlint-disable MD024 DOCSMD001 -->

# <a name="secure-and-manage"></a>Защита и управление

После переноса среды в Azure важно рассмотреть средства безопасности и методы, используемые для управления средой. Azure предоставляет множество функций и возможностей для реализации этих требований в решении.

## <a name="azure-monitor"></a>[Azure Monitor](#tab/monitor)

Служба Azure Monitor обеспечивает максимальную доступность и производительность приложений, предоставляя полноценное решение для сбора, анализа и обработки данных телеметрии из облачных и локальных сред. Она поможет вам понять, как выполняются приложения, а также заранее определить проблемы, влияющие на них, и ресурсы, от которых они зависят.

### <a name="use-and-configure-azure-monitor"></a>Использование и настройка Azure Monitor

1. Выберите **Монитор** на портале Azure.
2. Выберите **Метрики**, **Журналы** или **Работоспособность служб** для просмотра.
3. Выберите любые релевантные полезные сведения.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview]" submitText="Go to Azure Monitor" :::

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>Дополнительные сведения

- [Общие сведения об Azure Monitor](/azure/azure-monitor/overview).

::: zone-end

## <a name="azure-service-health"></a>[Служба "Работоспособность служб Azure"](#tab/serviceHealth)

Работоспособность служб Azure предоставляет индивидуальные инструкции и средства поддержки на случай проблем со службами Azure. Служба может сообщать о масштабе проблем и уведомлять вас после их устранения. Эта служба также помогает подготовиться к запланированному техническому обслуживанию и изменениям, которые могут повлиять на доступность ваших ресурсов.

Служба "Работоспособность служб Azure" предоставляет такие сведения:

- **Состояние Azure:** Глобальное представление со сведениями о работоспособности служб Azure.
- **Работоспособность служб:** Персонализированное представление со сведениями о работоспособности ваших служб Azure.
- **Работоспособность ресурса:** Подробное представление работоспособности отдельных ресурсов, подготовленных вашими службами Azure.

Сочетая эти представления, можно получить исчерпывающие сведения о работоспособности Azure с интересующим вас уровнем детализации.

### <a name="access-service-health"></a>Получение информации о работоспособности служб

1. Выберите **Монитор** на портале Azure.
2. выберите **Работоспособность служб**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/serviceIssues]" submitText="Go to Service Health" :::

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>Дополнительные сведения

Дополнительные сведения см. в статье [Документация по службе "Работоспособность служб Azure"](/azure/service-health).

::: zone-end

## <a name="azure-advisor"></a>[Помощник по Azure](#tab/advisor)

Помощник по Azure — это персонализированный облачный консультант, который поможет следовать рекомендациям по оптимизации развернутых служб Azure. Он анализирует конфигурацию и данные телеметрии использования ресурсов. Затем он рекомендует решения, позволяющие повысить производительность, безопасность и уровень доступности ресурсов, выявляя при этом любые возможности сократить общие затраты на Azure.

### <a name="access-azure-advisor"></a>Вызов Помощника по Azure

1. Перейдите к **Помощнику** на портале Azure или выполните поиск ресурса.
2. Выберите **Высокий уровень доступности**, **Безопасность**, **Производительность** или **Стоимость**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Expert/AdvisorMenuBlade/overview]" submitText="Go to Azure Advisor" :::

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>Дополнительные сведения

[Обзор](/azure/advisor/advisor-overview).

::: zone-end

## <a name="azure-security-center"></a>[Центр безопасности Azure](#tab/security)

Центр безопасности Azure — единая система управления безопасностью инфраструктуры, которая повышает уровень защищенности центров обработки данных и предоставляет средства Расширенной защиты от угроз Azure для гибридных рабочих нагрузок в облаке независимо от того,&mdash;находятся ли они в Azure&mdash;, а также локально.

### <a name="access-azure-security-center"></a>Переход к Центру безопасности Azure

1. Перейдите к **Центру безопасности** на портале Azure или выполните поиск ресурса.
2. Выберите **Рекомендации**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/0]" submitText="Go to Security Center" :::

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>Дополнительные сведения

[Обзор](/azure/security-center/security-center-intro)

::: zone-end

## <a name="azure-backup"></a>[Azure Backup](#tab/backup)

Azure Backup — это служба на платформе Azure, используемая для резервного копирования (защиты) и восстановления данных в Microsoft Cloud. Azure Backup позволяет заменить существующее локальное или автономное решение для резервного копирования на надежное, безопасное и экономичное облачное решение.

### <a name="enable-backup-for-an-azure-vm"></a>Включение резервного копирования для виртуальной машины Azure

1. На портале Azure щелкните **Виртуальные машины**, а затем выберите виртуальную машину для репликации.
1. Из списка **Операции** выберите **Резервное копирование**.
1. Выберите существующее или создайте новое хранилище Служб восстановления.
1. Выберите **Create (or edit) a new policy** (Создать (или изменить) новую политику).
1. Настройте расписание и период хранения.
1. Щелкните **ОК**.
1. Выберите **Включить резервное копирование**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

[Обзор](/azure/backup/backup-overview)

::: zone-end

## <a name="azure-site-recovery"></a>[Azure Site Recovery](#tab/siteRecovery)

После завершения миграции Azure Site Recovery также создает критически важный компонент в рамках стратегии аварийного восстановления.

Служба Azure Site Recovery позволяет реплицировать виртуальные машины и рабочие нагрузки, размещенные в основном регионе Azure, в их копии, размещенные в дополнительном регионе. При возникновении сбоя в основном регионе можно выполнить отработку отказа на копию, работающую в дополнительном регионе, и продолжить работу со своими приложениями и службами. После устранения сбоя и восстановления работоспособности основной копии виртуальной машины можно восстановить ее размещение.

### <a name="replicate-an-azure-vm-to-another-region-with-site-recovery-service"></a>Репликация виртуальной машины Azure в другой регион с помощью службы Site Recovery

Ниже описывается процесс использования службы Site Recovery для репликации виртуальной машины Azure в другой регион (из Azure в Azure).

>
> [!TIP]
> В зависимости от сценария конкретные действия могут немного отличаться.
>

### <a name="enable-replication-for-the-azure-vm"></a>Включение репликации виртуальной машины Azure

1. На портале Azure щелкните **Виртуальные машины**, а затем выберите виртуальную машину для репликации.
1. В разделе **Операции** щелкните **Аварийное восстановление**.
1. В разделе **Настройка аварийного восстановления** > **Целевой регион** выберите целевой регион, в который будет выполняться репликация.
1. Для выполнения действий, описанных в этом кратком руководстве, примите другие значения по умолчанию.
1. Выберите **Включить репликацию**. Будет запущено задание для включения репликации виртуальной машины.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

### <a name="verify-settings"></a>Проверка параметров

После завершения задания репликации можно узнать состояние репликации, проверить работоспособность репликации и протестировать развертывание.

1. В меню виртуальной машины щелкните **Аварийное восстановление**.
2. Проверьте работоспособность репликации, созданные точки восстановления, а также исходный и целевой регионы на карте.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>Дополнительные сведения

- [Обзор Azure Site Recovery](/azure/site-recovery/site-recovery-overview)
- [Репликация виртуальной машины Azure в другой регион](/azure/site-recovery/azure-to-azure-quickstart)

::: zone-end
