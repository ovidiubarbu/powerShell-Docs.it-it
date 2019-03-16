---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055547"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Questo esempio illustra come sovrascrivere i metodi per supportare le chiamate per il `Clear-Content`, `Get-Content`, e `Set-Content` cmdlet. Questi metodi devono essere implementati quando l'utente deve gestire il contenuto degli elementi nell'archivio dati. La classe provider in questo esempio deriva dal [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe che implementa il [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaccia.

## <a name="demonstrates"></a>Illustra

> [!IMPORTANT]
> Classe del provider verrà probabilmente derivare da una delle seguenti classi e possibilmente implementare altre interfacce del provider:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe. Visualizzare [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe. Visualizzare [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.
>
> Per altre informazioni sulla scelta di quale classe provider derivano dal basato sulle funzionalità del provider, vedere [la progettazione del Provider di Windows PowerShell](./provider-types.md).

In questo esempio viene illustrato quanto segue:

- La dichiarazione di `CmdletProvider` attributo.

- Definizione di una classe di provider che deriva dal [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe e che dichiara il [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaccia.

- Sovrascrivendo il [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metodo per modificare il comportamento del `Clear-Content` cmdlet, consentendo all'utente di rimuovere il contenuto da un elemento. (In questo esempio non illustra come aggiungere parametri dinamici al `Clear-Content` cmdlet.)

- Sovrascrivendo il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) per modificare il comportamento del metodo di `Get-Content` cmdlet, consentendo all'utente di recuperare il contenuto di un elemento. (In questo esempio non illustra come aggiungere parametri dinamici al `Get-Content` cmdlet.).

- Sovrascrivendo il [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) per modificare il comportamento del metodo di `Set-Content` cmdlet, consentendo all'utente di aggiornare il contenuto di un elemento. (In questo esempio non illustra come aggiungere parametri dinamici al `Set-Content` cmdlet.)

## <a name="example"></a>Esempio

In questo esempio mostra come sovrascrivere i metodi necessari per cancellare, ottenere e impostare il contenuto degli elementi in una data di Microsoft Access base.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Progettazione del Provider di Windows PowerShell](./provider-types.md)