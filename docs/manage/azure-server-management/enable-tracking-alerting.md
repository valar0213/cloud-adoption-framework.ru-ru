---
title: Отслеживание и оповещения о критических изменениях
description: Включите отслеживание и оповещение о критических изменениях в гибридной среде с помощью Azure Отслеживание изменений и инвентаризации.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: a8826b82e9ec3aa503e79e0aa5345a3a494a2bef
ms.sourcegitcommit: 011525720bd9e2d9bcf03a76f371c4fc68092c45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/18/2020
ms.locfileid: "88567552"
---
<!-- cSpell:ignore HKEY kusto -->

# <a name="enable-tracking-and-alerting-for-critical-changes"></a>Включение отслеживания и предупреждений для критических изменений

Отслеживание изменений и Инвентаризация Azure предоставляют оповещения о состоянии конфигурации гибридной среды и изменениях в этой среде. Он может сообщать о критических изменениях файла, службы, программного обеспечения и реестра, которые могут повлиять на развернутые серверы.

По умолчанию служба инвентаризации Azure Automation не отслеживает файлы и параметры реестра. Решение предоставляет список разделов реестра, которые мы рекомендуем использовать для мониторинга. Чтобы просмотреть этот список, перейдите к учетной записи службы автоматизации в портал Azure, а **Inventory**затем выберите  >  **Параметры редактирования**для инвентаризации.

![Снимок экрана с представлением инвентаризации Azure Automation в портал Azure](./media/change-tracking1.png)

Дополнительные сведения о каждом разделе реестра см. в разделе [Отслеживание изменений раздела реестра](/azure/automation/automation-change-tracking#registry-key-change-tracking). Выберите любой ключ для вычисления, а затем включите его. Этот параметр применяется ко всем виртуальным машинам, включенным в текущей рабочей области.

Вы также можете использовать службу для трассировки критических изменений файлов. Например, может потребоваться отслеживание файла C:\windows\system32\drivers\etc\hosts, так как операционная система использует его для преобразования имен узлов в IP-адреса. Изменения в этом файле могут вызвать проблемы с подключением или перенаправить трафик на опасные веб-сайты.

Чтобы включить отслеживание содержимого файлов для файлов hosts, выполните действия, описанные в разделе [Включение отслеживания содержимого файлов](/azure/automation/change-tracking-file-contents#enable-file-content-tracking).

Можно также добавить оповещение для изменений отслеживаемых файлов. Например, предположим, что необходимо настроить оповещение об изменениях в файле hosts. Выберите **log Analytics** на панели команд или в поле поиска по журналам для связанной log Analytics рабочей области. В Log Analytics используйте следующий запрос для поиска изменений в файле hosts:

  ```kusto
  ConfigurationChange | where FieldsChanged contains "FileContentChecksum" and FileSystemPath contains "hosts"
  ```

![Снимок экрана редактора запросов Log Analytics в портал Azure](./media/change-tracking2.png)

Этот запрос выполняет поиск изменений в содержимом файлов, имеющих путь, содержащий слово «hosts». Можно также выполнить поиск определенного файла, изменив параметр path. (Например, `FileSystemPath ==  "c:\\windows\\system32\\drivers\\etc\\hosts"`).
  
После того как запрос вернет результаты, выберите **создать правило генерации оповещений** , чтобы открыть редактор правил предупреждений. Вы также можете перейти к этому редактору с помощью Azure Monitor в портал Azure.

В редакторе правил предупреждений Проверьте запрос и измените логику оповещения, если это необходимо. В этом случае мы хотим, чтобы предупреждение вызывалось при обнаружении каких либо изменений на любом компьютере в среде.

![Снимок экрана редактора правил оповещения Log Analytics в портал Azure](./media/change-tracking3.png)

После настройки логики условий можно назначить группы действий для выполнения действий в ответ на предупреждение. В этом примере при возникновении предупреждения отправляются сообщения электронной почты и создается билет ITSM. Вы можете использовать множество других полезных действий, например, активировать функцию Azure, модуль Runbook службы автоматизации Azure, веб-перехватчик или приложение логики.

![Снимок экрана с примером сводки правила генерации оповещений в портал Azure](./media/change-tracking4.png)

После настройки всех параметров и логики примените предупреждение к среде.

## <a name="tracking-and-alerting-examples"></a>Примеры отслеживания и оповещения

В этом разделе показаны другие распространенные сценарии для отслеживания и создания предупреждений, которые могут потребоваться использовать.

### <a name="driver-file-changed"></a>Файл драйвера изменен

Используйте следующий запрос, чтобы определить, были ли файлы драйверов изменены, добавлены или удалены. Это полезно для отслеживания изменений в критических системных файлах.

  ```kusto
  ConfigurationChange | where ConfigChangeType == "Files" and FileSystemPath contains " c:\\windows\\system32\\drivers\\"
  ```

### <a name="specific-service-stopped"></a>Определенная служба остановлена

Используйте следующий запрос для наблюдения за изменениями системных служб, критических для системы.

  ```kusto
  ConfigurationChange | where SvcState == "Stopped" and SvcName contains "w3svc"
  ```

### <a name="new-software-installed"></a>Установлено новое программное обеспечение

Используйте следующий запрос для сред, в которых необходимо заблокировать конфигурации программного обеспечения.

  ```kusto
  ConfigurationChange | where ConfigChangeType == "Software" and ChangeCategory == "Added"
  ```

### <a name="specific-software-version-is-or-isnt-installed-on-a-machine"></a>Определенная версия программного обеспечения или не установлена на компьютере

Используйте следующий запрос для оценки безопасности. Этот запрос ссылается на `ConfigurationData` , который содержит журналы инвентаризации и предоставляет Последнее состояние конфигурации, а не изменения.

  ```kusto
  ConfigurationData | where SoftwareName contains "Monitoring Agent" and CurrentVersion != "8.0.11081.0"
  ```

### <a name="known-dll-changed-through-the-registry"></a>Известная библиотека DLL изменена в реестре

Используйте следующий запрос для обнаружения изменений в хорошо известных разделах реестра.

  ```kusto
  ConfigurationChange | where RegistryKey == "HKEY_LOCAL_MACHINE\\System\\CurrentControlSet\\Control\\Session Manager\\KnownDlls"
  ```

## <a name="next-steps"></a>Дальнейшие действия

Узнайте, как служба автоматизации Azure может [создавать расписания обновления](./update-schedules.md) для управления обновлениями серверов.

> [!div class="nextstepaction"]
> [Создание расписаний обновления](./update-schedules.md)
