---
title: Стратегия мониторинга в облаке
description: Получите представление о том, как определить эффективную стратегию мониторинга в облаке.
author: mgoedtel
ms.author: magoedte
ms.date: 06/18/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 86bc5245ba358d8f13e232f8342937b47588c7f7
ms.sourcegitcommit: 4e12d2417f646c72abf9fa7959faebc3abee99d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2020
ms.locfileid: "90776267"
---
<!-- cSpell:ignore SIEM Nagios Zabbix DIKW -->

# <a name="cloud-monitoring-guide-formulate-a-monitoring-strategy"></a>Руководство по мониторингу облака: Разработка стратегии мониторинга

По мере того, как вы простроили цифровое преобразование в облако, важно спланировать и разработать эффективную стратегию мониторинга облака с участием разработчиков, специалистов по эксплуатации и инженеров инфраструктуры. Стратегия должна быть ориентирована на рост, быть определена по меньшей мере, а затем последовательно уточнена; всегда соответствует потребностям бизнеса. Его результат представляет собой динамическую модальность операций, направленную на способность Организации заблаговременно отслеживать сложные распределенные приложения, от которых зависит бизнес.

## <a name="where-to-start"></a>Как начать работу?

Чтобы упростить путешествие в облако, используйте [этап стратегии](./index.md) и [плановый этап](../plan/index.md) инфраструктуры внедрения облачных технологий. Мониторинг влияет на мотивацию, результаты бизнеса и инициативы. Включите мониторинг на этапах стратегии и плана, ваших инициатив и проектов. Например, Узнайте, как первый проект внедрения устанавливает раннее управление операциями в Azure. Представьте себе, как должна выглядеть облачная Рабочая модель, включая роль мониторинга. Мониторинг лучше обслуживается с помощью подхода, основанного на службах, в качестве функции, где мониторинг является консультационной службой, а также поставщиком знаний для бизнеса и ИТ-потребителей.

Ниже приведены важные аспекты, которые сильно влияют на стратегию мониторинга звука.

- Отслеживайте работоспособность приложений на основе его компонентов и отношений с другими зависимостями. Начните с платформы облачных служб, ресурсов, сети и последнего приложения, собирая метрики и журналы там, где это применимо. Для модели гибридного облака включите локальную инфраструктуру и другие системы, на которых полагается приложение.

- Включите измерение взаимодействия конечного пользователя в плане мониторинга производительности приложений, копируя типичные взаимодействия клиента с приложением.

- Убедитесь, что требования безопасности соответствуют политике соответствия вашей организации требованиям безопасности.

- Выровняйте предупреждения о том, что считается важным и практичным инцидентом (например, предупреждениями и исключениями), и выровняйте серьезность с учетом важности инцидента и матрицы укрупнения срочности.

- Собирайте только те метрики и журналы, которые полезны, измеримы и идентифицируются для бизнеса и ИТ-организации.

- Определите план интеграции с существующими решениями ITSM, такими как "исправить" или "ServiceNow" для создания инцидентов или вышестоящего мониторинга. Определите, какие оповещения следует перенаправлять, требуется ли обогащение предупреждений для поддержки определенных требований к фильтрации и как настроить.

- Сведения о том, кому нужна видимость, что они должны видеть, а также о том, как их следует отображать в зависимости от их ролей и обязанностей.

В основе управления операциями ИТ ИТ – организациям необходимо обеспечить централизованное управление и делегирование в отношении подходов к созданию, эксплуатации и управлению ИТ – службами.

### <a name="initial-strategy-goals"></a>Начальные цели стратегии

В качестве архитектора или стратегического планировщика может потребоваться разработать раннюю стратегию управления операциями, при которой мониторинг играет важную роль. Рассмотрим следующие четыре результата:

1. Управляйте облачными рабочими службами, когда они переходят в рабочую среду, например в сеть, приложения, безопасность и виртуальная инфраструктура.

2. Примените ограниченные ресурсы, чтобы рационализировать существующие средства мониторинга, навыки и знания, а затем используйте облачный мониторинг, чтобы снизить сложность.

