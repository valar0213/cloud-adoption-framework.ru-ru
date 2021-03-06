---
title: Приступая к работе. Создание группы по управлению облаком
description: Создание области, конечных результатов и возможностей группы управления для подготовки к успешному управлению облаком.
author: JanetCThomas
ms.author: janet
ms.date: 05/15/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: e3683c652ef69b9cd327164a992966cff1ce4868
ms.sourcegitcommit: 8b82889dca0091f3cc64116f998a3a878943c6a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/09/2020
ms.locfileid: "89603040"
---
# <a name="get-started-build-a-cloud-governance-team"></a>Приступая к работе. Создание группы по управлению облаком

Группа управления облаком обеспечивает правильную оценку и управление рисками при внедрении облака и отказоустойчивостью. Группа определяет риски, которые не допускают бизнес, и преобразовывают риски в Управление корпоративными политиками.

![Приступая к созданию группы по управлению облаком](../../_images/get-started/governance-team-map.png)

## <a name="step-1-determine-whether-a-cloud-governance-team-is-needed"></a>Шаг 1. Определение необходимости в группе по управлению облаком

Официальное руководство по облачной инфраструктуре внедрения — всегда создавать группу управления облаком. Сначала группа может быть очень небольшой. Независимо от его размера, его роль важна. Если команда не нужна, группа или пользователь в существующей группе перехода должны согласиться с соблюдением обязанностей, связанных с функциями управления в [облаке](../../organize/cloud-governance.md).

**Результатам**

- Определите, нужна ли вам группа по управлению облаком.
- Выровняйте обязанности между командами, разработав межкомандную матрицу, которая определяет *ответственных, осведомленных, проконсультируйтесь и информированные (RACI)* стороны. Задокументируйте решение и ответственных лиц, используя [шаблон RACI](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/organize/raci-template.xlsx) на `Org Alignment` листе.

**Рекомендации по поддержке готовности к завершению.**

- [Функции управления облаком](../../organize/cloud-governance.md) могут быть уже распределены между несколькими пользователями или группами. Команда, которая проходит по названию "группа по управлению облаком", не важна, но необходимые возможности должны быть предоставлены с учетом субъекта или группы.
- Если долгосрочная стратегия внедрения в облако компании может быть доставлена из одной целевой зоны в одной облачной среде, объем операций управления и эксплуатации может быть достаточно мал для доставки одним человеком или одной группой. Эта группа вряд ли будет называться Cloud управление, так как она обслуживает множество функций, помимо Cloud управление. Даже для этой группы это руководство по началу работы может помочь в обеспечении этой важной функции управления.

<br>

| Команда, подучетная запись | Ответственные и вспомогательные команды |
| --- | --- |
| <li> Группа по облачной стратегии | <li> Группа по внедрению облака |

## <a name="step-2-align-with-other-teams"></a>Шаг 2. согласование с другими командами

Группа управления обеспечивает согласованность и соответствие набору общих политик. Эти политики берутся из текущего выравнивания с другими командами.

Прежде чем устанавливать политики или автоматизированное управление облаком, Группа управления облаком должна соответствовать другим командам, определенным в шаблоне RACI. Это позволит обеспечить выравнивание по критически важным темам, таким как безопасность, затраты, производительность, эксплуатация и развертывание. Шаги 4 и 5 могут помочь упростить выравнивание.

**Результатам**

- Обсуждение реализации текущего состояния и текущих планов внедрения с каждой командой.

**Рекомендации по поддержке готовности к завершению.**

- Изучите [стратегию и шаблон плана](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/plan/cloud-adoption-framework-strategy-and-plan-template.docx) вашей компании с членами группы "облачная стратегия", чтобы понять мотивацию, метрики и стратегию.
- Изучите план внедрения в Организации в [облаке](../../plan/template.md) с членами группы по внедрению в облако, чтобы понять временные сроки и приоритеты.
- Изучите [книгу Operations Management](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) Team, чтобы узнать о требованиях к эксплуатации и обязательствах, которые были установлены в бизнесе.

<br>

| Команда, подучетная запись | Ответственные и вспомогательные команды |
| --- | --- |
| <li> Группа по системе управления облаком | <li> Группа по облачной стратегии <li> Группа по внедрению облака <li> Группа по эксплуатации облака <li> Облачный центр для ИТ и специалистов по ИТ |

## <a name="step-3-establish-a-cadence-with-other-teams"></a>Шаг 3. Создание ритмичности с помощью других команд

Внедрение в облако обычно приходит на волны или выпуски. Обычная ритмичность, согласованная с этими выпусками, позволяет команде управления облаком проследить за рисками, которые будут представлены в следующей волновой области. Использование групп стратегии, внедрения и эксплуатации во время планирования и анализа также помогает группе управления оставаться в курсе рисков.

**Результатам**

- Создайте ритмичность с помощью вспомогательных групп. По возможности выровняйте этот ритмичность с циклами выпуска и планирования.
- Создайте отдельную ритмичность непосредственно с помощью группы облачных стратегий (или различных членов группы), чтобы ознакомиться с рисками, связанными со следующей волной внедрения, и оцените уровень отказоустойчивости группы для этих рисков.

**Рекомендации по поддержке готовности к завершению.**

