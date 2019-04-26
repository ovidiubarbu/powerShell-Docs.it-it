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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081022"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="3fefa-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="3fefa-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="3fefa-103">Questo esempio illustra come sovrascrivere metodi contenitore per supportare le chiamate per il `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3fefa-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="3fefa-104">Questi metodi devono essere implementati quando l'archivio dati contiene elementi che sono contenitori.</span><span class="sxs-lookup"><span data-stu-id="3fefa-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="3fefa-105">Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune.</span><span class="sxs-lookup"><span data-stu-id="3fefa-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="3fefa-106">La classe provider in questo esempio deriva dal [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="3fefa-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3fefa-107">Di seguito viene illustrato</span><span class="sxs-lookup"><span data-stu-id="3fefa-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3fefa-108">Classe del provider molto probabilmente esegue la derivazione da di [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="3fefa-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="3fefa-109">In questo esempio viene illustrato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="3fefa-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="3fefa-110">La dichiarazione di `CmdletProvider` attributo.</span><span class="sxs-lookup"><span data-stu-id="3fefa-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="3fefa-111">Definizione di una classe di provider che deriva dal [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="3fefa-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="3fefa-112">Sovrascrivendo il [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metodo per modificare il comportamento del `Copy-Item` cmdlet che consente all'utente di copiare gli elementi da una posizione a un'altra.</span><span class="sxs-lookup"><span data-stu-id="3fefa-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="3fefa-113">(In questo esempio non illustra come aggiungere parametri dinamici al `Copy-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="3fefa-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="3fefa-114">Sovrascrivendo il [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metodo per modificare il comportamento del cmdlet Get-ChildItems, che consente all'utente di recuperare gli elementi figlio dell'elemento padre .</span><span class="sxs-lookup"><span data-stu-id="3fefa-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="3fefa-115">(In questo esempio mostra come aggiungere parametri dinamici per il cmdlet Get-ChildItems).</span><span class="sxs-lookup"><span data-stu-id="3fefa-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="3fefa-116">Sovrascrivendo il [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metodo per modificare il comportamento del cmdlet Get-ChildItems quando il `Name` parametro del cmdlet è specificato.</span><span class="sxs-lookup"><span data-stu-id="3fefa-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="3fefa-117">Sovrascrivendo il [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metodo per modificare il comportamento del `New-Item` cmdlet, che consente all'utente di aggiungere elementi all'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="3fefa-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="3fefa-118">(In questo esempio non illustra come aggiungere parametri dinamici al `New-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="3fefa-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="3fefa-119">Sovrascrivendo il [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) per modificare il comportamento del metodo di `Remove-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3fefa-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="3fefa-120">(In questo esempio non illustra come aggiungere parametri dinamici al `Remove-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="3fefa-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="3fefa-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="3fefa-121">Example</span></span>

<span data-ttu-id="3fefa-122">In questo esempio mostra come sovrascrivere i metodi necessari per copiare, creare e rimuovere elementi, nonché i metodi per il recupero di elementi di un elemento padre l'elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="3fefa-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="3fefa-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3fefa-123">See Also</span></span>

[<span data-ttu-id="3fefa-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="3fefa-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="3fefa-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="3fefa-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="3fefa-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="3fefa-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="3fefa-127">Progettazione del Provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3fefa-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)