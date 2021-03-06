---
title: Руководства по управлению облаком
description: Ознакомьтесь с руководствами по управлению облаком, иллюстрирующими рекомендации по поэтапному подходу к любому сценарию управления.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: a39440dff04e267a80fa085dfdf6c565d33762cb
ms.sourcegitcommit: 8b82889dca0091f3cc64116f998a3a878943c6a1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/09/2020
ms.locfileid: "89604845"
---
# <a name="cloud-governance-guides"></a>Руководства по управлению облаком

В практических руководствах по системе управления, приведенных в этом разделе, описан поэтапный подход, реализуемый моделью управления Cloud Adoption Framework на основе ранее описанной [методологии управления](../methodology.md). Вы можете создать гибкую систему управления облаком, которая будет развиваться с учетом изменяющихся потребностей в рамках любого сценария управления облаком.

## <a name="review-and-adopt-cloud-governance-best-practices"></a>Проверка и применение рекомендаций по управлению облачными решениями

Чтобы приступить к внедрению облачных технологий, выберите одно из следующих руководств по системе управления. Каждое руководство включает ряд рекомендаций, основанных на сценарии для вымышленного клиента. Читателям, которые еще не знакомы с поэтапным подходом в рамках модели управления Cloud Adoption Framework, мы рекомендуем ознакомиться с общей теорией управления, прежде чем следовать руководствам.

- [Руководство по организации системы управления для стандартных предприятий.](./standard/index.md) Рекомендации для большинства организаций основаны на предпочтительной модели с двумя подписками, предназначенной для развертываний в нескольких регионах, но не охватывающей общедоступные и национальные или правительственные облака.

> [!div class="nextstepaction"]
> [Руководство по организации системы управления для стандартных предприятий](./standard/index.md)

- [Руководство по организации системы управления для сложных предприятий](./complex/index.md) Рекомендации для предприятий, которые управляются несколькими независимыми ИТ-подразделениями или которые охватывают общедоступные и национальные или правительственные облака.

> [!div class="nextstepaction"]
> [Руководство по организации системы управления для сложных предприятий](./complex/index.md)

## <a name="an-incremental-approach-to-cloud-governance"></a>Поэтапный подход к организации облачной системы управления

## <a name="choose-a-governance-guide"></a>Выбор руководства по организации системы управления

Из этих руководств вы узнаете, как реализовать MVP системы управления. В каждом руководстве показано, как команда по управлению облачными решениями может на шаг опережать команды по внедрению облачных решений в рамках сотрудничества для ускорения внедрения. Модель управления Cloud Adoption Framework регламентирует применение системы управления, начиная с реализации базовой системы и ее последующим усовершенствованием и развитием.

Для начала выберите один из предложенных ниже вариантов. Эти варианты отражают сценарии вымышленных клиентов. Они разделены на основе сложности структуры предприятий, чтобы упростить выбор и облегчить навигацию. Ваше решение может быть более сложным. В следующей таблице представлены различия между двумя стратегиями.

> [!WARNING]
> Вам с самого начала может потребоваться более надежная система управления. В таких случаях следует рассмотреть возможности [целевой зоны CAF корпоративного уровня](../../ready/enterprise-scale/index.md). Этот подход предназначен для команд по внедрению, цель которых — в средние сроки (в течение 24 месяцев) разместить в облаке более 1000 ресурсов (компонентов инфраструктуры, приложений или данных). Целевая зона CAF корпоративного уровня — это стандартное решение для реализации сложных систем управления, связанных с масштабными усилиями по внедрению облака.
<!-- -->
> [!NOTE]
> Маловероятно, что инструкции в каком-то из этих руководств будут полностью соответствовать вашему сценарию. Ваша задача — выбрать подходящее руководство в качестве отправной точки, чтобы на основе предоставленных сведений привести решения в соответствие с определенными критериями.

### <a name="business-characteristics"></a>Характеристики бизнеса

| Характеристика | Стандартная организация | Сложное предприятие |
|---|---|---|
| Географическое расположение (страна или геополитический регион) | Клиенты или сотрудники находятся преимущественно в одном регионе. | Клиенты или сотрудники находятся в разных регионах или им требуется использовать национальные облака. |
| Затронутые подразделения | Подразделения, совместно использующие общую ИТ-инфраструктуру | Разные подразделения, не использующие совместно общую ИТ-инфраструктуру. |
| Бюджет на ИТ | Единый ИТ-бюджет. | Отдельный бюджет для нескольких бизнес-подразделений и валют. |
| Инвестиции в ИТ | Инвестиции с учетом капитальных затрат планируются один раз в год и обычно покрывают только основные операции обслуживания. | Инвестиции с учетом капитальных затрат планируются один раз в год и часто покрывают обслуживание и цикл обновления длительностью от 3 до 5 лет. |

### <a name="current-state-before-adopting-cloud-governance"></a>Текущее состояние перед внедрением системы управления облачными решениями

