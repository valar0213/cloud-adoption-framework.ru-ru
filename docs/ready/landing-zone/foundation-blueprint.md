---
title: Развертывание схемы КАФ Foundation в Azure
description: Узнайте, как развернуть проект КАФ Foundation в Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 46ed8211a9206c7eed07760a0452ed97df2e5901
ms.sourcegitcommit: 4e12d2417f646c72abf9fa7959faebc3abee99d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2020
ms.locfileid: "90776318"
---
<!-- docutune:ignore "CAF Foundation blueprint" -->

# <a name="deploy-a-caf-foundation-blueprint-in-azure"></a>Развертывание схемы КАФ Foundation в Azure

В проекте КАФ Foundation не выполняется развертывание целевой зоны. Вместо этого он развертывает средства, необходимые для определения MVP по управлению (минимально приемлемый продукт), для начала разработки дисциплин управления. Эта схема предназначена для добавления в существующую целевую зону и может быть применена к схеме КАФ миграции целевой зоны с одним действием.

## <a name="deploy-the-blueprint"></a>Развертывание схемы

Прежде чем использовать чертеж КАФ Foundation в облачной инфраструктуре внедрения, ознакомьтесь со следующими принципами разработки, допущениями, решениями и рекомендациями по реализации. Если это руководство соответствует требуемому плану внедрения в облако, то [проект КАФ Foundation](/azure/governance/blueprints/samples/caf-foundation) можно развернуть с помощью шагов развертывания.

> [!div class="nextstepaction"]
> [Развертывание образца схемы](/azure/governance/blueprints/samples/caf-foundation/deploy)

## <a name="design-principles"></a>Принципы проектирования

Этот вариант реализации обеспечивает упрямого подход к общим областям проектирования, общим для всех целевых зон Azure. Дополнительные технические сведения см. в приведенных ниже допущениях и решениях.

### <a name="deployment-options"></a>Параметры развертывания

Этот вариант реализации развертывает MVP, чтобы служить основой для ваших дисциплин управления. Группа будет следовать основанному на рефакторингу подходу к более зрелым дисциплинам управления с помощью [управляемой методологии](../../govern/index.md).

### <a name="enterprise-enrollment"></a>Регистрация на предприятии

Этот вариант реализации не принимает встроенную точку на корпоративную регистрацию. Этот подход предназначен для клиентов независимо от договорных соглашений с корпорацией Майкрософт или партнерами Майкрософт. Перед развертыванием этого варианта реализации предполагается, что клиент уже создал целевую подписку.

### <a name="identity"></a>Идентификация

В этом варианте реализации предполагается, что Целевая подписка уже связана с экземпляром Azure Active Directory в соответствии с [рекомендациями по управлению удостоверениями](/azure/security/fundamentals/identity-management-best-practices?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json).

### <a name="network-topology-and-connectivity"></a>Топология сети и возможности подключения

В этом варианте реализации предполагается, что в целевой зоне уже есть определенная топология сети в соответствии с [рекомендациями по безопасности сети](/azure/security/fundamentals/network-best-practices?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json).

### <a name="resource-organization"></a>Организация ресурсов

Этот параметр реализации показывает, как политика Azure может добавлять некоторые элементы Организации ресурсов через приложение тегов. В частности, `CostCenter` тег будет добавлен к ресурсам с помощью политики Azure.

Группа управления должна сравнивать и относиться к элементам Организации ресурсов, чтобы их можно было решать с помощью тегов и тем, которые должны быть решены посредством разработки подписки. Эти фундаментальные решения будут сообщать Организации ресурсов о ходе выполнения планов внедрения в облако.

Чтобы упростить это сравнение в циклах перехода, следует учитывать следующие статьи:

