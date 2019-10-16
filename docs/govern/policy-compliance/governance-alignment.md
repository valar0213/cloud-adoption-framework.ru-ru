---
title: Сопоставление руководства по проектированию управления облаком с корпоративной политикой
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Сопоставление руководства по проектированию управления облаком с корпоративной политикой
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: b1d5562b6e8248f371e01473d141aefecf1554b4
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223748"
---
# <a name="align-your-cloud-governance-design-guide-with-corporate-policy"></a>Сопоставление руководства по проектированию управления облаком с корпоративной политикой

После [определения облачных политик](./policy-definition.md) на основе [определенных рисков](./business-risk.md) вам потребуется создать практические рекомендации, соответствующие этим политикам, для ИТ-специалистов и разработчиков. Руководство по проектированию для управления облаком позволяет указать конкретные структурные, технологические и процессы на основе инструкций политики, созданных для каждой из [пяти дисциплин](../governance-disciplines.md).

Руководство по проектированию облачной системы управления должно определить варианты архитектуры и конструктивные шаблоны для каждого из основных компонентов инфраструктуры облачных развертываний, которые наилучшим образом соответствуют требованиям политики. Вместе с ними необходимо предоставить основное объяснение технологий, инструментов и процессов, которые будут поддерживать каждое проектное решение.

Несмотря на то, что анализ рисков и операторы политики могут, в некоторой степени, быть независимыми от облачной платформы, руководство по проектированию должно предоставить сведения о реализации для конкретной платформы, которые могут использоваться ИТ-специалистами и группами разработчиков при создании и развертывании облачных рабочих нагрузок. Сосредоточьтесь на архитектуре, средствах и функциях выбранной платформы при выборе проектного решения и предоставлении руководства.

Хотя руководства по проектированию облачной системы должны принимать во внимание некоторые технические сведения, связанные с каждым компонентом инфраструктуры, они не являются обширными техническими документами или спецификацией. Убедитесь, что руководства построили свои операторы политики и четкое решение по проектированию состояния в формате, который легко понять и на что они ссылаются.

<!-- markdownlint-enable MD033 -->

## <a name="using-the-actionable-governance-guides"></a>Использование практических руководств по управлению

Если вы планируете использовать платформу Azure для внедрения в облако, инфраструктура внедрения облаков предоставляет практические [руководства по управлению](../guides/index.md) , иллюстрирующие добавочный подход к модели управления инфраструктуры внедрения в облако. Эти руководства посвящены широкому спектру распространенных сценариев внедрения, включая бизнес-риски, требования к допуску и операторы политики, которые приходили к созданию минимально допустимого продукта системы управления (MVP). Эти руководства представляют собой синтез реального пользовательского интерфейса процесса внедрения в облако в Azure.

Хотя каждое внедрение облака имеет уникальные цели, приоритеты и трудности, эти примеры должны предоставлять хороший шаблон по превращению политики в руководство. Выберите самый подходящий в вашей ситуации сценарий в качестве отправной точки и примените его в соответствии с потребностями конкретной политики.

## <a name="next-steps"></a>Следующие шаги

Сформировав руководство по проектированию, установите процессы, обеспечивающие соблюдение политики, для обеспечения соответствия ее требованиям.

> [!div class="nextstepaction"]
> [Разработка процессов, обеспечивающих соблюдение политик](./processes.md)