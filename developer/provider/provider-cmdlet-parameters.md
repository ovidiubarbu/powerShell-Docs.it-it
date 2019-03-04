---
title: I parametri del cmdlet provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: d0fb81ee1ca1f80e216c021e1bd64771b8de4dc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860117"
---
# <a name="provider-cmdlet-parameters"></a>Parametri del cmdlet del provider

Cmdlet del provider sono dotate di un set di parametri statici che sono disponibili a tutti i provider che supportano il cmdlet, nonché come dinamici parametri che vengono aggiunti quando l'utente specifica un determinato valore per determinati parametri statici del cmdlet del provider.

## <a name="provider-cmdlet-static-parameters"></a>Parametri statici Cmdlet del provider

Parametri statici sono definiti da Windows PowerShell. Un ampio set di questi parametri viene implementato da Windows PowerShell per ottenere la coerenza tra tutti i provider e per fornire un'esperienza di sviluppo più semplice. Esempi di questi parametri includono il `literalPath`, `exclude`, e `include` i parametri del `Get-Item` cmdlet. Un set più piccolo di questi parametri può essere sovrascritte per fornire azioni specifiche per il provider. Esempi di questi parametri includono il `Path` e `Value` parametro del `Set-Item` cmdlet. Ecco un elenco dei parametri che possono essere sovrascritte per i cmdlet del provider.

`Clear-Content` è possibile definire come il provider userà i valori passati al cmdlet di `Path` parametro del `Clear-Content` cmdlet implementando il [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)metodo.

`Clear-Item` è possibile definire come il provider userà i valori passati al cmdlet di `Path` parametro del `Clear-Item` cmdlet implementando il [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) metodo.

`Clear-ItemProperty` è possibile definire come il provider userà i valori passati al cmdlet di `Path` e `Name` i parametri del `Clear-ItemProperty` cmdlet implementando il [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) (metodo).

`Copy-Item` è possibile definire come il provider userà i valori passati al cmdlet di `Path`, `Destination`, e `Recurse` i parametri del `Copy-Item` cmdlet implementando il [ System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) (metodo).

Cmdlet Get-ChildItems è possibile definire come il provider userà i valori passati al `Path` e `Recures` i parametri delle `Get-ChildItem` cmdlet implementando il [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) e [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metodi.

`Get-Content` è possibile definire come il provider userà i valori passati al cmdlet di `Path` parametro del `Get-Content` cmdlet implementando il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metodo.

`Get-Item` è possibile definire come il provider userà i valori passati al cmdlet di `Path` parametro del `Get-Item` cmdlet implementando il [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) (metodo).

`Get-ItemProperty` è possibile definire come il provider userà i valori passati al cmdlet di `Path` e `Name` i parametri del `Get-ItemProperty` cmdlet implementando il [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) (metodo).

`Invoke-Item` è possibile definire come il provider userà i valori passati al cmdlet di `Path` parametro del `Invoke-Item` cmdlet implementando il [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)metodo.

`Move-Item` è possibile definire come il provider userà i valori passati al cmdlet di `Path` e `Destination` i parametri del `Move-Item` cmdlet implementando il [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) (metodo).

`New-Item` è possibile definire come il provider userà i valori passati al cmdlet di `Path`, `ItemType`, e `Value` i parametri del `New-Item` cmdlet implementando il [ System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) (metodo).

`New-ItemProperty` è possibile definire come il provider userà i valori passati al cmdlet di `Path`, `Name`, `PropertyType`, e `Value` parametri del `New-ItemProperty` cmdlet implementando il [ Microsoft.Powershell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) (metodo).

`Remove-Item` È possibile definire come il provider userà i valori passati al `Path` e `Recurse` i parametri delle `Remove-Item` cmdlet implementando il [System.Management.Automation.Provider.Containercmdletprovider.Removeitem* ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) (metodo).

`Remove-ItemProperty` È possibile definire come il provider userà i valori passati al `Path` e `Name` i parametri delle `Remove-ItemProperty` cmdlet implementando il [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) (metodo).

`Rename-Item` è possibile definire come il provider userà i valori passati al cmdlet di `Path` e `NewName` i parametri del `Rename-Item` cmdlet implementando il [ System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) (metodo).

`Rename-ItemProperty` È possibile definire come il provider userà i valori passati al `Path`, `NewName`, e `Name` i parametri del `Rename-ItemProperty` cmdlet implementando il [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) (metodo).

`Set-Content` è possibile definire come il provider userà i valori passati al cmdlet di `Path` parametro del `Set-Content` cmdlet implementando il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) metodo.

`Set-Item` è possibile definire come il provider userà i valori passati al cmdlet di `Path` e `Value` i parametri del `Set-Item` cmdlet implementando il [System.Management.Automation.Provider.Itemcmdletprovider.Setitem* ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) (metodo).

`Set-ItemProperty` è possibile definire come il provider userà i valori passati al cmdlet di `Path` e `Value` i parametri del `Set-Item` cmdlet implementando il [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) (metodo).

`Test-Path` è possibile definire come il provider userà i valori passati al cmdlet di `Path` parametro del `Test-Path` cmdlet implementando il [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)metodo.

Inoltre, è possibile specificare le caratteristiche di questi parametri, ad esempio se sono facoltative o obbligatorie, né può è assegnare un alias a questi parametri oppure specificare uno degli attributi di convalida. Al contrario, è possibile specificare le caratteristiche del parametro nel cmdlet autonomo con gli attributi, ad esempio il `Parameters` attributo.

## <a name="provider-cmdlet-dynamic-parameters"></a>Parametri dinamici di Cmdlet del provider

I parametri dinamici per i provider di cmdlet sono simili ai provider dinamico per i cmdlet autonomi. In entrambi i casi, i parametri vengono aggiunti al cmdlet quando l'utente specifica un determinato valore per uno dei parametri predefiniti, ad esempio il `path` parametro. Tuttavia, non tutti i parametri statici è utilizzabile per attivare l'aggiunta di parametri dinamici. Per altre informazioni sui parametri dinamici, vedere [parametri dinamici del Provider di Cmdlet](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Vedere anche

[Parametri dinamici di Cmdlet del provider](./provider-cmdlet-dynamic-parameters.md)

[Scrittura di un Provider di Windows PowerShell](./writing-a-windows-powershell-provider.md)