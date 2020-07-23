---
title: Планирование миграции центра Azure Stack
description: Планирование миграции центра Azure Stack
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/19/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: fd756ec02305c2bdc9a5c6d106f6b5b4c170c60c
ms.sourcegitcommit: 9163a60a28ffce78ceb5dc8dc4fa1b83d7f56e6d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2020
ms.locfileid: "86452460"
---
# <a name="plan-for-azure-stack-hub-migration"></a>Планирование миграции центра Azure Stack

В этой статье предполагается, что вы проверили, как [интегрировать Azure Stack в облачную стратегию](./index.md) и что ваш путешествие соответствует примерам в этой статье.

Прежде чем переходить непосредственно к усилиям по миграции, важно правильно задать ожидания для Azure и центра Azure Stack. Это помогает избежать ошибок и задержки в проекте. Ключом к успешной реализации является хорошее понимание того, когда следует использовать Azure и когда использовать центр Azure Stack.

## <a name="digital-estate-alignment"></a>Выравнивание цифровых площадок

Это начинается с нескольких простых вопросов, которые необходимо запросить при выполнении [рационализации цифровых площадок](../../digital-estate/index.md).

- Что такое мотивация для сохранения приложений и данных в локальной среде, например нормативных требований, сила притяжения данных или требования соответствия?
- Какие конкретные требования к нормативным требованиям или соответствия требованиям влияют на принятие решения в центре обработки данных?
- Как будет действовать перенос данных на уровень конфиденциальности?
- Является ли миграция определена как модернизацииное путешествие?
- Если да, вы определили следующие шаги и цели, необходимые после миграции?
- Каковы требования соглашения об уровне обслуживания, RPO, RTO и доступности?

Для некоторых рабочих нагрузок эта информация будет загорюча беседы о значении в Azure и центре Azure Stack для этой рабочей нагрузки.

## <a name="assessment-best-practices"></a>Рекомендации по оценке

Рекомендации по [оценке цифровых площадок с помощью службы "миграция Azure](../../plan/contoso-migration-assessment.md) " могут ускорить оценку и выравнивание рабочих нагрузок и ресурсов в цифровом расположении. Эта рекомендация позволяет получить представление о полном портфеле ИТ. Кроме того, он позволяет выявление технических требований к емкости, масштабированию и настройке, чтобы помочь вам в переносе.

Используя правильные данные оценки, группа может сделать выбор и установить более четкие приоритеты при оценке параметров для платформ общедоступных или частных облаков в Azure.

## <a name="planning-best-practices"></a>Рекомендации по планированию

Следующие ресурсы помогут понять различия между Azure и центром Azure Stack.

- [Azure Stack обзор и план](https://azure.microsoft.com/resources/videos/ignite-2018-azure-stack-overview-and-roadmap/)
- [Планирование емкости для Azure Stack](https://docs.microsoft.com/azure/azure-stack/capacity-planning)
- [Руководство. Интеграция центра обработки данных в Azure Stack Hub](https://docs.microsoft.com/azure-stack/operator/azure-stack-customer-journey)
- [Возможности виртуальных машин Azure Stack](https://docs.microsoft.com/azure-stack/user/azure-stack-vm-considerations?view=azs-1910)

Получив представление о наилучшей платформе для каждой рабочей нагрузки, вы можете интегрировать эти решения в [план внедрения облака](../../plan/template.md) , чтобы управлять миграцией общедоступных и частных облаков как единое согласованное.

## <a name="next-step-prepare-your-environment-for-azure-stack-hub-migrations"></a>Следующий шаг: подготовка среды для миграции Azure Stack концентратора

Приведенный ниже список статей поможет вам найти рекомендации в конкретных точках в процессе внедрения в облако. Первая статья о [готовности среды](./ready.md) — предлагаемый следующий шаг.

- [Готовность окружающей среды](./ready.md)
- [Оценка рабочих нагрузок для центра Azure Stack](./migrate-assess.md)
- [Развертывание рабочих нагрузок в центре Azure Stack](./migrate-deploy.md)
- [Управление центром Azure Stack](./govern.md)
- [Управление Azure Stack Hub](./manage.md)