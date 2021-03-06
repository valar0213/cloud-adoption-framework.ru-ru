---
title: Перенос активов
description: Подготовьтесь к миграции в Azure, определив подходящие инструменты для использования, включая нативные инструменты, сторонние инструменты и инструменты управления проектами.
author: matticusau
ms.author: mlavery
ms.date: 09/02/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 1a52864576b7965a10a2fb7a4f3ea773cd4979c9
ms.sourcegitcommit: fbfd66dab002b549d3e9cbf1b7efa0099d0b7700
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282943"
---
# <a name="deploy-workloads-and-assets-infrastructure-apps-and-data"></a>Развертывание рабочих нагрузок и ресурсов (инфраструктуры, приложений и данных)

На этом этапе перехода вы используете результаты этапа оценки, чтобы инициировать миграцию среды. Это руководство поможет вам найти соответствующие инструменты для достижения состояния готовности. Вы изучите встроенные и сторонние инструменты, а также инструменты для управления проектами.

## <a name="native-migration-tools"></a>[Собственные инструменты миграции](#tab/Tools)

В следующих разделах описываются собственные инструменты Azure, доступные для выполнения миграции или ее упрощения. Сведения о выборе нужных инструментов для поддержки переноса приведены в [руководстве по принятию решений о миграции с помощью Cloud Adoption Framework](../../decision-guides/migrate-decision-guide/index.md).

### <a name="azure-migrate"></a>Служба "Миграция Azure"

Служба "Миграция Azure" обеспечивает согласованную и расширяемую процедуру миграции. Миграция Azure предоставляет единую, выделенную среду для отслеживания миграции на этапах оценки и перехода в Azure. Эта служба дает возможность использовать выбранные вами инструменты и отслеживать в них ход выполнения миграции.

Миграция Azure — это централизованное решение для оценки и переноса серверов, инфраструктуры, приложений и данных из локальной среды в Azure. Решение предоставляет следующие возможности:

- Унифицированная платформа с возможностями оценки, миграции и отслеживания хода выполнения.
- Улучшенные возможности оценки и миграции.
    - Локальные серверы, включая Hyper-V и VMware.
    - Выполняемая без агента миграция виртуальных машин VMware в Azure.
    - Миграция баз данных в Базу данных SQL Azure или Управляемый экземпляр SQL.
    - Веб-приложения
    - Инфраструктура виртуальных рабочих столов (VDI) для Виртуального рабочего стола Windows в Azure.
    - Сбор больших данных с помощью продуктов Azure Data Box.
- Возможность интеграции с решениями независимых поставщиков программного обеспечения (например, Cloudamize).

Чтобы выполнить перенос с помощью службы "Миграция Azure", сделайте следующее:

1. Выполните поиск службы "Миграция Azure" в разделе **Все службы**. Чтобы продолжить, выберите **Миграция Azure**.
1. Выберите **Добавить инструмент** , чтобы запустить проект миграции.
1. Выберите подписку, группу ресурсов и географию для размещения миграции.
1. Выберите **Выберите инструмент оценки** > **Azure Migrate: Server Assessment (Миграция Azure: оценка сервера)**  > **Далее**.
1. Выберите **Review + add tools** (Проверка и добавление инструментов) и проверьте конфигурацию. Щелкните **Добавить инструменты** , чтобы запустить задание по созданию проекта миграции и регистрации выбранных решений.

> [!NOTE]
> Инструкции, применимые к вашему сценарию, см. в руководствах и [документации](/azure/migrate/migrate-services-overview) по Миграции Azure.
>

#### <a name="learn-more"></a>Дополнительные сведения

- [Сведения о службе "Миграция Azure"](/azure/migrate/migrate-services-overview)
- [Руководство по работе со службой "Миграция Azure". Перенос физических и виртуализированных серверов в Azure](/azure/migrate/tutorial-migrate-physical-virtual-machines)

### <a name="azure-database-migration-service"></a>Azure Database Migration Service

Azure Database Migration Service — это полностью управляемая служба, которая обеспечивает прозрачную миграцию из нескольких баз данных-источников на платформы данных Azure с минимальным временем простоя (миграцию в интерактивном режиме). Database Migration Service выполняет все необходимые действия. Можно запустить проекты миграции и больше не беспокоиться об этом процессе, зная, что будут выполнены рекомендации корпорации Майкрософт.

