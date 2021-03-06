---
title: Процессы обеспечения соответствия политикам управления затратами
description: Используйте инфраструктуру внедрения в облаке для Azure, чтобы изучить подход к созданию процессов, которые поддерживают дисциплину управления затратами.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 3e1a6b1b562242c77e6c3e35b43eb2e464736673
ms.sourcegitcommit: 07d56209d56ee199dd148dbac59671cbb57880c0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/26/2020
ms.locfileid: "88883813"
---
# <a name="cost-management-policy-compliance-processes"></a>Процессы обеспечения соответствия политикам управления затратами

В этой статье рассматривается подход к созданию процессов, которые поддерживают эффективную [дисциплину управления затратами](./index.md). Эффективное управление облачными затратами начинается с повторяющихся неавтоматизированных процессов, разработанных для поддержки соответствия политике. Это требует постоянного вовлечения группы управления облачными специалистами и заинтересованных заинтересованных лиц для просмотра и обновления политики и обеспечения соответствия политике. Кроме того, многие текущие процессы мониторинга и принудительного применения можно автоматизировать или дополнить с помощью набора инструментов, чтобы сократить расходы на управление и обеспечить более быстрый отклик на отклонение политики.

## <a name="planning-review-and-reporting-processes"></a>Планирование, проверка и составление отчетности

Лучшие средства Управления затратами в облаке хороши только в тех процессах и политиках, которые они поддерживают. Ниже приведен набор примеров процессов, часто использующихся в дисциплине "Управление затратами". Используйте эти примеры в качестве отправной точки при планировании процессов, которые позволят вам продолжить обновлять политику затрат на основе бизнес-изменений и отзывов от коммерческих групп, подчиняются руководству по управлению затратами.

**Первоначальная оценка рисков и планирование:** В рамках первоначального внедрения дисциплины управления затратами вы определяете основные бизнес-риски и отклонения, связанные с облачными затратами. Используйте эти сведения для обсуждения бюджета и рисков, связанных с затратами, с членами своих бизнес-групп и команд по безопасности и для разработки базового плана политик для снижения этих рисков, чтобы установить начальную стратегию управления.

**Планирование развертывания:** Перед развертыванием любого ресурса Установите Прогнозируемый бюджет на основе ожидаемого распределения облака. Убедитесь, что информация о владельцах и учетных данных для развертывания задокументирована.

**Ежегодное планирование:** Ежегодно выполните сводный анализ всех развернутых и развернутых ресурсов. Приведите в соответствие бюджеты по бизнес-подразделениям, отделам, командам и другим соответствующим подразделениям, чтобы расширить возможности внедрения самообслуживания. Убедитесь, что руководитель каждого платежного подразделения осведомлен о бюджете и о том, как отслеживать расходы.

Это лучшее время, чтобы сделать предварительное ассигнование средств или предварительную покупку для максимизации дисконтирования. Разумно привести годовой бюджет в соответствие с финансовым годом поставщика облачных ресурсов, чтобы в дальнейшем выгодно использовать варианты скидок в конце года.

**Квартальное планирование:** На квартальной основе просматривайте бюджеты с каждым лидером единицы выставления счетов, чтобы выстроить прогноз и фактические расходы. Если имеются изменения плана или неожиданные шаблоны расходов, приведите в соответствие бюджет и перераспределите его.

Этот процесс ежеквартального планирования также является хорошим временем для ознакомления с текущим членством вашей команды по управлению облаком с учетом разрывов знаний, связанных с текущими или будущими бизнес-планами. Пригласите соответствующих специалистов и владельцев рабочих нагрузок для участия в обзорах и планировании в качестве временных консультантов или постоянных участников вашей команды.

Обучение **и обучение:** На бимонсли можно предложить обучающий семинар, чтобы обеспечить актуальность бизнес-и ИТ-специалистов в соответствии с последними требованиями политики управления затратами. В рамках этого процесса вы можете проверить и обновить документацию, руководство или другие обучающие материалы, чтобы убедиться, что они синхронизированы с последними инструкциями корпоративной политики.

**Ежемесячные отчеты:** По месячной основе отчет о фактических расходах задается по прогнозу. Уведомляйте руководителей платежных подразделений о любых неожиданных отклонениях.

Эти базовые процессы помогут привести в соответствие расходы и заложить основу для дисциплины "Управление затратами".

## <a name="processes-for-ongoing-monitoring"></a>Процессы для постоянного мониторинга

Успешная стратегия управления затратами зависит от видимости за прошлые, текущие и запланированные будущие расходы, связанные с облаком. Без возможности анализировать соответствующие метрики и данные имеющихся расходов вы не можете выявить изменения в рисках или обнаружить нарушения рискоустойчивости. Текущие процессы управления, описанные выше, требуют данных о качестве, чтобы обеспечить возможность изменения политики для оптимальной защиты инфраструктуры от изменяющихся бизнес-требований и облачного потребления.

Убедитесь, что ваши ИТ-команды реализовали автоматизированные системы мониторинга расходов на облако и потребления в случае незапланированных отклонений от ожидаемых расходов. Предоставьте системы отчетности и оповещений, чтобы быстро обнаруживать потенциальные нарушения политики и устранять связанные с ними риски.

## <a name="compliance-violation-triggers-and-enforcement-actions"></a>Триггеры нарушения соответствия и принудительные действия

При обнаружении нарушений следует предпринять принудительные действия для обеспечения соблюдения политики. Вы можете автоматизировать большинство триггеров нарушения с помощью средств, описанных в [цепочке инструментов Управления затратами для Azure](./toolchain.md).

Ниже приведены примеры триггеров.

- **Месячные отклонения бюджета:** Обсудите любые отклонения в месячных расходах, превышающие соотношение прогнозируемых и фактических значений в 20% с руководителем единицы выставления счетов. Запишите решение проблемы и изменения запланированного бюджета.
- **Скорость внедрения:** Любое отклонение на уровне подписки, превышающее 20%, вызовет проверку с руководителем единицы выставления счетов. Запишите решение проблемы и изменения запланированного бюджета.

## <a name="next-steps"></a>Дальнейшие шаги

Используйте [шаблон дисциплины управления затратами](./template.md) для документирования процессов и триггеров, которые совпадают с текущим планом внедрения в облаке.

Рекомендации по выполнению политик управления затратами по согласованию с планами внедрения см. в статье [улучшение специализации в управлении затратами](./discipline-improvement.md).

> [!div class="nextstepaction"]
> [Улучшения дисциплины "Управление затратами"](./discipline-improvement.md)
