---
title: Выравнивание портфеля
description: Узнайте о стратегиях балансировки миграции, инноваций и экспериментов, чтобы максимально эффективно воспользоваться вашими усилиями по миграции в облако.
author: BrianBlanchard
ms.author: brblanch
ms.date: 03/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 56ee70ac6d695159f2baeee50b49decd1cb08543
ms.sourcegitcommit: 8b82889dca0091f3cc64116f998a3a878943c6a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/09/2020
ms.locfileid: "89605120"
---
# <a name="balance-the-portfolio"></a>Выравнивание портфеля

Внедрение облачных решений — это деятельность по управлению портфелем, которая хорошо замаскирована в качестве технической реализации. Как и в любом упражнении по управлению портфелем, балансировка портфеля является критической. На стратегическом уровне это означает балансировку миграции, инноваций и экспериментов для максимально эффективного использования облака. Когда усилия по внедрению в облако повышаются в одном направлении, сложность находит свой путь к усилиям по внедрению. В этой статье представлены различные способы достижения баланса в портфеле.

## <a name="general-scope-expansion"></a>Расширение общей области

Балансировка портфеля является стратегическим по своей природе. Поэтому подход, приведенный в этой статье, тоже является стратегическим. В этой статье предполагается, что вы выполнили стратегию для принятия решений, основанных на данных [, и начали](../digital-estate/index.md) этот процесс. Цель этого подхода — помочь в оценке рабочих нагрузок и обеспечить правильный баланс в портфеле с помощью качественных вопросов и корректировки портфеля.

<!-- docutune:casing 2M -->

### <a name="document-business-outcomes"></a>Структура бизнес-результатов

Перед балансировкой портфеля важно документировать и поделиться результатами бизнеса, влияющими на облачные миграции. Следующая таблица поможет задокументировать и предоставить желаемые бизнес-результаты. Важно отметить, что большинство компаний преследуют сразу несколько целей. Важность этого упражнения состоит в том, чтобы уточнить результаты, которые наиболее тесно связаны с процессом миграции в облако.

| Результат | Измерение | Цель | Интервал времени | Приоритет действия |
|--|--|--|--|--|
| Сокращение расходов на ИТ | Бюджет центра обработки данных | Уменьшение на 2 MБ USD | 12 месяцев | 1 |
| Выход из центра обработки данных | Выход из центров обработки данных | 2 центра обработки данных | 6 месяцев | 2 |
| Повышение гибкости организации | Сокращение времени выхода на рынок | Сокращение времени развертывания на шесть месяцев | 2 года | 3 |
| Улучшение качества взаимодействия с клиентами | Удовлетворенность клиентов (КСАТ) | Улучшение на 10 % | 12 месяцев | 4 |

> [!IMPORTANT]
> Приведенная выше таблица является вымышленным примером и не должна использоваться для установки приоритетов. Во многих случаях эту таблицу можно рассматривать как антишаблонную, помещая экономию затрат выше, чем у клиентов.

Приведенная выше таблица могла бы точно представить приоритеты группы облачной стратегии и группы внедрения в облако. Из-за краткосрочных ограничений эта группа отдает предпочтение снижению расходов на ИТ и использует для этого уход из центра обработки данных. При этом, указав в таблице альтернативные приоритеты, команда по внедрению в облако может помочь команде по вопросам облачной стратегии определить возможности, позволяющие эффективнее реализовать стратегию комплексного портфеля.

### <a name="move-fast-while-maintaining-balance"></a>Быстрые действия с сохранением баланса

В рекомендациях по [добавочной рационализации цифровых активов](../digital-estate/index.md) предлагается подход, при котором процесс рационализации начинается с несбалансированной позиции. Команда по вопросам облачной стратегии должна оценить совместимость каждой рабочей нагрузки с методом повторного размещения. Этот подход рекомендуется, так как он позволяет быстро оценить сложные цифровые активы на основе количественных данных. Такое первоначальное предположение позволяет команде по внедрению в облако быстро действовать, сократив период внедрения в организации. Однако, как указано в этой статье, качественные вопросы обеспечат необходимый баланс в портфеле. В этой статье описывается процесс создания обещанного баланса.

### <a name="importance-of-sunset-and-retire-decisions"></a>Важность решений о прекращении использования

