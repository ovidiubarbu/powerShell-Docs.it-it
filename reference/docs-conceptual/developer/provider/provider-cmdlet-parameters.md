---
title: Parametri del cmdlet provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366310"
---
# <a name="provider-cmdlet-parameters"></a>Parametri del cmdlet del provider

I cmdlet del provider sono dotati di un set di parametri statici disponibili per tutti i provider che supportano il cmdlet, nonché parametri dinamici aggiunti quando l'utente specifica un determinato valore per determinati parametri statici del cmdlet del provider.

## <a name="provider-cmdlet-static-parameters"></a>Parametri statici del cmdlet provider

I parametri statici sono definiti da Windows PowerShell. Un ampio set di questi parametri viene implementato da Windows PowerShell per garantire la coerenza tra tutti i provider e fornire un'esperienza di sviluppo più semplice. Esempi di questi parametri includono i parametri `literalPath`, `exclude` e `include` del cmdlet `Get-Item`. Un set più piccolo di questi parametri può essere sovrascritto per fornire azioni specifiche per il provider. Esempi di questi parametri includono il parametro `Path` e `Value` del cmdlet `Set-Item`. Di seguito è riportato un elenco dei parametri che possono essere sovrascritti per i cmdlet del provider.

cmdlet `Clear-Content` è possibile definire il modo in cui il provider utilizzerà i valori passati al parametro `Path` del cmdlet `Clear-Content` implementando il metodo [System. Management. Automation. provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) .

cmdlet `Clear-Item` è possibile definire il modo in cui il provider utilizzerà i valori passati al parametro `Path` del cmdlet `Clear-Item` implementando il metodo [System. Management. Automation. provider. Itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) .

cmdlet `Clear-ItemProperty` è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path` e `Name` del cmdlet `Clear-ItemProperty` implementando il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) .

cmdlet `Copy-Item` è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path`, `Destination` e `Recurse` del cmdlet `Copy-Item` implementando [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) Metodo.

Cmdlet Get-ChildItems è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path` e `Recurse` del cmdlet `Get-ChildItem` implementando [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) e metodi [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) .

cmdlet `Get-Content` è possibile definire il modo in cui il provider utilizzerà i valori passati al parametro `Path` del cmdlet `Get-Content` implementando il metodo [System. Management. Automation. provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) .

cmdlet `Get-Item` è possibile definire il modo in cui il provider utilizzerà i valori passati al parametro `Path` del cmdlet `Get-Item` implementando il metodo [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) .

cmdlet `Get-ItemProperty` è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path` e `Name` del cmdlet `Get-ItemProperty` implementando il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) .

cmdlet `Invoke-Item` è possibile definire il modo in cui il provider utilizzerà i valori passati al parametro `Path` del cmdlet `Invoke-Item` implementando il metodo [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

cmdlet `Move-Item` è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path` e `Destination` del cmdlet `Move-Item` implementando il metodo [System. Management. Automation. provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) .

cmdlet `New-Item` è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path`, `ItemType` e `Value` del cmdlet `New-Item` implementando [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) Metodo.

cmdlet `New-ItemProperty` è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path`, `Name`, `PropertyType` e `Value` del cmdlet `New-ItemProperty` implementando [Microsoft. PowerShell. Commands. Registryprovider. newproperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) Metodo.

`Remove-Item` è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path` e `Recurse` del cmdlet `Remove-Item` implementando il metodo [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) .

`Remove-ItemProperty` è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path` e `Name` del cmdlet `Remove-ItemProperty` implementando [System. Management. Automation. provider. Idynamicpropertycmdletprovider. RemoveProperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) Metodo.

cmdlet `Rename-Item` è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path` e `NewName` del cmdlet `Rename-Item` implementando il metodo [System. Management. Automation. provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) .

`Rename-ItemProperty` è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path`, `NewName` e `Name` del cmdlet `Rename-ItemProperty` implementando [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renameproperty * ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)metodo.

cmdlet `Set-Content` è possibile definire il modo in cui il provider utilizzerà i valori passati al parametro `Path` del cmdlet `Set-Content` implementando il metodo [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) .

cmdlet `Set-Item` è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path` e `Value` del cmdlet `Set-Item` implementando il metodo [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) .

cmdlet `Set-ItemProperty` è possibile definire il modo in cui il provider utilizzerà i valori passati ai parametri `Path` e `Value` del cmdlet `Set-Item` implementando il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) .

cmdlet `Test-Path` è possibile definire il modo in cui il provider utilizzerà i valori passati al parametro `Path` del cmdlet `Test-Path` implementando il metodo [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

Non è inoltre possibile specificare le caratteristiche di questi parametri, ad esempio se sono facoltative o obbligatorie, né è possibile assegnare a questi parametri un alias o specificare uno degli attributi di convalida. Al contrario, è possibile specificare le caratteristiche dei parametri nei cmdlet autonomi utilizzando attributi come l'attributo `Parameters`.

## <a name="provider-cmdlet-dynamic-parameters"></a>Parametri dinamici del cmdlet provider

I parametri dinamici per i provider di cmdlet sono simili ai provider dinamici per i cmdlet autonomi. In entrambi i casi, i parametri vengono aggiunti al cmdlet quando l'utente specifica un determinato valore per uno dei parametri predefiniti, ad esempio il parametro `path`. Tuttavia, non tutti i parametri statici possono essere utilizzati per attivare l'aggiunta di parametri dinamici. Per ulteriori informazioni sui parametri dinamici, vedere [parametri dinamici dei cmdlet del provider](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Vedere anche

[Parametri dinamici del cmdlet provider](./provider-cmdlet-dynamic-parameters.md)

[Scrittura di un provider di Windows PowerShell](./writing-a-windows-powershell-provider.md)