3. Сделайте решение для мониторинга более эффективным, более быстрым и плавным, масштабироваться и быстро изменять их.

4. Учетная запись для планирования и мониторинга узлов в Организации на основе облачных моделей. Приработайте к цели, чтобы сократить требования Организации от IaaS к PaaS, а затем к SaaS.

## <a name="determine-what-you-have"></a>Определение того, что у вас есть

Как эксперт по управляемости, вы можете тесно работать с Комитетом по управлению, архитектором и стратегическим планировщиком. Вы можете работать над формулировкой стратегии мониторинга, оценивая текущее состояние управления системами, включая людей, партнеров, аутсорсингы, средства, сложность, зазоры и риски. Оценка поможет определить приоритеты для набора обнаруженных проблем и выбрать основные возможности, которые улучшат текущую ситуацию. Определите также, какие службы, системы и данные, как правило, остаются в локальной среде как один важный результат. В идеале управление требуется для плана инициатив, но в прямой пропорции к известному периоду планирования. Обсуждение неизвестных проблем имеет большое значение.

## <a name="high-level-modeling"></a>Высокоуровневое моделирование

Так как бизнес определяет, какие службы следует переместить, необходимо тщательно вкладывать ресурсы. В локальной среде вы владеете всеми обязанностями для мониторинга и сильно инвестированы. Например, перемещения, сделанные в отношении служб SaaS, не устраняют ответственность за мониторинг. Вы решите, кому нужен доступ, кто получает оповещения и кому требуется доступ к аналитике как минимум. [Azure Monitor](/azure/azure-monitor/) и служба " [дуга Azure](https://azure.microsoft.com/services/azure-arc/) " — это службы Azure с гибкой адресацией сценариев мониторинга для всех четырех облачных моделей, а не только ресурсов в Azure. Вам нужно взглянуть на общие облачные модели, как показано ниже. Если вы используете Microsoft Office приложения, поставляемые службами [Microsoft 365](/microsoft-365/?view=o365-worldwide) в Организации, необходимо включить мониторинг безопасности и соответствия требованиям с помощью Microsoft 365 в дополнение к [центру безопасности Azure](/azure/security-center/). Сюда входят удостоверения, Управление конечными точками и мониторинг устройств за пределами корпоративной сети.

![Схема облачных моделей](./media/monitoring-strategy/cloud-models.png)

## <a name="monitoring-informs-strategy"></a>Стратегия наблюдения за согласованиями

Рассмотрим, где стратегия раннего мониторинга *информирует о стратегии*. Многие решения зависят от раннего мониторинга данных, чтобы создать план возможностей, который описывает ограниченные ресурсы и обеспечивает уверенность. Стратегиям также требуются реальные входные данные для мониторинга включения службы.

Учтите, что мониторинг ролей играет в стратегиях для постепенной защиты и защиты цифрового пространства:

- Журналы действий и мониторинг безопасности необходимы для измерения использования каталога и внешнего общего доступа к конфиденциальному содержимому, чтобы известить добавочный подход к уровню защиты функций и добиться правильного баланса с мониторингом конфиденциальности.

- Политики и базовые планы будут сообщать цели рациональности (миграция, прогноз и смена архитектуры), а также повысить уверенность в том, что данные и сведения можно перенести из локальной среды в облачные службы.

Далее в этом пошаговом окне вы узнаете о некоторых распространенных сценариях мониторинга или вариантах использования, которые помогут ускорить внедрение.

## <a name="formulate-a-monitoring-architecture"></a>Разработка архитектуры мониторинга

Определите текущую и будущую архитектуру управления системами, которая включает в себя мониторинг:

- Используйте ограниченные ресурсы для консолидации инвестиций в мониторинг.

- Решите, как мониторинг поможет реализовать будущие службы в ваших бизнес-целях: Облачный мониторинг высокомасштабируемых, устойчивых и глобально осведомленных облачных служб.

