---
title: Рекомендации по обеспечению готовности к работе в Azure
description: Ознакомьтесь с рекомендациями и дополнительными инструкциями, которые помогут вашей команде настроить и подготовить среду Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: c3c9ab2d1177a023e3a7bed569cad317d5dc117a
ms.sourcegitcommit: 011525720bd9e2d9bcf03a76f371c4fc68092c45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/18/2020
ms.locfileid: "88574556"
---
# <a name="best-practices-for-azure-readiness"></a>Рекомендации по обеспечению готовности к работе в Azure

В рамках подготовки к работе с облаком очень важно обучить персонал техническим навыкам, требуемым для внедрения облачных решений и подготовки целевой среды к размещению перемещаемых в облако ресурсов и рабочих нагрузок. Ознакомьтесь с этими и другими рекомендациями, которые помогут вашей команде подготовить среду Azure.

## <a name="azure-fundamentals"></a>Основные понятия Azure

Организация и развертывание ресурсов в среде Azure.

- [Основные понятия Azure.](../considerations/fundamental-concepts.md) Изучите основные понятия и термины и узнайте, как они связаны друг с другом.
- [Создайте исходные подписки.](./initial-subscriptions.md) Определите набор исходных подписок Azure, чтобы начать внедрение в облако.
- [Масштабируйте среду Azure, используя несколько подписок.](../azure-best-practices/scale-subscriptions.md) Изучите задачи и стратегии создания дополнительных подписок для масштабирования среды Azure.
- [Организация ресурсов с помощью групп управления Azure.](../azure-best-practices/organize-subscriptions.md) Узнайте, как группы управления Azure помогают управлять ресурсами, роли, политиками и развертываниями в нескольких подписках.
- [Следуйте рекомендациям по именованию и добавлению тегов.](../azure-best-practices/naming-and-tagging.md) Ознакомьтесь с подробными рекомендациями по именованию и ресурсов и расстановке в них тегов. Эти рекомендации касаются внедрения облачных решений в организации.
- [Обеспечение согласованности гибридного облака.](../considerations/hybrid-consistency.md) Создайте гибридные облачные решения, которые предоставляют преимущества облачных технологий наряду со многими функциями локального управления.

## <a name="networking"></a>Сеть

Подготовьте сетевую инфраструктуру облака для использования рабочих нагрузок.

- [Решения по выбору сетей.](../considerations/networking-options.md) Выберите сетевые службы, средства и архитектуру с учетом требований к корпоративной рабочей нагрузке, системе управления и подключению.
- [Планирование виртуальной сети.](/azure/virtual-network/virtual-network-vnet-plan-design-arm?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) Спланируйте виртуальные сети с учетом требований к изоляции, подключению и расположению.
- [Рекомендации по защите сети.](/azure/security/fundamentals/network-best-practices?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) Ознакомьтесь с рекомендациями по устранению общих проблем с защитой сети с помощью встроенных возможностей Azure.
- [Сети периметра.](./perimeter-networks.md) Включите безопасное подключение между облачными сетями и локальными или физическими сетями центра обработки данных, а также двухсторонний обмен данными с Интернетом.
- [Звездообразная топология сети](./hub-spoke-network-topology.md). Эффективно управляйте общими требованиями к обмену данными или безопасности для сложных рабочих нагрузок и устраняйте возможные ограничения, связанные с использованием подписок.

## <a name="identity-and-access-control"></a>Идентификаторы и управление доступом

Проектируйте инфраструктуру управления удостоверениями и доступом, чтобы оптимизировать работу систем управления и безопасности для рабочих нагрузок.

- [Рекомендации по защите управления удостоверениями и доступом в Azure.](/azure/security/fundamentals/identity-management-best-practices?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) Ознакомьтесь с рекомендациями по управлению удостоверениями и доступом с помощью встроенных возможностей Azure.
- [Рекомендации по управлению доступом на основе ролей.](../considerations/roles.md) Включите избирательное управление доступом и управление доступом на основе групп для ресурсов, связанных с ролями пользователей.
- [Защита привилегированного доступа для гибридных и облачных развертываний в Azure Active Directory.](/azure/active-directory/users-groups-roles/directory-admin-roles-secure?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) Убедитесь, что корпоративные учетные записи административного доступа и привилегированные учетные записи защищены в пределах облачной и локальной сред.

## <a name="storage"></a>Память

- [Рекомендации по выбору службы хранилища Azure.](../considerations/storage-options.md) Выберите оптимальное решение службы хранилища Azure в соответствии с вашими сценариями использования.
- [Руководство по защите службы хранилища Azure.](/azure/storage/blobs/security-recommendations?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) Узнайте о функциях системы безопасности службы хранилища Azure.

## <a name="databases"></a>Базы данных

- [Выбор оптимального варианта SQL Server в Azure.](/azure/sql-database/sql-database-paas-vs-sql-server-iaas?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) Выберите решение PaaS или IaaS, которое наилучшим образом подходит для ваших рабочих нагрузок SQL Server.
- [Рекомендации по защите базы данных.](/azure/security/azure-database-security-best-practices?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) Ознакомьтесь с рекомендациями по защите базы данных в Azure.
- [Выбор подходящего хранилища данных](/azure/architecture/guide/technology-choices/data-store-overview). Выберите хранилище данных в соответствии со своими требованиями. В базах данных SQL и NoSQL доступны сотни вариантов реализации. Хранилища данных обычно различают по методам структурирования данных и типам поддерживаемых операций. В этой статье описаны некоторые распространенные модели хранилища.

## <a name="cost-management"></a>управления затратами;

- [Отслеживание затрат в бизнес-подразделениях, средах и проектах.](./track-costs.md) Ознакомьтесь с рекомендациями по созданию оптимальных механизмов отслеживания затрат.
- [Оптимизация инвестиций в облако с помощью Управления затратами и выставления счетов Azure.](/azure/cost-management-billing/costs/cost-mgt-best-practices?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) Реализуйте стратегию по управлению затратами и узнайте об инструментах для решения сопутствующих задач.
- [Создание бюджетов и управление ими.](/azure/cost-management-billing/costs/tutorial-acm-create-budgets?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) Узнайте, как создавать бюджеты и управлять ими с помощью Управления затратами и выставления счетов Azure.
- [Экспорт данных о затратах.](/azure/cost-management-billing/costs/tutorial-export-acm-data?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) Узнайте, как экспортировать данные о затратах с помощью Управления затратами и выставления счетов Azure.
- [Оптимизация затрат на основе рекомендаций.](/azure/cost-management-billing/costs/tutorial-acm-opt-recommendations?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) Узнайте, как определять малоиспользуемые ресурсы и сокращать затраты с помощью Управления затратами и выставления счетов Azure, а также Помощника по Azure.
- [Использование оповещений о затратах для мониторинга потребления и расходов.](/azure/cost-management-billing/costs/cost-mgt-alerts-monitor-usage-spending?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) Узнайте, как использовать оповещения Управления затратами и выставления счетов Azure для отслеживания потребления и расходов в Azure.
