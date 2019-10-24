---
title: Управление выравниванием по всем дисциплинам управления облаком
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Управление выравниванием по всем дисциплинам управления облаком
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 294ea288af478e0e451c9fd38663a26acb10359d
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/21/2019
ms.locfileid: "72682595"
---
# <a name="management-leveling-across-cloud-management-disciplines"></a>Управление выравниванием по всем дисциплинам управления облаком

Ключом к надлежащему управлению в любой среде являются согласованность и повторяемые процессы. Существуют бесконечные варианты, которые можно выполнять в Azure. Аналогично, существуют бесчисленные подходы к управлению облаком. Чтобы обеспечить согласованность и повторяемость, важно уменьшить эти параметры до согласованного набора процессов и средств управления, которые будут предлагаться для рабочих нагрузок, размещенных в облаке.

## <a name="suggested-management-levels"></a>Рекомендуемые уровни управления

Так как рабочие нагрузки в портфеле ИТ не одинаковы, маловероятно, что для каждой рабочей нагрузки будет достаточно одного уровня управления. Для поддержки различных рабочих нагрузок и различных бизнес-обязательств рекомендуется, чтобы группа облачных операций или группа операций платформы установили несколько уровней управления операциями.

![Управление уровнями управления и зрелости в облачной инфраструктуре внедрения](../../_images/manage/cloud-management-maturity.png)

Следующие уровни управления (также изображенные выше) представляют собой несколько рекомендуемых уровней, которые служат отправной точкой:

- **Базовый план управления**: базовый план управления облаком (или базовый план управления) — это определенный набор инструментов, процессов и соответствующих цен, которые будут служить основой для всех облачных средств управления в Azure. Чтобы установить базовый план управления облаком, ознакомьтесь с таблицей в следующем разделе и определите, какие инструменты будут включаться в базовое предложение для вашего бизнеса.
- **Улучшенный базовый план**: для некоторых рабочих нагрузок может потребоваться улучшение базовых показателей, которые не обязательно относятся к одной платформе или рабочей нагрузке. Хотя эти улучшения не являются экономичными для каждой рабочей нагрузки, в ней должны быть распространены процессы, средства и решения для любой рабочей нагрузки, которые могут стоить дополнительной поддержки управления.
- **Специализация платформы**. в любой конкретной среде присутствуют общие платформы, используемые различными рабочими нагрузками. Эта общая архитектура не меняется, когда предприятие применяет облако. Специализация платформы — это уровень управления с повышенными правами, который использует данные и архитектурные знания, чтобы обеспечить более высокий уровень оперативного управления. Примеры специализации платформы включают функции управления, относящиеся к SQL Server, контейнерам, Active Directoryам или другим службам, которые можно лучше управлять с помощью последовательных, повторяемых процессов, средств и архитектур.
- **Специализация рабочей нагрузки**. для тех рабочих нагрузок, которые являются критически важными, может быть обоснованием затрат для более глубокого управления рабочей нагрузкой. В специализации рабочей нагрузки используются данные телеметрии рабочих нагрузок, чтобы определить более новые подходы к ежедневному управлению. Эти же данные часто определяют улучшения в отношении автоматизации, развертывания и проектирования, которые могут привести к повышенной устойчивости, надежности и устойчивости, помимо того, что возможно только в операционных системах управления.
- Не **поддерживается**. так же важно сообщать об общих процессах управления, которые не будут доставляться с помощью дисциплин облачного управления, для любой рабочей нагрузки, классифицированной как неподдерживаемая или Некритическая.

В остальных статьях этой серии будут описаны процессы, которые обычно встречаются в каждой из этих дисциплин.
В [руководстве по управлению Azure](../azure-management-guide/index.md) демонстрируются средства, которые могут поддерживать каждый из этих процессов. Чтобы получить помощь в создании базового плана управления, начните с руководства по управлению Azure. После установки базового плана эта серия статей и рекомендации помогут вам расширить этот базовый план, чтобы определить другие уровни поддержки управления.

## <a name="cloud-management-disciplines"></a>Дисциплины управления облаком

Каждый из предлагаемых уровней управления может вызываться в различных дисциплинах управления облачными средствами. Однако сопоставление предназначено для облегчения поиска предлагаемых процессов и средств для предоставления соответствующего уровня управления облачными средствами.

В большинстве случаев «базовый уровень управления», описанный выше, будет состоять из процессов и средств из следующих дисциплин. В каждом случае выделено несколько процессов и средств для демонстрации "улучшенных базовых функций".

- **Инвентаризация и видимость**. как минимум, базовый план управления должен включать средства инвентаризации ресурсов и просмотра состояния выполнения каждого ресурса.
- **Операционное соответствие:** Регулярное управление конфигурацией, изменением размера, стоимостью и производительностью ресурсов является ключом к обеспечению ожидания производительности и базовым показателям управления.
- **Защита и восстановление:** Минимизация эксплуатационных прерываний и ускорения восстановления каждая помогает избежать потери производительности и влияния дохода. Обнаружение и восстановление являются важными аспектами этой дисциплины в рамках любого базового плана управления.

Уровень специализации платформы управления извлекает из процессов и средств, согласованных с дисциплинами операций платформы.
Аналогичным образом, уровень специализации рабочей нагрузки в управлении извлекается из процессов и средств, согласованных с операциями рабочей нагрузки.
  
## <a name="next-steps"></a>Дальнейшие действия

Следующий шаг к определению каждого уровня управления облачными средствами — это понимание [инвентаризации и видимости](./inventory.md).

> [!div class="nextstepaction"]
> [Параметры инвентаризации и видимости](./inventory.md)