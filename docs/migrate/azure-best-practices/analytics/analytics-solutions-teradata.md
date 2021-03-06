---
title: Миграция Azure синапсе Analytics для Teradata
description: Используйте инфраструктуру внедрения в облаке для Azure, чтобы узнать о решениях аналитики для Teradata и переходе на Azure синапсе Analytics.
author: v-hanki
ms.author: brblanch
ms.date: 07/14/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 7df0db259902f3b840c21138e111f06ab492aca4
ms.sourcegitcommit: c1d6c1c777475f92a3f8be6def84f1779648a55c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/21/2020
ms.locfileid: "92334805"
---
<!-- cSpell:ignore DATEADD DATEDIFF Inmon NUSI Informatica Talend BTEQ FASTEXPORT QUALIFY ORC Parquet "Parallel Data Transporter" Attunity "Qlik Replicate" -->

# <a name="azure-synapse-analytics-solutions-and-migration-for-teradata"></a>Решения и миграция Azure синапсе Analytics для Teradata

Многие организации готовы выполнить шаг сдвига дорогостоящих задач хранилища данных, таких как обслуживание инфраструктуры и разработка платформ, для поставщика облачных служб. Организации теперь стремятся воспользоваться преимуществами инновационного облака, инфраструктуры как услуги и предложений платформы как услуги в более новых средах, таких как Azure.


Azure синапсе Analytics — это неограниченная служба аналитики, которая объединяет корпоративные хранилища данных и аналитику больших данных. Это дает возможность запрашивать данные на ваших условиях в масштабе, используя либо бессерверные, либо подготовленные ресурсы. Узнайте, что нужно спланировать при переносе устаревшей системы Teradata в Azure синапсе.

Хотя Teradata и Azure синапсе похожи на базы данных SQL, предназначенные для использования методов массовой параллельной обработки для достижения высокой производительности запросов на больших объемах данных, они имеют некоторые базовые отличия.

- Устаревшие системы Teradata устанавливаются локально и используют собственное оборудование. Azure синапсе — это облачная служба, которая использует ресурсы вычислений и хранилища Azure.
- Обновление конфигурации Teradata — это основная задача, которая требует дополнительного физического оборудования и потенциально длительной перенастройки или дампа базы данных, а также перезагрузки. В Azure синапсе ресурсы вычислений и хранилища разделяются, поэтому вы можете легко масштабировать их независимо с помощью эластичной масштабируемости Azure.
- Без физической системы для поддержки можно приостановить или изменить размер Azure синапсе, чтобы сократить использование ресурсов и затрат. В Azure у вас есть доступ к глобально доступной, высокозащищенной и масштабируемой облачной среде, которая включает Azure синапсе в экосистему поддерживаемых средств и возможностей.

В этой статье рассматривается миграция схемы с целью получения эквивалентной или повышенной производительности перенесенного хранилища данных Teradata и киосков данных в Azure синапсе. Мы рассмотрим вопросы, которые применяются специально для перехода с существующей среды Teradata.

На высоком уровне процесс миграции включает в себя шаги, перечисленные в следующей таблице.

| Подготовка        | Миграция                             | Действия после миграции |
| :----------------- | :----------------------------- | :---------------- |
| <ul><li> Определение области действия: что нужно перенести?</li><li>Создание инвентаризации данных и процессов для миграции.</li><li>Определите любые изменения модели данных.</li><li>Укажите лучшие средства и функции Azure и сторонних производителей для использования.</li><li>Заблаговременное обучение персонала на новой платформе.</li><li>Настройте целевую платформу Azure.</li></ul> |  <ul><li>Начните с небольших и простых.</li><li>Автоматизируйте, где это возможно.</li><li>Используйте встроенные средства и функции Azure, чтобы сократить усилия по переносу.</li><li>Перенесите метаданные для таблиц и представлений.</li><li>Перенос соответствующих исторических данных.</li><li>Миграция и реструктуризация хранимых процедур и бизнес-процессов.</li><li>Миграция или рефакторинг процессов добавочной загрузки ETL/ELT.</li></ul> | <ul><li> Отслеживайте и документируйте все этапы процесса миграции.</li><li>Используйте интерфейс для создания шаблона для будущих миграций.</li><li>При необходимости репроизводительировать модель данных, используя производительность и масштабируемость новой платформы.</li><li>Тестирование приложений и средств запросов.</li><li>Производительность и оптимизация производительности запросов.</li></ul> |

