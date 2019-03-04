---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859407"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

In questo esempio illustra come sovrascrivere i [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) i metodi per supportare le chiamate per il `Get-Item` e `Set-Item` cmdlet. La classe provider in questo esempio deriva dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

## <a name="demonstrates"></a>Illustra

> [!IMPORTANT]
> Classe del provider verrà probabilmente derivare da una delle seguenti classi e possibilmente implementare altre interfacce del provider:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe. Visualizzare [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe. Visualizzare [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Per altre informazioni sulla scelta di quale classe provider derivano dal basato sulle funzionalità del provider, vedere [la progettazione del Provider di Windows PowerShell](./provider-types.md).

In questo esempio viene illustrato quanto segue:

- La dichiarazione di `CmdletProvider` attributo.

- Definizione di una classe di provider che deriva dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

- Sovrascrivendo il [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) per modificare il comportamento del metodo di `New-PSDrive` cmdlet, che consente all'utente di creare nuove unità. (In questo esempio non illustra come aggiungere parametri dinamici al `New-PSDrive` cmdlet.)

- Sovrascrivendo il [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metodo per supportare la rimozione di unità esistente.

- Sovrascrivendo il [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metodo per modificare il comportamento del `Get-Item` cmdlet, consentendo all'utente di recuperare gli elementi dall'archivio dati. (In questo esempio non illustra come aggiungere parametri dinamici al `Get-Item` cmdlet.)

- Sovrascrivendo il [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metodo per modificare il comportamento del `Set-Item` cmdlet, consentendo all'utente di aggiornare gli elementi nell'archivio dati. (In questo esempio non illustra come aggiungere parametri dinamici al `Get-Item` cmdlet.)

- Sovrascrivendo il [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) per modificare il comportamento del metodo di `Test-Path` cmdlet. (In questo esempio non illustra come aggiungere parametri dinamici al `Test-Path` cmdlet.)

- Sovrascrivendo il [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metodo per determinare se il percorso specificato sia valido.

## <a name="example"></a>Esempio

In questo esempio mostra come sovrascrivere i metodi necessari per ottenere e impostare gli elementi in una data di Microsoft Access base.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Progettazione del Provider di Windows PowerShell](./provider-types.md)