#### <a name="create-an-azure-database-migration-service-instance"></a>Создание экземпляра Azure Database Migration Service

Если вы впервые используете Azure Database Migration Service, необходимо зарегистрировать поставщик ресурсов для своей подписки Azure.

1. Последовательно выберите элементы **Все службы** > **Подписки** и выберите целевую подписку.
1. Выберите параметр **Поставщики ресурсов**.
1. В поле поиска введите `migration`, а затем справа от **Microsoft.DataMigration** щелкните **Зарегистрировать**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Billing/SubscriptionsBlade]" submitText="Go to Subscriptions" :::

::: zone-end

После регистрации поставщика ресурсов можно создать экземпляр Azure Database Migration Service.

1. Выберите элемент **+ Создать ресурс** и найдите **Azure Database Migration Service** в marketplace.
1. Завершите работу мастера создания Migration Service и нажмите кнопку **Создать**.

Теперь служба готова к переносу поддерживаемых баз данных-источников на целевые платформы, такие как SQL Server, MySQL, PostgreSQL или MongoDB.

::: zone target="chromeless"

::: form action="Create[#create/Microsoft.AzureDMS]" submitText="Create an Azure Database Migration Service instance" :::

::: zone-end

::: zone target="docs"

Дополнительные сведения см. в разделе:

