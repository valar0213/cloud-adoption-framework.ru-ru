---
title: Какую роль репликация и синхронизация играют в процессе миграции?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Процесс миграции в облако, предназначенный для выполнения задач миграции рабочих нагрузок в облако.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 3e65631f0adf2584bbf0ee24b10d20df73ece715
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70833418"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-role-does-replication-play-in-the-migration-process"></a>Какую роль репликация играет в процессе миграции?

Локальные центры обработки данных заполнены физическими ресурсами, такими как серверы, устройства и сетевые устройства. Однако каждый сервер — это просто физическая оболочка. Реальное значение имеют двоичные файлы, выполняемые на сервере. Приложения и данные являются целью центра обработки данных. Это основные двоичные файлы, которые будут перенесены. Работу этих приложений и хранилищ данных обеспечивают другие цифровые активы и двоичные источники, такие как операционные системы, сетевые маршруты, файлы и протоколы безопасности.

Репликация — это основа процесса миграции. Это процесс копирования версий различных двоичных файлов на определенный момент времени. Затем двоичные моментальные снимки копируются на новую платформу и развертываются на новом оборудовании в ходе процесса, называемого *присвоением начального значения*. При правильном выполнении начальная копия двоичных данных должна быть идентична исходным двоичным данным на старом оборудовании. Однако этот моментальный снимок двоичных данных тут же становится неактуальным и несогласованным с первоначальным источником. Чтобы сохранить согласованность новых и старых двоичных данных, процесс, называемый *синхронизацией*, постоянно обновляет копию, хранящуюся на новой платформе. Синхронизация будет продолжаться до тех пор, пока ресурс не будет перемещен в рабочую среду в соответствии с выбранной моделью перемещения в рабочую среду. На этом этапе синхронизация прерывается.

## <a name="required-prerequisites-to-replication"></a>Необходимые условия для репликации

Перед репликацией необходимо подготовить *новую платформу* и оборудование для получения копий двоичных данных. В статье, посвященной [предварительным требованиям](../prerequisites/index.md), описаны минимальные требования к среде, которые помогут создать надежную платформу для получения двоичных реплик.

*Исходные двоичные данные* также должны быть подготовлены для репликации и синхронизации. В статьях, посвященных оценке, архитектуре и исправлению, описывается, что нужно сделать, чтобы подготовить исходные двоичные файлы к репликации и синхронизации.

Необходимо реализовать *цепочку инструментов*, которая соответствует новой платформе и исходным двоичным данным, чтобы выполнять процессы репликации и синхронизации и управлять ими. В статье о [параметрах репликации](./replicate-options.md) описаны различные инструменты, которые могут использоваться для миграции в Azure.

## <a name="replication-risks---physics-of-replication"></a>Риски репликации: физика репликации

При планировании репликации любых исходных двоичных данных в новое место назначения следует учитывать несколько фундаментальных законов, которые распространяются на этапы планирования и выполнения.

- **Скорость света.** При перемещении больших объемов данных оптоволоконные кабели по-прежнему является самым быстрым вариантом. К сожалению, эти кабели позволяют перемещать данные только со скоростью в две третьих от скорости света. Это означает, что не существует метода мгновенной или неограниченной репликации данных.
- **Скорость конвейера глобальной сети.** Помимо непосредственно скорости перемещения данных следует учитывать и пропускную способность канала исходящей связи, которая определяет объем данных, которые могут передаваться в секунду через существующую глобальную сеть компании в целевой центр обработки данных.
- **Скорость при расширении возможностей глобальной сети.** Если размер бюджета ограничен, можно увеличить пропускную способность глобальной сети компании. Однако на приобретение, подготовку к работе и интеграцию дополнительных оптоволоконных подключений могут потребоваться недели или месяцы.
- **Скорость дисков.** Если данные могут передаваться быстрее, а пропускная способность подключения между расположением исходных двоичных данных и целевым местом назначения не ограничена, то ограничения будут обусловлены физическим оборудованием. Данные можно реплицировать только с той же скоростью, с которой они могут быть считаны с исходных дисков. Для считывания всех данных или нуля с каждого из дисков в центре обработки данных требуется время.
- **Скорость принятия решений человеком.** Диски и свет движутся быстрее, чем процессы принятия решений человеком. Если группе людей нужно совместно работать и принимать решения, то получение результатов будет происходить еще медленнее. Репликация никак не избавит вас от задержек, связанных с человеческим интеллектом.

Каждый из этих законов физики приводит к появлению следующих рисков, которые обычно влияют на планы миграции.

- **Время репликации.** Расширенные инструменты репликации не могут преодолеть основополагающие законы физики — для репликации требуется время и пропускная способность. Планы должны содержать реалистичные временные шкалы, отражающие количество времени, необходимое для репликации двоичных данных. *Общая доступная пропускная способность для миграции* — это максимальный объем пропускной способности, измеряемой в мегабитах в секунду (Мбит/с) или гигабитах в секунду (Гбит/с), который не используется другими решениями организации с более высоким приоритетом. *Общее хранилище миграции* — это общее дисковое пространство, измеряемое в гигабайтах или терабайтах, необходимое для хранения моментального снимка всех ресурсов, которые подлежат миграции. Первоначальную оценку времени можно рассчитать, разделив *общее хранилище миграции* на *общую доступную пропускную способность миграции*. Обратите внимание на преобразование битов в байты. Для более точного расчета времени ознакомьтесь со следующим фактором, совокупным результатом отклонения дисков.
- **Совокупный результат отклонения дисков.** С момента репликации до перемещения ресурса в рабочую среду исходные и целевые двоичные данные должны синхронизироваться. *Отклонение* в двоичных данных потребляет дополнительную пропускную способность, так как все изменения в двоичных данных должны реплицироваться на повторяющийся основе. Во время синхронизации все отклонения в двоичных данных должны учитываться при вычислении общего хранилища миграции. Чем больше времени требуется для перемещения ресурса в рабочую среду, тем больше будет накапливаться отклонений данных. Чем больше ресурсов синхронизируется, тем большая пропускная способность потребляется. При синхронизации всех ресурсов тратится немного больше, чем общая доступная пропускная способность миграции.
- **Период изменения организации.** Как упоминалось в предыдущем пункте, "Совокупный результат отклонения дисков", длительность синхронизации оказывает накопительное негативное влияние на скорость миграции. Установка приоритетов невыполненной работы и расширенная подготовка к [плану изменения организации](../optimize/business-change-plan.md) крайне важны для скорости миграции. Самое важное тестирование соответствия деловой и технической инфраструктуры организации при миграции выполняется на этапе перемещения в рабочую среду. Чем быстрее ресурс может быть перемещен в рабочую среду, тем меньше влияние отклонения дисков на пропускную способность и тем больше пропускной способности и времени можно выделить для репликации следующей рабочей нагрузки.

## <a name="next-steps"></a>Следующие шаги

После завершения репликации могут начаться [промежуточные действия](./stage.md).

> [!div class="nextstepaction"]
> [Промежуточные действия во время миграции](./stage.md)