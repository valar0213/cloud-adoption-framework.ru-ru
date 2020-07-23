---
title: Перенос баз данных SQL Server в Azure
description: Узнайте, как Contoso переносит свои локальные базы данных SQL в Azure.
author: deltadan
ms.author: abuck
ms.date: 07/01/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: azure-migrate
ms.openlocfilehash: 44269a67e406abe6f67c2b5e233d4ea676f45163
ms.sourcegitcommit: bcc73d194c6d00c16ae2e3c7fb2453ac7dbf2526
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86198988"
---
<!-- cSpell:ignore BACPAC FILESTREAM -->

# <a name="migrate-sql-server-databases-to-azure"></a>Перенос баз данных SQL Server в Azure

В этой статье показано, как вымышленная компания Contoso оценивает, планирует и переносит свои различные локальные SQL Server базы данных в Azure.

Компании Contoso требуется провести техническую и финансовую оценку, чтобы определить, можно ли выполнить перенос своих локальных рабочих нагрузок в облако Azure. В частности, команда компании Contoso хочет оценить совместимость компьютеров и баз данных для миграции. Кроме того, он хочет оценить емкость и затраты на выполнение ресурсов Contoso в Azure.

## <a name="business-drivers"></a>Бизнес-факторы

В компании Contoso возникают различные проблемы, связанные с поддержанием всех версий SQL Server рабочих нагрузок, существующих в сети. После совещания с последними инвесторами финансовый директор и CTO приняли решение переместить все эти рабочие нагрузки в Azure. Это позволит им переходить от структурированной модели затрат к модели с гибкими операционными издержками.

Группа специалистов по ИТ тесно работала с бизнес-партнерами для понимания бизнес-и технических требований:

- **Повышение безопасности.** Компания Contoso должна иметь возможность более своевременно отслеживать и защищать все ресурсы данных. Они также хотели бы получить более централизованную настройку системы отчетности для шаблонов доступа к базе данных.

- **Оптимизация ресурсов вычислений:** Компания Contoso развернула большую локальную серверную инфраструктуру. Они имеют несколько SQL Server экземпляров, которые используют, но не используют базовые ЦП, память и диск, выделенные эффективно.

- **Повышение эффективности:** Компании Contoso необходимо удалить ненужные процедуры и упростить процессы для разработчиков и пользователей. Бизнес нуждается в том, чтобы ИТ были быстрыми и чтобы не тратить время или деньги, обеспечивая более высокие требования клиентов. Администрирование базы данных должно быть уменьшено и/или свернуто после миграции.

- **Повышение гибкости:** Компания Contoso должна быть в большей мере реагировать на потребности бизнеса. Должна реагировать быстрее, чем изменения на рынке, чтобы включить успех в глобальную экономику реагирования. Он не должен мешать или становиться помехой для бизнеса.

- **Масштаб:** По мере успешного развития бизнеса компания Contoso должна предоставить системы, которые могут расти в одном темпе. Существует несколько устаревших аппаратных сред, которые не могут быть обновлены, а также заканчиваются или близки к окончанию поддержки.

- **Затраты:** Владельцы бизнеса и приложений хотят, чтобы они не заработали с высокими затратами на облако по сравнению с выполнением локальных приложений.

## <a name="migration-goals"></a>Цели миграции

Группа разработчиков Contoso Cloud прикрепляет цели для различных миграций. Эти цели использовались для определения лучших методов переноса.

