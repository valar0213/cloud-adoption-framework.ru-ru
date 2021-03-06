---
title: Проверка параметров данных
description: Узнайте, как определить требования к данным для размещения рабочих нагрузок, с помощью платформы облачных технологий Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 9ad7787dd44314e0c83b55d5d799a111de021f6c
ms.sourcegitcommit: 07d56209d56ee199dd148dbac59671cbb57880c0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/26/2020
ms.locfileid: "88885071"
---
# <a name="review-your-data-options"></a>Проверка параметров данных

При подготовке среды зоны размещения для внедрения в облако необходимо определить требования к данным для размещения рабочих нагрузок. Продукты и службы баз данных Azure поддерживают различные сценарии и возможности хранения данных. То, как вы настраиваете среду зоны размещения для поддержки требований к данным, зависит от требований к системе управления рабочей нагрузкой, а также технических и бизнес-требований.

## <a name="identify-data-services-requirements"></a>Определение требований к службам данных

В рамках оценки и подготовки зоны размещения необходимо определить хранилища данных, которые должна поддерживать зона размещения. Процесс включает оценку каждого из приложений и служб в составе рабочих нагрузок, чтобы определить их требования к хранилищу данных и доступу. После того как вы определили и задокументировали эти требования, вы можете создать политики для своей зоны размещения, чтобы управлять разрешенными типами ресурсов в зависимости от потребностей рабочей нагрузки.

Для каждого приложения или службы, которые будут развернуты в среде зоны размещения, необходимо использовать приведенное ниже дерево решений в качестве отправной точки. Оно поможет вам определить соответствующие службы хранилища данных для использования.

![Дерево решений служб баз данных Azure ](../../_images/ready/data-decision-tree.png)
 _. 1. Дерево принятия решений служб базы данных Azure._

### <a name="key-questions"></a>Основные вопросы

Ответьте на следующие вопросы о рабочих нагрузках, которые помогут вам в принятии решения на основе дерева решений служб баз данных Azure.