При миграции из устаревшей среды Teradata в Azure синапсе в дополнение к более общим темам, описанным в документации по Teradata, необходимо учитывать некоторые конкретные факторы.

## <a name="initial-migration-workload"></a>Начальная Рабочая нагрузка миграции

Устаревшие среды Teradata обычно развиваются со временем, чтобы охватывать несколько областей субъектов и смешанных рабочих нагрузок. Если вы решите, где начать с первоначального проекта миграции, имеет смысл выбрать область, которая:

- Подтверждает жизнеспособность перехода на Azure синапсе, быстро предоставляя преимущества новой среды.
- Позволяет внутренним техническим сотрудникам получить опыт работы с новыми процессами и инструментами, чтобы они могли использовать их для переноса других областей.
- Создает шаблон на основе текущих средств и процессов для использования при дополнительной миграции из исходной среды Teradata.

Хорошим кандидатом для первоначальной миграции из среды Teradata, которая поддерживала эти цели, обычно является одна из них, которая реализует рабочую нагрузку Power BI или аналитики, а не рабочую нагрузку OLTP. Рабочая нагрузка должна иметь модель данных, которая может быть перенесена с минимальными изменениями, например со схемой «звезда» или «снежинка».

В качестве размера важно, чтобы объем данных, переносимый в начальном упражнении, был достаточно большим, чтобы продемонстрировать возможности и преимущества среды Azure синапсе с коротким временем для демонстрации ценности. Размер, который обычно соответствует требованиям, находится в диапазоне от 1 до 10 терабайт (ТБ).

Подход к первоначальному проекту миграции, который уменьшает риск и время реализации, позволяет ограничить область миграции до киосков данных. В Teradata хорошим примером является часть базы данных OLAP в хранилище данных Teradata. Этот подход является хорошей отправной точкой, так как он ограничивает область миграции и часто может быть достигнут на коротком шкале времени.

Начальная область миграции киосков данных не позволяет устранить более широкие возможности, такие как миграция ETL и исторических данных. Эти области необходимо устранить на последующих этапах и проделать перенесенный слой киоска данных данными и процессами, необходимыми для их построения.

## <a name="lift-and-shift-approach-vs-phased-approach"></a>Подход с приближением и сдвигом в сравнении с поэтапным подходом

Независимо от драйверов и области, выбранных для миграции, можно выбрать один из двух общих типов миграции:

- **Подход с нулификацией и сдвигом:** При таком подходе существующая модель данных, например схема «звезда», переносится в новую платформу Azure синапсе без изменений. Основное внимание уделяется минимизации риска и времени, затрачиваемого на миграцию, путем уменьшения объема работы, необходимой для достижения преимуществ перехода в облачную среду Azure.

  Этот подход хорошо подходит для существующих сред Teradata, в которых предполагается перенос одного киоска данных, и если данные уже находятся в хорошо спроектированной схеме «звезда» или «снежинка». Этот подход хорошо подходит для тех, кто испытывает затраты времени и затрат на переход в более современные облачные среды.

- **Поэтапный подход, включающий изменения:** Если хранилище прежних версий изменилось со временем, может потребоваться перехватить хранилище данных для поддержания необходимой производительности или поддержки новых источников данных, таких как потоки IoT. Переход на Azure синапсе для широко известных преимуществ масштабируемой облачной среды может рассматриваться как часть процесса реконструирования. Этот процесс может включать изменение базовой модели данных, например переход с модели Inmon на хранилище данных Azure.

  Рекомендуемый подход заключается в первоначальном перемещении существующей модели данных "как есть" в Azure. Затем воспользуйтесь преимуществами производительности и гибкости служб Azure, чтобы применить изменения, внесенные в процессе реконструирования, не затрагивая существующую исходную систему.

## <a name="virtual-machine-colocation-to-support-migration"></a>Совместное размещение виртуальных машин для поддержки миграции

Необязательный подход к миграции из локальной среды Teradata использует недорогое облачное хранилище и масштабируемость эластичных баз данных в Azure. Сначала создайте экземпляр Teradata на виртуальной машине Azure, совместно размещенной с целевой средой Azure синапсе. Затем вы используете стандартную служебную программу Teradata, например, параллельный транспорт Teradata, или сторонние средства репликации данных, такие как Qlik Sense replicate (ранее Attunity), для эффективного перемещения подмножества таблиц Teradata, переносимых на экземпляр виртуальной машины. Все задачи миграции выполняются в среде Azure.

Такой подход имеет несколько преимуществ.