- Выровняйте наблюдение за будущими службами и ресурсами, которые будут отслеживаться в облаке.

- Выявление пропусков в трех измерениях (глубину, охват и между ними) модели работоспособности.

- Моделирование финансовых аспектов, затрат и факторов поддержки, которые поддерживают анализ выгодных затрат.

- Пошаговые решения для гибридных решений, которые необходимо выполнить.

Одним из принципов мониторинга является видимость службы. Чтобы служба, ресурс или компонент были полностью видны, необходимо сбалансировать три стороны этого принципа:

1. Подробное наблюдение за счет сбора значимых и соответствующих сигналов.
2. Отслеживайте сквозную или ширину с самого нижнего уровня стека вплоть до приложения.
3. Восточная часть — основное внимание уделяется его аспектам работоспособности (доступность, производительность, безопасность и непрерывность).

![Пример с тремя сторонами Куба](./media/monitoring-strategy/three-sided-cube.png)

Ниже приведены некоторые ключевые вопросы.

- Как вы создаете журналы безопасности и защищаете их доступ к безопасности и новым элементам управления конфиденциальностью?

- Какие службы будут глобально доступны и, как таковые, можно глобально отслеживать на границе службы?

- Как насчет сетевых точек между вашей сетевой инфраструктурой и сетевым подключением к конечным точкам службы и приложений, которые сообщают нам о том, когда это ваш сотрудник или поставщик облачных услуг?

- Каковы границы операций безопасности в сравнении с работоспособностью и производительностью? Как можно предоставить сводные данные о работоспособности и состоянии для операций безопасности, а также обратную передачу владельцам служб?

Чтобы собрать эту архитектуру, ниже приведены некоторые рекомендации.

- Подход к потоку данных, запускаемый из ресурсов службы и поступающий в стек: метрики и данные журналов, созданные инфраструктурой, устройствами IoT, мобильными устройствами и др. Все ли элементы находятся в области управления — средства мониторинга (средний уровень)? Переместитесь вверх и наружу (ITSM средства, Глобальный мониторинг, сведения о безопасности и управление событиями (SIEM), Пользовательский пользовательское оповещение и другие).

- Следует ли продолжить [System Center Operations Manager](/system-center/scom/welcome?view=sc-om-2019) или другие средства мониторинга.

- Экономические расходы.

- Как предприятие будет использовать журналы и метрики. Azure Monitor приводит значительный объем данных журналов и временных рядов к производительности и работоспособности мониторинга, аналогично работе с операциями безопасности. Журналы и метрики — это два основных компонента данных архитектуры Azure Monitor. Причины, по которым это важно:

   1. Так как вы можете создавать крупномасштабные комплексные облачные службы, затраты на управление проблемами сокращаются для анализа, корреляции и определения причин проблем в одном месте, что снижает потребность в доступе к ресурсам напрямую, тем самым улучшая безопасность.

   2. Как и в случае с SIEM, Azure Monitor выполняет консолидацию данных компьютеров непосредственно из локальных ресурсов, а также ресурсов Azure (включая журналы действий, данные клиента и подписки, а также любые данные журналов от клиента RESTFUL) и предоставляет простой язык запросов для обеспечения анализа данных далеко от того, что было возможно раньше.

Рассмотрим потоки данных и средства:

- Источники и типы (телеметрия, трассировки, с отслеживанием состояния, временные ряды).

- Средства и наборы (строки): (столбцы: доступность, емкость, безопасность, непрерывность и соответствие).

- Роль глобального мониторинга или верхнего уровня.

- Роль интеграции управление ИТ-услугами (ITSM) с триггерами для существенных событий.

Рассмотрим единую политику в плане управления для значимости событий в рамках предприятия, чтобы создавать оповещения и уведомления. Это одна из ключевых политик стратегии мониторинга. В следующей таблице приведен пример модели приоритета управления инцидентами для стандартизации событий, значимости и предупреждений, используемых для уведомлений.

![Пример уровня серьезности влияния и матрицы приоритетов](./media/monitoring-strategy/incident-priority-severity-matrix.png)