- [Первоначальные подписки Azure](../azure-best-practices/initial-subscriptions.md). на этом этапе масштабирования внедрения для вашей операционной модели требуется две, три или четыре подписки?
- [Масштабирование подписок](../azure-best-practices/scale-subscriptions.md): как масштабирование внедрения, какие критерии будут использоваться для масштабирования подписки?
- [Упорядочение подписок](../azure-best-practices/organize-subscriptions.md): как вы организуете подписки при масштабировании?
- [Стандарты тегов](../azure-best-practices/naming-and-tagging.md#metadata-tags): какие другие критерии должны быть постоянно захвачены в тегах для расширения проекта подписки?

Чтобы помочь в этом сравнении, когда группы работают дальше вместе с внедрением в облаке, ознакомьтесь с разделом Управление шаблонов [руководства Руководство по руководству](../../govern/guides/complex/prescriptive-guidance.md#application-of-governance-defined-patterns) . В этом разделе в нормативных руководствах демонстрируется набор шаблонов на основе определенного описания и операционной модели. В этом руководстве также содержатся ссылки на другие шаблоны, которые следует учитывать.

### <a name="governance-disciplines"></a>Дисциплины управления

В этой реализации демонстрируется один из подходов к зрелости управления затратами в отношении управляемой методологии. В частности, здесь показано, как можно использовать политику Azure для создания списка разрешенных номеров SKU. Ограничение типов и размеров ресурсов, которые могут быть развернуты в целевой зоне, снижает риск снижения затрат.

Чтобы ускорить параллельную разработку других дисциплин, ознакомьтесь с [управляемой методологией](../../govern/index.md). Чтобы продолжить совершенствующейся управления затратами, ознакомьтесь с [руководством по дисциплине управления затратами](../../govern/guides/complex/cost-management-improvement.md#incremental-improvement-of-the-best-practices).

> [!WARNING]
> По мере разработки дисциплин может потребоваться рефакторинг. Может потребоваться рефакторинг. В частности, ресурсы позже потребуется [переместить в новую подписку или группу ресурсов](/azure/azure-resource-manager/management/move-resource-group-and-subscription?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json).

### <a name="operations-baseline"></a>Базовый план операций

Этот вариант реализации не реализует никаких аспектов базовых показателей операций. В отсутствие определенного базового плана операций эта Целевая зона не должна использоваться для критически важных рабочих нагрузок или конфиденциальных данных. Предполагается, что эта Целевая зона используется для ограниченного рабочего развертывания, чтобы начать обучение, итерацию и разработку всей операционной модели параллельно с этими усилиями на раннем этапе миграции.

Чтобы ускорить параллельную разработку базовых показателей операций, просмотрите [методологию управления](../../manage/index.md) и попробуйте развернуть [руководство по управлению сервером Azure](../../manage/azure-server-management/index.md).

> [!WARNING]
> При разработке базового плана операций может потребоваться рефакторинг. В частности, ресурсы позже потребуется [переместить в новую подписку или группу ресурсов](/azure/azure-resource-manager/management/move-resource-group-and-subscription?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json).

### <a name="business-continuity-and-disaster-recovery-bcdr"></a>Непрерывность бизнес-процессов и аварийное восстановление (BCDR)

Этот вариант реализации не реализует ни одно решение BCDR. Предполагается, что решение для защиты и восстановления будет решаться при разработке базовых показателей операций.

## <a name="assumptions"></a>Предположения

В этом исходном проекте предполагается, что группа совершенствующейся возможности управления в параллельном режиме с первоначальными усилиями по миграции в облако. Если эти предположения согласованы с вашими ограничениями, можно использовать схему для начала процесса разработки зрелости системы управления.

- **Соответствие требованиям:** В этой зоне не требуется никаких требований к соответствию сторонних разработчиков.
- **Ограниченная Рабочая область:** В этой целевой зоне потенциально могут размещаться рабочие нагрузки. Это не подходящая среда для конфиденциальных данных или критически важных рабочих нагрузок.

Если эти предположения согласованы с текущими потребностями внедрения, то эта схема может быть отправной точкой для создания целевой зоны.

## <a name="customize-or-deploy-this-blueprint"></a>Настроить или развернуть этот проект

Узнайте больше и скачайте образец схемы КАФ Foundation для развертывания или настройки в примерах схемы Azure.

> [!div class="nextstepaction"]
> [Развертывание образца схемы](/azure/governance/blueprints/samples/caf-foundation/deploy)

## <a name="next-steps"></a>Дальнейшие действия

После развертывания первой целевой зоны вы можете расширить целевую зону.

> [!div class="nextstepaction"]
> [Расширение целевой зоны](../considerations/index.md)
