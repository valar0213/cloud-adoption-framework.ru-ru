---
title: Что такое агенты искусственного интеллекта?
description: Сведения об агентах ии и диалоговых интерфейсах. Планирование, сборка, тестирование, публикация, подключение и оценка робота.
author: v-hanki
ms.author: janet
ms.date: 07/14/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: f268e1a91f70b3cfb114e8769ef6cea66077eee3
ms.sourcegitcommit: 8b82889dca0091f3cc64116f998a3a878943c6a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/09/2020
ms.locfileid: "89604560"
---
<!-- docutune:casing "natural language understanding" -->
<!-- cSpell:ignore Twilio -->

# <a name="what-are-ai-agents"></a>Что такое агенты искусственного интеллекта?

Пользователи работают больше и больше с помощью диалоговых интерфейсов, что может представлять более естественную работу, когда люди выражают свои потребности с помощью естественного языка и быстро завершают задачи. Во многих компаниях приложения искусственного интеллекта становятся конкурентным отличием. Во многих организациях стратегически делает программы-роботы доступными в тех же платформах обмена сообщениями, в которых их клиенты тратят время.

Организации по всему миру преобразуют свои предприятия в беседы, что позволяет повысить эффективность и естественные взаимодействия с клиентами и их сотрудниками. Ниже приведены некоторые распространенные варианты использования.

- Поддержка клиентов
- Помощник по выпуску Enterprise
- Оптимизация центра обработки вызовов
- Автомобильный речевой помощник

## <a name="build-a-bot"></a>Создание бота

Служба Azure Bot и Bot Framework предлагают интегрированный набор средств и служб, помогающих в этом процессе. Выберите предпочтительную среду разработки или программы командной строки, чтобы создать программу-робот. Пакеты SDK существуют для C#, JavaScript, TypeScript и Python. Пакет SDK для Java находится в разработке. Мы предоставляем средства, помогающие на разных этапах проектирования и разработки ботов.

![Схема, в которой показаны инструменты для различных этапов разработки Bot.](../../_images/ai-bot-dev-tools.png)

### <a name="plan"></a>План

Наличие глубокого понимания целей, процессов и потребностей пользователей важно для процесса создания успешной программы-робота. Прежде чем приступать к написанию кода, ознакомьтесь с [руководствами по разработке](/azure/bot-service/bot-service-design-principles?view=azure-bot-service-4.0) роботов, чтобы получить рекомендации и выяснить потребности программы-робота. Вы можете создать простой робот или включить в него более сложные возможности, такие как речь, понимание естественного языка и ответ на вопросы.

При проектировании программы-робота на этапе планирования необходимо учитывать следующие аспекты:

- Определение персонажей-роботов:
  - Как выглядит ваш робот?
    - Что следует назвать?
    - Какова личность вашего робота? Есть ли у него пол?
    - Как программа-робот должна справляться с сложными ситуациями и вопросами?
- Поток диалогового окна разработки:
  - Какие типы бесед можно рассчитывать на варианты использования?
- Определите план оценки:
  - Как бы вы измеряли успешность?
  - Какие измерения вы хотите использовать для улучшения службы?

Дополнительные сведения о проектировании роботов см. в разделе [принципы создания](/azure/bot-service/bot-service-design-principles?view=azure-bot-service-4.0)роботов.

### <a name="build"></a>Сборка

