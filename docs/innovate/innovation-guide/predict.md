---
title: Руководство по инновациям Azure. Прогнозирование и влияние
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Узнайте, как прогнозировать использование Azure и влиять на него.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 5bd467e6e74ff1289a7db40add87a049d2b0697e
ms.sourcegitcommit: 7ffb0427bba71177f92618b2f980e864b72742f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2019
ms.locfileid: "73047624"
---
::: zone target="docs"

# <a name="azure-innovation-guide-predict-and-influence"></a>Руководство по инновациям Azure. Прогнозирование и влияние

::: zone-end

::: zone target="chromeless"

# <a name="predict-and-influence"></a>Прогнозирование и влияние

::: zone-end

Ваша инновационная компания может анализировать данные, поведение и потребности клиента. Изучение этих полезных сведений поможет прогнозировать потребности клиентов, возможно даже до того, как они сами о них узнают. В этой статье приводится несколько подходов к предоставлению прогнозных решений. В последних разделах статьи рассматриваются подходы к интеграции этих прогнозов в решение с целью повлиять на поведение клиентов.

Представленная ниже таблица поможет вам найти оптимальное решение с учетом потребностей реализации.

|Service  |Предварительно созданные модели  |Создание и экспериментирование  |Обучение и создание с помощью Python|Необходимые навыки|
|---------|---------|---------|---------|---------|
|Azure Cognitive Services|Yes|Нет|Нет|API и навыки разработчиков|
|Студия машинного обучения Azure|Yes|Да|Нет|Общее представление о прогнозных алгоритмах|
|Служба машинного обучения|Yes|Да|Yes|специалист по анализу и обработке данных;|

## <a name="azure-cognitive-servicestabcognitiveservices"></a>[Azure Cognitive Services](#tab/CognitiveServices)

Самый быстрый и простой способ прогнозирования потребностей клиентов — использование Azure Cognitive Services. Службы Cognitive Services позволяют делать прогнозы на основе существующих моделей, что не требует дополнительного обучения. Эти службы — оптимальный и эффективный вариант, если среди ваших сотрудников нет специалиста по анализу и обработке данных для обучения прогнозной модели. Для некоторых служб обучение не требуется, в то время как для других требуется в минимальном объеме.

Список доступных служб и необходимый объем обучения см. в разделе [Требования к службам для модели данных](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-and-machine-learning#service-requirements-for-the-data-model).

### <a name="action"></a>Действие

Чтобы использовать API-интерфейс Cognitive Services, выполните приведенные ниже действия.

1. На [портале Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts) откройте раздел **Cognitive Services**.
2. Нажмите кнопку **Добавить**, чтобы найти API-интерфейс Cognitive Services в Azure Marketplace.
3. Выполните одно из приведенных ниже действий.
   * Если вы знаете имя нужной службы, введите его в поле **Поиск в Marketplace**.
   * Чтобы получить список API-интерфейсов Cognitive Services, щелкните ссылку **Подробности** рядом с заголовком Cognitive Services.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts]" submitText="Go to Cognitive Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Перейдите непосредственно к Cognitive Services на [портале Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts).

::: zone-end

## <a name="azure-machine-learning-studiotabmachinelearningstudio"></a>[Студия машинного обучения Azure](#tab/MachineLearningStudio)

Если имеющиеся модели в Cognitive Services не совпадают с необходимым прогнозом, Студия машинного обучения Azure может предоставить способ создания нужных прогнозов, не требующий глубоких навыков по анализу данных.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Действие

С помощью Студии машинного обучения Azure Machine вы можете создать модель и экспериментировать с нею, выполнив приведенные ниже действия.

1. На [портале Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces) откройте **Студию машинного обучения Azure**.
2. Нажмите **Создать рабочую область Студии машинного обучения** и следуйте инструкциям на экране, чтобы создать рабочую область.

   Новая рабочая область предоставляет интерфейс перетаскивания для создания модели и проведения экспериментов с ней в качестве альтернативы углубленному обучению.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces]" submitText="Go to Azure Machine Learning Studio" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Перейдите непосредственно к службе "Студия машинного обучения Azure" на [портале Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces).

::: zone-end

## <a name="azure-machine-learning-servicetabmachinelearningservice"></a>[Служба "Машинное обучение Azure"](#tab/MachineLearningService)

Служба "Машинное обучение Azure" предоставляет более системный подход на основе кода, необходимый для более глубокого обучения наборов данных клиентов. Используя такие языки, как Python, специалисты по обработке и анализу данных могут обучить, а затем собрать алгоритм для прогнозирования потребностей клиентов.

### <a name="action"></a>Действие

Специалисты по анализу и обработке данных могут использовать службу "Машинное обучение Azure" для обучения и создания модели с использованием таких языков, как Python:

1. Перейдите к **Службе машинного обучения Azure**.
2. Нажмите **Создать рабочую область Службы машинного обучения** и следуйте инструкциям на экране, чтобы создать рабочую область.
3. Новая рабочая область предоставляет специалистам по обработке и анализу данных подход на основе кода для обучения и создания моделей, которым требуется более сложная аналитика для точного прогнозирования потребностей клиентов.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces]" submitText="Go to Azure Machine Learning service" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Перейдите непосредственно к службе "Студия машинного обучения Azure" на [портале Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces).

::: zone-end

## <a name="influence"></a>Влияние

Все описанные выше подходы приводят к созданию API, который предоставляет модель прогнозирования для приложений. Используйте в своем решении любой из этих подходов для передачи данных, полученных от клиента, в API прогнозирования. Затем рекомендуется интегрировать результаты в пользовательский интерфейс.

Рекомендуемые дальнейшие действия помогают повлиять на привычки клиентов и их реакцию. Так как предлагаемые дальнейшие действия основаны на прогнозных алгоритмах, для прогнозирования потребностей клиентов и их удовлетворения (часто до того, как клиент сам узнает о них) используются предыдущие потребности клиентов и доступные данные.