- [Общие сведения о службе Azure Database Migration Service](/azure/dms/dms-overview)
- [Создание экземпляра Azure Database Migration Service](/azure/dms/quickstart-create-data-migration-service-portal)
- [Миграция Azure на портале Azure](https://portal.azure.com/#blade/Microsoft_Azure_ManagementGroups/HierarchyBlade)
- [Портал Azure: создание проекта миграции](https://portal.azure.com/#create/Microsoft.AzureMigrate)

::: zone-end

### <a name="azure-app-service-migration-assistant"></a>Помощник по миграции Службы приложений Azure

Помощник по миграции Службы приложений Azure входит в состав [более крупного набора приложений](https://azure.microsoft.com/services/azure-migrate/), которые помогают организациям при переходе в облако. Помощник по миграции предоставляет интерактивный пользовательский интерфейс в стиле мастера, выполняющий две задачи:

1. Он выполняет оценку конкретного веб-приложения, установленного в Windows Server. При этом в веб-приложении запускаются проверки совместимости, выполняемые перед миграцией, чтобы определить, можно ли перенести веб-приложение в Службу приложений Azure, не изменяя его.
1. Если оценка подтверждает, что веб-приложение можно перенести, Помощник по миграции выполняет миграцию. Для этого нужно предоставить Помощнику по миграции доступ к своей учетной записи Azure, выбрать группу ресурсов, которую хотите использовать, выбрать имя веб-приложения и другие аналогичные сведения.
Кроме того, Помощник по миграции создает шаблон Azure Resource Manager, который можно использовать для переноса веб-приложения автоматическим повторяемым способом.

#### <a name="migrate-a-web-app-to-azure-app-service"></a>Перенос веб-приложения в Службу приложений Azure

Помощник по миграции начинает процесс миграции, собирая основные сведения об учетной записи Azure, а затем выполняет миграцию.

Сначала войдите в учетную запись Azure и свяжите сеанс Помощника по миграции со своей учетной записью, используя уникальный код. Затем выберите подписку, группу ресурсов и доменное имя веб-сайта. Вы можете создать новый план Службы приложений Azure для размещения приложения или выбрать существующий. От этого выбора зависит географический регион, где будет размещаться приложение. Вы также сможете включить задачи по переносу в существующий проект миграции Azure. Наконец, можно либо пропустить настройку базы данных, либо настроить гибридное подключение, чтобы обеспечить соединение с базой данных.

Когда Помощник по миграции соберет и проверит выбранные вами параметры, он создает необходимые ресурсы Службы приложений Azure в выбранном регионе и группе ресурсов. Средство запаковывает исходные файлы веб-приложения в ZIP-архив и развертывает их с помощью API развертывания Службы приложений Azure. Наконец, он выполняет дополнительные действия по миграции, такие как помощь в настройке гибридного подключения.

После успешной миграции необходимо завершить все обычные задачи, выполняемые после миграции. К ним могут относиться:

- Перемещение параметров приложения и строк подключения из файла web.config в Службу приложений вручную.
- Перенос данных из локального экземпляра SQL Server в базу данных SQL Azure.
- Настройка SSL-сертификата.
- Настройка имен личных доменов.
- Настройка разрешений в Azure Active Directory.

Кроме того, вы можете изменить план размещения Службы приложений Azure и другие параметры, такие как автомасштабирование и слоты развертывания.

Дополнительные сведения см. в разделах: 

[Перенос приложений ASP.NET в Azure](/learn/paths/migrate-dotnet-apps-azure)

### <a name="data-migration-assistant"></a>Помощник по миграции данных

Помощник по миграции данных (DMA) помогает выполнить переход на современную платформу данных благодаря обнаружению проблем совместимости, которые могут влиять на функциональные возможности базы данных в новой версии SQL Server или Базы данных SQL Azure. DMA предлагает рекомендации по повышению производительности и надежности целевой среды, а также позволяет переместить схему, данные и неавтономные объекты с исходного сервера на целевой сервер.

Помощник по миграции данных интегрирован с Миграцией Azure, что позволяет отслеживать ход выполнения оценки на панели мониторинга Миграции Azure. Запустите DMA из Миграции Azure, добавив средство оценки баз данных Миграции Azure. Затем добавьте оценку базы данных в Миграцию Azure, нажав кнопку "Отправить в Миграцию Azure" в DMA.

> [!NOTE]
> Для крупномасштабных миграций (с точки зрения количества и размера баз данных) рекомендуется использовать службу Azure Database Migration Service, которая может переносить базы данных в нужном масштабе.
>

Начните использовать Помощник по миграции данных, выполнив следующие действия:

1. Скачайте Помощник по миграции данных из [Центра загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=53595) и установите его.
1. Создайте оценку, щелкнув значок **Создать (+)** и выбрав тип проекта **Оценка**.
1. Укажите тип исходного и целевого серверов, а затем щелкните **Создать**.
1. Настройте необходимые параметры оценки (рекомендуется использовать все значения по умолчанию).
1. Добавьте базы данных для оценки.
1. Щелкните **Далее** , чтобы запустить оценку.
1. Просмотрите результаты в Помощнике по миграции данных.

Для предприятия рекомендуется использовать подход, описанный в статье [Оценка предприятия и объединение отчетов оценки с помощью DMA](/sql/dma/dma-consolidatereports). Так вы сможете оценить несколько серверов, объединить отчеты и использовать предоставленные отчеты Power BI для анализа результатов.

Дополнительные сведения, включая подробные инструкции по использованию, доступны в следующих статьях:

- [Общие сведения о Помощнике по миграции данных](/sql/dma/dma-overview)
- [Оценка предприятия и объединение оценки с помощью DMA](/sql/dma/dma-consolidatereports)
- [Анализ консолидированных отчетов об оценке, созданных Помощником по миграции данных с помощью Power BI](/sql/dma/dma-powerbiassesreport)

### <a name="sql-server-migration-assistant"></a>Помощник по миграции SQL Server

Помощник по миграции Microsoft SQL Server (SSMA) — это средство для автоматизации переноса баз данных в SQL Server из Microsoft Access, DB2, MySQL, Oracle и SAP ASE. Общий принцип заключается в сборе данных, оценке и последующей проверке с помощью этих инструментов. Но ввиду различий между процессами для каждой исходной системы рекомендуется ознакомиться с подробной [документацией по Помощнику по миграции SQL Server](/sql/ssma/sql-server-migration-assistant).

Дополнительные сведения см. в разделе:

- [Общие сведения о Помощнике по миграции SQL Server](/sql/ssma/sql-server-migration-assistant)

### <a name="database-experimentation-assistant"></a>Database Experimentation Assistant

Database Experimentation Assistant (DEA) — это новое решение для A/B-тестирования обновлений SQL Server. Оно поможет оценить целевую версию SQL для конкретной рабочей нагрузки. Клиенты, которые обновляют предыдущие версии SQL Server (SQL Server 2005 и более поздние версии) до любой новой версии SQL Server, могут использовать эти метрики анализа.

Database Experimentation Assistant использует следующие действия рабочего процесса:

- **Запись.** Первый этап A/B-тестирования SQL Server — запись трассировки на исходном сервере. Исходным сервером обычно является рабочий сервер.
- **Воспроизведение.** Второй этап A/B-тестирования SQL Server — воспроизведение файла трассировки, который был записан, на целевых серверах. Затем выполняется сбор расширенных трассировок воспроизведения для анализа.
- **Анализ.** Заключительным этапом является создание аналитического отчета на основе трассировок воспроизведения. Аналитический отчет поможет получить полезные сведения о влиянии предлагаемого изменения на производительность.

Дополнительные сведения см. в разделе:

- [Общие сведения о Database Experimentation Assistant](/sql/dea/database-experimentation-assistant-overview)

### <a name="azure-cosmos-db-data-migration-tool"></a>Средство переноса данных Azure Cosmos DB

Средство переноса данных Azure Cosmos DB позволяет импортировать данные из различных источников в коллекции и таблицы Azure Cosmos DB. Данные можно импортировать из JSON-файлов, CSV-файлов, с сервера SQL, из MongoDB, хранилища таблиц Azure, Amazon DynamoDB и даже из коллекций API SQL для базы данных Azure Cosmos DB. Средство переноса данных можно также использовать при миграции из односекционной коллекции в многосекционную для API SQL.

Дополнительные сведения см. в разделе:

- [Средство переноса данных Azure Cosmos DB](/azure/cosmos-db/import-data)

## <a name="third-party-migration-tools"></a>[Инструменты миграции сторонних производителей](#tab/third-party-tools)

Процесс миграции можно упростить, воспользовавшись несколькими инструментами миграции сторонних производителей и службами независимых поставщиков программного обеспечения. Каждый из эти инструментов обеспечивает различные преимущества и возможности. Вот эти средства.

### <a name="unifycloud"></a>UnifyCloud

UnifyCloud — это служба ISV, которая предоставляет средства для автоматизации оценки, миграции и модернизации.

[Дополнительные сведения](https://www.unifycloud.com)

### <a name="cloudamize"></a>Cloudamize

Cloudamize — это служба независимого поставщика программного обеспечения, охватывающая все этапы стратегии миграции.

[Дополнительные сведения](https://www.cloudamize.com)

### <a name="zerto"></a>Zerto

Zerto обеспечивает виртуальную репликацию, которая обрабатывает как среды Microsoft Hyper-V, так и VMware vSphere.

[Дополнительные сведения](https://www.zerto.com/modernize)

### <a name="carbonite"></a>Carbonite

Carbonite предоставляет решения для переноса серверов и данных, позволяющие переносить рабочие нагрузки между любыми физическими, виртуальными или облачными средами.

[Дополнительные сведения](https://www.carbonite.com/data-protection/data-migration-software)

### <a name="movere"></a>Movere

Movere — это решение для обнаружения, которое предоставляет данные и аналитические сведения, необходимые для планирования миграции в облако и непрерывной оптимизации, мониторинга и анализа ИТ-сред.

[Дополнительные сведения](https://www.movere.io)

### <a name="azure-cosmos-db-partners"></a>Партнеры по Azure Cosmos DB

Вы можете выбрать из множества опытных партнеров и инструментов для системного интегратора, которые помогут с переносом данных в Azure Cosmos DB в соответствии с требованиями вашей базы данных NoSQL.

[Дополнительные сведения](/azure/cosmos-db/partners-migration-cosmosdb#migration-tools)

Посетите [Центр миграции Azure](https://azure.microsoft.com/migration/support), чтобы найти организации, предлагающие готовые к использованию технические решения партнеров, соответствующие вашим сценариям миграции. Узнайте больше о дополнительных инструментах миграции сторонних производителей и службах поддержки.

Из [этого руководства](https://datamigration.microsoft.com) вы узнаете о вариантах переноса баз данных в Azure. Кроме того, в получите пошаговые рекомендации по работе со встроенными возможностями и партнерами.

## <a name="project-management-tools"></a>[Инструменты управления проектами](#tab/project-management-tools)

В работе с проектами, которые не отслеживаются и не контролируются, скорее всего, возникнут проблемы. Чтобы обеспечить успешный результат, мы полагаем, важно использовать инструмент управления проектами. Существует множество различных инструментов, и у руководителей проектов в вашей организации уже могут быть любимые инструменты.

Azure DevOps — это рекомендуемое средство для управления проектами во время миграции в облако. Чтобы ускорить использование Azure DevOps, в Cloud Adoption Framework реализовано средство для автоматического развертывания шаблона проекта. Этот шаблон включает задачи, которые обычно выполняются во время миграции. Разверните шаблон, следуя инструкциям из статьи [Плана внедрения облачных технологий и Azure DevOps](/azure/architecture/cloud-adoption/plan/template). Затем вы можете изменить шаблон и внести данные о переносимых [рабочих нагрузках](/azure/architecture/cloud-adoption/plan/workloads) и [ресурсах](/azure/architecture/cloud-adoption/plan/assets).

Корпорация Майкрософт также предлагает следующие инструменты управления проектами, которые можно совместно использовать для расширения возможностей:

- [Планировщик (Майкрософт).](https://tasks.office.com) Простое визуальное средство организации командной работы.
- [Microsoft Project.](https://products.office.com/project/project-and-portfolio-management-software) Управление проектами, портфелем, емкостью ресурсов и финансами, а также учет рабочего времени и управление расписанием.
- [Microsoft Teams.](https://products.office.com/microsoft-teams) Средство совместной работы и обмена данными. Teams также интегрируется с планировщиком и другими инструментами для улучшения совместной работы.
- [Azure DevOps Services.](/azure/devops/user-guide/what-is-azure-devops?view=azure-devops) Шаблон планирования Cloud Adoption Framework не обязательно применять для работы с Azure DevOps. Вы можете использовать службу без шаблона и управлять инфраструктурой как кодом или использовать рабочие элементы и доски для управления проектами. По мере развития ваша организация может воспользоваться возможностями CI/CD.

Эти средства управления проектами не являются единственными доступными решениями. Многие другие инструменты сторонних производителей широко применяются в сообществе управления проектами.

### <a name="set-up-for-devops"></a>Настройка для использования DevOps

При переходе на облачные технологии предоставляется возможность внедрить в организации DevOps и CI/CD. Даже если ваша организация только управляет инфраструктурой, так как вы начинаете управлять инфраструктурой как кодом и используете отраслевые шаблоны и методики для DevOps, то вы сможете начать повышать гибкость с помощью конвейеров CI/CD. Это позволит быстрее адаптироваться к сценариям изменения, роста, выпуска и даже восстановления.

Azure DevOps предоставляет необходимые функции и обеспечивает интеграцию с Azure, локальными средами и другими облаками. Дополнительные сведения см. на странице [Azure DevOps](https://azure.microsoft.com/services/devops). Пошаговые инструкции для обучения см. в [кратком руководстве по CI/CD и Azure DevOps](https://microsoft.github.io/PartsUnlimited/pandp/200.1x-PandP-CICDQuickstartwithVSTS.html).

### <a name="suggested-skills"></a>Предлагаемые навыки

Microsoft Learn — это новый подход к изучению. Готовность к новым обязанностям, связанным с освоением и внедрением облачных технологий, дается нелегко. Microsoft Learn предоставляет более результативный подход к практическим занятиям, которые помогают быстрее достичь целей. Получайте баллы, проходите уровни и достигайте более высоких результатов.

Вот пример индивидуальной схемы обучения в Microsoft Learn, которая дополняет руководство по подготовке к DevOps в Cloud Adoption Framework.

[Создание приложений с помощью Azure DevOps](/learn/paths/build-applications-with-azure-devops): совместная работа с другими пользователями над сборкой приложений с помощью Azure Pipelines и GitHub; выполнение автоматических тестов в конвейере для проверки качества кода; проверка исходного кода и сторонних компонентов на предмет потенциальных уязвимостей; определение нескольких конвейеров, которые совместно используются при сборке приложения; сборка приложений с помощью агентов, размещенных в Майкрософт, и собственных агентов сборки.

## <a name="cost-management"></a>[Управление затратами](#tab/ManageCost)

При переносе ресурсов в облачную среду важно выполнять периодический анализ затрат. Так как процесс миграции может предусматривать дополнительные требования к использованию служб, периодический анализ затрат поможет вам избежать непредвиденных расходов на использование. Можно также изменить размер ресурсов, чтобы сбалансировать затраты и рабочую нагрузку. Дополнительные сведения см. в статье об [оптимизации и преобразовании](./optimize-and-transform.md).
