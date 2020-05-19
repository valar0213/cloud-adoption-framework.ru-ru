---
title: Начало работы. повышение надежности с помощью правильных элементов управления
description: Изучите основы повышения надежности с помощью элементов управления и базовых показателей управления.
author: JanetCThomas
ms.author: janet
ms.date: 04/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: c75b7a17c8c2676688f5221ec0e4d0f2ed0641a5
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2020
ms.locfileid: "83400214"
---
# <a name="get-started-improve-reliability-with-the-right-controls"></a>Начало работы. повышение надежности с помощью правильных элементов управления

Как применить нужные элементы управления для повышения надежности? Это поможет минимизировать сбои, связанные с несовпадениями в конфигурации, Организации ресурсов, базовых показателях безопасности или защите ресурсов. Действия, описанные в этом руководстве, помогут группе операций сбалансировать надежность и стоимость ИТ-портфеля и помочь группе управления в обеспечении согласованного применения баланса. Надежность также зависит от других ролей и функций. В этой статье сопоставлены различные вспомогательные функции, помогающие создать выравнивание между участниками группы.

Управление операциями — это равные партнеры в рамках корпоративной надежности. Решения, принятые в отношении рабочих методик, устанавливают базовый уровень надежности. Подходы, используемые для того, чтобы управлять общей средой, обеспечивают согласованность во всех ресурсах. Первые два шага в этом руководстве помогут обоим командам начать работу. Хотя они перечислены последовательно, выполнение следующих шагов может осуществляться параллельно. Последующие шаги помогут вам быстро начать работу над всеми надежными решениями на всем предприятии.

![Приступая к работе с корпоративной надежностью](../_images/get-started/reliability-map.png)

## <a name="step-1-establish-operations-management-requirements"></a>Шаг 1. Определение требований к управлению операциями

Все рабочие нагрузки не создаются равными. В любой среде существуют рабочие нагрузки с прямым и постоянным влиянием на бизнес. Кроме того, предусмотрена поддержка бизнес-процессов и рабочих нагрузок, которые оказывают меньшее влияние на общий бизнес. На этом шаге группа облачных операций определяет и реализует начальные требования для поддержки всего ИТ.

**Результатам**

- Реализуйте базовый план управления для определения стандартных операций, необходимых для всех рабочих нагрузок.
- Согласуйте бизнес-обязательства с группой облачных стратегий, чтобы разработать план для расширенных операций и требований к устойчивости.
- Разверните свой базовый план управления, если для большинства рабочих нагрузок требуются дополнительные операции.
- Примените расширенные требования к зонам и ресурсам, которые поддерживают рабочие нагрузки с более высоким уровнем важности.
- Задокументируйте решения по работе с портфелем ИТ в [книге Operations Management](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx).

**Рекомендации по поддержке готовности к завершению.**

- **[Базовый план управления](../manage/considerations/discipline.md):**

  - [Инвентаризация и видимость](../manage/considerations/inventory.md): [собственные средства облака](../manage/azure-management-guide/inventory.md) могут помочь в [собрании данных](../manage/monitor/data-collection.md), [настройке оповещений](../manage/monitor/index.md)и реализации [платформы мониторинга](../manage/monitor/index.md) , которая лучше подходит для вашей операционной модели.
  - [Оперативное соответствие](../manage/considerations/operational-compliance.md). наибольшие проценты простоев обычно происходят из изменений в конфигурации ресурсов или при неудовлетворительных приемах обслуживания. Следуйте инструкциям [руководства по управлению Azure Server](../manage/azure-server-management/index.md) для реализации собственных средств Cloud для управления исправлениями и изменения конфигурации ресурсов.
  - [Защита и восстановление](../manage/considerations/protect.md): сбои неизбежны на любой платформе. В случае нарушения работы подготовьте [решения резервного копирования и восстановления](../manage/azure-management-guide/protect-recover.md) , чтобы минимизировать продолжительность сбоев.

- **[Дополнительные операции](../manage/design-principles.md).** используйте базовый план управления в качестве основы для общения с [деловыми](../manage/considerations/business-alignment.md) обобщением, чтобы создать ясность в отношении [критических](../manage/considerations/criticality.md), [бизнес-последствий](../manage/considerations/impact.md)и [обязательств по эксплуатации](../manage/considerations/commitment.md). Деловое выравнивание помогает количественным и проверенным запросам на [Расширенные базовые показатели](../manage/azure-management-guide/enhanced-baseline.md), управление конкретными [технологическими платформами](../manage/azure-management-guide/workload-specialization.md)или [операции, связанные с рабочей нагрузкой](../manage/azure-management-guide/platform-specialization.md).