Бот — это веб-служба, которая реализует интерфейс для общения, а также взаимодействует со службой Azure Bot для отправки и получения сообщений и событий. Служба платформы Bot — это один из компонентов службы Azure Bot и Bot Framework. Боты можно создавать в большом количестве языков и сред. Вы можете начать разработку в [портал Azure](/azure/bot-service/bot-service-quickstart?view=azure-bot-service-4.0) или использовать шаблоны [C#, JavaScript или Python](/azure/bot-service/dotnet/bot-builder-dotnet-sdk-quickstart?view=azure-bot-service-4.0) для локальной разработки. Также у вас есть доступ к различным [примерам](https://github.com/microsoft/botbuilder-samples), которые демонстрируют многие возможности, доступные через пакет SDK. Эти примеры отлично подходят для разработчиков, которым требуется более широкая отправная точка.

В рамках службы Azure Bot и Bot Framework мы предлагаем дополнительные компоненты, которые можно использовать для расширения функциональных возможностей программы-робота.

| Компонент | Описание | Ссылка |
| --- | --- | --- |
| Добавление возможности обработки естественного языка | Попросите робота понять естественный язык, понять орфографические ошибки, использовать речь и распознать намерение пользователя. | Использование [LUIS](/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0) |
| Ответы на вопросы | Добавьте базу знаний, чтобы ответить на вопросы, которые пользователи запрашивают более естественным образом. | Использование [QnA Maker](/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0) |
| Объединение нескольких моделей | Если вы используете более одной модели, например для LUIS и QnA Maker, интеллектуально определите, когда использовать их во время диалога робота. | Средство [Dispatch](/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0) |
| Добавление карточек и кнопок | Улучшайте работу пользователей с помощью мультимедиа, отличного от текста, например графики, меню и карточек. | [Добавление карточек](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0) |

> [!NOTE]
> Эта таблица не является исчерпывающим списком. Дополнительные сведения см. в [документации по службе Azure Bot](/azure/bot-service/).

### <a name="test"></a>Тест

Программы-роботы — это сложные приложения с множеством различных частей, которые работают вместе. Как и любое другое сложное приложение, эта сложность может привести к некоторым интересным ошибкам или вызвать поведение программы-робота не так, как ожидалось. Перед публикацией программы-робота протестируйте ее. Мы предоставляем несколько способов тестирования программы-роботы, прежде чем они будут выпущены для использования:

- Тестирование в локальной среде с помощью [эмулятора](/azure/bot-service/bot-service-debug-emulator?view=azure-bot-service-4.0). Эмулятор Bot Framework — это автономное приложение, которое не только предоставляет интерфейс разговора, но и средства отладки и опроса, которые помогут понять, как и зачем делает робот. Эмулятор можно запускать локально в той же системе, что и разрабатываемый бот.
- Проверка бота в [Интернете](/azure/bot-service/bot-service-manage-test-webchat?view=azure-bot-service-4.0). После настройки программы Bot с помощью портал Azure ее также можно получить через интерфейс веб-разговора. Интерфейс веб-разговора — это отличный способ предоставить доступ к роботам тестерам и другим людям, у которых нет прямого доступа к выполняющемуся коду.
- [Модульное тестирование программы Bot](/azure/bot-service/unit-test-bots) с июльским ОБНОВЛЕНИЕМ пакета SDK для Bot Framework.

### <a name="publish"></a>Публикация

Когда вы будете готовы сделать программу Bot доступной в Интернете, [опубликуйте ее в Azure](/azure/bot-service/bot-builder-howto-deploy-azure?view=azure-bot-service-4.0) или в собственной веб-службе или центре обработки данных. Наличие адреса в общедоступном Интернете — это первый этап, с помощью которого программа-робот будет работать на вашем сайте или в каналах разговора.

### <a name="connect"></a>Подключение

Подключите робот к таким каналам, как Facebook, Messenger, KiK, Skype, резерв времени, Microsoft Teams, Telegram, Text/SMS, Twilio, Кортана и Skype. Программа Bot Framework выполняет большую часть работы, необходимой для отправки и получения сообщений со всех этих платформ. Приложение-робот получает унифицированный нормализованный поток сообщений независимо от числа и типа каналов, к которым он подключен. Дополнительные сведения о добавлении каналов см. в разделе [каналы](/azure/bot-service/bot-service-manage-channels?view=azure-bot-service-4.0).

### <a name="evaluate"></a>Evaluate

Используйте данные, собранные в портал Azure, чтобы выбрать возможности для улучшения возможностей и производительности программы-робота. Вы можете получить данные уровня службы и инструментирования, например трафик, задержку и интеграцию. Аналитика также предоставляет отчеты на уровне беседы по данным пользователя, сообщения и канала. Дополнительные сведения см. [в разделе Сбор данных аналитики](/azure/bot-service/bot-service-manage-analytics?view=azure-bot-service-4.0).

### <a name="patterns-for-common-use-cases"></a>Шаблоны для распространенных вариантов использования

Существуют распространенные шаблоны, используемые для реализации приложения искусственного интеллекта.

- **База знаний:** Робот базы знаний может быть разработан для предоставления сведений практически любой темы. Например, один робот базы знаний может ответить на вопросы о таких событиях, как «какие события Bot есть на Конференции?». Или "когда — следующая реггае показывать?" Другой робот может ответить на вопросы, связанные с ИТ, например "как обновить операционную систему?". Еще одна программа-робот может ответить на вопросы о контактах, например "кто это Джон Петров?". Или «что такое адрес электронной почты Джейн Петров?»

   Сведения об элементах дизайна для базы знаний программы-роботы см. в разделе [Разработка знаний программы-роботы](/azure/bot-service/bot-service-design-pattern-knowledge-base?view=azure-bot-service-4.0).

- **Передать персоналу:** Независимо от того, какой объем искусственного интеллекта владеет, могут быть все время, когда необходимо передать беседу человеку. В таких случаях робот должен распознать, когда необходимо передать, и предоставить пользователю плавный переход.

   Дополнительные сведения об этих шаблонах см. в разделе [Переход от Bot к человеку](/azure/bot-service/bot-service-design-pattern-handoff-human?view=azure-bot-service-4.0).

- **Внедрение программы-робота в приложение:** Несмотря на то что программы-роботы чаще всего существует вне приложений, их также можно интегрировать с приложениями. Например, можно встроить в приложение [робот базы знаний](/azure/bot-service/bot-service-design-pattern-knowledge-base?view=azure-bot-service-4.0) , чтобы помочь пользователям найти информацию. Вы также можете внедрить робот в приложение службы поддержки, чтобы он выступал в качестве первого респондента для входящих запросов пользователей. Бот может независимо устранять простые проблемы и [передавать](/azure/bot-service/bot-service-design-pattern-handoff-human?view=azure-bot-service-4.0) более сложные агенту-человеку.

   Сведения о способах интеграции программы Bot в приложение см. в разделе [встраивание программы-робота в приложение](/azure/bot-service/bot-service-design-pattern-embed-app?view=azure-bot-service-4.0).

- **Внедрение робота в веб-сайт:** Подобно внедрению программы-роботы в приложениях, программы-роботы также можно внедрить в веб-сайт, чтобы обеспечить несколько режимов обмена данными между каналами.

   Сведения о способах интеграции программы Bot в веб-сайт см. [в статье встраивание робота в веб-](/azure/bot-service/bot-service-design-pattern-embed-web-site?view=azure-bot-service-4.0)сайт.

## <a name="next-steps"></a>Дальнейшие действия

- Ознакомьтесь с техническими материалами по машинному обучению и электронной книгой о [службе Azure Bot](https://azure.microsoft.com/resources/whitepapers/search/?service=bot-service).
- Ознакомьтесь с [архитектурой ии и машинное обучение](/azure/architecture/browse/).
- [Создание интеллектуальных приложений с помощью API-интерфейсов для перестроения (электронная книга)](https://azure.microsoft.com/resources/building-intelligent-apps-with-cognitive-apis/).
- [Часто задаваемые вопросы об архитектуре чат-бот](https://azure.microsoft.com/resources/faq-chatbot-architecture/).
