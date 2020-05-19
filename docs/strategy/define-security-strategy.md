---
title: Определение стратегии безопасности
description: Используйте платформу внедрения облачных технологий для Azure, чтобы научиться создавать обоснование для миграции в облако.
author: MarkSimos
ms.author: mas
ms.date: 04/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 36fa032ce989dedd393886e7154aa46e1c7e376b
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83229929"
---
<!-- cSpell:ignore MarkSimos NIST CISO COVID -->

# <a name="define-a-security-strategy"></a>Определение стратегии безопасности

Конечные цели для организации безопасности не изменяются при внедрении облачных служб, но их назначение изменится. Группы безопасности по-прежнему должны сосредоточиться на снижении бизнес-рисков от атак и работы, чтобы получить сведения о конфиденциальности, целостности и доступности, встроенные во все информационные системы и данные.

## <a name="modernize-your-security-strategy"></a>Модернизировать стратегию безопасности

Группам безопасности необходимо модернизировать стратегии, архитектуры и технологии, так как организация применяет облако и работает со временем. Хотя размер и количество изменений могут показаться непростыми, модернизации программы безопасности позволяет системе безопасности пролить некоторые ненужные проблемы, связанные с традиционными подходами. Организация может временно взаимодействовать с унаследованной стратегией и инструментами, но этот подход трудно поддерживать с темпом изменения в облаке и в среде угроз:

- Группы безопасности, скорее всего, не будут принимать решение о принятии решений по внедрению, если они занимают устаревшую систему безопасности "подлокотников", где ответ всегда начинается с "No" (вместо совместной работы с ИТ и бизнес-группами для снижения риска при включении бизнеса).
- Группы безопасности будут труднее обнаруживать атаки в облаке и выполнять защиту от них, если они используют только устаревшие локальные средства и исключительно периметр сети Doctrine для всех средств защиты и мониторинга. Защита в масштабе облака требует использования облачных средств обнаружения и автоматизации, а также введения периметра удостоверения для отслеживания и защиты облачных и мобильных ресурсов.

Поскольку это преобразование может быть значительным, мы рекомендуем группам безопасности использовать гибкий подход к модернизации безопасности, который быстро модернизирована наиболее важные аспекты стратегии, а затем постоянно улучшать его.

### <a name="security-of-the-cloud-and-from-the-cloud"></a>Безопасность облака и облачных служб

По мере внедрения облачных служб в организации группы безопасности будут работать с двумя основными целями:

- **Безопасность \* \* облака (защита облачных ресурсов).** безопасность должна быть интегрирована в планирование и эксплуатацию облачных служб, чтобы обеспечить единообразное применение этих ключевых мер безопасности ко всем ресурсам.
- **Безопасность \* из \* облака (с использованием облака для преобразования безопасности).** безопасность должна немедленно начать планирование и подумать об использовании облачных технологий для модернизировать средств и процессов безопасности, в особенности встроенных средств безопасности. Другие средства безопасности размещаются в облаке и предоставляют возможности, которые трудно или невозможно выполнить в локальной среде.

Многие организации начинают с рассмотрения облачных ресурсов в качестве дополнительного _виртуального центра обработки данных_, который очень хорошо работает в качестве отправной точки для обеспечения безопасности облака. По мере того, как Организации модернизировать безопасность из облака, большинство из них быстро найдут на эту модель. Защита программно-определяемого центра обработки данных с помощью облачных средств обеспечивает возможности, которые могут быть доступны не только в локальных моделях:

- Быстрое включение и масштабирование возможностей обеспечения безопасности.
- Высоко эффективная Инвентаризация активов и конфигурация безопасности санации Discovery.
- Непрерывная оценка уровня безопасности и элементов управления Организации.
- Значительно улучшенное обнаружение угроз, которое использует большие репозитории для анализа угроз и практически неограниченную обработку или хранение облака.

### <a name="the-right-level-of-security-friction"></a>Правильный уровень трения системы безопасности

Безопасность естественным образом создает трение, которое замедляет процессы, очень важно определить, какие элементы являются работоспособными в DevOps и ИТ-процессах, а какие нет:

