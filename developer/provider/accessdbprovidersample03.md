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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081071"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="a1083-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="a1083-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="a1083-103">In questo esempio illustra come sovrascrivere i [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) i metodi per supportare le chiamate per il `Get-Item` e `Set-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1083-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="a1083-104">La classe provider in questo esempio deriva dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="a1083-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a1083-105">Di seguito viene illustrato</span><span class="sxs-lookup"><span data-stu-id="a1083-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a1083-106">Classe del provider verrà probabilmente derivare da una delle seguenti classi e possibilmente implementare altre interfacce del provider:</span><span class="sxs-lookup"><span data-stu-id="a1083-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="a1083-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="a1083-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="a1083-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="a1083-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="a1083-109">Visualizzare [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="a1083-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="a1083-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="a1083-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="a1083-111">Visualizzare [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="a1083-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="a1083-112">Per altre informazioni sulla scelta di quale classe provider derivano dal basato sulle funzionalità del provider, vedere [la progettazione del Provider di Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="a1083-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="a1083-113">In questo esempio viene illustrato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="a1083-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="a1083-114">La dichiarazione di `CmdletProvider` attributo.</span><span class="sxs-lookup"><span data-stu-id="a1083-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="a1083-115">Definizione di una classe di provider che deriva dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="a1083-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="a1083-116">Sovrascrivendo il [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) per modificare il comportamento del metodo di `New-PSDrive` cmdlet, che consente all'utente di creare nuove unità.</span><span class="sxs-lookup"><span data-stu-id="a1083-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="a1083-117">(In questo esempio non illustra come aggiungere parametri dinamici al `New-PSDrive` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="a1083-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="a1083-118">Sovrascrivendo il [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metodo per supportare la rimozione di unità esistente.</span><span class="sxs-lookup"><span data-stu-id="a1083-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="a1083-119">Sovrascrivendo il [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metodo per modificare il comportamento del `Get-Item` cmdlet, consentendo all'utente di recuperare gli elementi dall'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="a1083-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="a1083-120">(In questo esempio non illustra come aggiungere parametri dinamici al `Get-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="a1083-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="a1083-121">Sovrascrivendo il [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metodo per modificare il comportamento del `Set-Item` cmdlet, consentendo all'utente di aggiornare gli elementi nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="a1083-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="a1083-122">(In questo esempio non illustra come aggiungere parametri dinamici al `Get-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="a1083-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="a1083-123">Sovrascrivendo il [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) per modificare il comportamento del metodo di `Test-Path` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1083-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="a1083-124">(In questo esempio non illustra come aggiungere parametri dinamici al `Test-Path` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="a1083-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="a1083-125">Sovrascrivendo il [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metodo per determinare se il percorso specificato sia valido.</span><span class="sxs-lookup"><span data-stu-id="a1083-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="a1083-126">Esempio</span><span class="sxs-lookup"><span data-stu-id="a1083-126">Example</span></span>

<span data-ttu-id="a1083-127">In questo esempio mostra come sovrascrivere i metodi necessari per ottenere e impostare gli elementi in una data di Microsoft Access base.</span><span class="sxs-lookup"><span data-stu-id="a1083-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="a1083-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a1083-128">See Also</span></span>

[<span data-ttu-id="a1083-129">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a1083-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="a1083-130">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a1083-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="a1083-131">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a1083-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="a1083-132">Progettazione del Provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1083-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)