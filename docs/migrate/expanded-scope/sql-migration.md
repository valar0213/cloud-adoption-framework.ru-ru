---
title: Ускорение миграции с миграцией SQL
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Ускорение миграции с миграцией SQL
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4af94af91874ac666f45a917eed003b3cf881c51
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558224"
---
# <a name="accelerate-migration-with-a-sql-migration"></a>Ускорение миграции с миграцией SQL

Миграция целых экземпляров SQL Server может ускорить миграцию рабочей нагрузки. Следующие рекомендации помогут расширить область [руководства по миграции Azure](../azure-migration-guide/index.md) , переполнив SQL Server за пределами рабочей нагрузки, ориентированной на миграцию. Такой подход может заполнять перенос нескольких рабочих нагрузок на одну платформу данных.

## <a name="general-scope-expansion"></a>Расширение общей области

Большая часть усилий, необходимых для этого расширения области, будет происходить во время выполнения предварительных требований, оценки, миграции и оптимизации процессов миграции.

<!-- markdownlint-disable MD026 -->

## <a name="is-this-expanded-scope-right-for-you"></a>Подходит ли эта развернутая область?

Рекомендуемый подход, описанный в разделе [руководством по миграции в Azure](../azure-migration-guide/index.md) , заключается в переносе каждой структуры данных вместе с связанными рабочими нагрузками в рамках одной миграции. Итеративный подход к миграции сокращает число операций обнаружения, оценки и других задач, которые могут создавать блокировки и снизить вероятность возврата бизнес-значений.

Однако некоторые структуры данных можно перенести более эффективно с помощью отдельной миграции платформы данных. Ниже приведено несколько примеров, которые могут привести к использованию этого расширенного руководства по области.