- После начальной репликации данных в исходной системе не влияют другие задачи миграции.
- Привычные интерфейсы, средства и служебные программы Teradata доступны в среде Azure.
- Когда миграция будет перемещена в среду Azure, у вас нет потенциальных проблем с доступностью пропускной способности сети между локальной исходной системой и облачной целевой системой.
- Такие средства, как фабрика данных Azure, эффективно вызывают такие служебные программы, как "параллельный транспорт Teradata", для быстрого и простого переноса данных.
- Процесс миграции управляется и контролируется полностью в среде Azure.

## <a name="metadata-migration"></a>Миграция метаданных

Есть смысл автоматизировать и управлять процессом миграции, используя возможности среды Azure. Такой подход позволяет снизить влияние на существующую среду Teradata, которая, возможно, уже работает, близко к полной емкости.

Фабрика данных Azure — это облачная служба интеграции данных. Фабрику данных можно использовать для создания управляемых данными рабочих процессов в облаке для координации и автоматизации перемещения и преобразования данных. Конвейеры фабрики данных могут принимать данные из разнородных хранилищ данных. Затем они обрабатывают и преобразуют данные с помощью служб вычислений, таких как Azure HDInsight, для Apache Hadoop и Apache Spark, Azure Data Lake Analytics и Машинное обучение Azure.

Начните с создания метаданных, в которой перечислены таблицы данных, которые необходимо перенести вместе с их расположением. Затем используйте возможности фабрики данных для управления процессом миграции.

## <a name="design-differences-between-teradata-and-azure-synapse"></a>Различия в проектировании для Teradata и Azure синапсе

При планировании миграции из устаревшей среды Teradata в Azure синапсе важно учитывать различия в проектировании между двумя платформами.

### <a name="multiple-databases-vs-a-single-database-and-schemas"></a>Сравнение нескольких баз данных и одной базы данных и схем

В среде Teradata может существовать несколько отдельных баз данных для различных частей общей среды. Например, у вас может быть отдельная база данных для приема данных и промежуточных таблиц, база данных для базовых таблиц хранилища и другая база данных для киосков данных (иногда называемых _семантическим слоем_). Для обработки отдельных баз данных в качестве конвейеров ETL/ELT в Azure синапсе может потребоваться реализация межбазовых соединений и перемещение данных между отдельными базами данных.

Среда Azure синапсе имеет одну базу данных. Схемы используются для разделения таблиц на логически разделенные группы. Мы рекомендуем использовать серию схем в Azure синапсе, чтобы имитировать любые отдельные базы данных, переносимые из Teradata.

При использовании схем в среде Teradata может потребоваться использовать новое соглашение об именовании для перемещения существующих таблиц и представлений Teradata в новую среду. Например, можно объединить существующую схему Teradata и имена таблиц в новое имя таблицы Azure синапсе, а затем использовать имена схем в новой среде для сохранения оригинальных отдельных имен баз данных.

Другой вариант — использовать представления SQL для базовых таблиц, чтобы сохранить их логические структуры. Существуют некоторые потенциальные недостатки использования представлений SQL:

- Представления в Azure синапсе доступны только для чтения, поэтому необходимо внести любые изменения в данные базовых базовых таблиц.
- Если уровни представлений уже существуют, добавление другого слоя представлений может повлиять на производительность.

### <a name="tables"></a>Таблицы

При переносе таблиц между различными технологиями физическим перемещением являются только необработанные данные и метаданные, описывающие их между двумя средами. Вы не переносите элементы базы данных, такие как индексы из исходной системы, так как они могут не потребоваться, или они могут быть реализованы по-разному в новой среде.

Тем не менее, понимание того, где в исходной среде используются оптимизации производительности, такие как индексы, может быть полезным для оптимизации производительности в новой среде. Например, если в исходной среде Teradata был создан неуникальный вторичный индекс, можно завершить создание некластеризованного индекса в перенесенной среде Azure синапсе или использовать другие методики оптимизации производительности, такие как репликация таблиц, возможно, будет предпочтительнее создать индекс Like.

### <a name="high-availability-database"></a>База данных высокой доступности

Teradata поддерживает репликацию данных между узлами с помощью `FALLBACK` параметра. Строки таблицы, расположенные физически на узле, реплицируются на другой узел в системе. Такой подход гарантирует, что данные не теряются в случае сбоя узла и предоставляют базу для сценариев отработки отказа.

