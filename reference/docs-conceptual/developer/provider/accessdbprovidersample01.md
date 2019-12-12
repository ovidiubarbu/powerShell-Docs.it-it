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
# <a name="accessdbprovidersample01"></a><span data-ttu-id="e47ef-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="e47ef-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="e47ef-103">Questo esempio illustra come dichiarare una classe di provider che deriva direttamente dalla classe [System. Management. Automation. provider. CmdletProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="e47ef-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="e47ef-104">È incluso solo per motivi di completezza.</span><span class="sxs-lookup"><span data-stu-id="e47ef-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e47ef-105">Illustra</span><span class="sxs-lookup"><span data-stu-id="e47ef-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e47ef-106">È probabile che la classe del provider derivi da una delle classi seguenti e possa implementare altre interfacce del provider:</span><span class="sxs-lookup"><span data-stu-id="e47ef-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="e47ef-107">Classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="e47ef-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="e47ef-108">Vedere [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="e47ef-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="e47ef-109">Classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="e47ef-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="e47ef-110">Vedere [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="e47ef-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="e47ef-111">Classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="e47ef-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="e47ef-112">Vedere [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="e47ef-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="e47ef-113">Per ulteriori informazioni sulla scelta della classe del provider da derivare da in base alle funzionalità del provider, vedere [progettazione del provider di Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="e47ef-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="e47ef-114">In questo esempio viene illustrato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="e47ef-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="e47ef-115">Dichiarazione dell'attributo `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="e47ef-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="e47ef-116">Definizione di una classe di provider che deriva direttamente dalla classe [System. Management. Automation. provider. CmdletProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="e47ef-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="e47ef-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="e47ef-117">Example</span></span>

<span data-ttu-id="e47ef-118">In questo esempio viene illustrato come definire una classe di provider e come dichiarare l'attributo `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="e47ef-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e47ef-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e47ef-119">See Also</span></span>

[<span data-ttu-id="e47ef-120">System. Management. Automation. provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="e47ef-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="e47ef-121">System. Management. Automation. provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="e47ef-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="e47ef-122">System. Management. Automation. provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="e47ef-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="e47ef-123">Progettazione del provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e47ef-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)