| Состояние | Стандартное предприятие | Сложное предприятие |
|---|---|---|
| Центр обработки данных или сторонние поставщики услуг размещения | Меньше пяти центров обработки данных. | Больше пяти центров обработки данных. |
| Сеть | Отсутствие глобальной сети или 1–2 поставщика глобальных сетей. | Сложная или глобальная сеть. |
| Идентификация | Один лес и один домен. | Сложная система с несколькими лесами и несколькими доменами. |

<!-- docutune:casing "Cost Management" "Security Baseline" -->

### <a name="desired-future-state-after-incremental-improvement-of-cloud-governance"></a>Требуемое будущее состояние после поэтапного улучшения системы облачного управления

| Состояние | Стандартная организация | Сложное предприятие |
|---|---|---|
| Управление затратами: учет расходов на облако | Модель виртуальных счетов. Счета выставляются централизованно через ИТ-подразделение. | Модель возвратных платежей. Счета могут выставляться через механизм ИТ-закупок. |
| Базовые показатели безопасности: защищенные данные | Финансовые данные и интеллектуальная собственность компании. Некоторые клиентские данные. Отсутствуют внешние требования к обеспечению соответствия. | Много разных наборов финансовых и персональных данных клиентов. Могут быть внешние требования к обеспечению соответствия. |

## <a name="caf-enterprise-scale-landing-zone"></a>Целевая зона CAF корпоративного уровня

[Целевая зона CAF корпоративного уровня](../../ready/enterprise-scale/index.md) помогает максимально эффективно использовать возможности облачной платформы Azure с соблюдением имеющихся требований к безопасности и системе управления.

По сравнению с традиционными локальными средами, Azure позволяет группам разработчиков рабочих нагрузок и их бизнес-спонсорам воспользоваться преимуществами гибкости развертывания, которые предлагают облачные платформы. Когда процесс внедрения облачных технологий охватывает критически важные данные и рабочие нагрузки, подобная гибкость может противоречить требованиям корпоративной безопасности и соответствия политикам, установленным ИТ-командами. Это особенно актуально для крупных предприятий, на которых установлены сложные требования к управлению и нормативные требования.

Архитектура целевой зоны CAF корпоративного уровня предназначена для решения этих задач на ранних этапах жизненного цикла внедрения с помощью архитектур, реализаций и рекомендаций, которые помогут согласовать требования команд по внедрению облака и центрального ИТ-отдела во время внедрения корпоративного облака. В основе этого подхода лежит принцип общей архитектуры служб и хорошо управляемых целевых зон.

Целевая зона CAF корпоративного уровня развертывает изолированное облако на платформе Azure, в котором интегрированы процессы управления, нормативные требования и процессы безопасности, предписываемые политиками системы управления. В пределах этой виртуальной границы целевая зона CAF корпоративного уровня предлагает примеры моделей для развертывания рабочих нагрузок, обеспечивая согласованное соответствие требованиям, а также предоставляет организации основные рекомендации по разделению ролей и обязанностей в облаке.

### <a name="caf-enterprise-scale-landing-zone-qualifications"></a>Квалификации целевой зоны CAF корпоративного уровня

Даже небольшие команды могут воспользоваться преимуществами архитектуры и рекомендаций для целевой зоны CAF корпоративного уровня. Наша цель — продолжить оптимизацию реализаций целевой зоны CAF корпоративного уровня, чтобы сделать их более удобными для небольших команд. В настоящее время этот подход предназначен для команд центрального ИТ-отдела, управляющих большими облачными средами.

Подход на основе [целевых зон CAF корпоративного уровня](../../ready/enterprise-scale/index.md) предназначен для команд по внедрению, задача которых — в средние сроки (в течение 24 месяцев) **разместить в облаке более 1000 ресурсов (компонентов инфраструктуры или ресурсов данных)** .

Организации, отвечающие приведенным ниже критериям, также могут начать с реализации [целевой зоны CAF корпоративного уровня](../../ready/enterprise-scale/index.md).

- Ваше предприятие обязано соблюдать нормативные требования, предписывающие применение централизованных средств мониторинга и аудита.
- Вам необходимо поддерживать общую политику и соответствие требованиям управления для основных служб, а также обеспечить централизованный ИТ-контроль над ними.
- Функционирование вашей отрасли зависит от сложной платформы, для управления которой требуются комплексные средства и глубокое понимание предметной области. Как правило, это касается крупных предприятий, работающих в сфере финансов, нефтегазовой промышленности и производственных отраслях.
- Существующие политики управления ИТ требуют более тесного сопоставления с существующими возможностями, даже на раннем этапе внедрения.

## <a name="next-steps"></a>Дальнейшие действия

Выберите одно из следующих руководств:

> [!div class="nextstepaction"]
> [Руководство по организации системы управления для стандартных предприятий](./standard/index.md)
>
> [Руководство по организации системы управления для сложных предприятий](./complex/index.md)
