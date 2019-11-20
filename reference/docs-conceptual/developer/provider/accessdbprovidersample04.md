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
ms.openlocfilehash: 7096f8066568c214a5902f6943a2c093932d3b56
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366340"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="e64d3-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="e64d3-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="e64d3-103">Questo esempio illustra come sovrascrivere i metodi del contenitore per supportare le chiamate ai cmdlet `Copy-Item`, `Get-ChildItem`, `New-Item` e `Remove-Item`.</span><span class="sxs-lookup"><span data-stu-id="e64d3-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="e64d3-104">Questi metodi devono essere implementati quando l'archivio dati contiene elementi che sono contenitori.</span><span class="sxs-lookup"><span data-stu-id="e64d3-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="e64d3-105">Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune.</span><span class="sxs-lookup"><span data-stu-id="e64d3-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="e64d3-106">La classe del provider in questo esempio deriva dalla classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="e64d3-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e64d3-107">Dimostra</span><span class="sxs-lookup"><span data-stu-id="e64d3-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e64d3-108">È probabile che la classe del provider derivi da [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="e64d3-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="e64d3-109">In questo esempio vengono illustrate le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="e64d3-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="e64d3-110">Dichiarazione dell'attributo `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="e64d3-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="e64d3-111">Definizione di una classe di provider che deriva dalla classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="e64d3-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="e64d3-112">Sovrascrivere il metodo [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) per modificare il comportamento del cmdlet `Copy-Item`, che consente all'utente di copiare gli elementi da una posizione a un'altra.</span><span class="sxs-lookup"><span data-stu-id="e64d3-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="e64d3-113">In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="e64d3-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="e64d3-114">Sovrascrivere il metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) per modificare il comportamento del cmdlet Get-ChildItems, che consente all'utente di recuperare gli elementi figlio dell'elemento padre.</span><span class="sxs-lookup"><span data-stu-id="e64d3-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="e64d3-115">(Questo esempio non Mostra come aggiungere parametri dinamici al cmdlet Get-ChildItems).</span><span class="sxs-lookup"><span data-stu-id="e64d3-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="e64d3-116">Sovrascrivere il metodo [System. Management. Automation. provider. Containercmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) per modificare il comportamento del cmdlet Get-ChildItems quando viene specificato il parametro `Name` del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e64d3-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="e64d3-117">Sovrascrivere il metodo [System. Management. Automation. provider. Containercmdletprovider. NewItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) per modificare il comportamento del cmdlet `New-Item`, che consente all'utente di aggiungere elementi all'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="e64d3-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="e64d3-118">In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `New-Item`.</span><span class="sxs-lookup"><span data-stu-id="e64d3-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="e64d3-119">Sovrascrivere il metodo [System. Management. Automation. provider. Containercmdletprovider. RemoveItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) per modificare il comportamento del cmdlet `Remove-Item`.</span><span class="sxs-lookup"><span data-stu-id="e64d3-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="e64d3-120">In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Remove-Item`.</span><span class="sxs-lookup"><span data-stu-id="e64d3-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="e64d3-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="e64d3-121">Example</span></span>

<span data-ttu-id="e64d3-122">In questo esempio viene illustrato come sovrascrivere i metodi necessari per copiare, creare e rimuovere elementi, nonché metodi per ottenere gli elementi figlio di un elemento padre.</span><span class="sxs-lookup"><span data-stu-id="e64d3-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="e64d3-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e64d3-123">See Also</span></span>

[<span data-ttu-id="e64d3-124">System. Management. Automation. provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="e64d3-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="e64d3-125">System. Management. Automation. provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="e64d3-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="e64d3-126">System. Management. Automation. provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="e64d3-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="e64d3-127">Progettazione del provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e64d3-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)