---
title: Начало работы с целевыми зонами Cloud Adoption Framework корпоративного уровня
description: Приступите к работе с целевыми зонами корпоративного уровня, используя Cloud Adoption Framework для Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 06/15/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 6a7d911677e9496119e1abcfbc97d13bd660c941
ms.sourcegitcommit: 4e12d2417f646c72abf9fa7959faebc3abee99d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2020
ms.locfileid: "90776420"
---
# <a name="start-with-cloud-adoption-framework-enterprise-scale-landing-zones"></a>Начало работы с целевыми зонами Cloud Adoption Framework корпоративного уровня

Архитектура корпоративного уровня представляет собой стратегический путь проектирования и целевое техническое состояние вашей среды Azure. Она продолжит развиваться вместе с платформой Azure и будет определяться различными решениями по проектированию, которые ваша организация должна принять, чтобы определить свой путь в Azure.

Не все организации внедряют Azure одинаково, поэтому применение Cloud Adoption Framework для архитектуры целевой зоны Azure корпоративного уровня в разных организациях может отличаться. Технические рекомендации и рекомендации по проектированию архитектуры корпоративного уровня могут привести к различным компромиссам в зависимости от сценария вашей организации. Возможны различные вариации, но если вы соблюдаете основные рекомендации, то итоговая целевая архитектура позволит вашей организации обеспечить стабильную масштабируемую среду.

## <a name="prescriptive-guidance"></a>Рекомендации

Архитектура корпоративного уровня предоставляет рекомендации, которые связаны с лучшими методиками Azure. В ней соблюдаются принципы проектирования в критически важных областях проектирования среды Azure вашей организации.

## <a name="qualifiers-should-i-start-with-enterprise-scale"></a>Квалификаторы: следует ли начать с корпоративного уровня?

Архитектура корпоративного уровня изначально является модульной. Она позволяет начать с базовых целевых зон для поддержки портфелей приложений, независимо от того, переносятся эти приложения или разрабатываются с нуля и развертываются в Azure. Архитектура может масштабироваться в соответствии с вашими бизнес-требованиями независимо от точки масштабирования.

## <a name="start-with-a-cloud-adoption-framework-enterprise-scale-landing-zone"></a>Начало работы с целевой зоной Cloud Adoption Framework корпоративного уровня

Подход корпоративного уровня к созданию целевых зон включает в себя три набора ресурсов, которые помогут командам разработчиков облачных решений.

- [Рекомендации по проектированию](./design-guidelines.md). Руководство по принятию критически важных решений, которые помогут спроектировать целевую зону Cloud Adoption Framework корпоративного уровня.
- [Архитектура](./architecture.md). Принципиальная эталонная архитектура, демонстрирующая области проектирования и лучшие методики.
- [Варианты реализации](./implementation.md). Шаблон Azure Resource Manager архитектуры для ускорения внедрения.

<!-- TODO: Reinstate once template.md is ready.
- [Template](./template.md): A documentation template to quickly capture decisions and any deviation from the suggested architecture or implementation.
-->

## <a name="community"></a>Сообщество

<!-- docutune:ignore "Cloud Solutions Unit" -->

Это руководство главным образом было разработано архитекторами Майкрософт и обширным техническим сообществом разработчиков облачных решений. Это сообщество активно совершенствует данное руководство, чтобы поделиться опытом, полученным во время внедрения решений корпоративного уровня.

В этом руководстве представлены те же принципы проектирования, что и в стандартной методологии готовности. В нем также подробно рассматриваются такие темы, как система управления и безопасность на ранних этапах планирования. Дополнение стандартного процесса необходимо ввиду нескольких естественных допущений, которые можно сделать, когда усилия по внедрению требуют изменений корпоративного уровня.

## <a name="next-steps"></a>Дальнейшие действия

[Реализация целевой зоны Cloud Adoption Framework корпоративного уровня](./implementation.md)
