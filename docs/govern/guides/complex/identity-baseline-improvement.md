---
title: 'Комплексное корпоративное управление: повышение дисциплины базовых показателей идентификаторов'
description: Используйте платформу внедрения облачных технологий для Azure, чтобы узнать о добавлении элементов управления базовых показателей для минимального уровня контроля (MVP).
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/06/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 1df1e0ae58572beac799f43304018672c9231c47
ms.sourcegitcommit: c2249056464d748a6ce15c82cb35a9f164d8f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91108148"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-identity-baseline-discipline"></a>Руководство по управлению для сложных предприятий: повышение дисциплины базовых показателей удостоверений

Эта статья посвящена добавлению элементов управления базовых показателей идентификаторов в MVP по управлению.

## <a name="advancing-the-narrative"></a>Будущие описания

Финансовый директор утвердил коммерческое обоснование для перемещения двух центров обработки данных в облако. При исследовании технической осуществимости было обнаружено несколько препятствий:

- Защищенные данные и критически важные приложения составляют 25 % рабочих нагрузок в двух центрах обработки данных. Ни одно из них не может быть устранено, пока текущие политики управления для конфиденциальных персональных данных и критически важных приложений не были удалены.
- 7 % ресурсов в этих центрах обработки данных не совместимы с облачными службами. Они будут перемещены в альтернативный центр обработки данных до прекращения действия контракта на использование центра обработки данных.
- 15 % ресурсов в центре обработки данных (750 виртуальных машин) зависят от устаревшей аутентификации или сторонней многофакторной проверки подлинности.
- VPN-подключение, которое соединяет существующие центры обработки данных и Azure, не предоставляет достаточной скорости передачи данных и приемлемую задержку для переноса объема ресурсов в течение двух лет, по истечении которых центр обработки данных будет снят с учета.

Первые два препятствий управляются параллельно. В этой статье рассматривается устранение третьего и четвертого препятствий.

### <a name="expand-the-cloud-governance-team"></a>Развернуть группу управления облаком

Команда по управлению облаком развернута. Учитывая потребность в дополнительной поддержке по управлению удостоверениями, системный администратор из группы базовых удостоверений теперь участвует в еженедельном совещании, чтобы члены группы осведомлены об изменениях.

### <a name="changes-in-the-current-state"></a>Изменения в текущем состоянии

ИТ – специалисты в области ИТ были одобрены, чтобы продвинуть два центра обработки данных в планы ДИРЕКТОРов и финансового директора. Группа заинтересована в том, что 750 (15%) ресурсы в этих центрах обработки данных должны быть перемещены в другое место, кроме облака.

### <a name="incrementally-improve-the-future-state"></a>Постепенно улучшайте будущее состояние

Новым планам будущего состояния требуется более надежное базовое решение удостоверений для переноса виртуальных машин 750 с устаревшими требованиями к проверке подлинности. Помимо этих двух центров обработки данных, эта задача должна повлиять на аналогичные процентные активы в других центрах обработки данных.

Теперь для будущего состояния также требуется подключение от поставщика облачных решений к решению MPLS/аренды компании.

Изменения в текущем и будущем состояниях представляют новые риски, требующие новых положений политики.

## <a name="changes-in-tangible-risks"></a>Изменения в материальных рисках

**Бизнес-прерывание во время миграции.** Миграция в облако создает контролируемую, временную угрозу, которой можно управлять. Перемещение устаревшего оборудования в другую часть мира предоставляет более высокий риск. Для избежания прерываний бизнес-операций требуется стратегия по устранению рисков.

**Существующие зависимости удостоверений.** Зависимости от существующих служб аутентификации и идентификации могут отложить или предотвратить перемещение некоторых рабочих нагрузок в облако. Если два центра обработки данных не удастся вернуть в срок, это повлечет необходимость выплатить миллионы долларов за их аренду.

Риски для бизнеса связаны со следующими техническими проблемами:

