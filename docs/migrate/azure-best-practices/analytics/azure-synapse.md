---
title: Высокий уровень доступности для аналитики Azure синапсе
description: Используйте функции Azure синапсе Analytics для решения требований к высокой доступности и аварийному восстановлению.
author: v-hanki
ms.author: brblanch
ms.date: 07/14/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 93b7a66a1c30ec4975a2cef092b54f56023eed0a
ms.sourcegitcommit: 163e703d9cbf90b26d96087c836a9cbd94fc7e35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87963287"
---
# <a name="high-availability-for-azure-synapse-analytics"></a>Высокий уровень доступности для аналитики Azure синапсе

Одно из ключевых преимуществ современной облачной инфраструктуры, например Microsoft Azure, заключается в том, что функции обеспечения высокого уровня доступности (HA) и аварийного восстановления (DR) встроены и просты в реализации и настройке. Эти средства часто являются менее затратными по сравнению с аналогичными функциями в локальной среде. Использование этих встроенных функций также означает, что не нужно переносить механизмы резервного копирования и восстановления в существующем хранилище данных.

В следующих разделах описываются стандартные функции Azure синапсе Analytics, которые устраняют требования к высокой доступности и аварийному восстановлению.

## <a name="high-availability"></a>Высокий уровень доступности

Azure синапсе Analytics использует моментальные снимки базы данных для обеспечения высокой доступности хранилища. Моментальный снимок хранилища данных создает точку восстановления, которую можно использовать для восстановления или копирования хранилища данных в предыдущее состояние. Так как Azure синапсе Analytics является распределенной системой, моментальный снимок хранилища данных состоит из множества файлов, расположенных в службе хранилища Azure. Моментальные снимки фиксируют добавочные изменения в данных, содержащихся в хранилище данных.

Azure синапсе Analytics автоматически создает моментальные снимки в течение дня для создания точек восстановления, доступных в течение семи дней. Этот период хранения нельзя изменить. Azure синапсе Analytics поддерживает целевую точку восстановления в 8 часов (RPO). Хранилище данных в основном регионе можно восстановить из одного из моментальных снимков, сделанных за последние семь дней.

Служба также поддерживает определенные пользователем точки восстановления. Запуск моментальных снимков вручную позволяет создавать точки восстановления хранилища данных до и после больших изменений. Эта возможность гарантирует логическую целостность точек восстановления. Логическая согласованность обеспечивает дополнительную защиту данных в случае прерываний рабочей нагрузки или ошибок пользователей для быстрого восстановления.

## <a name="disaster-recovery"></a>Аварийное восстановление

В дополнение к моментальным снимкам, описанным выше, Azure синапсе Analytics выполняет стандартную геоархивацию один раз в день в парный центр обработки данных. Целевая точка восстановления для геовосстановления составляет 24 часа. Геоархивацию можно восстановить на сервере в любом другом регионе, где поддерживается Azure синапсе Analytics. Геоархивация гарантирует, что хранилище данных можно восстановить в случае, если точки восстановления в основном регионе недоступны.
