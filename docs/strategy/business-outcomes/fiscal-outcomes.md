---
title: Примеры финансовых результатов
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Примеры финансовых результатов
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.custom: governance
ms.openlocfilehash: ac62364b6117e4744b0432a5c4fbb46b7ee914b8
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/16/2019
ms.locfileid: "71029101"
---
# <a name="examples-of-fiscal-outcomes"></a>Примеры финансовых результатов

На верхнем уровне рассмотрение финансов состоит из трех основных принципов:

- **Доход**: Будет ли больше денег поступать в предприятия в результате продажи товаров или услуг.
- **Затраты** — Будет ли потрачено меньше денег на создание, маркетинг, продажи или доставку товаров или услуг.
- **Прибыль**: Хотя они редки, некоторые преобразования могут увеличить доходы и снизить затраты. Это результат прибыли.

Оставшаяся часть этой статьи посвящена этим финансовым результатам в контексте преобразования в облако.

> [!NOTE]
> Приведенные ниже примеры являются гипотетическими и не должны считаться гарантией возврата при внедрении любой стратегии облака.

## <a name="revenue-outcomes"></a>Результаты дохода

### <a name="new-revenue-streams"></a>Новые источники доходов

Облако может помочь в создании новых продуктов клиентам или доставлять существующие продукты новым способом. Новые потоки доходов являются инновационными, Слоан и интересными для многих людей в сфере бизнеса. Новые потоки доходов также подвержены ошибкам и, как и многие компании, имеют высокий риск. При предложении результатов, относящихся к доходу, скорее всего, это будет сопротивление. Чтобы добавить доверие к этим результатам, партнер с бизнес-лидером, который является проверенным инноватораом. Проверка потока доходов на ранних этапах процесса помогает избежать препятствийности бизнеса.

- **Пример**: Компания занимается продажей книг уже более ста лет. Сотрудник компании понимает, что содержимое может быть доставлено в электронном виде. Сотрудник создает устройство, которое можно продать в книжном магазине, что позволяет загружать одни и те же книги напрямую, $X в новых продажах книги.

### <a name="revenue-increases"></a>Увеличение дохода

Благодаря глобальному масштабированию и цифровому доступу облако может помочь компаниям повысить доходы от существующих потоков доходов. Часто этот тип результата поступает из выравнивания с руководством по продажам или маркетингу.

- **Пример**: Компания, которая продает мини-приложения, может продавать больше мини-приложений, если менеджеры могут безопасно получить доступ к цифровому каталогу и запасным уровням компании. К сожалению, эти данные находятся только в ERP-системе компании, доступ к которой можно получить только через устройство, подключенное к сети. Создание службы фасадной для взаимодействия с ERP и предоставление списка каталогов и неконфиденциальных складских запасов приложению в облаке позволит менеджерам по продажам получать доступ к необходимым им данным, а не к сайту с клиентом. Расширение локальных Active Directory с помощью Azure Active Directory (Azure AD) и интеграция доступа на основе ролей в приложение позволит компании обеспечить безопасность данных. Этот простой проект может повлиять на доход от имеющейся линейки продуктов на _x%_ .

### <a name="profit-increases"></a>Увеличение прибыли

В редких случаях одно усилие одновременно увеличивает доход и уменьшает затраты. Однако, когда это происходит, выровняйте выписки результатов от одного или нескольких результатов дохода с помощью одного или нескольких результатов затрат, чтобы сообщить желаемый результат.

## <a name="cost-outcomes"></a>Результаты затрат

### <a name="cost-reduction"></a>Сокращение затрат

Облачные вычисления могут сократить капитальные затраты на оборудование и программное обеспечение, настроить центры обработки данных, запускать центры обработки данных на месте и т. д. Затраты на стойки серверов, циклическое электричество для питания и охлаждения, а также ИТ-специалистов по управлению инфраструктурой быстро добавляются. Завершение работы центра обработки данных может снизить обязательства по капитальным затратам. Обычно это называется "выходом из бизнеса центра обработки данных". Снижение затрат обычно измеряется в долларах текущего бюджета, что может охватывать от одного до пяти лет в зависимости от того, как финансовый директор управляет финансами.

- **Пример #1**: Центр обработки данных компании потребляет большой процент ежегодного ИТ-бюджета. Он решает выполнить миграцию в облако и переносить активы из этого центра обработки данных в решения "инфраструктура как услуга" (IaaS), создавая снижение стоимости за три года.
- **Пример #2**: Холдинговая компания недавно приобрела новую компанию. В приобретении термины определяют, что новая сущность должна быть удалена из текущих центров обработки данных в течение шести месяцев. Несоблюдение этого действия приведет к появлению отличного от 1 000 000 долл. США в месяц для холдинга. Перемещение цифровых ресурсов в облако в облачной миграции может привести к быстрому списанию старых ресурсов.
- **Пример #3**: Компания, подоходная от компании, которая применяет клиентов к 70 процента годового дохода в течение первых трех месяцев года. В оставшейся части года его большие инвестиции в ИТ находятся относительно неактивно. Миграция в облако может позволить ИТ-подрешению развернуть ресурсы вычислений и размещения, необходимые в течение этих трех месяцев. В течение оставшихся девяти месяцев затраты на IaaS будут значительно снижены за счет сокращения объема вычислительных ресурсов.

### <a name="example-coverdell"></a>Пример: Coverdell