Цель архитектуры высокого уровня доступности в базе данных SQL Azure — гарантировать, что ваша база данных будет работать в 99,99% времени. Не нужно думать, как операции обслуживания и сбои могут повлиять на рабочую нагрузку. Azure автоматически обрабатывает критически важные задачи обслуживания, такие как исправление, резервное копирование и обновление Windows и SQL, а также незапланированные события, такие как базовое оборудование, программное обеспечение или сбои в сети.

Моментальные снимки — это встроенная функция службы, которая создает точки восстановления в Azure синапсе. Моментальные снимки обеспечивают автоматическое резервное копирование хранилища данных в Azure синапсе. Вам не нужно включать эту возможность. В настоящее время отдельные пользователи не могут удалять точки автоматического восстановления, используемые службой для обслуживания соглашений об уровне обслуживания для восстановления.

Azure синапсе создает моментальные снимки хранилища данных в течение дня. Создаваемые точки восстановления доступны в течение семи дней. Невозможно изменить срок хранения. Azure синапсе поддерживает целевую точку восстановления в 8 часов. Хранилище данных в основном регионе можно восстановить из любого моментального снимка, сделанного за последние семь дней. Другие определяемые пользователем параметры доступны, если Организация нуждается в более детализированных резервных копиях.

### <a name="unsupported-teradata-table-types"></a>Неподдерживаемые типы таблиц Teradata

Teradata включает поддержку специальных табличных типов для временных рядов и временных данных. Azure синапсе напрямую не поддерживает синтаксис и некоторые функции для этих табличных типов, но можно перенести данные в стандартную таблицу, имеющую необходимые типы данных, индексирование или секционирование в столбце даты и времени.

Teradata реализует функциональность временных запросов с помощью перезаписи запросов для добавления фильтров к временному запросу, чтобы ограничить соответствующий диапазон дат. Если вы используете временные запросы в исходной среде Teradata и хотите перенести их, необходимо добавить фильтры к соответствующим временным запросам.

Среда Azure также включает в себя функции для комплексной аналитики данных временных рядов в масштабе с помощью службы "аналитика временных рядов Azure". Аналитика временных рядов предназначена для приложений для анализа данных Интернета вещей и может быть более подходящей для этого варианта использования. Дополнительные сведения см. в статье служба " [аналитика временных рядов Azure](https://azure.microsoft.com/services/time-series-insights/)".

### <a name="teradata-data-type-mapping"></a>Сопоставление типов данных Teradata

Некоторые типы данных Teradata не поддерживаются в Azure синапсе напрямую. В следующей таблице показаны эти типы данных и рекомендованный способ их обработки. В таблице тип столбца Teradata — это тип, хранящийся в системном каталоге (например, в `DBC.ColumnsV` ).

Используйте метаданные из таблиц каталога Teradata, чтобы определить, следует ли перенести какой либо из этих типов данных, а затем запланируйте поддержку ресурсов в плане миграции. Например, можно использовать SQL-запрос, подобный приведенному в следующем разделе, чтобы найти все вхождения неподдерживаемых типов данных, которые необходимо решить.

Сторонние поставщики предлагают средства и службы, которые могут автоматизировать миграцию, включая сопоставление типов данных между платформами. Если в среде Teradata уже используется сторонний инструмент ETL, например Informatica или Таленд, можно использовать это средство для реализации всех необходимых преобразований данных.

## <a name="sql-data-manipulation-language-dml-syntax-differences"></a>Различия в синтаксисе языка обработки данных SQL (DML)

Вы должны знать о некоторых различиях в синтаксисе языка манипулирования данными SQL (DML) между Teradata SQL и Azure синапсе:

- `QUALIFY`: Teradata поддерживает `QUALIFY` оператор.

   Пример:

  `SELECT col1 FROM tab1 WHERE col1='XYZ'`

  Сторонние средства и службы могут автоматизировать задачи сопоставления данных:

  `QUALIFY ROW_NUMBER() OVER (PARTITION by col1 ORDER BY col1) = 1;`

  В Azure синапсе можно добиться того же результата, используя следующий синтаксис:

  `SELECT * FROM (SELECT col1, ROW_NUMBER() OVER (PARTITION by col1 ORDER BY col1) rn FROM tab1 WHERE c1='XYZ' ) WHERE rn = 1;`

