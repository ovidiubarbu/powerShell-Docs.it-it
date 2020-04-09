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
ms.openlocfilehash: bea70ccf0dfbf65298890104a55e3cf472090887
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977581"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Questo esempio illustra come sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) per supportare le chiamate ai cmdlet `Get-Item` e `Set-Item`. La classe del provider in questo esempio deriva dalla classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

## <a name="demonstrates"></a>Dimostra

> [!IMPORTANT]
> È probabile che la classe del provider derivi da una delle classi seguenti e possa implementare altre interfacce del provider:
>
> -   Classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .
> -   Classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Vedere [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   Classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Vedere [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Per ulteriori informazioni sulla scelta della classe del provider da derivare da in base alle funzionalità del provider, vedere [progettazione del provider di Windows PowerShell](./provider-types.md).

In questo esempio viene illustrato quanto segue:

- Dichiarazione dell'attributo `CmdletProvider`.
- Definizione di una classe di provider che deriva dalla classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .
- Sovrascrivere il metodo [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) per modificare il comportamento del cmdlet `New-PSDrive`, consentendo all'utente di creare nuove unità.
  In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `New-PSDrive`.
- Sovrascrivere il metodo [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) per supportare la rimozione delle unità esistenti.
- Sovrascrivere il metodo [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) per modificare il comportamento del cmdlet `Get-Item`, consentendo all'utente di recuperare elementi dall'archivio dati. In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Get-Item`.
- Sovrascrivere il metodo [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) per modificare il comportamento del cmdlet `Set-Item`, consentendo all'utente di aggiornare gli elementi nell'archivio dati. In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Get-Item`.
- Sovrascrivere il metodo [System. Management. Automation. provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) per modificare il comportamento del cmdlet `Test-Path`. In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Test-Path`.
- Sovrascrivere il metodo [System. Management. Automation. provider. Itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) per determinare se il percorso specificato è valido.

## <a name="example"></a>Esempio

In questo esempio viene illustrato come sovrascrivere i metodi necessari per ottenere e impostare elementi in un database di Microsoft Access.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-976":::

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Progettazione del provider di Windows PowerShell](./provider-types.md)