## <a name="formulate-initiatives"></a>Формулировка инициатив

Специалист по мониторингу или системный администратор обнаружил, что мониторинг в облаке выполняется быстрее и проще в установке, что приводит к недорогым демонстрациям или экспериментам. Чтобы преодолеть тенденция, чтобы остаться в демонстрационном режиме, необходимо постоянно касаться стратегии и обеспечить возможность выполнения в планах мониторинга, ориентированных на работу в рабочей среде. Поскольку стратегия имеет множество неуверенности и неизвестных, вы не будете знать все требования к мониторингу заранее. Поэтому следует принять решение о первом наборе планов внедрения, исходя из того, что является минимально эффективным для бизнеса и ИТ-управления. Вы можете вызвать эту базовую возможность *, которая необходима для начала пути*. Ниже приведены два примера инициатив, которые помогают объявить перенаправление вперед:

- Инициатива 1. *чтобы уменьшить разнообразие и сложность текущих инвестиций в мониторинг, мы будем вкладываться в создание основных возможностей с помощью Azure Monitor, учитывая те же навыки и готовность, что и в других областях облачного мониторинга.*

- Инициатива 2. *чтобы принять решение о том, как мы используем наши планы лицензирования для идентификации, доступа и общей защиты информации, мы поможем вам использовать офисы в области безопасности и конфиденциальности, устанавливая раннее наблюдение за пользователями и содержимым при их переносе в облако, чтобы уточнить вопросы по меткам классификации, предотвращению потери данных, шифрованию и политикам хранения.*

### <a name="consider-scale"></a>Рассмотрите возможность масштабирования

Рассмотрите возможность масштабирования стратегии и того, кто будет определять и стандартизировать *мониторинг как код*. Организация должна спланировать создание стандартизированных решений с помощью различных средств, таких как:

- Шаблоны Azure Resource Manager.
- Определение и политики инициативы по мониторингу политик Azure.
- GitHub для создания системы управления версиями для сценариев, кода и документации.

### <a name="consider-privacy-and-security"></a>Учитывайте конфиденциальность и безопасность

В Azure вам потребуется защитить определенные данные мониторинга, предоставляемые ресурсами и действиями плоскости управления, зарегистрированными в Azure, которые называются журналами действий. Кроме того, специализированные журналы, которые записывают действия пользователя, такие как Azure Active Directory журналов входа и аудита, а также интегрированный Microsoft 365 журнал аудита, так как они содержат конфиденциальные данные, которые могут потребоваться защищать от законов о конфиденциальности.

Стратегия мониторинга должна включать следующие компоненты:

- Отделение данных, не относящихся от мониторинга, от данных мониторинга
- Ограничение доступа к ресурсам

### <a name="consider-business-continuity"></a>Учитывайте непрерывность бизнес-процессов

Azure Monitor собирает, индексирует и анализирует данные, созданные на компьютере и ресурсах в режиме реального времени, чтобы обеспечить поддержку ваших операций и помогает решить деловые решения. В редких случаях ресурсы целого региона могут стать недоступными (например, из-за сбоев сети) или полностью потерянными (например, из-за стихийных бедствий). Полагаться на эти службы в облаке, ваше планирование не влияет на устойчивость инфраструктуры и высокую доступность, а также на его планирование:

- Доступность для приема данных из всех зависимых служб и ресурсов в Azure, ресурсов в других облаках и из локальной среды.
- Доступность данных для получения ценных сведений, решений, книг и других визуализаций, предупреждений, интеграции с ITSM и других служб управления плоскостью в Azure, поддерживающих эксплуатационные требования.

Разработайте план восстановления и убедитесь, что он охватывает такие ситуации, как восстановление данных, сбои сети, сбои зависимых служб и прерывание работы служб во всем регионе.

### <a name="consider-maturity"></a>Рекомендуемая дата_вступл_в_силу