- **Работоспособность трения:** Как и в случае с сопротивлением, в упражнении значительно повышается степень защиты системы или приложения путем принудительного выполнения критического мышления в нужное время. Как правило, это позволяет понять, почему и как злоумышленник может попытаться нарушить безопасность приложения или системы во время разработки, а также просмотреть, определить и в идеале устранять потенциальные уязвимости, которые злоумышленник может использовать в коде программного обеспечения, конфигурациях или методиках эксплуатации.
- **Неработоспособное состояние трения:** Противостоит большему значению, чем защищается. Это часто случается, когда ошибки безопасности, создаваемые инструментами, имеют высокий ложный положительный результат (например, ложные сигналы), или если усилия по обнаружению или исправлению проблем безопасности значительно превышают потенциальное воздействие атаки.

### <a name="standalone-and-integrated-responsibilities"></a>Автономные и интегрированные обязанности

Чтобы обеспечить конфиденциальность, целостность и доступность, необходимо, чтобы специалисты по безопасности работали с выделенными функциями безопасности и тесно работали с другими группами в Организации:

- **Уникальные функции безопасности:** Группы безопасности выполняют независимые функции, которые не находятся в другом расположении в Организации, такие как операции безопасности, управление уязвимостью и другие функции.
- **Интеграция безопасности в другие функции:** Группы безопасности также служат экспертами в качестве экспертов для других команд и функций в Организации, которые создают бизнес-инициативы, оценивают риски, проектирование и разработку приложений, а также операционные системы ИТ. Группы безопасности рекомендовать эти команды опытным и контекстным атакам, методам атак и тенденциям, уязвимостям, которые могут привести к несанкционированному доступу, а также варианты действий по устранению рисков, их возможных преимуществ или ловушек. Эта функция безопасности похожа на функцию качества, так как она будет вовен на множество мест, больших и маленьких для поддержки одного результата.

Учитывая эти обязанности, вы сможете обеспечить быстрое изменение в облаке и преобразовать бизнес, чтобы группы безопасности модернизировать свои средства, технологии и процессы.

## <a name="transformations-mindsets-and-expectations"></a>Преобразования, постановки и ожидания

Многие организации управляют цепочкой нескольких одновременных преобразований в Организации. Эти внутренние преобразования обычно начинают, так как почти все внешние рынки преобразуются в соответствии с новыми предпочтениями клиента для мобильных и облачных технологий. Организации часто сталкиваются с конкурентной угрозой новых запусков и цифровым преобразованием традиционных конкурентов, которые могут нарушить работу рынка.

![Цепочка нескольких одновременных преобразований в Организации](../_images/security/transformation-chain.png)

Процесс внутреннего преобразования обычно включает в себя следующее:

- **Цифровое преобразование** бизнеса для сбора новых возможностей и обеспечения конкурентоспособности от цифровых запусков машинного кода.
- **Технологические преобразования** ИТ ИТ для поддержки инициативы с облачными службами, современными методиками разработки и связанными изменениями.
- **Преобразование безопасности** для адаптации к облаку и одновременного решения более сложной среды угроз.

### <a name="internal-conflict-can-be-costly"></a>Внутренний конфликт может быть дорогостоящим

Изменение создает нагрузку и конфликтует, что может привести к остановке принятия решений. Это особенно справедливо в обеспечении безопасности, когда ответственность за риск нарушения безопасности часто возникает неверно в экспертных целях (командах по обеспечению безопасности), а не на владельцах активов (бизнес-владельцев), которые могут учитывать результаты бизнеса и другие типы рисков. Это неверно размещенная отчетность часто возникает потому, что все заинтересованные лица неправильно просматривают безопасность как технические или абсолютные проблемы, которые необходимо решить, а не динамические риски, такие как корпоративные шпионажем и другие традиционные уголовные действия.

В течение этого времени лидер по всем группам должен активно работать, чтобы снизить конфликт, который может сорвать критические проекты и группы инцентивизе, чтобы обойти риски безопасности. Конфликт интернеЦине между командами может привести к следующим результатам:

- **Повышенная угроза безопасности** , такая как предотвращение инцидентов безопасности или повышение ущерба от атак (особенно когда команды загружаются системой безопасности и обходят нормальные процессы, или когда злоумышленники легко обходят устаревшие методы безопасности).
- **Отрицательное влияние на бизнес или задачи** , например на то, что бизнес-процессы не включаются или не обновляются достаточно быстро, чтобы удовлетворить потребности рынка (часто, когда процессы безопасности отвечают основным бизнес-инициативам).