Компания Coverdell модернизирует свою инфраструктуру, чтобы обеспечить рекордную экономию средств с помощью Azure. Решение Coverdell инвестировать в Azure и объединить свою сеть веб-сайтов, приложений, данных и инфраструктуры в этой среде привело к экономии средств, превышающей все ожидания. Миграция в среду, предназначенную только для Azure, позволила сократить ежемесячные расходы на услуги по совместному размещению на 54 000 долл. США. С учетом новой, только Коверделлной инфраструктуры компании, в течение двух следующих трех лет мы планируем сохранить приблизительный 1 000 000 долларов США.

> "Доступ к стеку технологий Azure открывает дверцу для некоторых масштабируемых, простых в реализации и высокодоступных решений, которые являются экономичными. Это позволяет нашим архитекторам быть гораздо более творческим благодаря предоставляемым ими решениям ".  
> Райан Соренсен  
> Директор по разработке приложений и корпоративной архитектуре  
> Coverdell

### <a name="cost-avoidance"></a>Экономия средств

Прекращение использования центра обработки данных может также обеспечить избежание затрат, предотвращая будущие циклы обновления. Цикл обновления — это процесс покупки нового оборудования и программного обеспечения для замены устаревших локальных систем. В Azure оборудование и ОС регулярно обслуживаются, исправляются и обновляются без дополнительных затрат для клиентов. Это позволяет финансовому директору удалять запланированные будущие затраты с долгосрочных финансовых прогнозов. Издержки издержек измеряются в долларах. Он отличается от сокращения затрат, в основном в отношении будущего бюджета, который еще не был полностью утвержден.

- **Пример**: Центр обработки данных компании поддается продлению аренды за шесть месяцев. Центр обработки данных был в службе в течение восьми лет. Четыре года назад все серверы были обновлены и виртуализированы. стоимость компании составляет миллион долларов. В следующем году компания планирует повторно обновить оборудование и программное обеспечение. Перенос ресурсов в этом центре обработки данных в рамках миграции в облако позволит избежать затрат путем удаления запланированного обновления с прогнозируемого бюджета в следующем году. Это также может привести к сокращению затрат за счет уменьшения или устранения затрат на аренду недвижимости.

### <a name="capital-expenses-vs-operating-expenses"></a>Капитальные и операционные расходы

Прежде чем обсуждать результаты затрат, важно понимать два основных варианта стоимости: капитальные и эксплуатационные расходы.

Следующие термины помогут понять различия между капитальными затратами и эксплуатационными расходами во время бизнес-обсуждений, отменяющих преобразование.

- **Капитал** — это деньги и активы, принадлежащие бизнесу для участия в конкретной цели, например для увеличения емкости сервера или создания приложения.
- **Капитальные расходы** создают преимущества в течение длительного периода. Эти расходы обычно являются невременными и приводят к приобретению постоянных активов. Создание приложения может считаться капитальным расходом.
- **Эксплуатационные расходы** — это постоянные затраты на выполнение бизнес-задач. Использование облачных служб в модели с оплатой по мере использования может считаться эксплуатационным расходом.
- **Активы** — это экономические ресурсы, которые могут быть владельцами или управляемыми для получения ценности. Серверы, озера данных и приложения могут считаться ресурсами.
- **Амортизация** — это уменьшение значения ресурса с течением времени. В большей степени важна связь с капитальными затратами и расходов на операционные расходы, так как затраты актива распределяются по периодам, в которых они используются. Например, если вы создаете приложение в этом году, но предполагается, что средний срок хранения составляет пять лет (например, большинство коммерческих приложений), стоимость команды разработчиков и необходимые инструменты, необходимые для создания и развертывания базы кода, будут начисляться равномерно на пять кумулятив.
- **Оценка** — это процесс оценки стоимости компании. В большинстве отраслей оценка зависит от способности компании генерировать доход и прибыль при соблюдении операционных расходов, необходимых для создания товаров, обеспечивающих этот доход. В некоторых отраслях, например в розничной торговле, или в некоторых типах транзакций, таких как частный капитал, активы и амортизация, могут играть большую часть оценки компании.

Часто это является надежным элементом, который различные руководители, в том числе главный директор капиталовложений (Executive), приспорим к использованию капитального капитала для роста компании в нужном направлении. Предоставление РУКОВОДИТЕЛю средства преобразования спорныминых заглавных расходов в четкие учетные записи за операционные расходы может быть привлекательным результатом. Во многих отраслях финансовые директоры активно ищут способы лучшего объединения финансовой отчетности со стоимостью продаваемых товаров.

Однако перед связыванием любого межстраничного преобразования с преобразованием такого типа с прописными и операционными расходами разумно соблюсти членов групп финансового директора или директора, чтобы узнать, какая структура затрат предпочтительна для бизнеса. В некоторых организациях уменьшение капитальных затрат в пользу эксплуатационных расходов является очень нежелательным результатом. Как упоминалось ранее, этот подход иногда встречается в розничных, холдинговых и частных капиталах, которые помещают более высокую ценность в традиционные модели учета активов, которые помещают на IP-адрес небольшое значение. Она также встречается в организациях, которые имели негативные впечатления при работе с ИТ-специалистами или другими функциями в прошлом.

Если требуется рабочая модель расходов, следующий пример может быть приемлемым результатом:

- **Пример**: В настоящее время центр обработки данных компании начисляется на _x долл. США_ в год в течение следующих трех лет. Для обновления оборудования в следующем году требуется дополнительный _y-USD_ . Можно преобразовать капитальные расходы в модель рабочих расходов с четностью в _z долл. США_ в месяц, что позволяет повысить эффективность управления и учета эксплуатационных расходов на технологии.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о [результатах гибкости](./agility-outcomes.md).

> [!div class="nextstepaction"]
> [Результаты гибкости](./agility-outcomes.md)