Дата_вступл_в_силу — важное замечание в стратегии мониторинга. Рекомендуется запускать минимально, собирать данные и с помощью этих сведений определить стратегию. Первые решения для мониторинга, которые необходимы для наблюдения, включают в себя наблюдаемые процессы, такие как управление инцидентами и проблемами. Вам предстоит сделать следующее:

- Создание одной или нескольких рабочих областей Log Analytics

- Включить агенты

- Включить параметры диагностики ресурсов

- Включить начальные правила генерации оповещений

Со временем вы получаете уверенность в Azure Monitorх возможностей с целью измерения показателей работоспособности, так что это включает в себя расширение контроля над сбором журналов, включение и использование аналитических данных и метрик, а также определение запросов поиска по журналам, которые позволяют оценить работоспособность или неработоспособность.

Циклы обучения включают в себя получение данных мониторинга и ценные сведения о менеджерах, а также гарантирует, что нужные потребители будут иметь необходимые данные мониторинга. Циклы обучения включают в себя непрерывную настройку и оптимизацию первоначальных планов мониторинга для адаптации, улучшения обслуживания и информирования планов внедрения.

![Стратегия мониторинга и контроля](./media/monitoring-strategy/monitoring-and-control-strategy.png)

<!-- docutune:ignore "Data to Information, Knowledge, and Wisdom" -->

<Sup>1 </sup> модель дикв является часто используемым методом с корнями в управлении знаниями, чтобы объяснить, каким образом мы перейдем от данных к информации, знаниям и знания с помощью компонента действий и решений.

Наблюдение основано на службах, создаваемых в Azure. Стратегия может помочь в решении этих четырех дисциплин современного мониторинга, чтобы определить минимальный уровень наблюдения и добиться уверенности в пошаговых действиях. Перемещение возможностей из реактивности в активное состояние и масштабирование его доступности конечным пользователям — это одна из целей.

- **Обратите внимание на следующее.** Во первых, следует сосредоточиться на установлении мониторинга для отслеживания работоспособности и состояния служб и ресурсов Azure. Настройте базовый мониторинг, а затем Автоматизируйте с помощью политик Azure и шаблонов Azure Resource Manager, чтобы установить начальную видимость служб и их гарантию: доступность, производительность или емкость, безопасность и соответствие конфигураций. Например, на основе минимальной допустимой настройки Azure Monitor, настройте ресурсы для мониторинга и диагностики, настройте оповещения и аналитические сведения. Включите знания и готовность потребителей мониторинга, определение и запуск событий для работы службы, например инцидентов и проблем. Один из индикаторов зрелости — это то, что можно автоматизировать, чтобы сократить ненужные человеческие затраты, чтобы вручную наблюдать за работоспособностью и состоянием. Чтобы узнать, какие службы являются работоспособными, важно получать оповещения о неработоспособных службах.

- **Мера:** Настройка сбора метрик и журналов из всех ресурсов для отслеживания симптомов и условий, которые представляют собой проблемы, которые указывают на возможное или фактическое воздействие на доступность службы, а также влияние потребителей службы или приложения. Пример:

  - При использовании функции в приложении отображается задержка времени ответа, возвращающая ошибку, когда я выбрал что-нибудь или не отвечает?

  - Убедитесь, что службы соответствуют соглашениям службы, измеряя служебную программу службы или приложения.

- **Ответ:** В зависимости от контекста известных проблем, которые необходимо отслеживать и измерять, оценивать, какие из них являются ошибками, автоматическим исправлением или требуется ручной ответ, в зависимости от того, что классифицируется как инцидент, проблема или изменение.

- **Обучение и улучшение.** Поставщики и потребители, участвующие в циклах обучения, подразумевают использование фактических данных мониторинга с помощью аналитических сведений, отчетов и книг, чтобы постоянно улучшать целевую службу и выполнять настройку и оптимизацию конфигурации мониторинга. Также необходимо изменить, так как Конфигурация мониторинга изменяется в сочетании с изменениями в службе (например, "новый", "изменено" или "снят с учета") и остается в соответствии с фактической гарантией службы.

