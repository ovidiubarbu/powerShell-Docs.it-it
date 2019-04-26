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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081122"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="512c1-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="512c1-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="512c1-103">In questo esempio viene illustrato come dichiarare una classe di provider che deriva direttamente dai [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="512c1-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="512c1-104">È incluso solo per motivi di completezza.</span><span class="sxs-lookup"><span data-stu-id="512c1-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="512c1-105">Di seguito viene illustrato</span><span class="sxs-lookup"><span data-stu-id="512c1-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="512c1-106">Classe del provider verrà probabilmente derivare da una delle seguenti classi e possibilmente implementare altre interfacce del provider:</span><span class="sxs-lookup"><span data-stu-id="512c1-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="512c1-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="512c1-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="512c1-108">Visualizzare [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="512c1-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="512c1-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="512c1-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="512c1-110">Visualizzare [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="512c1-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="512c1-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="512c1-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="512c1-112">Visualizzare [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="512c1-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="512c1-113">Per altre informazioni sulla scelta di quale classe provider derivano dal basato sulle funzionalità del provider, vedere [la progettazione del Provider di Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="512c1-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="512c1-114">In questo esempio viene illustrato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="512c1-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="512c1-115">La dichiarazione di `CmdletProvider` attributo.</span><span class="sxs-lookup"><span data-stu-id="512c1-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="512c1-116">Definizione di una classe di provider che deriva direttamente dai [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="512c1-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="512c1-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="512c1-117">Example</span></span>

<span data-ttu-id="512c1-118">Questo esempio viene illustrato come definire una classe di provider e su come dichiarare il `CmdletProvider` attributo.</span><span class="sxs-lookup"><span data-stu-id="512c1-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="512c1-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="512c1-119">See Also</span></span>

[<span data-ttu-id="512c1-120">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="512c1-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="512c1-121">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="512c1-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="512c1-122">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="512c1-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="512c1-123">Progettazione del Provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="512c1-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)