---
title: Как продукты Azure поддерживают иерархию портфеля?
description: Как продукты Azure поддерживают иерархию портфеля?
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: a4ff0091473a7ea2882625dcbffe2f00d91b4ff6
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2020
ms.locfileid: "83401209"
---
<!-- markdownlint-disable MD026 -->

# <a name="how-do-azure-products-support-the-portfolio-hierarchy"></a>Как продукты Azure поддерживают иерархию портфеля?

Для [понимания и согласования иерархии портфеля](./hosting-hierarchy.md)набор определений для иерархии портфеля и сопоставления ролей установил иерархию областей для большинства подходов к портфелю. Как описано в этой статье, вам может не понадобиться каждый из выставляемых уровней или _областей_. Минимизация количества слоев сокращает сложность, поэтому эти слои не должны рассматриваться как требование.

В этой статье показано, как каждый уровень или область иерархии поддерживается в Azure с помощью средств Организации, средств развертывания и управления, а также некоторых решений в инфраструктуре внедрения Microsoft Cloud для Azure.

## <a name="organizing-the-hierarchy-in-azure"></a>Организация иерархии в Azure

Azure Resource Manager включает несколько организационных подходов, помогающих организовывать ресурсы на каждом уровне облачной иерархии.

В панелях слайдов на следующей схеме показаны распространенные варианты выравнивания. Серые части полос слайдов являются общими, но их следует использовать только для конкретных бизнес-требований. В точках после образа описана Рекомендуемая рекомендация.

![Организация ресурсов, выравниваемая по иерархии](../../_images/ready/hierarchy-with-organizing-tools.png)

- **Портфель:** Корпоративная или бизнес-подразделение, вероятно, не будет содержать никаких технических ресурсов, но может повлиять на затраты. Подразделения предприятия и подразделения представлены в корневых узлах иерархии группы управления.
- **Облачные платформы:** Каждая среда имеет собственный узел в иерархии группы управления.
- **Целевые зоны и Cloud Foundation:** Каждая целевая зона представлена в виде подписки. Аналогичным образом, Платформа платформы содержится в собственных подписках. Некоторые модели подписки могут вызывать для подписки на облако или на рабочую нагрузку, что привело бы к изменению инструмента Организации для каждого из них.
- **Рабочие нагрузки:** Каждая рабочая нагрузка представлена в виде группы ресурсов. Группы ресурсов часто используются для представления решений, развертываний или других технических групп ресурсов.
- **Активы:** Каждый ресурс по сути представляется в Azure как ресурс.

## <a name="organizing-with-tags"></a>Упорядочение с помощью тегов

Отклонения от наилучшей методики являются общими. Вы можете записать их, разметив все активы тегами. Используйте тег для представления каждого из соответствующих уровней иерархии. Дополнительные сведения см. в разделе [Рекомендуемые правила именования и добавления тегов](../../ready/azure-best-practices/naming-and-tagging.md).