- Дополнительные сведения о ритмичности для собраний см. в статье [управление облаком](../../organize/cloud-governance.md#deliverable).

<br>

| Команда, подучетная запись | Ответственные и вспомогательные команды |
| --- | --- |
| <li> Группа по системе управления облаком | <li> Группа по облачной стратегии <li> Группа по внедрению облака <li> Группа по эксплуатации облака |

## <a name="step-4-review-the-methodology"></a>Шаг 4. Проверка методологии

Чтобы повысить управляемость и работать с этим представлением в будущем, ознакомьтесь со статьей управление методологией облачной инфраструктуры внедрения.

**Результатам**

- Получите представление о методологии, подходе и реализации, поддерживающей управляющую методологию.

**Рекомендации по поддержке готовности к завершению.**

- Изучите [управляющую методологию](../../govern/methodology.md).

**Подгруппа для учетных записей:**

- Группа по управлению облаком позволяет определить концепцию и подход к управлению.

## <a name="step-5-complete-the-governance-benchmark"></a>Шаг 5. завершение тестирования производительности системы управления

Управление — это обширный раздел. Короткая оценка может помочь команде понять, где приступить к работе.

**Результатам**

- Пройдите оценку производительности управления на основе общения с различными заинтересованными лицами. Или попросите других команд выполнить оценку самостоятельно.

**Рекомендации по поддержке готовности к завершению.**

- Используйте [тестовый контроль производительности](../../govern/benchmark.md) для оценки потребностей и приоритетов управления.

**Подгруппа для учетных записей:**

- Группа по управлению облаком должна понимать пропуски, выявленные в контрольном тесте управления, а затем предоставлять направление управления, помогающее устранить эти промежутки.

## <a name="step-6-implement-the-initial-governance-best-practice-and-configuration"></a>Шаг 6. Реализация рекомендаций и конфигурации начального руководства

Управляемая методология включает два подхода к первоначальному руководству по управлению. Ознакомьтесь с каждым из подходов и реализуйте тот, который наиболее полно соответствует вашим потребностям.

**Результатам**

- Развертывание базовых средств управления и конфигураций Организации, которые необходимы для регулирования среды в течение следующих нескольких волновых усилий по внедрению.

**Рекомендации по поддержке готовности к завершению.**

- Рекомендации по настройке и реализации см. в статье [Создание начального плана управления облаком](../../govern/initial-foundation.md).

**Подгруппа для учетных записей:**

- Группа по управлению облаком предназначена для просмотра и реализации рекомендаций по управлению и первоначальной основы управления.

## <a name="step-7-continuously-improve-governance-maturity"></a>Шаг 7. непрерывное повышение зрелости управления

Управление необходимо увеличивать по мере завершения дополнительных усилий по внедрению в облако. Оставайтесь в курсе с текущим планом внедрения, чтобы обеспечить соответствие подхода к управлению и управлению ими.

**Результатам**

- Реализуйте улучшения управления, чтобы защититься от изменяющихся рисков и потребностей в управлении.

**Рекомендации по поддержке готовности к завершению.**

- Чтобы улучшить первоначальную систему управления, реализуйте [Расширенные сценарии](../../govern/foundation-improvements.md)управления.

**Подгруппа для учетных записей:**

- Группа по управлению облаком учитывается при согласовании с текущими планами внедрения.

## <a name="step-8-evaluate-landing-zone-changes"></a>Шаг 8. Оценка изменений в целевой зоне

После развертывания и расширения зон размещения могут возникнуть новые риски или нарушения управления. Периодически просматривайте конфигурации основной зоны, чтобы определить отклонения от политики, которые не перехватываются средствами управления, собственными в облаке. Убедитесь, что каждое развертывание целевой зоны соответствует рекомендациям по управлению зонами.

**Результатам**

- Помогите группе облачной платформы разрабатывать усовершенствования в целевой зоне, которая должна соответствовать политикам управления.

**Рекомендации по поддержке готовности к завершению.**

- Улучшите [Управление зоной](../../ready/considerations/landing-zone-governance.md)размещения.

**Подгруппа для учетных записей:**

- Группа управления облаком должна убедиться, что каждое развертывание размещенной зоны соответствует рекомендациям по управлению.

## <a name="step-9-adoption-handoffs"></a>Шаг 9. Внедрение хандоффс

По мере выполнения новых действий по внедрению группа внедрения в облако передает эксплуатационные обязанности группе облачных операций и группам управления в облаке. Оставайтесь в курсе с ритмичностью выпуска внедрения, чтобы обеспечить правильную документацию и выравнивание политик, а также помочь группе в обеспечении ответственности за рабочие нагрузки.

**Результатам**

- Регулярно просматривайте и примите хандоффс от других специалистов по внедрению в облако.

**Рекомендации по поддержке готовности к завершению.**

- Создайте процесс для [адаптации новых рабочих нагрузок и ресурсов](/azure/azure-resource-manager/custom-providers/concepts-resource-onboarding).

<br>

| Команда, подучетная запись | Ответственные и вспомогательные команды |
| --- | --- |
| <li> Группы внедрения в облако | <li> Группа по системе управления облаком <li> Группа по эксплуатации облака |

## <a name="whats-next"></a>Что дальше?

Все компании являются уникальными, и поэтому их потребности в управлении. Выберите уровень зрелости, соответствующий вашей организации, и используйте платформу внедрения облачных решений, чтобы ознакомиться с методиками, процессами и инструментами, которые помогут вам в этом.

По мере развития облачного управления группы могут расширить возможности работы с облаком в более быстром темпе. Непрерывные усилия по внедрению в облако обычно инициируют зрелости в ИТ. Чтобы гарантировать, что управление является частью разработки операций, разрабатывайте [группу облачных операций](./cloud-operations.md) или синхронизируйте с существующей группой облачных операций.
