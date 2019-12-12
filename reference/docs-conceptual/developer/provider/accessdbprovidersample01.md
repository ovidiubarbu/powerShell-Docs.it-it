---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360000"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Questo esempio illustra come dichiarare una classe di provider che deriva direttamente dalla classe [System. Management. Automation. provider. CmdletProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . È incluso solo per motivi di completezza.

## <a name="demonstrates"></a>Illustra

> [!IMPORTANT]
> È probabile che la classe del provider derivi da una delle classi seguenti e possa implementare altre interfacce del provider:
>
> -   Classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Vedere [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   Classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Vedere [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   Classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Vedere [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Per ulteriori informazioni sulla scelta della classe del provider da derivare da in base alle funzionalità del provider, vedere [progettazione del provider di Windows PowerShell](./provider-types.md).

In questo esempio viene illustrato quanto segue:

- Dichiarazione dell'attributo `CmdletProvider`.

- Definizione di una classe di provider che deriva direttamente dalla classe [System. Management. Automation. provider. CmdletProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .

## <a name="example"></a>Esempio

In questo esempio viene illustrato come definire una classe di provider e come dichiarare l'attributo `CmdletProvider`.

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Progettazione del provider di Windows PowerShell](./provider-types.md)