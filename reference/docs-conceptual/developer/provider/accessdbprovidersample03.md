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
ms.openlocfilehash: aa67bb605f90c1ea40323b4583766069ff1226fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359990"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="9a4df-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="9a4df-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="9a4df-103">Questo esempio illustra come sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System. Management. Automation. provider. Itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) per supportare le chiamate ai cmdlet `Get-Item` e `Set-Item`.</span><span class="sxs-lookup"><span data-stu-id="9a4df-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="9a4df-104">La classe del provider in questo esempio deriva dalla classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="9a4df-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9a4df-105">Illustra</span><span class="sxs-lookup"><span data-stu-id="9a4df-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a4df-106">È probabile che la classe del provider derivi da una delle classi seguenti e possa implementare altre interfacce del provider:</span><span class="sxs-lookup"><span data-stu-id="9a4df-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="9a4df-107">Classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="9a4df-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="9a4df-108">Classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="9a4df-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="9a4df-109">Vedere [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="9a4df-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="9a4df-110">Classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="9a4df-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="9a4df-111">Vedere [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="9a4df-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="9a4df-112">Per ulteriori informazioni sulla scelta della classe del provider da derivare da in base alle funzionalità del provider, vedere [progettazione del provider di Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="9a4df-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="9a4df-113">In questo esempio viene illustrato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="9a4df-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="9a4df-114">Dichiarazione dell'attributo `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="9a4df-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="9a4df-115">Definizione di una classe di provider che deriva dalla classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="9a4df-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="9a4df-116">Sovrascrivere il metodo [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) per modificare il comportamento del cmdlet `New-PSDrive`, consentendo all'utente di creare nuove unità.</span><span class="sxs-lookup"><span data-stu-id="9a4df-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="9a4df-117">In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `New-PSDrive`.</span><span class="sxs-lookup"><span data-stu-id="9a4df-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="9a4df-118">Sovrascrivere il metodo [System. Management. Automation. provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) per supportare la rimozione delle unità esistenti.</span><span class="sxs-lookup"><span data-stu-id="9a4df-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="9a4df-119">Sovrascrivere il metodo [System. Management. Automation. provider. Itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) per modificare il comportamento del cmdlet `Get-Item`, consentendo all'utente di recuperare elementi dall'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="9a4df-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="9a4df-120">In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="9a4df-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="9a4df-121">Sovrascrivere il metodo [System. Management. Automation. provider. Itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) per modificare il comportamento del cmdlet `Set-Item`, consentendo all'utente di aggiornare gli elementi nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="9a4df-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="9a4df-122">In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="9a4df-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="9a4df-123">Sovrascrivere il metodo [System. Management. Automation. provider. Itemcmdletprovider. itemExists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) per modificare il comportamento del cmdlet `Test-Path`.</span><span class="sxs-lookup"><span data-stu-id="9a4df-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="9a4df-124">In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Test-Path`.</span><span class="sxs-lookup"><span data-stu-id="9a4df-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="9a4df-125">Sovrascrivere il metodo [System. Management. Automation. provider. Itemcmdletprovider. IsValidPath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) per determinare se il percorso specificato è valido.</span><span class="sxs-lookup"><span data-stu-id="9a4df-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="9a4df-126">Esempio</span><span class="sxs-lookup"><span data-stu-id="9a4df-126">Example</span></span>

<span data-ttu-id="9a4df-127">In questo esempio viene illustrato come sovrascrivere i metodi necessari per ottenere e impostare elementi in un database di Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="9a4df-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="9a4df-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9a4df-128">See Also</span></span>

[<span data-ttu-id="9a4df-129">System. Management. Automation. provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="9a4df-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="9a4df-130">System. Management. Automation. provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="9a4df-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="9a4df-131">System. Management. Automation. provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="9a4df-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="9a4df-132">Progettazione del provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a4df-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