- **Арифметические операции с датами:** В Azure синапсе есть такие `DATEADD` операторы `DATEDIFF` , как и, которые можно использовать в `DATE` или `DATETIME` .

   Teradata поддерживает прямое вычитание по датам:

  - `SELECT DATE1 - DATE2 FROM ...`

  - Синтаксис `LIKE ANY`

    Пример

    `SELECT * FROM CUSTOMER WHERE POSTCODE LIKE ANY ('CV1%', 'CV2%', CV3%') ;`.

    Эквивалент в синтаксисе Azure синапсе:

    `SELECT * FROM CUSTOMER WHERE (POSTCODE LIKE 'CV1%') OR (POSTCODE LIKE 'CV2%') OR (POSTCODE LIKE 'CV3%') ;`

- В зависимости от параметров системы, сравнение символов в Teradata может не зависеть от регистра по умолчанию. В Azure синапсе эти сравнения всегда зависят от регистра.

## <a name="functions-stored-procedures-triggers-and-sequences"></a>Функции, хранимые процедуры, триггеры и последовательности

При переносе хранилища данных из зрелой устаревшей среды, такой как Teradata, часто приходится переносить элементы, отличные от простых таблиц и представлений, в новую целевую среду. Примеры элементов, не являющихся таблицами в Teradata, которые может потребоваться перенести в Azure синапсе — это функции, хранимые процедуры, триггеры и последовательности. На этапе подготовки миграции необходимо создать инвентаризацию объектов для миграции. В плане проекта определите метод обработки всех объектов и выделите соответствующие ресурсы для их переноса.

Вы можете найти службы в среде Azure, которые заменяют функциональные возможности, реализованные в виде функций или хранимых процедур, в среде Teradata. Как правило, более эффективно использовать встроенные возможности Azure вместо перекодирования функций Teradata.

Ниже приведены дополнительные сведения о миграции функций, хранимых процедур, триггеров и последовательностей.

- **Функции:** Как и большинство продуктов баз данных, Teradata поддерживает системные функции и определяемые пользователем функции в реализации SQL. При переносе общих системных функций на другую платформу баз данных, например Azure синапсе, они обычно доступны в новой среде и могут быть перенесены без изменений. Если в новой среде системные функции имеют немного другой синтаксис, то обычно можно автоматизировать необходимые изменения.

  Может потребоваться Recode произвольные определяемые пользователем функции и системные функции, которые не имеют эквивалента в новой среде. Используйте языки, доступные в новой среде. Azure синапсе использует популярный язык Transact-SQL для реализации определяемых пользователем функций.

- **Хранимые процедуры:** В большинстве современных продуктов баз данных можно хранить процедуры в виде n. Хранимая процедура обычно содержит инструкции SQL и некоторую логику. Он также может возвращать данные или состояние.

  Teradata предоставляет язык хранимых процедур для создания хранимых процедур. Azure синапсе поддерживает хранимые процедуры с помощью T-SQL. При миграции хранимых процедур в Azure синапсе необходимо Recode их с помощью T-SQL.

- **Триггеры:** Вы не можете создавать триггеры в Azure синапсе, но можно реализовать триггеры в фабрике данных.

- **Последовательности:** Последовательности синапсе для Azure обрабатываются аналогично тому, как они обрабатываются в Teradata. Используйте `IDENTITY` столбцы или код SQL для создания следующего порядкового номера в ряде.

## <a name="metadata-and-data-extraction"></a>Извлечение метаданных и данных

При планировании извлечения метаданных и данных из среды Teradata учитывайте следующие сведения:

- **Создание языка описания данных (DDL):** Как было сказано ранее, можно изменить существующие Teradata `CREATE TABLE` и `CREATE VIEW` скрипты, чтобы создать эквивалентные определения с измененными типами данных, если это необходимо. В этом сценарии обычно необходимо удалить дополнительные предложения, относящиеся к Teradata (например, `FALLBACK` ).

  Сведения, указывающие текущую таблицу и определения представлений, хранятся в системных таблицах каталога. Таблицы системных каталогов являются лучшим источником информации, так как таблицы, вероятнее всего, являются актуальными и готовыми к работе. Возможно, документация, обслуживаемая пользователем, не синхронизирована с текущими определениями таблиц.

  Доступ к данным можно получить с помощью представлений в каталоге, таких как `DBC.ColumnsV` . Вы также можете использовать представления для создания эквивалентных `CREATE TABLE` инструкций языка описания данных DDL для эквивалентных таблиц в Azure синапсе.

  Средства миграции и извлечения, используемые сторонними производителями, также используют сведения о каталоге для достижения того же результата.

