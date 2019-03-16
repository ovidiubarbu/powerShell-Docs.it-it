---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057621"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Questo esempio illustra come sovrascrivere metodi contenitore per supportare le chiamate per il `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlet. Questi metodi devono essere implementati quando l'archivio dati contiene elementi che sono contenitori. Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune. La classe provider in questo esempio deriva dal [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

## <a name="demonstrates"></a>Illustra

> [!IMPORTANT]
> Classe del provider molto probabilmente esegue la derivazione da di [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

In questo esempio viene illustrato quanto segue:

- La dichiarazione di `CmdletProvider` attributo.

- Definizione di una classe di provider che deriva dal [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.

- Sovrascrivendo il [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metodo per modificare il comportamento del `Copy-Item` cmdlet che consente all'utente di copiare gli elementi da una posizione a un'altra. (In questo esempio non illustra come aggiungere parametri dinamici al `Copy-Item` cmdlet.)

- Sovrascrivendo il [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metodo per modificare il comportamento del cmdlet Get-ChildItems, che consente all'utente di recuperare gli elementi figlio dell'elemento padre . (In questo esempio mostra come aggiungere parametri dinamici per il cmdlet Get-ChildItems).

- Sovrascrivendo il [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metodo per modificare il comportamento del cmdlet Get-ChildItems quando il `Name` parametro del cmdlet è specificato.

- Sovrascrivendo il [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metodo per modificare il comportamento del `New-Item` cmdlet, che consente all'utente di aggiungere elementi all'archivio dati. (In questo esempio non illustra come aggiungere parametri dinamici al `New-Item` cmdlet.)

- Sovrascrivendo il [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) per modificare il comportamento del metodo di `Remove-Item` cmdlet. (In questo esempio non illustra come aggiungere parametri dinamici al `Remove-Item` cmdlet.)

## <a name="example"></a>Esempio

In questo esempio mostra come sovrascrivere i metodi necessari per copiare, creare e rimuovere elementi, nonché i metodi per il recupero di elementi di un elemento padre l'elemento figlio.

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Progettazione del Provider di Windows PowerShell](./provider-types.md)