- **Конец службы:** Быстрое перемещение SQL Server экземпляра во избежание проблем, возникающих в конце обслуживания, позволяет выровнять использование этого руководством за пределами стандартных усилий по переносу.
- **SQL Server службы:** Структура данных является частью более широкого решения, требующего SQL Server выполнения на виртуальной машине. Это распространено для решений, использующих SQL Server служб, таких как SQL Server Reporting Services, SQL Server Integration Services или SQL Server Analysis Services.
- **Высокая плотность, базы данных с низким уровнем использования:** SQL Server имеет высокую плотность баз данных. Каждая из этих баз данных имеет низкие объемы транзакций и требует небольших ресурсов вычислений. Следует учитывать другие современные решения, но подход IaaS может значительно снизить эксплуатационную стоимость.
- **Совокупная стоимость владения:** Если это применимо, можно применить [преимущества гибридного использования Azure](https://azure.microsoft.com/pricing/hybrid-benefit) к прейскуранту, создавая наименьшую стоимость владения для серверов SQL Server. Это особенно распространено для клиентов, которые размещают SQL Server в многооблачных сценариях.
- **Ускоритель миграции:** Миграция переноса SQL Server экземпляра может перемещать несколько баз данных за одну итерацию. Этот подход иногда позволяет будущим итерациям сосредоточиться на приложениях и виртуальных машинах, переносить больше рабочих нагрузок за одну итерацию.
- **Миграция VMware:** Общая локальная архитектура включает в себя приложения и виртуальные машины на виртуальном узле и в базах данных на компьютере без операционной системы. При переносе этой общей архитектуры миграция узла VMWare в службу VMWare Azure (AVS) может быть предоставлена в этом руководством для переноса целых SQL Server экземпляров для поддержки этих виртуальных узлов. Дополнительные рекомендации см. в разделе [Миграция узла VMware](./vmware-host.md).

Если ни одно из указанных выше условий не применимо к этой миграции, рекомендуется продолжить [процесс стандартного переноса](../index.md). В стандартном процессе структуры данных переносятся итеративно вместе с каждой рабочей нагрузкой.

Если это руководств соответствует вашим критериям, продолжайте работу с развернутой областью действия в рамках [стандартного процесса миграции](../index.md). На этапе предварительных требований можно интегрировать усилия в общий план внедрения.

## <a name="suggested-prerequisites"></a>Рекомендуемые предварительные требования

Перед выполнением SQL Server миграции Начните с расширения **цифрового пространства** , включив место для данных. В области данных регистрируется Инвентаризация ресурсов данных, которые предполагается перенести. В следующих таблицах описывается подход к записи данных.

### <a name="server-inventory"></a>Инвентаризация серверов

Ниже приведен пример инвентаризации сервера для серверов SQL Server.

|SQL Server|Цель|Версия|[Важности](../../manage/considerations/criticality.md)|[Уровень конфиденциальности](../../govern/policy-compliance/data-classification.md)|Число баз данных|Integration Services|Служба|АДАПТЕРЫ|Кластер|Количество узлов|
|---------|---------|---------|---------|---------|---------|---------|---------|
|SQL-01|Основные приложения|2016|Критически важная задача|Строго конфиденциально|40|Н/Д|Н/Д|Н/Д|ДА|3|
|SQL-02|Основные приложения|2016|Критически важная задача|Строго конфиденциально|40|Н/Д|Н/Д|Н/Д|ДА|3|
|SQL-03|Основные приложения|2016|Критически важная задача|Строго конфиденциально|40|Н/Д|Н/Д|Н/Д|ДА|3|
|SQL-04|BI|2012|Высокая|XX|6|Н/Д|Конфиденциально|Да — многомерный куб|Нет|1|
|SQL-05|Интеграция|2008 R2|Низкая|Общие сведения|20|ДА|Н/Д|Н/Д|Нет|1|

### <a name="database-inventory"></a>Инвентаризация базы данных

Ниже приведен пример инвентаризации базы данных для одного из серверов SQL Server, описанных выше.

|Сервер|База данных|[Важности](../../manage/considerations/criticality.md)|[Уровень конфиденциальности](../../govern/policy-compliance/data-classification.md)|Результаты DMA|Исправление DMA|Целевая платформа|
|---------|---------|---------|---------|---------|---------|---------|
|SQL-01|DB-1|Критически важная задача|Строго конфиденциально|Совместимы|Н/Д|Базы данных SQL Azure|
|SQL-01|DB-2|Высокая|Конфиденциально|Требуется изменение схемы|Реализованные изменения|Базы данных SQL Azure|
|SQL-01|DB-1|Высокая|Общие сведения|Совместимы|Н/Д|Управляемый экземпляр SQL Azure|
|SQL-01|DB-1|Низкая|Строго конфиденциально|Требуется изменение схемы|Запланированные изменения|Управляемый экземпляр SQL Azure|
|SQL-01|DB-1|Критически важная задача|Общие сведения|Совместимы|Н/Д|Управляемый экземпляр SQL Azure|
|SQL-01|DB-2|Высокая|Конфиденциально|Совместимы|Н/Д|Базы данных SQL Azure|

### <a name="integration-with-the-cloud-adoption-plan"></a>Интеграция с планом внедрения в облако

После завершения обнаружения план можно добавить в [план внедрения в облако](../../plan/template.md). В рамках плана внедрения в облако добавьте каждый экземпляр SQL Server для переноса в качестве отдельной [рабочей нагрузки](../../plan/workloads.md). В каждой рабочей нагрузке базы данных и службы (SSIS, SSAS, SSRS) могут добавляться в качестве [ресурсов](../../plan/workloads.md). Дополнительные сведения о добавлении рабочих нагрузок и ресурсов в план внедрения см. в статье [Добавление и изменение рабочих элементов с помощью Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

После включения рабочих нагрузок и ресурсов в план группа может продолжить работу со стандартным процессом миграции, используя план внедрения, чтобы поработать с руководством. Когда группа внедрения переходит в процессы оценки, миграции и оптимизации, необходимо учитывать следующие изменения.

## <a name="assessment-process-changes"></a>Изменения процесса оценки

Если любую базу данных в плане можно перенести в платформу данных PaaS, используйте Помощник по миграции данных, чтобы оценить совместимость выбранной базы данных. Если базе данных требуются преобразования схемы, рекомендуется выполнить эти преобразования в рамках процесса оценки, чтобы избежать сбоев конвейера миграции.

### <a name="suggested-action-during-the-assessment-process"></a>Предлагаемое действие в процессе оценки

Для баз данных, которые можно перенести в решение PaaS, в процессе оценки будут выполнены следующие действия.

- **Оценка с помощью помощник по миграции данных:** Используйте Помощник по миграции данных для обнаружения проблем совместимости, которые могут повлиять на функциональность базы данных в управляемом экземпляре базы данных SQL Azure, чтобы рекомендовать улучшения производительности и надежности, а также для перемещения схемы, данных и неавтономных объектов. с исходного сервера на целевой сервер. Дополнительные сведения см. в разделе [Помощник по миграции данных](/sql/dma/dma-overview).
- **Исправление и преобразование:** В зависимости от выходных данных Помощник по миграции данных преобразуйте схему источника данных, чтобы устранить проблемы совместимости. Протестируйте преобразованную схему данных с помощью зависимых приложений.

## <a name="migrate-process-changes"></a>Изменения в процессе миграции

Во время миграции существует несколько вариантов средств и подходов. Но каждый подход соответствует простому процессу: миграция схемы, данных и объектов. Синхронизация данных с целевым источником данных.

Цель и источник структуры данных и служб могут сделать эти два действия довольно сложными. Ознакомьтесь со следующими разделами, чтобы понять наилучший выбор средств на основе ваших решений о миграции.

### <a name="suggested-action-during-the-migrate-process"></a>Предлагаемое действие во время процесса миграции

Предлагаемый путь для миграции и синхронизации использует сочетание следующих трех средств. В следующих разделах описаны более сложные варианты миграции и синхронизации, которые позволяют использовать более широкий спектр целевых и исходных решений.

|Параметр миграции|Цель|
|---------|---------|
|[Azure Database Migration Service](/sql/dma/dma-overview)|Azure DMS поддерживает режим "в сети" (минимальное время простоя) и "автономный" (один раз) миграция в управляемый экземпляр базы данных SQL Azure из SQL Server 2005, SQL Server 2008 и SQL Server 2008 R2, SQL Server 2012, SQL Server 2014, SQL Server 2016 и SQL Server 2017.|
|[Репликация транзакций](/sql/relational-databases/replication/administration/enhance-transactional-replication-performance)|Репликация транзакций в управляемый экземпляр базы данных SQL Azure поддерживается для миграций из: SQL Server 2012 (с пакетом обновления 2 (SP2), SP3 или более поздней версии), SQL Server 2014 (RTM CU10 или более поздней версии или SP1 CU3 или более поздней версии), SQL Server 2016, SQL Server 2017|
|[Выполнить небольшую загрузку](/sql/t-sql/statements/bulk-insert-transact-sql)|Используйте массовый загрузку в управляемый экземпляр базы данных SQL Azure для хранения данных в SQL Server 2005, SQL Server 2008 и SQL Server 2008 R2, SQL Server 2012, SQL Server 2014, SQL Server 2016 и SQL Server 2017.|

### <a name="guidance-and-tutorials-for-suggested-migration-process"></a>Руководство и учебники по предложенному процессу миграции

Выбор лучших рекомендаций для миграции с помощью DMS зависит от выбранной исходной и целевой платформы. В следующей таблице приведены руководства по каждому из стандартных подходов к переносу базы данных SQL с помощью DMS.

|Источник  |Выбор пути миграции  |Средство  |Тип миграции  |Руководство  |
|---------|---------|---------|---------|---------|
|SQL Server|Базы данных SQL Azure|DMS|Автономно|[Руководство](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql)|
|SQL Server|Базы данных SQL Azure|DMS|В сети|[Руководство](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online)|
|SQL Server|Управляемый экземпляр базы данных SQL Azure|DMS|Автономно|[Руководство](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)|
|SQL Server|Управляемый экземпляр базы данных SQL Azure|DMS|В сети|[Руководство](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)|
|SQL Server RDS|База данных SQL Azure (или Управляемый экземпляр)|DMS|В сети|[Руководство](https://docs.microsoft.com/azure/dms/tutorial-rds-sql-server-azure-sql-and-managed-instance-online)|

### <a name="guidance-and-tutorials-for-various-services-to-equivalent-paas-solutions"></a>Руководства и руководства по различным службам для эквивалентных решений PaaS

После перемещения баз данных из SQL Server в DMS можно разместить схему и данные в нескольких решениях PaaS. Однако другие необходимые службы по-прежнему могут работать на этом сервере. Следующие три руководства помогут в перемещении служб SSIS, SSAS и SSRS в эквивалентные службы PaaS в Azure.

|Источник  |Выбор пути миграции  |Средство  |Тип миграции  |Руководство  |
|---------|---------|---------|---------|---------|
|Служба интеграции SQL Server|Integration Runtime фабрики данных|Фабрика данных Azure|Автономно|[Руководство](https://docs.microsoft.com/azure/data-factory/create-azure-ssis-integration-runtime)|
|Служба SQL Server Analysis Service — табличная модель|Azure Analysis Service|SSDT|Автономно|[Руководство](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy)|
|Служба отчетов SQL Server|Сервер отчетов Power BI|Power BI|Автономно|[Руководство](/power-bi/report-server/migrate-report-server)|

### <a name="guidance-and-tutorials-for-migration-from-sql-server-to-an-iaas-instance-of-sql-server"></a>Руководство и руководства по миграции с SQL Server на экземпляр IaaS SQL Server

После миграции баз данных и служб в экземпляры PaaS могут существовать структуры данных и службы, несовместимые с PaaS. Если существующие ограничения препятствуют переносу структур данных или служб, приведенный ниже учебник поможет перенести различные ресурсы из портфеля данных в решения Azure IaaS.

Этот подход можно использовать для переноса баз данных на SQL Server или других служб, работающих на исходном SQL Server.

|Источник  |Выбор пути миграции  |Средство  |Тип миграции  |Руководство  |
|---------|---------|---------|---------|---------|
|SQL Server одного экземпляра|Сервер SQL Server в IaaS|Изменяем|Автономно|[Руководство](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)|

## <a name="optimization-process-changes"></a>Изменения процесса оптимизации

Во время оптимизации каждая структура данных, служба или экземпляр SQL Server может быть протестирована, оптимизирована и перенесена в рабочую среду. Это наибольшее воздействие на отклонения от модели миграции рабочей нагрузки.

В идеале зависимые рабочие нагрузки, приложения и виртуальные машины будут перенесены в ту же итерацию, что и экземпляр SQL Server. В этом случае рабочую нагрузку можно протестировать вместе с источником данных. После тестирования структуру данных можно повысить до рабочей среды, после чего процесс синхронизации может завершиться.

К сожалению, самое важное изменение процесса оптимизации во время миграции, не связанных с рабочей нагрузкой, происходит в случае значительного промежутка времени между миграцией базы данных и рабочей нагрузкой. При переносе нескольких баз данных в рамках миграции SQL Server эти базы данных могут сосуществовать как в облаке, так и в локальной среде для нескольких итераций. В течение этого времени необходимо поддерживать синхронизацию данных до тех пор, пока эти зависимые ресурсы не будут перенесены, протестированы и подвергнуты повышению уровня.

До тех пор, пока все зависимые рабочие нагрузки не будут выдвинуты, группа будет отвечать за поддержку синхронизации данных из исходной системы с целевой системой. Эта синхронизация потребляет пропускную способность сети, облачные затраты и, что самое важное, время для People. Правильное выравнивание плана внедрения в рабочей нагрузке SQL Server миграции "и всех зависимых рабочих нагрузках и приложениях снижает эти дорогостоящие издержки.

### <a name="suggested-action-during-the-optimization-process"></a>Предлагаемое действие во время процесса оптимизации

Во время процессов оптимизации следующие задачи должны быть выполнены каждый раз, пока все структуры и службы данных не будут переведены в рабочую среду.

1. Проверка синхронизации данных.
2. Протестируйте перенесенные приложения.
3. Оптимизируйте приложение и структуру данных для настройки затрат.
4. Повышение уровня приложений до рабочей среды.
5. Проверка непрерывного локального трафика в локальной базе данных.
6. Завершите синхронизацию любых данных, перешедших в рабочую среду.
7. Завершите работу исходной базы данных источника.

До тех пор пока шаг 5 не проходит, базы данных и синхронизация не могут быть завершены. Пока все базы данных в SQL Server не пройдут шаги 1-7, локальная SQL Server должна рассматриваться как Рабочая и должна поддерживаться вся синхронизация.

## <a name="next-steps"></a>Дальнейшие действия

Вернитесь к [контрольному списку расширенной области](./index.md), чтобы убедиться, что выбранный метод миграции полностью вам подходит.

> [!div class="nextstepaction"]
> [Контрольный список расширенной области](./index.md)