- Устаревшая аутентификация может оказаться недоступной в облаке, что ограничивает развертывание некоторых приложений.
- Текущее решение многофакторной идентификации стороннего производителя может быть недоступно в облаке, что ограничивает развертывание некоторых приложений.
- При переведении или перемещении могут быть созданы простои или затраты.
- Скорость и стабильность работы VPN-подключения могут помешать миграции.
- Трафик, входящий в облако, может вызвать проблемы безопасности в других частях глобальной сети.

## <a name="incremental-improvement-of-the-policy-statements"></a>Добавочное улучшение операторов политики

Следующие изменения в политике помогут устранить новые риски и пошаговое внедрение.

- Выбранный поставщик облачных служб должен предоставить средства аутентификации с помощью устаревших методов.
- Выбранный поставщик облачных служб должен предоставлять средства проверки подлинности с помощью текущего стороннего решения многофакторной идентификации.
- Необходимо установить высокоскоростное частное подключение между поставщиком облачных услуг и поставщиком Telco компании, подключив поставщик облачных служб к глобальной сети центров обработки данных.
- Пока необходимые требования безопасности не определены, общедоступный входящий трафик не может получить доступ к ресурсам компании, размещенным в облаке. Все порты заблокированы для всех источников за пределами глобальной сети.

## <a name="incremental-improvement-of-best-practices"></a>Добавочное улучшение рекомендаций

Проект MVP по управлению изменяется для включения новых политик Azure и реализации Active Directory на виртуальной машине. Совокупно эти изменения проекта позволяют внедрить новые положения корпоративной политики.

Ниже приведены новые рекомендации:

- Схема **защищенной гибридной виртуальной сети:** Локальная сеть гибридной сети должна быть настроена на разрешение взаимодействия между следующим решением и локальными серверами Active Directory. Эта рекомендация требует наличия сети периметра для включения домен Active Directory служб через границы сети.
- **Шаблоны Azure Resource Manager:**
    1. Определите NSG для блокировки внешнего трафика и разрешите внутренний трафик.
    2. Развертывание двух Active Directory виртуальных машин в паре с балансировкой нагрузки на основе эталонного образа. При первой загрузке этот образ запускает сценарий PowerShell для присоединения к домену и регистрации в доменных службах. Дополнительные сведения см. в статье [Расширение доменных служб Active Directory в Azure](/azure/architecture/reference-architectures/identity/adds-extend-domain).
- Политика Azure. Примените NSG ко всем ресурсам.
- Проекты Azure:
    1. Создайте схему Azure с именем `active-directory-virtual-machines`.
    2. Добавьте в проект каждый шаблон Active Directory и политики.
    3. Опубликуйте схему в любую применимую группу управления.
    4. Примените схему к любой подписке, которая требует устаревшей или сторонней многофакторной идентификации.
    5. Экземпляр Active Directory, выполняющийся в Azure, теперь можно использовать как расширение локального Active Directoryного решения, что позволяет интегрировать его с существующим средством многофакторной проверки подлинности и обеспечивать проверку подлинности на основе утверждений с помощью существующих функций Active Directory.

## <a name="conclusion"></a>Заключение

Добавление этих изменений в MVP по управлению помогает устранить многие риски, описанные в этой статье, позволяя каждой группе внедрения в облако быстро переходить за эту препятствием.

## <a name="next-steps"></a>Дальнейшие действия

По мере того как внедрение в облако продолжится и обеспечивает дополнительную ценность для бизнеса, риски и потребности в управлении облаком тоже изменятся. Ниже приведены некоторые изменения, которые могут возникнуть. Для этой вымышленной компании следующим триггером является включение защищенных данных в план внедрения облака. Для этого изменения требуются дополнительные средства управления безопасностью.

> [!div class="nextstepaction"]
> [Улучшение основных способов защиты](./security-baseline-improvement.md)