- **Руководство по проверке архитектуры:** Для удовлетворения требований к операциям могут потребоваться изменения архитектуры на уровне рабочей нагрузки. [Инфраструктура архитектуры Azure](https://docs.microsoft.com/azure/architecture/framework/cost/tradeoffs) и [Проверка архитектуры Azure](https://docs.microsoft.com/assessments?id=azure-architecture-review) могут помочь в обсуждении этих бесед с техническим владельцем определенной рабочей нагрузки.

<!-- markdownlint-disable MD033 -->
<br>

| Команда, подучетная запись | Ответственные и вспомогательные команды |
| --- | --- |
| <li> Группа по эксплуатации облака | <li> Группа по облачной стратегии <li> Группа по внедрению облака <li> Группа по системе управления облаком <li> Облачный центр для ИТ и централизованного ИТ |

## <a name="step-2-consistently-apply-the-management-baseline"></a>Шаг 2. согласованное применение базового плана управления

Для обеспечения корпоративной надежности требуется единообразное применение базовых показателей управления. Такая согласованность обусловлена соответствующей корпоративной политикой, ИТ процессами и автоматизированными инструментами для управления реализацией базовых показателей для всех затронутых ресурсов.

**Результатам**

- Обеспечьте правильное применение базовых показателей управления для всех затронутых систем.
- Задокументируйте политики согласованности ресурсов, процессы и руководство по проектированию в [шаблоне дисциплины согласованности ресурсов](../govern/resource-consistency/template.md).

**Рекомендации по поддержке готовности к завершению.**

- Убедитесь, что все рабочие нагрузки и ресурсы соответствуют [соглашениям об именовании и маркировке](../ready/azure-best-practices/naming-and-tagging.md) , и [применяйте соглашения о тегах с помощью политики Azure](https://docs.microsoft.com/azure/governance/policy/tutorials/govern-tags)с особым выделением тегов для "критическость".
- Если вы не знакомы с Cloud управление, установите [политики управления, процессы и дисциплины](../govern/index.md) , используя управляемую методологию.
- Если вы не знакомы с дисциплиной управления затратами, рассмотрите [статью улучшения управления затратами](../govern/guides/complex/cost-management-improvement.md)и сосредоточьтесь на разделе [Реализация](../govern/guides/complex/cost-management-improvement.md#incremental-improvement-of-the-best-practices) .

> [!NOTE]
> **Действия по запуску отношений надежности с другими командами:** Различные решения в рамках жизненного цикла внедрения в облако могут оказать прямое воздействие на надежность. Следующие шаги помогают описать партнерство и вспомогательные усилия, необходимые для обеспечения согласованной надежности в портфеле ИТ.

<!-- markdownlint-disable MD033 -->
<br>

| Команда, подучетная запись | Ответственные и вспомогательные команды |
| --- | --- |
| <li> Группа по системе управления облаком | <li> Группа по облачной стратегии <li> Группа по эксплуатации облака <li> Облачный центр для ИТ и централизованного ИТ |

## <a name="step-3-define-your-strategy"></a>Шаг 3. Определение стратегии

**Результатам**

- Записывайте мотивации, результаты и деловое обоснование в [шаблоне стратегии и плана](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx).
- Убедитесь, что базовый план управления обеспечивает операционную поддержку, которая соответствует стратегическому направлению внедрения в облако.

**Рекомендации по поддержке готовности к завершению.**

- Основные [сведения о причинах](../strategy/motivations.md): критические бизнес-события и некоторые причины миграции обычно учитывают стоимость, что повышает важность управления затратами для всех последующих усилий. Другие посторонние решения, связанные с инновациями или ростом благодаря миграции, могут быть сосредоточены на высшей прибыли. Понимание причин помогает понять, насколько высокий уровень управления затратами на приоритет.
- [Результаты бизнеса](../strategy/business-outcomes/index.md). Некоторые финансовые результаты, как правило, чувствительны к чрезвычайно затратам. Когда желаемые результаты сопоставляются с финансовыми метриками, следует заранее привкладываться в систему управления затратами.
- [Коммерческое обоснование](../strategy/cloud-migration-business-case.md). Деловое обоснование служит обобщенным представлением общего финансового плана для внедрения в облако. Это может быть хорошим источником для первоначальных усилий по бюджетированию.

Стратегические решения напрямую влияют на надежность, истечение жизненного цикла внедрения и в долгосрочные операции. Стратегическая ясность повышает надежность.

<!-- markdownlint-disable MD033 -->
<br>

| Команда, подучетная запись | Ответственные и вспомогательные команды |
| --- | --- |
| <li> Группа по облачной стратегии | <li> Группа по системе управления облаком <li> Группа по эксплуатации облака <li> Облачный центр для ИТ и централизованного ИТ |

## <a name="step-4-develop-a-cloud-adoption-plan"></a>Шаг 4. Разработка плана внедрения в облако

Цифровая организация (или анализ существующего ИТ-портфеля) может помочь в проверке делового обоснования и предоставить полное представление об общем ИТ-портфеле. План внедрения обеспечивает ясность действий во время перехода. Согласование этого плана и анализа цифровых площадей предоставляет средства планирования для будущих зависимостей управления операциями. Понимание плана также приглашает группы облачных операций в циклы разработки для оценки и планирования любых изменений в базовом плане управления, необходимых для предоставления операций рабочей нагрузки.

**Результатам**

- Обновите [шаблон стратегии и плана](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) , чтобы отразить изменения, необходимые для реализации требуемой стратегии. Записанные изменения могут включать следующее:
  - Оценка существующего цифрового пространства.
  - План внедрения в облако, отражающий необходимые изменения и связанные с ним работы.
  - Организационное изменение, необходимое для предоставления плана.
  - План для решения навыков, необходимых для того, чтобы существующая группа успешно выполнила необходимую работу.
- Работа с группой управления для согласования моделей затрат и моделей прогнозирования, включая усилия по началу оптимизации расходов с помощью количественного анализа.

**Рекомендации по поддержке готовности к завершению.**

- [Сбор данных инвентаризации](../digital-estate/inventory.md). Создайте источник данных для анализа цифрового пространства перед внедрением.
- [Рекомендации по переносу Azure](../plan/contoso-migration-assessment.md). Используйте службу "миграция Azure" для сбора данных инвентаризации.
- [Инкрементное обоснование](../digital-estate/rationalize.md#incremental-rationalization). Во время инкрементного обоснования количественный анализ может выявляет облачные кандидаты для целей бюджетирования.
- [Выровняйте модели затрат и модели прогнозирования](../digital-estate/calculate.md). Используйте службу "Управление затратами Azure" для согласования моделей затрат и прогнозов путем [создания бюджетов](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-create-budgets?toc=/azure/cloud-adoption-framework/toc.json&bc=/azure/cloud-adoption-framework/_bread/toc.json).
- [Создайте план внедрения в облако](../plan/plan-intro.md#build-your-cloud-adoption-plan). Создайте план с рабочей нагрузкой, активами и сведениями о временной шкале.

<!-- markdownlint-disable MD033 -->
<br>

| Команда, подучетная запись | Ответственные и вспомогательные команды |
| --- | --- |
| <li> Группа по облачной стратегии | <li> Группа по внедрению облака <li> Группа по системе управления облаком <li> Группа по эксплуатации облака <li> Облачный центр для ИТ и централизованного ИТ |

## <a name="step-5-implement-landing-zone-best-practices"></a>Шаг 5. Реализация рекомендаций для целевой зоны

Методология готовности облачной инфраструктуры внедрения сосредоточена на разработке целевых зон для размещения рабочих нагрузок в облаке. Во время реализации зоны размещения несколько решений могут повлиять на операции. Обратитесь к группе облачных операций, чтобы помочь в обзоре зоны для улучшения операций. Также ознакомьтесь с группой по управлению облаком, чтобы узнать о политиках согласованности ресурсов и рекомендациях по проектированию, которые могут повлиять на структуру целевой зоны.

**Результатам**

- Разверните одну или несколько целевых зон, способных размещать рабочие нагрузки в краткосрочном плане внедрения.
- Убедитесь, что все целевые зоны соответствуют принятым решениям и требованиям к согласованности ресурсов.

**Рекомендации по поддержке готовности к завершению.**

- [Улучшение операций размещения зоны](../ready/considerations/landing-zone-operations.md). рекомендации по улучшению операций в рамках определенной целевой зоны.

<!-- markdownlint-disable MD033 -->
<br>

| Команда, подучетная запись | Ответственные и вспомогательные команды |
| --- | --- |
| <li> Группа по внедрению облака | <li> Группа по эксплуатации облака <li> Группа по облачной стратегии <li> Группа по системе управления облаком <li> Облачный центр для ИТ и централизованного ИТ |

## <a name="step-6-complete-waves-of-adoption-effort-and-change"></a>Шаг 6. выполнение волновых усилий по внедрению и изменение

На долгосрочные операции могут влиять решения, сделанные во время перехода и внедрения инноваций. Поддержание согласованного выравнивания на ранних этапах процесса внедрения помогает устранять барьеры в рабочих выпусках и сокращает усилия, необходимые для адаптации новых решений к методикам управления операциями.

**Результатам**

- Протестируйте готовность рабочих развертываний в рабочей среде с помощью политик согласованности ресурсов.
- Проверяйте соответствие требованиям руководства по проектированию согласованности ресурсов и требований к операциям.
- Задокументируйте все расширенные требования к операциям в [книге Operations Management](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx).

**Рекомендации по поддержке готовности к завершению.**

- [Контрольный список готовности среды](../migrate/migration-considerations/prerequisites/planning-checklist.md)
- [Контрольный список перед продвижением](../migrate/migration-considerations/optimize/ready.md)
- [Контрольный список рабочей версии](../migrate/migration-considerations/optimize/promote.md)

<!-- markdownlint-disable MD033 -->
<br>

| Команда, подучетная запись | Ответственные и вспомогательные команды |
| --- | --- |
| <li> Группа по внедрению облака | <li> Группа по облачной стратегии <li> Группа по эксплуатации облака <li> Группа по системе управления облаком <li> Облачный центр для ИТ и централизованного ИТ |

## <a name="value-statement"></a>Оператор значения

Описанные выше действия помогут реализовать необходимые элементы управления и процессы, которые необходимы для обеспечения надежности всего предприятия и всех размещенных ресурсов.