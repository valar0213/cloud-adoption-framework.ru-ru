---
title: Инновации в сфере цифровой экономики
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Узнайте о принципах внедрения инновационных облачных решений в соответствии с Cloud Adoption Framework.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 2417241e2dc607b005f32c9c647cc88913167148
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2019
ms.locfileid: "72556587"
---
# <a name="innovation-in-the-digital-economy"></a>Инновации в сфере цифровой экономики

Цифровая экономика — это сила, движущая практически каждую отрасль. Во время предыдущей промышленной революции основными ресурсами, которые требовались для внедрения рыночных инноваций, были бензин, конвейерные ленты и человеческая изобретательность. Качество продукции, цена и логистика оказывали влияние на рынок, так как компании стремились быстрее предоставлять клиентам более качественные продукты. Цифровая экономика меняет способ взаимодействия между клиентами и корпорациями. В итоге меняется все: и первичные формы капитала, и отличительные особенности рынка. В эпоху цифровой экономики клиентов куда меньше заботит логистика. Сфера их интересов — общая удовлетворенность от использования продукта. Этот сдвиг обусловлен непосредственным повседневным взаимодействием с технологиями и реализацией ценностных предложений, связанных с этим взаимодействием.

На этапе реализации инноваций в соответствии с Cloud Adoption Framework мы сосредоточимся на изучении потребностей клиентов и быстром создании инновационных решений, определяющих способ взаимодействия ваших клиентов с вашими продуктами. Мы проиллюстрируем подход к реализации ценности минимально жизнеспособного продукта (MVP). Мы также опишем решения, общие для инновационных циклов, чтобы помочь вам понять, как облако может способствовать внедрению инноваций и созданию партнерских отношений с клиентами.

## <a name="innovate-methodology"></a>Методология внедрения инноваций

Простая методология облачных инноваций в соответствии с Cloud Adoption Framework показана на следующем рисунке. В следующих статьях этой серии будет показано, как определять основные процессы, подходы и механизмы для поиска и развития инновационных решений в вашей компании.

![Схема инновационной методологии Cloud Adoption Framework](../../_images/innovate/innovate-methodology.png)

В этой серии статей мы раскрываем описываемую методологию следующим образом.

- Во-первых, всегда начинайте с принятия потребностей клиента, чтобы создавать циклы обратной связи "создание — оценка — обучение", которые помогают формировать партнерские отношения.
- Во-вторых, изучите подходы к разработке цифровых изобретений с прицелом на процесс внедрения.

В следующем разделе приведена формула, описывающая процесс внедрения инноваций, и обязательства, выполнение которых поможет вам достичь успеха при реализации этого подхода.

## <a name="formula-for-innovation"></a>Формула, описывающая процесс внедрения инноваций

Успешная инновация — это не волшебное превращение в результате большого взрыва и не явление неуловимого волшебного единорога. Успех в реализации инноваций идет рука об руку с планомерными действиями. Это можно проиллюстрировать простой формулой: **инновации = изобретение + внедрение.**

Инновации возникают на стыке таких процессов, как изобретение и внедрение. Настоящие инновации — это результат медленной корректировки человеческого опыта с учетом новых подходов, процессов и технологий. В этой формуле изобретение представляет собой создание нового решения, которое отвечает потребностям клиента. С другой стороны, внедрение — это применение нового решения для формирования человеческого поведения и взаимодействия. Чтобы найти оптимальный баланс между изобретением и внедрением, необходимо выполнять итерации, принимать решения на основе данных, а также постоянно обучаться и развивать мышление. Для этого также требуются технологии, предусматривающие бесчисленные возможности для обучения в современном цифровом обществе.

Облако часто является превосходной платформой для изобретений или разработки технологических аспектов инновационных решений. При реализации большинства великих идей люди терпят неудачу во время непростого процесса внедрения, а не в процессе генерации идей и изобретений. Гарантия успеха заключается в том, что команды разработчиков всегда должны начинать с этапа внедрения, тестируя свои инновационные решения. Чтобы ускорить сдвиг парадигмы, мы разработали методологию, которая начинается с этапа внедрения. Применяя эту методологию, команда должна прийти к консенсусу относительно следующих трех обязательств:

- [обязательство по приоритету клиентов над технологиями](#commitment-to-prioritize-customers-over-technology);
- [обязательство придерживаться принципов прозрачности](#commitment-to-transparency);
- [обязательство выполнять итерации](#commitment-to-iteration).

## <a name="cultural-commitments"></a>Культурные обязательства

Внедрение [инновационной методологии](../index.md) требует соблюдения некоторых культурных обязательств для эффективного использования показателей, описываемых в этой статье. Прежде чем менять свой подход к внедрению инноваций, убедитесь, что профильная команда и руководство готовы взять на себя эти важные обязательства.

## <a name="commitment-to-prioritize-customers-over-technology"></a>Обязательство по приоритету клиентов над технологиями

У каждой команды разработчиков есть набор инструментов и технологий, с которыми они работают чаще всего. Разумно использовать эти сильные стороны и применять то, что с чем вы уже знакомы. Но чтобы инновации были успешными, команды должны сосредоточиться на потребностях клиентов и проверяемой гипотезе. Иногда эта нацеленность может не соответствовать возможностям конкретного инструмента или архитектурного подхода. Для успешной реализации инноваций разработчики должны взять на себя обязательство быть непредвзятыми. Изобретая, старайтесь, чтобы технические решения основывались на потребностях клиента, а не на предпочтениях команды.

## <a name="commitment-to-transparency"></a>Обязательство придерживаться принципов прозрачности

Чтобы понять важность измерений в реализации инновационных решений, необходимо сначала понять, для чего нужна приверженность принципам прозрачности. Инновации могут процветать только в той среде, где придерживаются **установки на развитие**. В основе такой установки лежит культурный императив учиться на опыте. Успешные инновации и постоянное обучение начинаются с приверженности принципам прозрачности при измерениях. Это обязательство должно быть без колебаний принято командой по внедрению облачных технологий. Но все это не имеет смысла, если такое решение не будет подкреплено обязательством сохранять прозрачность, принятым руководителями и командой по вопросам облачной стратегии.

Прозрачность важна, так как измерение воздействия на клиентов не отвечает на вопрос, связанный с правильностью или неправильностью. Измерение степени воздействия также не указывает на качество работы или производительность команды по внедрению. Скорее, это является возможностью для обучения, которая поможет удовлетворять потребности ваших клиентов еще лучше. Неправильное использование данных измерений, связанных с инновациями, задушит эту культуру. В конечном итоге это приведет к манипуляциям с данными измерений, а значит, к долговременным проблемам с сотрудниками, занимающимися изобретениями, вспомогательным персоналом и руководящим отделом, который неправильно использовал данные измерений. Лидеры и участники должны использовать данные измерений только в качестве средства для изучения и улучшения решения MVP.

## <a name="commitment-to-iteration"></a>Обязательство выполнять итерации

Только одно обещание звучит правдоподобно на всех этапах процесса реализации инноваций: вы не получите нужные результаты с первой же попытки. Измерения помогут вам понять, какие корректировки необходимо внести для достижения нужных результатов. Требуемые изменения — это результат итераций цикла "создание — оценка — обучение". Команда по внедрению облачных решений и команда по вопросам облачной стратегии должны принять такой итеративный подход, прежде чем реализовывать стратегию развития мышления или цикл "создание — оценка — обучение".

## <a name="next-steps"></a>Дополнительная информация

Прежде чем изобретать следующее замечательное решение, начните с принятия потребностей клиента, используя цикл обратной связи [создание — оценка — обучение](./adoption.md).

> [!div class="nextstepaction"]
> [Принятие потребностей клиента с использованием цикла обратной связи "создание — оценка — обучение"](./adoption.md)