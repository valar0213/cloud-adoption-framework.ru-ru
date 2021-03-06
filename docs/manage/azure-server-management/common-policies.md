---
title: Общие примеры политики Azure
description: Используйте инфраструктуру внедрения в облаке для Azure, чтобы обеспечить соответствие требованиям политики управления, создав политики с помощью командлетов PowerShell.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 0b82f70aa7d7e2e0e9553f586b66a6dd8673b1c5
ms.sourcegitcommit: 8b82889dca0091f3cc64116f998a3a878943c6a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/09/2020
ms.locfileid: "89604081"
---
# <a name="common-azure-policy-examples"></a>Общие примеры политики Azure

[Политика Azure](/azure/governance/policy/overview) поможет вам применить управление к облачным ресурсам. Эта служба поможет вам создать снятие, обеспечивающую соответствие требованиям политики управления в масштабах всей Организации. Чтобы создать политики, используйте командлеты портал Azure или PowerShell. В этой статье приведены примеры командлетов PowerShell.

> [!NOTE]
> С помощью политики Azure политики принудительного применения ( `DeployIfNotExists` ) не развертываются автоматически на существующих виртуальных машинах. Для обеспечения соответствия виртуальных машин требуется исправление. Дополнительные сведения см. в статье [исправление несоответствующих ресурсов с помощью политики Azure](/azure/governance/policy/how-to/remediate-resources).

## <a name="common-policy-examples"></a>Примеры общих политик

В следующих разделах описываются некоторые часто используемые политики.

### <a name="restrict-resource-regions"></a>Ограничить регионы ресурсов

Нормативные требования и соответствие политике часто зависят от управления физическим расположением, в котором развертываются ресурсы. Вы можете использовать встроенную политику, позволяющую пользователям создавать ресурсы только в определенных регионах Azure.

Чтобы найти эту политику на портале, выполните поиск по слову "расположение" на странице определения политики. Или выполните этот командлет, чтобы найти политику:

```powershell
Get-AzPolicyDefinition | Where-Object { ($_.Properties.policyType -eq 'BuiltIn') `
  -and ($_.Properties.displayName -like '*location*') }
```

В следующем сценарии показано, как назначить политику. Измените `$SubscriptionID` значение, указав подписку, которой вы хотите назначить политику. Перед выполнением скрипта выполните вход с помощью командлета [Connect-азаккаунт](/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) .

```powershell
# Specify the value for $SubscriptionID.
$SubscriptionID = <subscription ID>
$scope = "/subscriptions/$SubscriptionID"

# Replace the -Name GUID with the policy GUID you want to assign.
$AllowedLocationPolicy = Get-AzPolicyDefinition -Name "e56962a6-4747-49cd-b67b-bf8b01975c4c"

# Replace the locations with the ones you want to specify.
$policyParam = '{ "listOfAllowedLocations":{"value":["eastus","westus"]}}'
New-AzPolicyAssignment -Name "Allowed Location" -DisplayName "Allowed locations for resource creation" -Scope $scope -PolicyDefinition $AllowedLocationPolicy -Location eastus -PolicyParameter $policyParam
```

Этот сценарий также можно использовать для применения других политик, описанных в этой статье. Просто замените GUID в строке, которая задает `$AllowedLocationPolicy` идентификатор GUID политики, которую необходимо применить.

### <a name="block-certain-resource-types"></a>Блокировать определенные типы ресурсов

Еще одна распространенная политика, используемая для управления затратами, может также использоваться для блокировки определенных типов ресурсов.

Чтобы найти эту политику на портале, выполните поиск по запросу "разрешенные типы ресурсов" на странице определения политики. Или выполните этот командлет, чтобы найти политику:

```powershell
Get-AzPolicyDefinition | Where-Object { ($_.Properties.policyType -eq "BuiltIn") -and ($_.Properties.displayName -like "*allowed resource types") }
```

Определив политику, которую вы хотите использовать, можно изменить пример PowerShell в разделе [ограничение области ресурсов](#restrict-resource-regions) , чтобы назначить политику.

### <a name="restrict-vm-size"></a>Ограничение размера виртуальной машины

Azure предлагает широкий спектр размеров виртуальных машин для поддержки различных рабочих нагрузок. Для управления бюджетом можно создать политику, которая допускает только подмножество размеров виртуальных машин в ваших подписках.

### <a name="deploy-antimalware"></a>Развертывание антивредоносной программы

С помощью этой политики можно развернуть расширение антивредоносной программы Майкрософт с конфигурацией по умолчанию для виртуальных машин, не защищенных с помощью антивредоносной программы.

GUID политики — `2835b622-407b-4114-9198-6f7064cbe0dc` .

В следующем сценарии показано, как назначить политику. Чтобы использовать скрипт, измените значение так, `$SubscriptionID` чтобы оно указывало на подписку, которой необходимо назначить политику. Перед выполнением скрипта выполните вход с помощью командлета [Connect-азаккаунт](/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) .

```powershell
# Specify the value for $SubscriptionID.
$subscriptionID = <subscription ID>
$scope = "/subscriptions/$subscriptionID"

$antimalwarePolicy = Get-AzPolicyDefinition -Name "2835b622-407b-4114-9198-6f7064cbe0dc"

# Replace location "eastus" with the value that you want to use.
New-AzPolicyAssignment -Name "Deploy Antimalware" -DisplayName "Deploy default Microsoft IaaSAntimalware extension for Windows Server" -Scope $scope -PolicyDefinition $antimalwarePolicy -Location eastus –AssignIdentity

```

## <a name="next-steps"></a>Дальнейшие действия

Узнайте о других доступных средствах и службах управления сервером.

> [!div class="nextstepaction"]
> [Средства и службы управления сервером Azure](./tools-services.md)
