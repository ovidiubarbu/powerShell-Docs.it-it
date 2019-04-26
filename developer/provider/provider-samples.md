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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080935"
---
# <a name="provider-samples"></a>Esempi di provider

In questa sezione include esempi di provider che accedono a un database Microsoft Access. Questi esempi includono le classi di provider che derivano da tutte le classi di provider di base.

## <a name="in-this-section"></a>Contenuto della sezione

Questa sezione include gli argomenti seguenti:

[Esempio AccessDBProviderSample01](./accessdbprovidersample01.md) in questo esempio viene illustrato come dichiarare la classe del provider che deriva direttamente dai [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe. È incluso solo per motivi di completezza.

[AccessDBProviderSample02](./accessdbprovidersample02.md) in questo esempio illustra come sovrascrivere i [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [ System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metodi per supportare le chiamate per il `New-PSDrive` e `Remove-PSDrive` cmdlet. La classe provider in questo esempio deriva dal [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe.

[AccessDBProviderSample03](./accessdbprovidersample03.md) in questo esempio illustra come sovrascrivere i [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [ System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metodi per supportare le chiamate per il `Get-Item` e `Set-Item` cmdlet. La classe provider in questo esempio deriva dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

[AccessDBProviderSample04](./accessdbprovidersample04.md) in questo esempio mostra come sovrascrivere metodi contenitore per supportare le chiamate per il `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlet. Questi metodi devono essere implementati quando l'archivio dati contiene elementi che sono contenitori. Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune. La classe provider in questo esempio deriva dal [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

[AccessDBProviderSample05](./accessdbprovidersample05.md) in questo esempio mostra come sovrascrivere metodi contenitore per supportare le chiamate per il `Move-Item` e `Join-Path` cmdlet. Questi metodi devono essere implementati quando l'utente deve spostare elementi all'interno di un contenitore e se l'archivio dati contiene contenitori annidati. La classe provider in questo esempio deriva dal [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.

[AccessDBProviderSample06](./accessdbprovidersample06.md) in questo esempio illustra come sovrascrivere i metodi per supportare le chiamate per il `Clear-Content`, `Get-Content`, e `Set-Content` cmdlet. Questi metodi devono essere implementati quando l'utente deve gestire il contenuto degli elementi nell'archivio dati. La classe provider in questo esempio deriva dal [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe che implementa il [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaccia.

## <a name="see-also"></a>Vedere anche

[Scrittura di un Provider di Windows PowerShell](./writing-a-windows-powershell-provider.md)