Чтобы обеспечить соответствие планов мониторинга стратегии, используйте следующую таблицу для категоризации различных сценариев мониторинга, которые выполняются более подробно. Это работает с пятью процессами рационализации, представленными выше на этапе плана. Если вы используете System Center Operations Manager, вы сможете использовать гибридные и облачные возможности для рационализировать инвестиций.

| Тип | Цель мониторинга | Пример цели |
|-----|---------------------|------------------|
| 1 | Только локально | System Center Operations Manager. Продолжайте наблюдение за службами, инфраструктурой, настройкой сети на уровне приложений в собственных центрах обработки данных без каких бы то ни было рекомендаций по облаку. |
| 2 | Из локальной среды в облако | Продолжайте использовать System Center Operations Manager и применяйте Microsoft 365 и пакеты управления Azure. |
| 3 | Локальное или с облаком (совместное использование), где службы работают как в облаке, так и в локальной среде. | Установка начального мониторинга с Azure Monitor. Подключите Azure Monitor к System Center Operations Manager и источникам оповещений, таким как Zabbix или Nagios. Развертывание агентов мониторинга Azure Monitor, многосетевых System Center Operations Manager, где они отслеживаются совместно. |
| 4 | Гибридная миграция | Отслеживайте миграцию, например Microsoft Exchange Server, чтобы Microsoft 365 Exchange Online. Работоспособность служб и использование службы Exchange Online, безопасность и соответствие требованиям — от Microsoft 365. Постепенное списание локального Exchange с System Center Operations Manager до завершения миграции. |
| 5 | Постоянное гибридное развертывание | System Center Operations Manager, Azure AD, Azure Monitor, центр безопасности Azure, Intune и другие. набор средств для работы с цифровыми ресурсами. |
| 6 | Полностью облачные | Azure Monitor, политика Azure, центр безопасности Azure, Microsoft 365, работоспособность службы Azure, служба работоспособности ресурсов Azure и другие. |
| 7 | Клиенты, принадлежащие к облаку (консолидация) | Централизованное наблюдение за множеством клиентов. Azure Лигхсаусе, политика Azure, Azure Monitor и Sentinel Azure. |
| 8 | Многооблачная экосистема | Централизованное отслеживание различных поставщиков облачных решений: Microsoft, Amazon, Google и др. |
| 9 | Потребитель > поставщика | Наблюдение за решениями и службами в качестве поставщика облачных служб. |

## <a name="formulate-monitoring-requirements"></a>Формулировка требований к мониторингу

По мере выполнения этого процесса ваша стратегия показывает, что в долгосрочном запуске может быть много времени. В конечном итоге ваше решение распространяется за пределы корпоративной сети на рабочее место, на устройства и конечные точки, а также в наружную границу с учетом подлинности как безопасности. Новая граница, определенная с помощью мониторинга облака, — это надежный мотивацией в отличие от того, как работает центр обработки данных и Рабочая область.

Вы можете использовать Azure для постепенного начала управления всеми или некоторыми аспектами локальных ресурсов, даже для служб, которые будут находиться в локальной среде. Вы также хотите, чтобы стратегия определяла свои обязанности мониторинга в соответствии с стратегией внедрения облачных технологий, основанной на модели облачной службы, которую применяет ваш бизнес. Даже для служб, основанных на IaaS, вы получаете метрики, журналы, представления и возможности оповещений с помощью службы работоспособности служб Azure. здесь вы настроите оповещения о доступности ресурсов Azure с работоспособностью ресурсов. С помощью служб SaaS, таких как Microsoft 365, многие из них уже предоставлены, и вам нужно настроить соответствующий доступ к порталам, панелям мониторинга, аналитикам и оповещениям. С точки зрения службы, большая служба с распределенными компонентами, например Microsoft 365 Exchange Online, имеет ряд целей, а не только следит за его работоспособностью и состоянием.