- **Вам нужен полный контроль над программным обеспечением базы данных или ОС узла или владение им?** В некоторых случаях требуется, чтобы вы имели высокий уровень управления или владения конфигурацией программного обеспечения и серверами узлов для рабочих нагрузок баз данных. В этих сценариях вы можете развернуть пользовательские виртуальные машины в рамках инфраструктуры как услуги (IaaS), чтобы полностью контролировать развертывание и настройку служб данных. Если у вас нет этих требований, службы баз данных "платформа как услуга" (PaaS) могут снизить затраты на управление и эксплуатацию.
- **Будут ли рабочие нагрузки использовать технологию реляционной базы данных?** Если да, какую технологию вы планируете использовать? Azure предоставляет возможности базы данных, управляемой на основе модели PaaS для [Базы данных SQL Azure](/azure/sql-database/sql-database-technical-overview), [MySQL](/azure/mysql/overview), [PostgreSQL](/azure/postgresql/overview) и [MariaDB](/azure/mariadb/overview).
- **Будут ли рабочие нагрузки использовать SQL Server?** В Azure рабочие нагрузки могут выполняться на [SQL Server на виртуальных машинах Azure](/azure/azure-sql/virtual-machines) на основе модели IaaS или в [размещенной службе Базы данных SQL Azure](/azure/sql-database/sql-database-technical-overview) на основе модели PaaS. Выбор варианта использования в первую очередь зависит от того, хотите ли вы управлять базой данных, применять исправления и создавать резервные копии, или же вы хотите делегировать эти операции Azure. В некоторых сценариях проблемы совместимости могут потребовать использования SQL Server, размещенного в IaaS. Дополнительные сведения о том, как выбрать правильный вариант для рабочих нагрузок, см. в статье [Choose the right deployment option in Azure SQL](/azure/sql-database/sql-database-paas-vs-sql-server-iaas) (Выбор правильного параметра SQL Server в Azure).
- **Будут ли рабочие нагрузки использовать хранилище базы данных пары "ключ — значение"?** [Кэш Azure для Redis](/azure/azure-cache-for-redis/cache-overview) предлагает высокопроизводительное кэшированное решение для хранения пары "ключ — значение", которое может использоваться для быстрых масштабируемых приложений. [Azure Cosmos DB](/azure/cosmos-db/introduction) также предоставляет возможности общего назначения для хранения пары "ключ — значение".
- **Будут ли рабочие нагрузки использовать документ или данные графа?** [Azure Cosmos DB](/azure/cosmos-db/introduction) — это многомодельная служба базы данных, которая поддерживает различные типы данных и API. Azure Cosmos DB также предоставляет возможности базы данных для работы с документами и графами.
- **Будут ли рабочие нагрузки использовать столбчатое хранилище данных?** [Apache HBase в Azure HDInsight](/azure/hdinsight/hbase/apache-hbase-overview) создан на основе Apache Hadoop. Он поддерживает большие объемы неструктурированных и частично структурированных данных в базе данных, которая не имеет схемы и упорядочена по семействам столбцов.
- **Требуются ли для рабочих нагрузок возможности высокопроизводительной аналитики данных?** [Хранилище данных SQL Azure](/azure/sql-data-warehouse/sql-data-warehouse-overview-what-is) можно использовать, чтобы хранить и запрашивать структурированные данные петабайтового уровня. Для неструктурированных рабочих нагрузок с большими данными можно использовать [Azure Data Lake](https://azure.microsoft.com/solutions/data-lake) для хранения и анализа файлов петабайтного уровня-size и миллиарды объектов.
- **Требуются ли для рабочих нагрузок возможности поисковой системы?** [Поиск Azure](/azure/search/search-what-is-azure-search) можно использовать для создания облачных индексов поиска на основе искусственного интеллекта, которые можно интегрировать в приложения.
- **Будут ли рабочие нагрузки использовать данные временных рядов?** Служба " [аналитика временных рядов Azure](/azure/time-series-insights/time-series-insights-overview) " предназначена для хранения, визуализации и запроса больших объемов данных временных рядов, таких как данные, созданные устройствами Интернета вещей.

> [!NOTE]
> Дополнительные сведения об оценке параметров базы данных для каждого приложения или службы см. в статье [Criteria for choosing a data store](/azure/architecture/guide/technology-choices/data-store-comparison) (Критерии выбора хранилища данных).

## <a name="common-database-scenarios"></a>Распространенные сценарии баз данных

В следующей таблице приведены некоторые требования сценариев общего использования и рекомендуемые службы баз данных для их обработки:

| Сценарий  | Служба данных |
|---|---|
| Мне нужна глобально распределенная многомодельная база данных с поддержкой вариантов NoSQL. | [Azure Cosmos DB](/azure/cosmos-db/introduction) |
| Мне нужна полностью управляемая реляционная база данных, которая масштабируется на лету, со встроенным механизмом безопасности, искусственным интеллектом и высокой скоростью развертывания. | [База данных SQL Azure](/azure/sql-database/sql-database-technical-overview) |
| Мне нужна полностью управляемая, масштабируемая реляционная база данных MySQL с высокой доступностью и встроенным механизмом безопасности без дополнительной платы. | [База данных Azure для MySQL](/azure/mysql/overview) |
| Мне нужна полностью управляемая, масштабируемая реляционная база данных PostgreSQL с высокой доступностью и встроенным механизмом безопасности без дополнительной платы. | [База данных Azure для PostgreSQL](/azure/postgresql/overview) |
| Я планирую размещать корпоративные приложения SQL Server в облаке и иметь полный контроль над ОС сервера. | [SQL Server на виртуальных машинах](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview) |
| Мне нужно полностью управляемое эластичное хранилище данных, обеспечивающее безопасность на каждом уровне масштабируемости без дополнительной платы. | [Хранилище данных SQL Azure](/azure/sql-data-warehouse/sql-data-warehouse-overview-what-is) |
| Мне нужны Data Lake Storage ресурсы, поддерживающие кластеры Hadoop или данные HDFS. | [Azure Data Lake](https://azure.microsoft.com/solutions/data-lake) |
| Мне нужна высокая пропускная способность и доступ к данным с малым временем задержки для поддержки быстрых масштабируемых приложений. | [Кэш Azure для Redis](/azure/azure-cache-for-redis/cache-overview) |
| Мне нужна полностью управляемая, масштабируемая реляционная база данных MariaDB с высокой доступностью и встроенной системой безопасности без дополнительной платы. | [База данных Azure для MariaDB](/azure/mariadb/overview) |

## <a name="regional-availability"></a>Доступность по регионам

Azure позволяет предоставлять службы в нужном масштабе, чтобы обеспечить доступ к своим клиентам и партнерам, **где бы они ни**находились. Ключевым фактором при планировании развертывания облака является определение того, в каком регионе Azure будут размещаться ресурсы рабочей нагрузки.

Большинство служб баз данных обычно доступны в большинстве регионов Azure. Но существует несколько регионов, в основном нацеленных на правительственных клиентов, которые поддерживают только подмножество этих продуктов. Прежде чем выбирать регионы, в которые будут развернуты ресурсы базы данных, рекомендуется обратиться к [странице регионов](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=data-factory,sql-server-stretch-database,redis-cache,database-migration,sql-data-warehouse,postgresql,mariadb,cosmos-db,mysql,sql-database) , чтобы проверить актуальное состояние доступности в регионах.

Дополнительные сведения о глобальной инфраструктуре Azure см. на странице [Регионы Azure](https://azure.microsoft.com/global-infrastructure/regions). Вы также можете просматривать [продукты, доступные по регионам](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=all) , для получения конкретных сведений об общих службах, доступных в каждом регионе Azure.

## <a name="data-residency-and-compliance-requirements"></a>Местонахождение данных и соответствие требованиям

Юридические и договорные требования, связанные с хранением данных, часто будут применяться к рабочим нагрузкам. Эти требования могут различаться в зависимости от местоположения организации, юрисдикции физических ресурсов, в которых размещены хранилища данных, и применимого бизнес-сектора. Компоненты обязательств по данным, которые необходимо учитывать, включают классификацию данных, расположение данных и соответствующие обязанности для защиты данных в соответствии с моделью общей ответственности. Дополнительные сведения об этих требованиях см. в техническом документе, который обеспечивает [соответствие требованиям местонахождение данных и безопасность в Azure](https://azure.microsoft.com/resources/achieving-compliant-data-residency-and-security-with-azure).

Процесс обеспечения соответствия может включать контроль физического расположения ресурсов базы данных. Регионы Azure объединены в группы, называемые географическими регионами. [География Azure](https://azure.microsoft.com/global-infrastructure/geographies) гарантирует соблюдение требований к расположению, соответствию нормам и устойчивости в определенных географических и политических границах. Если на рабочие нагрузки распространяются независимость данных или другие требования соответствия, вы должны развернуть ресурсы хранилища в регионах в соответствующем географическом регионе Azure.

## <a name="establish-controls-for-database-services"></a>Установка элементов управления для служб баз данных

При подготовке среды зоны размещения вы можете установить элементы управления, ограничивающие возможности развертывания хранилищ данных для пользователей. Элементы управления позволяют управлять затратами и ограничивать риски безопасности, одновременно позволяя разработчикам и ИТ-специалистам развертывать и настраивать ресурсы, необходимые для поддержки рабочих нагрузок.

После определения и документирования требований зоны размещения вы можете использовать [Политику Azure](/azure/governance/policy/overview) для управления ресурсами базы данных, которые пользователям разрешено создавать. Элементы управления могут [разрешать или запрещать создание типов ресурсов базы данных](/azure/governance/policy/samples/allowed-resource-types). Например, вы можете разрешить пользователям создавать только ресурсы Базы данных SQL Azure. Кроме того, с помощью политики можно управлять допустимыми параметрами при создании ресурса, например ограничивать возможности [подготовки номеров SKU базы данных SQL](/azure/governance/policy/samples/allowed-sql-db-skus) или разрешать установку на виртуальную машину IaaS [только определенных версий SQL Server](/azure/governance/policy/samples/require-sql-12) .

Политика может быть масштабирована на ресурсы, группы ресурсов, подписки и группы управления. Вы можете включить свои политики в определения схемы [Azure](/azure/governance/blueprints/overview) и многократно применять их во время облачной организации.
