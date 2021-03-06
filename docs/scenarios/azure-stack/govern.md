---
title: Управление экземпляром Azure в центре обработки данных
description: Узнайте, как управлять экземпляром Azure, работающим на Azure Stack концентраторе данных.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/19/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 2cb7faca74334538f48b1a57e3bd6b70f3983e43
ms.sourcegitcommit: 07d56209d56ee199dd148dbac59671cbb57880c0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/26/2020
ms.locfileid: "88885530"
---
# <a name="govern-an-azure-instance-in-your-datacenter"></a>Управление экземпляром Azure в центре обработки данных

Управление гибридными решениями на платформах общедоступных и частных облаков повышает сложность. Так как центр Azure Stack — это собственный частный экземпляр Azure, работающий в вашем центре обработки данных, сложность по сути снижается.

Бизнес-процессы, дисциплины и многие рекомендации, описанные в статье Управление [методологией](../../govern/index.md) облачной инфраструктуры внедрения, по-прежнему можно применять к гибридным системам управления с помощью центра Azure Stack. Многие собственные средства облака, используемые в общедоступной облачной версии Azure, также можно использовать в центре Azure Stack.

## <a name="azure-stack-hub-governance-considerations"></a>Рекомендации по управлению центром Azure Stack

В следующей серии блогов показано, как ваша организация может реализовать концепции управления облаком для центра Azure Stack:

- [Службы Организации](https://azure.microsoft.com/blog/azure-stack-iaas-part-seven/) , такие как группы ресурсов, управление доступом на основе РОЛЕЙ (RBAC), аудит изменений, блокировки и теги.
- [Службы безопасности](https://azure.microsoft.com/blog/azure-stack-iaas-part-four/), включая брандмауэры по умолчанию, ограничения, обновления ВМ и управление исправлениями, а также состояние вредоносных программ.
- [DevOps параметры](https://azure.microsoft.com/blog/azure-stack-iaas-part-seven-2/), включая инфраструктуру как код, портал с PowerShell и интерфейсом командной строки, Azure Application Insights и интеграцию с Azure DevOps и Jenkins.

## <a name="governance-toolchain-for-azure-stack-hub"></a>Управление цепочки инструментов для центра Azure Stack

Рекомендации по применению собственных средств управления в облаке для Azure Stack центральных средах см. в следующих статьях:

- [Azure Resource Manager шаблоны и настройка требуемого состояния](/azure-stack/user/azure-stack-arm-templates?view=azs-2002)
- [PowerShell](/azure-stack/user/azure-stack-powershell-overview?view=azs-2002)
- [Политика Azure](/azure-stack/user/azure-stack-policy-module?view=azs-2002)
- [Управление доступом на основе ролей](/azure-stack/user/azure-stack-manage-permissions?view=azs-2002)

## <a name="next-steps"></a>Дальнейшие шаги

Рекомендации по конкретным элементам процесса внедрения облачных технологий см. в следующих статьях:

- [Управление Azure Stack Hub](./manage.md)
