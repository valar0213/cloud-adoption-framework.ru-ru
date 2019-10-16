---
title: Список невыполненных работ по итерации и выпуску
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Составление списка невыполненных работ по итерации и выпуску
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: d2dddb4893a2781da38969949972fa516e32b46c
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025397"
---
# <a name="manage-change-in-an-incremental-migration-effort"></a>Управление изменениями в процессе поэтапной миграции

В этой статье предполагается, что процессы миграции являются поэтапными и выполняются параллельно с [процессом управления](../../../govern/index.md). Тем не менее те же рекомендации можно использовать, чтобы определить начальные задачи в структурной декомпозиции работы для традиционных подходов каскадного управления изменениями.

## <a name="release-backlog"></a>Список невыполненных работ по выпуску

Список *невыполненных работ по выпуску* состоит из ряда ресурсов (виртуальных машин, баз данных, файлов и приложений), которые необходимо перенести, прежде чем можно будет выпустить рабочую нагрузку для использования в облаке. Во время каждой итерации команда по внедрению в облако документирует и оценивает усилия, необходимые для переноса каждого ресурса в облако. См. приведенный ниже раздел "Список невыполненных работ по итерации".

## <a name="iteration-backlog"></a>Список невыполненных работ по итерации

*Список невыполненных работ по итерации* — это подробный список работ, необходимых для переноса определенного числа ресурсов из существующих цифровых активов в облако. Записи в этом списке часто хранятся в качестве рабочих элементов в таком средстве гибкого управления, как Azure DevOps.

Перед началом первой итерации команда по внедрению в облако указывает длительность итерации (обычно от двух до четырех недель). Этот период времени важен для определения времени начала и окончания каждого набора утвержденных действий. Поддержание согласованных окон выполнения позволяет легко оценивать скорость (темпы миграции) и выполнять изменения в соответствии с изменяющимися бизнес-потребностями.

До каждой итерации команда рассматривает список невыполненных работ по выпуску, оценивая усилия и приоритеты ресурсов, которые необходимо перенести. Затем они утверждают определенное число согласованных миграций. Когда все будет согласовано командой по внедрению в облако, список действий станет *текущим списком невыполненных работ по итерации*.

Во время каждой итерации члены команды работают вместе для выполнения обязательств в рамках текущего списка невыполненных работ по итерации.

## <a name="next-steps"></a>Следующие шаги

Когда список невыполненных работ по итерации будет определен и принят командой по внедрению в облако, этап [утверждения в рамках управления изменениями](./approve.md) можно завершить.

> [!div class="nextstepaction"]
> [Утверждение изменений архитектуры перед миграцией](./approve.md)