| Основная цель | Цель и результат |
|-------------------|------------------|
| Мониторинг работоспособности и состояния | Целостное наблюдение, оценка, изучение и улучшение долгосрочной гарантии службы или компонента, включая уровни обслуживания, в следующих аспектах: доступность, емкость, производительность, безопасность и соответствие требованиям. Работоспособная система, служба или компонент находятся в режиме «в сети», обеспечивают высокий уровень безопасности и совместимости. Мониторинг работоспособности включает в себя журналы и отслеживает состояния работоспособности и метрики в реальном времени. Он также включает отчеты о тенденциях, аналитические сведения и тенденции использования службы. |
| Мониторинг служебной программы | Обратите внимание на, измерьте, изучите и улучшите качество или качественные аспекты того, как система доставляет ценность. Взаимодействие с пользователем — это один из вариантов использования мониторинга. |
| Мониторинг безопасности | Проследите, оцените, изучите и улучшите защиту в поддержке стратегии и функций кибербезопасности, таких как операции безопасности, идентификация и доступ, защита информации, конфиденциальность, управление угрозами и соответствие требованиям. Мониторинг с помощью центра безопасности Azure и Azure Sentinel, а также Microsoft 365. |
| Мониторинг затрат | Отслеживайте использование и оцените затраты, используя Azure Monitor и управление затратами Azure + выставление счетов в качестве новой первичной цели. Azure Cost Management + API-интерфейсы выставления счетов предоставляет возможность исследовать данные о затратах и использовании с помощью многомерного анализа. |

| Третичные цели | Цель и результат |
|---------------------|------------------|
| Мониторинг активности | Проследите, оцените, изучите и улучшите использование, безопасность и соответствие, используя такие источники, как журналы действий Azure, журналы аудита и Microsoft 365 единый журнал аудита для событий уровня подписки, действия с ресурсами, действия пользователей и администраторов, содержимое, данные, а также требования к безопасности и соответствию требованиям в Azure и Microsoft 365. |
| Использование службы | Владельцы служб хотят, чтобы аналитики и аналитические данные измерены, изучать и улучшать использование Azure и Microsoft 365 Services (IaaS, PaaS, SaaS) с отчетами об использовании служб, аналитикой и аналитическими сведениями. Убедитесь, что планы включают пользователей, которым требуется доступ к порталам администрирования, панелям мониторинга, аналитическим данным и отчетам. |
| Служба и работоспособность ресурсов | Следите за работоспособностью облачных ресурсов, а также от простоев и рекомендаций служб корпорации Майкрософт, чтобы получать сведения об инцидентах и обслуживании. Включите работоспособность ресурсов при наблюдении за доступностью ресурсов и предупреждения об изменениях доступности. |
| Мониторинг емкости и производительности | Для поддержки мониторинга работоспособности ваши потребности могут потребовать более глубокой и специализации. |
| Мониторинг изменений и соответствия требованиям | Отслеживайте, измеряйте, изучите и улучшайте управление конфигурацией ресурсов, которые теперь должны включать в себя безопасность в формулировку, на которые влияет хорошее использование политики Azure для стандартизации конфигураций мониторинга и усиления безопасности. Данные журнала для фильтрации основных изменений, внесенных в ресурсы. |
| Мониторинг удостоверений и доступа | Проследите, изучите и улучшите использование и безопасность Active Directory, Azure Active Directory и управления удостоверениями, которые интегрируют пользователей, приложения, устройства и другие ресурсы независимо от того, где они находятся. |
| Защита информации | Не только Azure Monitor, но Azure Information Protection в зависимости от плана, включает аналитику использования, важную для разработки надежной стратегии защиты информации в Azure и корпорации Майкрософт. |
| Мониторинг конфиденциальности | Организациям, которые сталкиваются с разворачиванием конфиденциальности, необходимо включить защиту информации об управлении цифровыми сферами, классификацию данных и предотвращении потери данных, чтобы снизить риски в отношении нарушений конфиденциальности и недолей. Microsoft 365 защита информации включает возможности мониторинга, которые также можно интегрировать с Azure Monitor. |
| Управление угрозами и встроенная защита от угроз | Облако объединяет отдельные традиционные роли мониторинга безопасности с мониторингом работоспособности. Например, интегрированная защита от угроз включает в себя мониторинг для ускорения оптимального состояния нулевого отношения доверия. Интеграция Azure Advanced Threat Protection позволяет выполнять миграцию с System Center Operations Manager для мониторинга Active Directory и интеграции сигналов Active Directory, связанных с безопасностью, для обнаружения сложных атак в гибридных средах. |

