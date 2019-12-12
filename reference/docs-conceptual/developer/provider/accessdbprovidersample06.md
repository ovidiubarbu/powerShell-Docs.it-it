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
# <a name="accessdbprovidersample06"></a><span data-ttu-id="fe781-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="fe781-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="fe781-103">Questo esempio illustra come sovrascrivere i metodi di contenuto per supportare le chiamate ai cmdlet `Clear-Content`, `Get-Content`e `Set-Content`.</span><span class="sxs-lookup"><span data-stu-id="fe781-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="fe781-104">Questi metodi devono essere implementati quando l'utente deve gestire il contenuto degli elementi nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="fe781-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="fe781-105">La classe del provider in questo esempio deriva dalla classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) e implementa l'interfaccia [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="fe781-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="fe781-106">Illustra</span><span class="sxs-lookup"><span data-stu-id="fe781-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fe781-107">È probabile che la classe del provider derivi da una delle classi seguenti e possa implementare altre interfacce del provider:</span><span class="sxs-lookup"><span data-stu-id="fe781-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="fe781-108">Classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="fe781-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="fe781-109">Vedere [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="fe781-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="fe781-110">Classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="fe781-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="fe781-111">Vedere [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="fe781-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="fe781-112">Classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="fe781-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="fe781-113">Per ulteriori informazioni sulla scelta della classe del provider da derivare da in base alle funzionalità del provider, vedere [progettazione del provider di Windows PowerShell](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="fe781-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="fe781-114">In questo esempio viene illustrato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="fe781-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="fe781-115">Dichiarazione dell'attributo `CmdletProvider`.</span><span class="sxs-lookup"><span data-stu-id="fe781-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="fe781-116">Definizione di una classe di provider che deriva dalla classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) e che dichiara l'interfaccia [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="fe781-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="fe781-117">Sovrascrivere il metodo [System. Management. Automation. provider. Icontentcmdletprovider. ClearContent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) per modificare il comportamento del cmdlet `Clear-Content`, consentendo all'utente di rimuovere il contenuto da un elemento.</span><span class="sxs-lookup"><span data-stu-id="fe781-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="fe781-118">In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Clear-Content`.</span><span class="sxs-lookup"><span data-stu-id="fe781-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="fe781-119">Sovrascrivere il metodo [System. Management. Automation. provider. Icontentcmdletprovider. GetContentReader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) per modificare il comportamento del cmdlet `Get-Content`, consentendo all'utente di recuperare il contenuto di un elemento.</span><span class="sxs-lookup"><span data-stu-id="fe781-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="fe781-120">In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Get-Content`.</span><span class="sxs-lookup"><span data-stu-id="fe781-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="fe781-121">Sovrascrivere il metodo [Microsoft. PowerShell. Commands. FileSystemProvider. Getcontentwriter \*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) per modificare il comportamento del cmdlet `Set-Content`, consentendo all'utente di aggiornare il contenuto di un elemento.</span><span class="sxs-lookup"><span data-stu-id="fe781-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="fe781-122">In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `Set-Content`.</span><span class="sxs-lookup"><span data-stu-id="fe781-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="fe781-123">Esempio</span><span class="sxs-lookup"><span data-stu-id="fe781-123">Example</span></span>

<span data-ttu-id="fe781-124">Questo esempio illustra come sovrascrivere i metodi necessari per cancellare, ottenere e impostare il contenuto di elementi in un database di Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="fe781-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="fe781-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fe781-125">See Also</span></span>

[<span data-ttu-id="fe781-126">System. Management. Automation. provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="fe781-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="fe781-127">System. Management. Automation. provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="fe781-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="fe781-128">System. Management. Automation. provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="fe781-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="fe781-129">Progettazione del provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe781-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