| Требования | Сведения |
| --- | --- |
| **Производительность** | После миграции приложения в Azure должны иметь те же возможности производительности, что и приложения в локальной среде компании Contoso. Переход в облако не означает, что производительность приложения менее важна. |
| **Совместимость** | Contoso необходимо понимать совместимость своих приложений и баз данных с Azure. Contoso также должен понимать возможности размещения Azure. |
| **Источники данных** | Все базы данных будут перемещены в Azure без исключений. На основе анализа базы данных и приложений используемых функций SQL они будут перемещены в PaaS, IaaS или управляемые экземпляры. Все базы данных должны перемещаться. |
| **Приложения** | Приложения должны быть перемещены в облако везде, где это возможно. Если они не могут переместиться, им будет разрешено подключаться к перенесенной базе данных через сеть Azure только через частные соединения. |
| **Затраты** | Компании необходимо получить сведения не только о параметрах миграции, но и о стоимости инфраструктуры после перехода в облако. |
| **Управление** | Группы управления ресурсами должны создаваться для различных отделов вместе с группами ресурсов для управления всеми переносимыми базами данных SQL. Все ресурсы должны быть помечены сведениями о отделе для требований к оплате. |
| **Ограничения** | Изначально не все филиалы, которые запускают приложения, будут иметь прямую ссылку ExpressRoute на Azure, поэтому этим офисам потребуется подключиться через шлюзы виртуальной сети. |

## <a name="solution-design"></a>Архитектура решения

