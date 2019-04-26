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
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080986"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="45ce4-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="45ce4-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="45ce4-103">Questo esempio illustra come sovrascrivere i metodi per supportare le chiamate per il `Clear-Content`, `Get-Content`, e `Set-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45ce4-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="45ce4-104">Questi metodi devono essere implementati quando l'utente deve gestire il contenuto degli elementi nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="45ce4-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="45ce4-105">La classe provider in questo esempio deriva dal [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe che implementa il [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="45ce4-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="45ce4-106">Di seguito viene illustrato</span><span class="sxs-lookup"><span data-stu-id="45ce4-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45ce4-107">Classe del provider verrà probabilmente derivare da una delle seguenti classi e possibilmente implementare altre interfacce del provider:</span><span class="sxs-lookup"><span data-stu-id="45ce4-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="45ce4-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="45ce4-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="45ce4-109">Visualizzare [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="45ce4-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="45ce4-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="45ce4-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="45ce4-111">Visualizzare [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="45ce4-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="45ce4-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="45ce4-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="45ce4-113">Per altre informazioni sulla scelta di quale classe provider derivano dal basato sulle funzionalità del provider, vedere [la progettazione del Provider di Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="45ce4-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="45ce4-114">In questo esempio viene illustrato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="45ce4-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="45ce4-115">La dichiarazione di `CmdletProvider` attributo.</span><span class="sxs-lookup"><span data-stu-id="45ce4-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="45ce4-116">Definizione di una classe di provider che deriva dal [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe e che dichiara il [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="45ce4-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="45ce4-117">Sovrascrivendo il [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metodo per modificare il comportamento del `Clear-Content` cmdlet, consentendo all'utente di rimuovere il contenuto da un elemento.</span><span class="sxs-lookup"><span data-stu-id="45ce4-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="45ce4-118">(In questo esempio non illustra come aggiungere parametri dinamici al `Clear-Content` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="45ce4-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="45ce4-119">Sovrascrivendo il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) per modificare il comportamento del metodo di `Get-Content` cmdlet, consentendo all'utente di recuperare il contenuto di un elemento.</span><span class="sxs-lookup"><span data-stu-id="45ce4-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="45ce4-120">(In questo esempio non illustra come aggiungere parametri dinamici al `Get-Content` cmdlet.).</span><span class="sxs-lookup"><span data-stu-id="45ce4-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="45ce4-121">Sovrascrivendo il [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) per modificare il comportamento del metodo di `Set-Content` cmdlet, consentendo all'utente di aggiornare il contenuto di un elemento.</span><span class="sxs-lookup"><span data-stu-id="45ce4-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="45ce4-122">(In questo esempio non illustra come aggiungere parametri dinamici al `Set-Content` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="45ce4-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="45ce4-123">Esempio</span><span class="sxs-lookup"><span data-stu-id="45ce4-123">Example</span></span>

<span data-ttu-id="45ce4-124">In questo esempio mostra come sovrascrivere i metodi necessari per cancellare, ottenere e impostare il contenuto degli elementi in una data di Microsoft Access base.</span><span class="sxs-lookup"><span data-stu-id="45ce4-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="45ce4-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="45ce4-125">See Also</span></span>

[<span data-ttu-id="45ce4-126">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="45ce4-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="45ce4-127">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="45ce4-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="45ce4-128">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="45ce4-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="45ce4-129">Progettazione del Provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="45ce4-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)