В таблице в разделе [Документирование бизнес-результатов](#document-business-outcomes) выше не хватает важного результата, который обеспечил бы первейшую цель снижения затрат на ИТ. Когда сокращение затрат на ИТ фигурирует в списке бизнес-результатов, важно учесть потенциальное истечение срока действия или прекращение использования рабочих нагрузок. В некоторых сценариях экономия затрат может возлагаться не на миграцию рабочих нагрузок, которые не гарантируют краткосрочные инвестиции. Некоторые клиенты сообщили, что им удалось добиться снижения затрат в 20 % от общего снижения затрат, прекратив использование недостаточно загруженных рабочих нагрузок.

Чтобы сбалансировать портфель, лучше отразить решения "Закат" и "снять с учета", Группа облачной стратегии и группа внедрения в облако должны задать следующие вопросы о каждой рабочей нагрузке на этапах оценки и миграции.

- Использовалась ли рабочая нагрузка пользователями в течение последних шести месяцев?
- Трафик пользователей остается стабильным или растет?
- Потребуется ли эта рабочая нагрузка в течение 12 месяцев с настоящего момента?

Если ответ на любой из этих вопросов равен «нет», то Рабочая нагрузка может быть кандидатом на выход. Если возможность прекращения использования подтверждается владельцем приложения, то нет смысла переносить эту рабочую нагрузку. Тут возникает несколько квалификационных вопросов:

- Можно ли установить план прекращения использования или план истечения срока действия для этой рабочей нагрузки?
- Можно ли прекратить использование этой рабочей нагрузки до ухода из центра обработки данных?

Если ответ на оба этих вопроса равен «Да», то было бы разумно *не* переносить рабочую нагрузку. Этот подход поможет достичь целей снижения затрат и ухода из центра обработки данных.

Если ответ на любой вопрос равен «нет», может быть разумно создать план для размещения рабочей нагрузки, пока он не будет снят. Этот план может включать в себя перемещение ресурсов в более экономичный центр обработки данных или альтернативный центр обработки данных, что также позволит достичь целей сокращения затрат и ухода из одного центра обработки данных.

## <a name="adopt-process-changes"></a>Принятие изменений процесса

Для балансировки портфеля требуется дополнительный качественный анализ во время фазы внедрения, что поможет упростить рациональное распределение портфеля.

Согласно данным из таблицы в разделе [Документирование бизнес-результатов](#document-business-outcomes) выше, существует риск того, что портфель слишком сильно смещен к модели выполнения, ориентированной на миграцию. Если бы удобство работы клиентов было главным приоритетом, то, вероятно, портфель был бы более инновационным. Ни одна из точек зрения не является правильной или неправильной. Однако слишком сильное смещение в одну сторону приводит к ухудшению результатов, повышению сложности и увеличению времени, требуемого для внедрения облачных технологий.

Чтобы снизить сложность, следует соблюдать традиционный подход к обоснованиям портфеля, но в итеративной модели. Ниже описывается качественную модель для такого подхода.

- Команда по облачной стратегии поддерживает очередь невыполненной работы с установленными приоритетами для рабочих нагрузок, которые будут перенесены.
- Команда по вопросам облачной стратегии и команда по внедрению в облако проводят собрание по планированию выпуска перед завершением каждого выпуска.
- На собрании по планированию выпуска группы договариваются о 5–10 основных рабочих нагрузках в очереди невыполненной работы с установленными приоритетами.
- До собрания по планированию выпуска группа по внедрению облачных технологий задает следующие вопросы владельцам приложений и профильным специалистам:
  - Можно ли заменить это приложение эквивалентным решением PaaS (платформа как услуга)?
  - Это приложение стороннего производителя?
  - Утвержден ли бюджет для вложений в текущую разработку приложения на следующие 12 месяцев?
  - Улучшит ли дополнительная разработка этого приложения взаимодействие с клиентами? Вы создаете конкурентное решение? Оно приносит дополнительный доход организации?
  - Будут ли данные в этой рабочей нагрузке участвовать в нижестоящих нововведениях, связанных с бизнес-аналитикой, машинным обучением, IoT или связанными технологиями?
  - Совместима ли рабочая нагрузка с современными платформами приложений, такими как Служба приложений Azure?
- Ответы на приведенные выше вопросы и результаты любого другого необходимого качественного анализа повлияют на изменение приоритетов невыполненной работы. Эти изменения могут включать в себя следующее.
  - Если рабочую нагрузку можно заменить решением PaaS, она может быть полностью удалена из очереди невыполненной работы по миграции. Как минимум, в качестве задачи будет добавлено дополнительное комплексное комплексное комплексное решение для выбора между перестановкой и заменой, временно уменьшая приоритет рабочей нагрузки из невыполненной работы миграции.
  - Если Рабочая нагрузка (или должна быть) перерабатывается в ходе разработки, она может быть лучше соответствовать модели реструктуризации и перестроения. Поскольку инновации и миграция занимают различные технические навыки, приложения, которые согласовываются с подходом реструктуризации и повторного построения, должны управляться посредством невыполненной работы инноваций, а не из-за необработанной миграции.
  - Если рабочая нагрузка используется в последующих инновациях, то может быть целесообразно выполнить рефакторинг платформы данных, а для прикладных уровней запланировать повторное размещение. Незначительный рефакторинг платформы данных рабочей нагрузки часто можно выполнить с помощью очереди невыполненной работы по миграции или инновации. Рационализация может привести к добавлению более детальных рабочих элементов в очередь невыполненной работы, но зато изменять приоритеты не потребуется.
  - Если рабочая нагрузка не является стратегический, но совместима с современными облачными платформами размещения приложений, возможно, будет целесообразно выполнить незначительный рефакторинг приложения, чтобы развернуть его как современное приложение. Это может повлиять на общую экономию, так как сократится количество лицензий для IaaS и ОС, необходимых для миграции в облако.
  - Если рабочая нагрузка является сторонним приложением, а ее данные не планируется использовать в последующих инновациях, то лучше оставить ее как кандидат для повторного размещения в очереди невыполненной работы.

Эти вопросы не должны быть степенью качественного анализа, выполненного для каждой рабочей нагрузки, но они помогают в обсуждении сложности несбалансированного портфеля.

## <a name="migration-process-changes"></a>Изменения процесса миграции

Во время миграции действия балансировки портфеля могут оказать негативное влияние на скорость миграции (скорость, с которой переносятся ресурсы). Приведенные ниже рекомендации помогут вам понять, для чего и как можно согласовать действия, чтобы избежать перерывов в работе при миграции.

Для рационализации портфеля требуется ряд технических операций. Непросто подобрать группы по внедрению облачных технологий, соответствующие разнообразию портфеля для миграции. Заинтересованные лица в организации требуют, чтобы всей очередью невыполненной работы по миграции занималась одна группа по внедрению облачных технологий. Такой подход редко рекомендуется, так как во многих случаях он контрпродуктивен.

Эти разнообразные усилия должны быть сегментированы между двумя или несколькими группами внедрения в облако. Использование модели с двумя командами в качестве примера режима выполнения Team 1 — группа миграции, а команда 2 — Группа инноваций. Для больших усилий эти команды могут быть еще более сегментированы на другие подходы, такие как операции Refactor/PaaS или незначительное рефакторинг. Ниже описаны навыки и роли, необходимые для повторного размещения, реструктуризации или незначительного переработки.

Повторное **Размещение:** Для повторного размещения требуется, чтобы члены команды реализовали изменения инфраструктуры. Обычно они используют такие инструменты, как Azure Site Recovery, чтобы перенести виртуальные машины или другие ресурсы в Azure. Эта работа хорошо подходит администраторам центра обработки данных или разработчикам ИТ. Команда по миграции в облако имеет все необходимое для выполнения этой работы в большом масштабе. В большинстве сценариев это самый быстрый подход к переносу существующих ресурсов.

**Рефакторинг:** Рефакторинг требует от членов команды изменять исходный код, изменять архитектуру приложения или внедрять новые облачные службы. Как правило, для этого применяются инструменты разработки, такие как Visual Studio, и инструменты конвейера развертывания, такие как Azure DevOps, для повторного развертывания модернизированных приложений в Azure. Эта работа хорошо подходит разработчикам приложений или разработчикам конвейеров DevOps. Группа облачных инноваций лучше структурирована для предоставления этой работы. Замена существующих ресурсов облачными ресурсами при таком подходе может занять больше времени, но приложения смогут использовать преимущества собственных функций облака.

**Незначительное рефакторинг:** Некоторые приложения могут быть состоять из незначительного рефакторинга на уровне данных или приложения. Для выполнения этой работы требуется, чтобы члены группы развертывали данные на облачных платформах данных или вносили незначительные изменения в конфигурацию приложения. Для этого может потребоваться небольшая помощь профильных специалистов по разработке данных или приложений. Однако разработчики ИТ выполняют такую же работу, когда развертывают сторонние приложения. Эту работу может легко выполнить группа по миграции в облако или группа по облачной стратегии. Хотя этот процесс выполняется дольше, чем миграция с повторным размещением, он занимает меньше времени, чем рефакторинг.

Во время миграции усилия должны быть разбиты на три указанных выше способа и выполнены соответствующей командой в соответствующей итерации. Хотя вы должны изменить портфель, следите за тем, чтобы усилия всегда были сосредоточены и разделены.

## <a name="next-steps"></a>Дальнейшие действия

Узнайте, как [глобальные решения на рынке](./global-markets.md) могут повлиять на путешествие преобразований.

> [!div class="nextstepaction"]
> [Общие сведения о глобальных рынках](./global-markets.md)