Очень важно следить за работоспособностью отношений в и между командами, чтобы помочь им переходить на альбом смены, что может привести к небезопасному и несопоставленному членам группы. Терпение, сопереживание и образование на этих условиях и положительные потенциальные возможности будущего помогут вашим командам лучше перемещаться по этому периоду, обеспечивая хорошие результаты безопасности для Организации.

Руководители могут упростить изменение языка и региональных параметров с помощью конкретных упреждающих шагов, таких как:

- Общедоступное моделирование поведения, ожидаемого их командами.
- Это прозрачное решение проблем, связанных с изменениями, включая выделение собственных вопросов для адаптации.
- Регулярное напоминание о группах срочности и важности модернизации и интеграции безопасности.

### <a name="cybersecurity-resilience"></a>Устойчивость кибербезопасности

Многие классические стратегии безопасности были сосредоточены исключительно на предотвращении атак, что не является достаточным для современных угроз. Специалисты по безопасности должны убедиться, что их стратегия выходит за рамки этого, а также позволяет быстро обнаруживать атаки, отреагировать на них и восстанавливать их, чтобы повысить устойчивость. В организациях необходимо предположить, что злоумышленники будут скомпрометированы некоторые ресурсы (иногда называемые «предполагаемым нарушением»), а также убедиться в том, что ресурсы и технические проекты сбалансированы между предотвращением атак и управлением атаками (а не обычным стандартным подходом только к предотвращению атак).

Многие организации уже находятся в этом пути, так как они управляют постоянным увеличением объема и сложности атак за последние годы. Это путешествие часто начинается с первого основного инцидента, который может быть эмоциональномом, когда люди теряют свои знания об уязвимости и безопасности. Хотя это событие не так серьезно, как в случае потери жизненного цикла, оно может активировать аналогичные эмоции, начиная с отказа и заканчивая принятием. Это предположение "сбой" может быть трудным для принятия в первую очередь, но оно имеет строгое согласование с хорошо установленным принципом инженерного проектирования, и предположение позволяет вашим командам сосредоточиться на улучшенном определении успеха: устойчивость.