Компания Contoso уже выполнила [оценку миграции](https://docs.microsoft.com/azure/cloud-adoption-framework/plan/contoso-migration-assessment) своего цифрового пространства с помощью функции " [Миграция Azure](https://docs.microsoft.com/azure/migrate/migrate-services-overview) " с [сопоставление служб](https://docs.microsoft.com/azure/azure-monitor/insights/service-map) .

Оценка дает несколько рабочих нагрузок, распределенных по нескольким отделам. Общий размер проекта миграции требует полного офиса управления проектами (PMO) для управления спецификой взаимодействия, ресурсами и планированием по расписанию.

![Процесс миграции](./media/contoso-migration-sql-server-db-to-azure/migration-process.png)

### <a name="solution-review"></a>Проверка решения

Contoso оценивает предлагаемый дизайн, составляя список плюсов и минусов.

| Рассматриваемый вопрос | Сведения |
| --- | --- |
| **Преимущества** | Azure предоставит единую область прозрачности для рабочих нагрузок базы данных. <br><br> Расходы будут отслеживаться с помощью службы управления затратами Azure и выставления счетов. <br><br> Оплата за подразделение обеспечивает простую выплату за API-интерфейсы выставления счетов Azure. <br><br> Обслуживание сервера и программного обеспечения будет сокращено до сред, основанных на IaaS. |
| **Недостатки** | Из-за требований виртуальных машин на основе IaaS по-прежнему необходимо управлять программным обеспечением на этих компьютерах. |

### <a name="budget-and-management"></a>Бюджет и управление

Перед миграцией необходима необходимая структура Azure для поддержки аспектов администрирования и выставления счетов в решении.

Для требований к управлению было создано несколько [групп управления](https://docs.microsoft.com/azure/governance/management-groups/overview) для поддержки организационной структуры.

В соответствии с требованиями к выставлению счетов каждый ресурс Azure [помечается](https://docs.microsoft.com/azure/azure-resource-manager/management/tag-resources) с помощью соответствующих тегов выставления счетов.

### <a name="migration-process"></a>Процесс миграции

Для переноса данных следует использовать стандартный повторяемый шаблон. Это включает следующие шаги, основанные на [рекомендациях корпорации Майкрософт](https://datamigration.microsoft.com/):

- Перед миграцией:
  - **Обнаружение:** Ресурсы базы данных инвентаризации и стек приложений.
  - **Оценка:** Оценка рабочих нагрузок и исправление рекомендаций.
  - **Преобразовать:** Преобразование исходной схемы для работы в целевом объекте.
- Миграция.
  - **Миграция:** Перенос исходной схемы, исходных данных и объектов в целевой объект.
  - **Данные синхронизации:** Синхронизация данных (для минимального времени простоя).
  - **Прямую миграцию:** Вырежьте источник на целевой объект.
- После миграции:
  - **Исправлять приложения:** Итеративное внесение и необходимые изменения в приложения.
  - **Выполнение тестов:** Итеративное выполнение функциональных и тестовых тестов производительности.
  - **Оптимизировать:** На основе тестов устраните проблемы с производительностью и повторите проверку, чтобы подтвердить повышение производительности.
  - **Снятие с учета ресурсов:** В старых виртуальных машинах и средах размещения выполняется резервное копирование и прекращение использования.

#### <a name="step-1-discovery"></a>Шаг 1. Обнаружение

Компания Contoso использовала миграцию Azure с Сопоставление служб для выявления зависимостей в среде Contoso. Служба "миграция Azure" автоматически обнаружила компоненты приложений в системах Windows и Linux и сопоставила взаимодействие между службами. С помощью Сопоставление служб функции службы "миграция Azure" отображаются подключения между серверами Contoso, процессами, задержкой входящего и исходящего подключения, а также портами в архитектуре, подключенной по протоколу TCP. Contoso требовалось только для установки [Microsoft Monitoring Agent](https://docs.microsoft.com/azure/log-analytics/log-analytics-agent-windows) и агентов [зависимостей Майкрософт](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-hybrid-cloud#install-the-dependency-agent-on-windows) .

Contoso также добавил Помощник по миграции данных в проект службы "миграция Azure". Выбрав это средство, вы сможете оценивать базы данных для миграции в Azure.

![Помощник по миграции данных](./media/contoso-migration-sql-server-db-to-azure/add-dma.png)

#### <a name="step-2-application-assessment"></a>Шаг 2. Оценка приложения

<!-- docsTest:ignore "mainly .NET-based" "non-.NET-based" -->

Результаты оценки предоставлены contoso с учетом того, что они используют в основном. Однако приложения на основе NET в течение нескольких лет использовали другие технологии, такие как PHP и Node.js. В приобретенных системах поставщика также появились приложения, не основанные на .NET. Они определили следующее:

- ~ 800 приложения Windows .NET
- ~ 50 приложения PHP
- 25 Node.js приложений
- 10 приложений Java

#### <a name="step-3-database-assessment"></a>Шаг 3. Оценка базы данных

При обнаружении каждой рабочей нагрузки базы данных запускается средство Помощник по миграции данных (DMA) для определения того, какие функции использовались. DMA помогает компании Contoso оценивать миграцию баз данных в Azure, выявляя проблемы совместимости, которые могут повлиять на функциональность базы данных в новой версии SQL Server или базы данных SQL Azure.

Компания Contoso проводила эти шаги, чтобы оценить свои базы данных, а затем передать данные результатов в службу "миграция Azure":

1. Скачайте DMA.
1. Создайте проект оценки.
1. В канале DMA Войдите в проект службы "миграция Azure" и синхронизируйте сводку оценки.

![Миграция и DMA Azure](./media/contoso-migration-sql-server-db-to-azure/azure-migrate-dma.png)

DMA рекомендует повысить производительность и надежность целевой среды и позволяет им перемещать свои схемы, данные и Неавтономные объекты с исходного сервера на целевой сервер.

Дополнительные сведения о [Помощник по миграции данных](https://docs.microsoft.com/sql/dma/dma-assesssqlonprem?view=sql-server-2017)

Компания Contoso использовала DMA для выполнения оценки, а затем перегрузила данные непосредственно в службу "миграция Azure".

![Отправка канала DMA в службу "миграция Azure"](./media/contoso-migration-sql-server-db-to-azure/upload-db-data.png)

Теперь, когда сведения о базе данных загружены в службу "миграция Azure", компания Contoso обнаружила более 1 000 экземпляров баз данных, которые необходимо перенести. Из этих экземпляров примерно 40% могут быть перемещены в базу данных SQL для Azure. Оставшиеся 60 процентов должны быть перемещены либо в SQL Server, выполняющихся на виртуальных машинах Azure, либо в Azure SQL Управляемый экземпляр. Из этих 60 процентов, около 10 процентов требуется подход на основе виртуальной машины, остальные экземпляры будут перемещены в Управляемый экземпляр Azure SQL.

Если DMA не удалось выполнить в источнике данных, были выполнены следующие рекомендации по миграции базы данных.

> [!NOTE]
> В рамках этапа оценки Contoso обнаружил различные базы данных с открытым исходным кодом. По отдельности, они следуют [этому руководству](./contoso-migration-oss-db-to-azure.md) по планированию миграции.

<!-- docsTest:ignore "custom .NET" -->

#### <a name="step-4-migration-planning"></a>Шаг 4. Планирование миграции

При наличии информации компания Contoso использует следующие рекомендации, чтобы определить, какой метод миграции следует использовать для каждой базы данных.

| целевого объекта | Использование базы данных | Сведения | Миграция по сети | Автономная миграция | Максимальный размер | Руководство по миграции |
| --- | --- | --- | --- | ---| --- | --- |
| База данных SQL Azure (PaaS) | SQL Server (только данные) | Эти базы данных просто используют основные таблицы, столбцы, хранимые процедуры и функции | [Помощник по миграции данных](https://docs.microsoft.com/sql/dma/dma-overview), [репликация транзакций](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transactional-replication) | [BACPAC](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database), [bcp](https://docs.microsoft.com/sql/tools/bcp-utility?view=sql-server-ver15) | 1 ТиБ | [Ссылка](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql) |
| Управляемый экземпляр SQL Azure | SQL Server (дополнительные функции) | Эти базы данных используют триггеры и другие [сложные концепции](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#service-broker) , такие как пользовательские типы .NET, брокеры служб и т. д. | [Помощник по миграции данных](https://docs.microsoft.com/sql/dma/dma-overview), [репликация транзакций](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transactional-replication) | [BACPAC](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database), [bcp](https://docs.microsoft.com/sql/tools/bcp-utility?view=sql-server-ver15), [собственная Архивация и восстановление](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started-restore) | 2 Тиб-8 тиб | [Ссылка](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online) |
| SQL Server на виртуальных машинах Azure (IaaS) | SQL Server (интеграция со сторонними разработчиками) | SQL Server должны иметь [неподдерживаемые функции SQL управляемый экземпляр](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#service-broker) (брокеры служб с несколькими экземплярами, поставщики служб шифрования, буферный пул, уровни совместимости ниже 100, зеркальное отображение базы данных, FILESTREAM, polybase, все, что требует доступа к файловым ресурсам, внешним сценариям, расширенным хранимым процедурам и другим) или программному обеспечению сторонних разработчиков для поддержки действий базы данных. | [Репликация транзакций](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transactional-replication) | [BACPAC](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database), [bcp](https://docs.microsoft.com/sql/tools/bcp-utility?view=sql-server-ver15), [репликация моментальных снимков](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transactional-replication), [собственная Архивация и восстановление](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started-restore), преобразование физического компьютера в виртуальную машину | 4 гиб-64 тиб | [Ссылка](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql) |

Из-за большого количества баз данных компания Contoso создала проект управления проектами (PMO) для наблюдения за каждым экземпляром миграции баз данных. [Ответственность и обязанности](https://docs.microsoft.com/azure/cloud-adoption-framework/migrate/migration-considerations/assess/) были назначены каждой группе бизнеса и приложений.

Contoso также выполнил [проверку готовности рабочей нагрузки](https://docs.microsoft.com/azure/cloud-adoption-framework/migrate/migration-considerations/assess/evaluate). Эта проверка проверила инфраструктуру, базу данных и компоненты сети.

#### <a name="step-5-test-migrations"></a>Шаг 5. Тестирование миграции

Первая часть подготовки к миграции включала в себя тестовую миграцию каждой базы данных в среды перед установкой. Чтобы сэкономить время, они записывали все операции для миграции и записывают временные показатели для каждого из них. Чтобы ускорить перенос, они обнаружили, какие операции миграции могли выполняться параллельно.

Все процедуры отката были обнаружены для каждой рабочей нагрузки базы данных в случае непредвиденных сбоев.

Для рабочих нагрузок на основе IaaS необходимо заранее настроить все необходимое программное обеспечение стороннего производителя.

После выполнения тестовой миграции компания Contoso могла использовать различные [средства оценки стоимости](https://docs.microsoft.com/azure/cloud-adoption-framework/migrate/migration-considerations/assess/estimate) Azure, чтобы получить более точную картину будущих эксплуатационных расходов на их миграцию.

#### <a name="step-6-migration"></a>Шаг 6. Миграция

Для рабочей миграции компания Contoso определила временные кадры для всех миграций баз данных и что может быть достаточно для выполнения в выходном окне (полночь с 00:00 до полуночи воскресенье) с минимальным временем простоя бизнеса.

В соответствии с задокументированными процедурами тестирования они выполняют каждую миграцию по мере возможности, ограничивая все ручные задачи для сворачивания ошибок.

Если во время выполнения каких-либо миграций происходит сбой, в следующем окне миграции выполняется откат и повторное планирование.

### <a name="clean-up-after-migration"></a>Очистка после миграции

Contoso определил окно архива для всех рабочих нагрузок базы данных. По мере истечения срока действия окна ресурсы будут удалены из локальной инфраструктуры.

В том числе:

- Удаление рабочих данных с локальных серверов.
- Прекращение использования сервера размещения после истечения срока действия последней рабочей нагрузки.

### <a name="review-the-deployment"></a>Проверка развертывания

Теперь, когда выполняется миграция ресурсов в Azure, компании Contoso необходимо полностью ввести его в эксплуатацию и защитить свою новую инфраструктуру.

#### <a name="security"></a>Безопасность

- Компания Contoso должна обеспечить безопасность своих новых рабочих нагрузок базы данных Azure. [Подробнее](https://docs.microsoft.com/azure/sql-database/sql-database-security-overview).
- В частности, компания Contoso должна проверить конфигурацию брандмауэра и виртуальной сети.
- Настройте [частную ссылку](https://docs.microsoft.com/azure/azure-sql/database/private-endpoint-overview) , чтобы весь трафик базы данных хранился в Azure и локальной сети.
- Включите [Azure Advanced Threat protection](https://docs.microsoft.com/azure/azure-sql/database/threat-detection-overview) для базы данных SQL Azure.

#### <a name="backups"></a>Резервные копии

- Убедитесь, что резервное копирование баз данных Azure выполняется с помощью геовосстановления. Это позволяет использовать резервные копии в парном регионе в случае регионального сбоя.
- **Важно.** Убедитесь, что ресурс Azure имеет [блокировку ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/management/lock-resources) , чтобы предотвратить удаление. Удаленные серверы нельзя восстановить.

#### <a name="licensing-and-cost-optimization"></a>Лицензирование и оптимизация затрат

- Многие рабочие нагрузки базы данных Azure можно масштабировать вверх или вниз, поэтому важно следить за производительностью сервера и баз данных, чтобы обеспечить соответствие вашим потребностям, а также снизить затраты.
- Ресурсы ЦП и хранилища связаны с затратами. Для выбора доступны несколько ценовых категорий. Убедитесь, что для рабочих нагрузок данных выбран соответствующий ценовой план.
- [Эластичные пулы](https://docs.microsoft.com/azure/sql-database/sql-database-service-tiers-dtu) должны быть реализованы для баз данных с совместимыми шаблонами использования ресурсов.
- Счета за каждую реплику чтения выставляются на основе выбранных вычислений и хранилища.
- Используйте зарезервированную емкость, чтобы сэкономить на затратах.

## <a name="conclusion"></a>Заключение

В этой статье компания Contoso оценивает, планирует и переносит свои рабочие нагрузки Microsoft SQL Server в Azure.