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
ms.openlocfilehash: 9c00ec6de987729fec42dc57245a949d11e31f4b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366330"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Questo esempio illustra come sovrascrivere i metodi di contenuto per supportare le chiamate ai cmdlet `Clear-Content`, `Get-Content`e `Set-Content`. Questi metodi devono essere implementati quando l'utente deve gestire il contenuto degli elementi nell'archivio dati. La classe del provider in questo esempio deriva dalla classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) e implementa l'interfaccia [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

## <a name="demonstrates"></a>Illustra

> [!IMPORTANT]
> È probabile che la classe del provider derivi da una delle classi seguenti e possa implementare altre interfacce del provider:
>
> -   Classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Vedere [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   Classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Vedere [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   Classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .
>
> Per ulteriori informazioni sulla scelta della classe del provider da derivare da in base alle funzionalità del provider, vedere [progettazione del provider di Windows PowerShell](./provider-types.md).

In questo esempio viene illustrato quanto segue:

- Dichiarazione dell'attributo `CmdletProvider`.

- Definizione di una classe di provider che deriva dalla classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) e che dichiara l'interfaccia [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

- Sovrascrivere il metodo [System. Management. Automation. provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) per modificare il comportamento del cmdlet `Clear-Content`, consentendo all'utente di rimuovere il contenuto da un elemento. In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Clear-Content`.

- Sovrascrivere il metodo [System. Management. Automation. provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) per modificare il comportamento del cmdlet `Get-Content`, consentendo all'utente di recuperare il contenuto di un elemento. In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Get-Content`.

- Sovrascrivere il metodo [Microsoft. PowerShell. Commands. FileSystemProvider. Getcontentwriter *](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) per modificare il comportamento del cmdlet `Set-Content`, consentendo all'utente di aggiornare il contenuto di un elemento. In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Set-Content`.

## <a name="example"></a>Esempio

Questo esempio illustra come sovrascrivere i metodi necessari per cancellare, ottenere e impostare il contenuto di elementi in un database di Microsoft Access.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Progettazione del provider di Windows PowerShell](./provider-types.md)
