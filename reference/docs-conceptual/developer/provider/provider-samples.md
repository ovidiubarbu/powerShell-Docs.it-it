---
title: Esempi di provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366300"
---
# <a name="provider-samples"></a>Esempi di provider

In questa sezione sono inclusi esempi di provider che accedono a un database di Microsoft Access. Questi esempi includono classi provider che derivano da tutte le classi del provider di base.

## <a name="in-this-section"></a>Contenuto della sezione

Questa sezione include gli argomenti seguenti:

[Esempio AccessDBProviderSample01](./accessdbprovidersample01.md) Questo esempio illustra come dichiarare la classe del provider che deriva direttamente dalla classe [System. Management. Automation. provider. CmdletProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . È incluso solo per motivi di completezza.

[AccessDBProviderSample02](./accessdbprovidersample02.md) Questo esempio illustra come sovrascrivere i metodi [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) per supportare le chiamate al `New-PSDrive` e `Remove-PSDrive` cmdlet. La classe del provider in questo esempio deriva dalla classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .

[AccessDBProviderSample03](./accessdbprovidersample03.md) Questo esempio illustra come sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) per supportare le chiamate a `Get-Item` e @no__ cmdlet t-4. La classe del provider in questo esempio deriva dalla classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

[AccessDBProviderSample04](./accessdbprovidersample04.md) Questo esempio illustra come sovrascrivere i metodi del contenitore per supportare le chiamate ai cmdlet `Copy-Item`, `Get-ChildItem`, `New-Item` e `Remove-Item`. Questi metodi devono essere implementati quando l'archivio dati contiene elementi che sono contenitori. Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune. La classe del provider in questo esempio deriva dalla classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

[AccessDBProviderSample05](./accessdbprovidersample05.md) Questo esempio illustra come sovrascrivere i metodi del contenitore per supportare le chiamate ai cmdlet `Move-Item` e `Join-Path`. Questi metodi devono essere implementati quando l'utente deve spostare elementi all'interno di un contenitore e se l'archivio dati contiene contenitori annidati. La classe del provider in questo esempio deriva dalla classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

[AccessDBProviderSample06](./accessdbprovidersample06.md) Questo esempio illustra come sovrascrivere i metodi di contenuto per supportare le chiamate ai cmdlet `Clear-Content`, `Get-Content` e `Set-Content`. Questi metodi devono essere implementati quando l'utente deve gestire il contenuto degli elementi nell'archivio dati. La classe del provider in questo esempio deriva dalla classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) e implementa l'interfaccia [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

## <a name="see-also"></a>Vedere anche

[Scrittura di un provider di Windows PowerShell](./writing-a-windows-powershell-provider.md)