- **Извлечение данных**

  Перенос необработанных данных из существующих таблиц Teradata с помощью стандартных служебных программ Teradata, таких как `BTEQ` и `FASTEXPORT` . В упражнении по миграции, как правило, важно извлекать данные как можно более эффективно. Для последних версий Teradata мы рекомендуем использовать параллельный транспорт Teradata, служебную программу, которая использует несколько параллельных `FASTEXPORT` потоков для достижения лучшей пропускной способности.

  Параллельный транспорт Teradata можно вызывать непосредственно из фабрики данных. Мы рекомендуем использовать этот подход для управления процессом переноса данных, будь то локальный или скопированный экземпляр Teradata на виртуальную машину в среде Azure, как описано выше.

  Форматы данных, которые мы рекомендуем использовать для извлеченных данных, — это текстовые файлы с разделителями- _запятыми_, файлы оптимизированных столбцов строк или файлы Parquet.

Подробные сведения о процессе переноса данных и ETL из среды Teradata см. в документации по Teradata.

## <a name="performance-tuning-recommendations"></a>Рекомендации по настройке производительности

На платформах есть некоторые различия, когда речь идет о оптимизации. В следующем списке рекомендаций по настройке производительности будут выделены различия в реализации Teradata и Azure синапсе и альтернативы для миграции.

- **Варианты распространения данных:** В Azure можно задать методы распределения данных для отдельных таблиц. Эта функция предназначена для уменьшения объема данных, перемещаемых между обрабатывающими узлами при выполнении запроса.

  При больших соединениях таблиц и больших таблиц распределение хэша в одной или обеих таблицах столбцов соединения позволяет обеспечить локальную обработку соединения, так как объединяемые строки данных уже размещены на одном и том же узле обработки.

  Azure синапсе предоставляет дополнительный способ для достижения локальных соединений для небольших таблиц и больших соединений таблиц (часто называемых *таблицей измерения или соединением таблицы фактов* в модели схемы типа «звезда»). Вы реплицируете меньшую таблицу по всем узлам, гарантируя, что любое значение ключа объединения для большей таблицы будет иметь совпадающую строку измерения, которая локально доступна. Накладные расходы на репликацию таблицы измерения относительно низкие, если таблицы не велики. В этом случае предпочтительнее использовать подход хэш-распределения, описанный выше.

- **Индексирование данных:** Azure синапсе предоставляет различные параметры индексирования, но параметры для операций и использования в параметрах индексирования в Teradata различаются. Дополнительные сведения о параметрах индексирования в Azure синапсе см. в статье [Разработка таблиц в пуле синапсе для Azure](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-tables-overview).

  Существующие индексы в исходной среде Teradata могут предоставить полезные сведения об использовании данных и указать столбцы кандидатов для индексирования в среде Azure синапсе.

- **Секционирование данных:** В хранилище данных предприятия таблицы фактов могут содержать много миллиардов строк данных. Секционирование — это способ оптимизации обслуживания и выполнения запросов в этих таблицах. Разделение таблиц на отдельные части сокращает объем обрабатываемых данных за один раз. Секционирование для таблицы определяется в `CREATE TABLE` инструкции.

  Для секционирования можно использовать только одно поле на таблицу. Поле, используемое для секционирования, часто является полем даты, так как многие запросы фильтруются по датам или по диапазонам дат. Можно изменить секционирование таблицы после начальной загрузки. Чтобы изменить секционирование таблицы, повторно создайте таблицу с новым распределением, использующим `CREATE TABLE AS SELECT` инструкцию. Подробное описание секционирования в Azure синапсе см. в статье [секционирование таблиц в пуле SQL Azure синапсе](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-tables-partition).

- **Статистика таблицы данных:** Можно обеспечить актуальность статистики по таблицам данных, добавив `COLLECT STATISTICS` шаг в заданиях ETL/ELT или включив автоматическую сбор статистики для таблицы.

- **Polybase для загрузки данных:** Polybase — наиболее эффективный метод для загрузки больших объемов данных в хранилище. Polybase можно использовать для загрузки данных в параллельных потоках.

- **Классы ресурсов для управления рабочей нагрузкой:** Azure синапсе использует классы ресурсов для управления рабочими нагрузками. Как правило, крупные классы ресурсов обеспечивают лучшую производительность отдельных запросов. Классы ресурсов меньшего размера обеспечивают более высокие уровни параллелизма. Динамические административные представления можно использовать для отслеживания использования, чтобы обеспечить эффективное использование соответствующих ресурсов.

## <a name="next-steps"></a>Дальнейшие шаги

Дополнительные сведения о реализации миграции Teradata см. в учетная запись Майкрософт представителя по локальным предложениям миграции.
