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
ms.openlocfilehash: 0d3133c75d8e608967f15ffb7345fc0f63e1cd5c
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977506"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Questo esempio illustra come sovrascrivere i metodi del contenitore per supportare le chiamate ai cmdlet `Copy-Item`, `Get-ChildItem`, `New-Item`e `Remove-Item`. Questi metodi devono essere implementati quando l'archivio dati contiene elementi che sono contenitori. Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune. La classe del provider in questo esempio deriva dalla classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

## <a name="demonstrates"></a>Dimostra

> [!IMPORTANT]
> È probabile che la classe del provider derivi da [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

In questo esempio viene illustrato quanto segue:

- Dichiarazione dell'attributo `CmdletProvider`.
- Definizione di una classe di provider che deriva dalla classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .
- Sovrascrivere il metodo [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) per modificare il comportamento del cmdlet `Copy-Item`, che consente all'utente di copiare gli elementi da una posizione a un'altra. In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Copy-Item`.
- Sovrascrivere il metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) per modificare il comportamento del cmdlet Get-ChildItems, che consente all'utente di recuperare gli elementi figlio dell'elemento padre. (Questo esempio non Mostra come aggiungere parametri dinamici al cmdlet Get-ChildItems).
- Sovrascrivere il metodo [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) per modificare il comportamento del cmdlet Get-ChildItems quando viene specificato il `Name` parametro del cmdlet.
- Sovrascrivere il metodo [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) per modificare il comportamento del cmdlet `New-Item`, che consente all'utente di aggiungere elementi all'archivio dati. In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `New-Item`.
- Sovrascrivere il metodo [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) per modificare il comportamento del cmdlet `Remove-Item`. In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Remove-Item`.

## <a name="example"></a>Esempio

In questo esempio viene illustrato come sovrascrivere i metodi necessari per copiare, creare e rimuovere elementi, nonché metodi per ottenere gli elementi figlio di un elemento padre.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-1635":::

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Progettazione del provider di Windows PowerShell](./provider-types.md)