## <a name="agile-solution-releases"></a>Выпуски Agile Solution

В конечном счете, вы будете предоставлять конфигурации мониторинга или решения в рабочей среде. Как ИТ-специалисту Operations Manager или мониторингу руководитель команды, рассмотрим стандартную, простую таксономию для улучшения взаимодействия с потребителями, менеджерами и ИТ-операциями. Подход Agile DevOps гарантирует, что мониторинг внедряется в группы, которые будут создавать и использовать облачные службы. В то время как традиционное управление проектом работает, оно не является достаточно быстрым и обычно не принимается в качестве стандартной практики группами эксплуатации.

Включите в стратегию и операционную модель взаимодействие планов мониторинга, целей и конфигураций (решений). Например, можно использовать Azure Boards:

| Термин Agile | Что следует включить | Примеры |
|----------|---------------|--------|
| Ситуации | Широкий мониторинг <br> Инициативы по стратегии мониторинга | Консолидация мониторинга облака Azure <br> Гибридный мониторинг облака <br> Мониторинг частного облака <br> Создание основной службы мониторинга |
| Компоненты | Отдельный мониторинг <br> Планы и проекты | Требования к мониторингу <br> Наблюдение за потребителями и поставщиками <br> Цели <br> Инструменты <br> Расписание |
| Пользовательские истории и задачи | Конечным результатом является конфигурация или решение мониторинга | Мониторинг сети (например, ExpressRoute); <br> Стандартизированный мониторинг виртуальных машин IaaS (например Azure Monitor для виртуальных машин, Application Insights, политика Azure, параметры, политики, отчеты, рабочие области). |

## <a name="establish-minimum-governance"></a>Установка минимального контроля

Как можно раньше, определите, как вы планируете управлять инвестициями в Cloud Monitoring. Помните, что Azure Monitor — это служба *клиента* с видимостью для групп управления и подписок, а пользователи могут ограничить их действия с помощью управления доступом на основе ролей в Azure.

Определите, кто будет иметь уровень доступа в Azure для поддержки своей роли и ответственности. Рекомендуется `Reader` заранее задать доступ к роли для потребителей мониторинга, а затем приступить к управлению тем, кому предоставлена `Contributor` роль.

Сначала необходимо выяснить роли, которые будут владеть группами ресурсов Azure и управлять ими в рамках вашей инфраструктуры управления:

- Будет ли группа мониторинга или один или несколько администраторов ресурсов и групп ресурсов иметь привилегированный доступ к `Monitoring Contributor` роли.

- Потребители, которым следует предоставить `Monitoring Reader` роль, которая обеспечивает доступ к функциям в Azure Monitor, а также исследовать проблемы в разделе "Мониторинг", который входит в состав каждого ресурса Azure.

- Какие диспетчеры нуждаются в доступе к другим ролям Azure Reader, таким как `Reports Reader` .

В заключение для ролей потребителей мониторинга, вероятно, необходим широкий доступ, а разработчикам и системным администраторам нужен доступ только к определенным ресурсам Azure на основе ролей. В качестве дополнительного ограничения убедитесь, что вы исключите читателей из доступа к конфиденциальным данным мониторинга, таким как безопасность, вход и журналы действий пользователей.

## <a name="establish-readiness"></a>Установить готовность

На раннем этапе следует сформулировать план готовности, чтобы помочь ИТ-специалистам принять новые навыки, методики и приемы для облачного мониторинга в Azure. Ознакомьтесь с [рекомендациями по обеспечению готовности](./suggested-skills.md) для мониторинга, которые включают в себя базовые потребности, а также сведения, относящиеся к мониторингу.