Функции [инфраструктуры NIST кибербезопасности](https://www.nist.gov/cyberframework) служат полезным руководством по обеспечению баланса инвестиций между дополнительными действиями по выявлению, защите, обнаружению, реагированию и восстановлению в отказоустойчивой стратегии.

Дополнительные сведения об устойчивости кибербезопасности и конечных целях элементов управления кибербезопасности обсуждаются в разделе [как обеспечить риск для вашей организации](https://docs.microsoft.com/azure/architecture/framework/security/resilience).

### <a name="how-the-cloud-is-changing-security"></a>Изменение безопасности в облаке

Переход к облаку для обеспечения безопасности — это больше, чем простое изменение технологии. оно является сдвигом на технологии в аналогии для перехода с мэйнфреймов на настольные компьютеры и на серверы предприятия. Для успешного перехода к этому изменению требуются фундаментальные изменения в ожидании и применении группами безопасности. Принятие правильных положений и ожиданий снизит число конфликтов в Организации и повысит эффективность групп безопасности.

Хотя они могут быть частью любого плана безопасности модернизации, быстрый темп изменений в облаке делает их более срочными.

- **Партнерство с общими целями.** В этом сроке принятия решений и постоянной эволюции процессов безопасность больше не может применять подход с подлокотниками для утверждения или запрета изменений в среде. Группы по обеспечению безопасности должны тесно взаимодействовать с бизнес-специалистами и группами ИТ для создания общих целей, связанных с производительностью, надежностью и безопасностью и совместной работой, совместно с этими партнерами для их достижения.

  Это партнерство является в итоге «сдвигом влево» &mdash; принципа интеграции безопасности в процессах, чтобы упростить и повысить эффективность решения проблем безопасности. Для этого требуется, чтобы язык и региональные параметры были изменены всеми вовлеченными (Security, Business и IT), при этом каждый из них должен изучить язык и региональные параметры и нормы других групп, одновременно одновременно обучить других пользователей.

  Группы по обеспечению безопасности должны:

  - **Узнайте** о задачах бизнеса и ИТ и о том, почему каждый из них важен и как они думают о достижении их по мере преобразования.
  - **Делитесь** тем, почему безопасность важна в контексте бизнес-целей и рисков, а также о том, что другие команды могут сделать для удовлетворения целей безопасности и как они должны делать это.

  Хотя это и не простая задача, важно обеспечить устойчивую защиту Организации и ее активов. Это партнерство, скорее всего, приведет к работоспособным компромиссам, в которых изначально могут выполняться только минимальные цели безопасности, бизнеса и надежности, но постепенно улучшаются с течением времени.

- **Безопасность является постоянным риском, а не проблемой.** Вы не можете «разрешить» преступления. По сути, безопасность — это просто дисциплина управления рисками, которая, в своюмся, посвящена вредоносным действиям, а не естественным событиям. Как и все риски, безопасность не является проблемой, которую можно устранить с помощью решения. это сочетание вероятности и воздействия на ущерб от отрицательного события, атаки. Она наиболее сравнима с традиционными корпоративными шпионажем и уголовными действиями, когда организации сталкиваются с человеческими злоумышленниками, обладающими финансовой стимулом к успешной атаке Организации.

- **Для достижения успеха в любой производительности или безопасности требуется и то, и другое.** Организация должна сосредоточиться на безопасности и производительности в современных условиях. Если организация не работает эффективно и не способствует новым нововведениям, она может потерять конкурентоспособность в Marketplace, что приводит к ослаблению финансовых или неудачи. Если организация не защищена и теряет контроль над ресурсами злоумышленников, она может потерять конкурентоспособность в Marketplace, которая приводит к ослаблению финансовых показателей и в конечном итоге привести к сбою.

- **Никто не идеален.** Организация не идеально подходит для внедрения облака, а не Майкрософт. Специалисты корпорации Майкрософт по ИТ и безопасности быи многие из тех же самых трудностей, которые наши клиенты делают, например, для выяснения того, как лучше структурировать программы, обеспечивать поддержку устаревшего программного обеспечения благодаря поддержке новейших инноваций и даже пропусков технологий в облачных службах. Поскольку эти группы научились лучше работать и защищать облако, они активно совместно используют свои уроки, полученные с помощью таких документов, как и другие на [сайте ИТ-специалистов](https://www.microsoft.com/itshowcase), а также постоянно предоставляют отзывы нашим группам инженеров и сторонним поставщикам для улучшения своих предложений.

  На основе нашего опыта мы рекомендуем, чтобы группы занимали стандарт непрерывного обучения и улучшения, а не стандарт совершенство.

- **Возможность в преобразовании.** Очень важно просматривать цифровое преобразование как положительную возможность для обеспечения безопасности. Хотя можно легко увидеть потенциальные недостатки и риск возникновения этого изменения, можно легко пропустить огромную возможность повторной инвентаризации роли безопасности и получения места в таблице, где принимаются решения. Партнерство с бизнес-предприятием может привести к увеличению финансирования безопасности, снижению непроизводительна повторяющихся усилий в области безопасности и повышению уровня безопасности, так как они будут более надежны для работы в Организации.

## <a name="adopting-the-shared-responsibility-model"></a>Принятие общей модели ответственности

Размещение ИТ-служб в облаке разделяет эксплуатационные обязанности и ответственность в безопасности для рабочих нагрузок между поставщиком облачных услуг и клиентом клиента, создавая партнерство «де-факто» с общими обязанностями. Все группы по обеспечению безопасности должны изучить и понять эту модель общей ответственности, чтобы адаптировать свои процессы, средства и наборы навыков к новому миру. Это поможет избежать случайного создания пробелов или перекрытия в целях безопасности, приводящих к угрозам безопасности или расходам ресурсов.

На этой схеме показано, как будут распределяться обязанности безопасности между поставщиками облачных и облачных клиентов в партнерской связи "де-факто":

![Распределенные обязанности в безопасности](../_images/security/security-responsibilities.png)

Так как существуют различные модели облачных служб, обязанности каждой рабочей нагрузки зависят от того, где они размещены: программное обеспечение как услуга (SaaS), платформа как услуга (PaaS), инфраструктура как услуга (IaaS) или локальный центр обработки данных.

## <a name="building-security-initiatives"></a>Создание инициатив по безопасности

На этой схеме показаны три основные инициативы по обеспечению безопасности, которые должны следовать большинству программ безопасности, чтобы настроить стратегию безопасности и цели программы безопасности для облака.

![Основные инициативы по безопасности](../_images/security/primary-security-initiatives.png)

Для создания отказоустойчивой системы безопасности в облаке требуется несколько параллельно дополняющих подходов:

- **Доверять, но проверить:** Для обязанностей, выполняемых поставщиком облачных служб, организациям следует использовать подход "доверять, но проверять". Организации должны оценить методы обеспечения безопасности своих поставщиков облачных служб и средств управления безопасностью, которые они предлагают, чтобы обеспечить соответствие поставщика облачных требований безопасности Организации.

- **Модернизировать инфраструктуры и безопасности приложений:** Для технических элементов в управлении организацией Установите приоритеты для средств безопасности модернизации и свяжите наборы навыков, чтобы максимально сокращать зазоры в области охвата для защиты ресурсов в облаке. Это состоит из двух различных дополнительных действий:

  - **Безопасность инфраструктуры:** Организации должны использовать преимущества облака, чтобы модернизировать их подход к защите и мониторингу общих компонентов, используемых многими приложениями, такими как операционные системы, сети, операционные системы и инфраструктура контейнеров. Эти облачные возможности часто включают в себя управление компонентами инфраструктуры в IaaS и в локальных средах. Оптимизация этой стратегии важна, так как эта инфраструктура является зависимостью от приложений и данных, которые выполняются на ней, что часто включает критически важные бизнес-процессы и хранят важные бизнес-данные.
  - **Безопасность приложений:** Организации также должны модернизировать способ защиты уникальных приложений и технологий, разработанных в или для своей организации. Эта дисциплина быстро изменяется благодаря внедрению процессов Agile DevOps, повышению использования компонентов с открытым исходным кодом и ознакомлению с облачными API и облачными службами для замены компонентов приложения или приложений Interconnect.

    Это право очень важно, так как эти приложения часто обеспечивают критически важные бизнес-процессы и хранят важные бизнес-данные.

  - **Современный периметр:** Организации должны иметь всеобъемлющий подход к защите данных во всех рабочих нагрузках, организациям следует создать современный периметр последовательно управляемых элементов управления идентификацией для защиты своих данных, устройств и учетных записей. На это сильно влияет стратегия нулевого доверия, подробно рассмотренная в модуле 3 перспективы семинаре, и дополнительные материалы.

### <a name="security-and-trust"></a>Безопасность и доверие

Обратите внимание, что использование слова «Trust» в системе безопасности может привести к путанице. Эта документация называется двумя способами, иллюстрирующими полезные приложения этой концепции:

- [Отсутствие доверия](https://www.microsoft.com/security/business/zero-trust) — это распространенный термин для стратегического подхода к безопасности, который предполагает, что корпоративная сеть или интрасеть является вредоносной (достойной "без доверия") и соответствующим образом проектирует безопасность.
- [Доверие, но проверка](https://en.wikipedia.org/wiki/trust,_but_verify) — это выражение, которое фиксирует суть двух разных организаций, работающих вместе в направлении к общей цели, несмотря на наличие других потенциально ненужных интересов. Это позволяет кратко захватывать множество различных нюансов поэтапного создания партнеров с помощью коммерческого поставщика облачных служб для организаций.

Поставщик облачных услуг и их методики и процессы можно учитывать в соответствии с контрактными и нормативными требованиями, которые могут заработать или потерять доверие. Сеть — это неживое подключение, которое не может повлиять на последствия использования злоумышленниками (подобно тому, что вы не можете удержать дорожку или автомобиль для злоумышленников, использующих их).

## <a name="how-cloud-is-changing-security-relationships-and-responsibilities"></a>Как облако изменяет отношения и обязанности в отношении безопасности

Как и в предыдущих переходах к новому поколению технологий, таких как настольные вычисления и корпоративные серверные вычисления, смена облачных вычислений нарушает долгосрочные отношения, роли, обязанности и наборы навыков. Описания заданий, которые мы привыкли к более чем за последние десятки десятилетий, не будут четко сопоставляться с предприятием, которое теперь включает возможности облака. По мере того, как отрасль работает для нормализации новой модели, организациям придется сосредоточиться на предоставлении как можно более четкого уточнения, чтобы помочь управлять неоднозначностью в течение этого периода изменения.

Группы безопасности затронули эти изменения в бизнес-и технологических технологиях, которые они поддерживают, а также собственные внутренние модернизации усилия, чтобы лучше ориентироваться на субъекты угроз. Злоумышленники активно развиваются для постоянного поиска самых слабых точек, которые могут быть использованы людьми, процессами и технологиями Организации и безопасности, должны разработать возможности и навыки для решения этих углов.

В этом разделе описываются основные связи, которые часто меняются в пути к облаку, в том числе уроки по минимизации рисков и принятию возможных сделок по улучшению:

- **Между безопасностью и заинтересованными сторонами бизнеса:** Лидерам в сфере безопасности необходимо все большее сопартнерство с бизнес-лидерами, чтобы позволить организациям снизить риски. Руководители безопасности должны поддерживать принятие бизнес-решений в качестве эксперта в области безопасности (экспертов) и должны стремиться к росту доверенных консультантов для этих руководителей. Эта связь поможет гарантировать, что бизнес-руководители будут рассматривать риски безопасности при принятии бизнес-решений, информировать о безопасности приоритетов бизнеса и обеспечить соблюдение приоритета инвестиций в систему безопасности вместе с другими вложениями.

- **Между лидерами в безопасности и членами группы:** Лидер в сфере безопасности должен принять эти ценные сведения от бизнес-лидера к своим командам, чтобы помочь им в планировании инвестиций.

  Установив тон взаимодействия с лидерами бизнеса и их командами, а не классической связью "подлокотники", руководители безопасности могут избежать отчуждения динамичности, что противопоставлено целям обеспечения безопасности и производительности.

  Руководители безопасности должны стремиться к повышению производительности своей команды по управлению ежедневными решениями на производительность и компромиссы в области безопасности, так как это может быть новым для многих групп.

- **Между группами приложений и инфраструктуры (и поставщиками облачных решений):** Это отношение является значительным изменением из-за нескольких тенденций в сфере ИТ и безопасности, направленных на повышение скорости инноваций и производительности разработчиков.

  Старые функции нормы и организации были прерваны, но новые нормы и функции по-прежнему возникают, поэтому мы рекомендуем принять условия неоднозначности, сохранить текущее обдумывание и поэкспериментировать с тем, что работает для ваших организаций, пока это не произойдет. Мы не рекомендуем использовать в этом пространстве подход "wait and", так как это может привести к постановке вашей организации в серьезные конкурентные недостатки.

  Эти тенденции являются сложной нормой для ролей и отношений между приложениями и инфраструктурой:

  - **DevOps — отказ от дисциплин:** В идеальном состоянии это эффективно создает единую функциональную группу, объединяющую оба набора знаний предметной области для быстрого внедрения, обновления выпуска и устранения проблем (безопасность и иным образом). Хотя это идеальное состояние займет некоторое время, а обязанности в середине по-прежнему являются неоднозначными, организации уже используют некоторые преимущества быстрых выпусков из-за этого подхода. Корпорация Майкрософт рекомендует интегрировать безопасность в этот цикл, чтобы помочь в изучении этих культур, совместном использовании сведений о безопасности и работе с целью быстрого выпуска безопасных и надежных приложений.

  ![DevOps — отказ от дисциплин](../_images/security/devops-disciplines.png)

  - **Контейнер становится общим компонентом инфраструктуры:** Приложения все чаще размещаются и управляются такими технологиями, как DOCKER, Kubernetes и аналогичные технологии. Эти технологии упрощают разработку и выпуск за счет абстракции множества элементов установки и настройки базовой операционной системы.

  ![Инфраструктура контейнеров](../_images/security/containerization.png)

  Хотя контейнеры начали использоваться в качестве технологии разработки приложений, управляемой командами разработчиков, она становится общим компонентом инфраструктуры, который все чаще переходит на группы инфраструктуры. Этот переход по-прежнему выполняется во многих организациях, но это естественное и положительное направление. Многие из текущих проблем лучше решить с помощью традиционных наборов навыков инфраструктуры, таких как сеть, хранилище и Управление емкостью.

  Группы инфраструктуры и члены группы безопасности, которые их поддерживают, должны предоставлять обучение, процессы и инструментарий, помогающие управлять, отслеживать и защищать эту технологию.

  - **Бессерверные и облачные службы приложений:** Одной из основных тенденций в отрасли теперь является сокращение времени и объема работ по разработке, необходимых для сборки или обновления приложений.

    ![Бессерверные и облачные службы приложений](../_images/security/serverless-model.png)

    Кроме того, разработчики все чаще используют облачные службы для:

    - Запуск кода вместо размещения приложений на виртуальных машинах и серверах.
    - Предоставьте функции приложения вместо разработки собственных компонентов. Это привело к _бессерверной_ модели, которая использует существующие облачные службы для распространенных функций. Количество и разнообразные облачные службы (и их темпы инноваций) также превышают способность групп безопасности оценивать и утверждать использование этих служб, оставляя им возможность выбирать между тем, чтобы разработчики могли использовать любую службу, попытаться предотвратить использование неутвержденных служб или попробовать найти более подходящий способ.
    - **Приложения, не имеющие кода, и приложения Power Apps:** Еще одна новая тенденция — использование Бескодовых технологий, таких как Microsoft Power Apps. Эта технология позволяет пользователям без навыков написания кода создавать приложения, которые обеспечивают результаты бизнеса. Из-за такого низкого уровня трения и высокой ценности эта тенденция может быстро подняться на популярность, а специалисты по безопасности будут разумно быстро понять его последствия. Усилия по обеспечению безопасности должны быть сосредоточены на областях, в которых человек может сделать ошибку в приложении, а именно спроектировать разрешения приложения и ресурса с помощью моделирования угроз для компонентов приложения, взаимодействий и связей, а также разрешений роли.

- **Между разработчиками и авторами компонентов с открытым исходным кодом:** Разработчики также увеличивают эффективность с помощью компонентов и библиотек с открытым исходным кодом вместо разработки собственных компонентов. Это повышает эффективность, но также приводит к угрозам безопасности за счет создания внешней зависимости и требования для надлежащего обслуживания и исправления этих компонентов. Разработчики фактически предполагают риск безопасности и других ошибок, когда они используют эти компоненты, и необходимо убедиться в том, что в плане есть план, способный снизить их по тем же стандартам, что и код, который они будут разрабатывать.

- **Между приложениями и данными:** Линия между безопасностью данных и приложений становится размытой в местах, а новые нормативы требуют более тесного взаимодействия между группами данных и конфиденциальности и группами безопасности:

  - **Алгоритмы машинного обучения (машинного обучения).** алгоритмы машинного обучения похожи на приложения в том, что они предназначены для обработки данных с целью создания результата. Ниже описаны основные различия.

    - **Машинное обучение с высокой ценностью:** Машинное обучение часто предоставляет значительное конкурентное преимущество и часто считается конфиденциальной интеллектуальной собственностью и коммерческим секретом.

    - **Отпечатке чувствительности:** Контролируемое машинное обучение настраивается с помощью наборов данных, которые распечатывать характеристики набора данных в алгоритме. По этой причине настроенный алгоритм может считаться конфиденциальным из-за набора данных, используемого для обучения. Например, изучение алгоритма машинного обучения для поиска секретов армии на карте с помощью набора данных секретных баз армии сделает его конфиденциальным ресурсом.

    > [!NOTE]
    > Не все примеры очевидны, поэтому очень важно объединить группу с нужными заинтересованными лицами из групп обработки и анализа данных, заинтересованных лиц, специалистов по безопасности, групп обеспечения конфиденциальности и других. Эти команды должны отвечать за выполнение распространенных целей инноваций и ответственности. Они должны решать распространенные проблемы, например, как и где хранить копии данных в незащищенных конфигурациях, как классифицировать алгоритмы, а также любые проблемы в организациях.
    >
    > Корпорация Майкрософт опубликовала наши [принципы ответственного ии](https://www.microsoft.com/ai/responsible-ai) , чтобы помочь нашим группам и нашим клиентам.

    - **Владение данными и конфиденциальность:** Такие положения, как GDPR, увеличивают видимость проблем данных и приложений. Группы приложений теперь могут управлять, защищать и отслеживать конфиденциальные данные на уровне, сравнимом с отслеживанием финансовых данных по банкам и финансовым учреждениям. Владельцым данных и группам приложений необходимо создать обширное представление о том, что такое хранилище приложений данных и какие элементы управления необходимы.

- **Между организациями и поставщиками облачных служб:** По мере того как организации размещают рабочие нагрузки в облаке, они входят в бизнес-отношения с каждым из этих поставщиков облачных служб. Использование облачных служб часто приводит к таким преимуществам, как:

  - **Ускорение инициатив по цифровому преобразованию** за счет сокращения времени до рынка для новых возможностей.

  - **Увеличение ценности ИТ-деятельности и действий по обеспечению безопасности** за счет использования команд, чтобы сосредоточиться на более высоких значениях (с учетом бизнеса), а не на более низких уровнях, которые более эффективны облачными службами от их имени.

  - **Повышенная надежность и скорость реагирования:** Большинство современных облаков также имеют чрезвычайно высокую бесперебойную работу по сравнению с традиционными локальными центрами обработки данных и показали, что они могут быстро масштабироваться (например, во время КОВИД-19 гриппа) и обеспечивать устойчивость следующих естественных событий, таких как молния (что позволило бы значительно сократить количество локальных эквивалентов).

    Хотя это и очень полезно, эта смена в облаке не имеет риска. Так как организации принимают облачные службы, они должны учитывать потенциальные области риска, в том числе:

  - **Непрерывность бизнес-процессов и аварийное восстановление:** Является ли облачный поставщик финансово работоспособным с бизнес-моделью, которая, скорее всего, будет стабильной и развиваться во время использования службы в Организации? Предоставил ли поставщик облачных услуг возможность бесперебойной работы клиентов, если у поставщика возникли финансовые или другие сбои, такие как предоставление им исходного кода клиентам или открытием открытых источников?

    Дополнительные сведения и документы, относящиеся к финансовой работоспособности корпорации Майкрософт, см. в [статье связи с Microsoft инвесторами](https://www.microsoft.com/investor).

  - **Безопасность:** Следует ли поставщику облачных услуг следовать рекомендациям по обеспечению безопасности? Прошло ли это проверку по независимым стандартам?

    - [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/risk-score) позволяет обнаруживать использование более 16 000 облачных приложений, которые ранжированы и оцениваются на основе более чем 70 факторов риска, что позволяет обеспечить постоянную видимость облачных ресурсов, а также создавать теневые копии и риски, которые она создает в вашей организации.
    - [Портал доверия служб Майкрософт](https://servicetrust.microsoft.com) обеспечивает сертификацию соответствия нормативным требованиям, отчеты об аудите, тесты пером и другие возможности для клиентов. Эти документы содержат множество подробных сведений о внутренних методах безопасности (в частности, отчет SOC 2 типа 2 и план безопасности FedRAMP среднего уровня системы).

  - **Бизнес-конкурент:** Является ли поставщик облачной службы значительным бизнес-конкурентом в вашей отрасли? Есть ли у вас достаточные меры защиты в контракте облачных служб или другие средства для защиты вашего бизнеса от потенциально вредоносных действий?

    Ознакомьтесь с [этой статьей](https://www.cnbc.com/2019/03/16/why-volkswagen-chose-microsoft-azure-over-aws.html) , чтобы комментировать, как корпорация Майкрософт помогает избежать конкурирующих клиентов с облачными клиентами.

  - **Многооблако:** Во многих организациях предусмотрена стратегия многооблачного или преднамеренного в нескольких облаках. Это может быть преднамеренная цель, которая позволит снизить нагрузку на одного поставщика или получить доступ к уникальным возможностям, но может быть вызвана тем, что разработчики выбрали предпочтительные или знакомые облачные службы или ваша организация приобрела другой бизнес. Независимо от причины, эта стратегия может привести к потенциальным рискам и затратам, которые должны быть управляемыми, включая:

    - **Время простоя из нескольких зависимостей:** Системы, разработанные для полагаться на несколько облаков, становятся более разными источниками риска, так как нарушения в работе поставщиков облачных услуг (или их использование командой) могут привести к сбою или сбою вашего бизнеса. Такое увеличение сложности системы также увеличит вероятность событий нарушения работы, так как члены группы менее вероятно могут полностью понять более сложную систему.
    - **Согласование питания:** В более крупных организациях также следует подумать о том, что одно облако (взаимное обязательство или партнерство) или стратегия в нескольких облаках (возможность смены бизнеса) будет оказывать больше влияния на облачные поставщики для получения приоритетных запросов к функциям Организации.
    - **Увеличенные затраты на обслуживание:** Ресурсы ИТ и безопасности уже перегружаются из существующих рабочих нагрузок и отслеживаются с учетом изменений в одной облачной платформе. Каждая дополнительная платформа дополнительно увеличивает эти издержки и берет на себя членов группы от более высоких значений, таких как упрощение технического процесса для ускорения бизнес-инноваций, консультации с бизнес-группами на более эффективном использовании технологий и т. д.
    - **Персонал и обучение:** Организации часто не учитывают требования к персоналу, необходимые для поддержки нескольких платформ, и обучение, необходимое для поддержания знаний и валюты новых функций, которые выпускаются в быстром темпе.