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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854157"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

In questo esempio viene illustrato come dichiarare una classe di provider che deriva direttamente dai [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe. È incluso solo per motivi di completezza.

## <a name="demonstrates"></a>Illustra

> [!IMPORTANT]
> Classe del provider verrà probabilmente derivare da una delle seguenti classi e possibilmente implementare altre interfacce del provider:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe. Visualizzare [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe. Visualizzare [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe. Visualizzare [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Per altre informazioni sulla scelta di quale classe provider derivano dal basato sulle funzionalità del provider, vedere [la progettazione del Provider di Windows PowerShell](./provider-types.md).

In questo esempio viene illustrato quanto segue:

- La dichiarazione di `CmdletProvider` attributo.

- Definizione di una classe di provider che deriva direttamente dai [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe.

## <a name="example"></a>Esempio

Questo esempio viene illustrato come definire una classe di provider e su come dichiarare il `CmdletProvider` attributo.

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

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Progettazione del Provider di Windows PowerShell](./provider-types.md)