---
title: Cmdlet del provider | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359980"
---
# <a name="provider-cmdlets"></a><span data-ttu-id="865c2-102">Cmdlet del provider</span><span class="sxs-lookup"><span data-stu-id="865c2-102">Provider cmdlets</span></span>

<span data-ttu-id="865c2-103">I cmdlet che l'utente può eseguire per gestire un archivio dati sono detti cmdlet del provider.</span><span class="sxs-lookup"><span data-stu-id="865c2-103">The cmdlets that the user can run to manage a data store are referred to as provider cmdlets.</span></span> <span data-ttu-id="865c2-104">Per supportare questi cmdlet, è necessario sovrascrivere alcuni dei metodi definiti dalle classi e dalle interfacce del provider di base.</span><span class="sxs-lookup"><span data-stu-id="865c2-104">To support these cmdlets, you need to overwrite some of the methods defined by the base provider classes and interfaces.</span></span>

## <a name="provider-cmdlets"></a><span data-ttu-id="865c2-105">Cmdlet del provider</span><span class="sxs-lookup"><span data-stu-id="865c2-105">Provider Cmdlets</span></span>

<span data-ttu-id="865c2-106">Ecco i cmdlet del provider che possono essere eseguiti dall'utente:</span><span class="sxs-lookup"><span data-stu-id="865c2-106">Here are the provider cmdlets that can be run by the user:</span></span>

### <a name="psdrive-cmdlets"></a><span data-ttu-id="865c2-107">Cmdlet PSDrive</span><span class="sxs-lookup"><span data-stu-id="865c2-107">PSDrive cmdlets</span></span>

- <span data-ttu-id="865c2-108">`Get-PSDrive`: questo cmdlet restituisce le unità di Windows PowerShell nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="865c2-108">`Get-PSDrive`: This cmdlet returns the Windows PowerShell drives in the current session.</span></span> <span data-ttu-id="865c2-109">Non è necessario sovrascrivere alcun metodo per supportare questo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="865c2-109">You do not need to overwrite any methods to support this cmdlet.</span></span>

- <span data-ttu-id="865c2-110">`New-PSDrive`: questo cmdlet consente all'utente di creare unità di Windows PowerShell per accedere all'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="865c2-110">`New-PSDrive`: This cmdlet allows the user to create Windows PowerShell drives to access the data store.</span></span> <span data-ttu-id="865c2-111">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System. Management. Automation. provider. Drivecmdletprovider. Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-111">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-112">`Remove-PSDrive`: questo cmdlet consente all'utente di rimuovere le unità di Windows PowerShell che accedono all'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="865c2-112">`Remove-PSDrive`: This cmdlet allows the user to remove Windows PowerShell drives that access the data store.</span></span> <span data-ttu-id="865c2-113">Per supportare questo cmdlet, sovrascrivere il metodo [System. Management. Automation. provider. Drivecmdletprovider. Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .</span><span class="sxs-lookup"><span data-stu-id="865c2-113">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span>

### <a name="item-cmdlets"></a><span data-ttu-id="865c2-114">Cmdlet Item</span><span class="sxs-lookup"><span data-stu-id="865c2-114">Item cmdlets</span></span>

- <span data-ttu-id="865c2-115">`Clear-Item`: questo cmdlet consente all'utente di rimuovere il valore di un elemento nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="865c2-115">`Clear-Item`: This cmdlet allows the user to remove the value of an item in the data store.</span></span> <span data-ttu-id="865c2-116">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) e [System. Management. Automation. provider. Itemcmdletprovider. Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-116">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-117">`Copy-Item`: questo cmdlet consente all'utente di copiare un elemento da una posizione a un'altra.</span><span class="sxs-lookup"><span data-stu-id="865c2-117">`Copy-Item`: This cmdlet allows the user to copy an item from one location to another.</span></span> <span data-ttu-id="865c2-118">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) e [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-118">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) and [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-119">`Get-Item`: questo cmdlet consente all'utente di recuperare i dati dall'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="865c2-119">`Get-Item`: This cmdlet allows the user to retrieve data from the data store.</span></span> <span data-ttu-id="865c2-120">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-120">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-121">`Get-ChildItem`: questo cmdlet consente all'utente di recuperare gli elementi figlio dell'elemento padre.</span><span class="sxs-lookup"><span data-stu-id="865c2-121">`Get-ChildItem`: This cmdlet allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="865c2-122">Per supportare questo cmdlet, sovrascrivere i metodi seguenti:</span><span class="sxs-lookup"><span data-stu-id="865c2-122">To support this cmdlet, overwrite the following methods:</span></span>

  - [<span data-ttu-id="865c2-123">System. Management. Automation. provider. Containercmdletprovider. getchilditems \*</span><span class="sxs-lookup"><span data-stu-id="865c2-123">System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [<span data-ttu-id="865c2-124">System. Management. Automation. provider. Containercmdletprovider. Getchilditemsdynamicparameters \*</span><span class="sxs-lookup"><span data-stu-id="865c2-124">System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [<span data-ttu-id="865c2-125">System. Management. Automation. provider. Containercmdletprovider. Getchildnames \*</span><span class="sxs-lookup"><span data-stu-id="865c2-125">System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [<span data-ttu-id="865c2-126">System. Management. Automation. provider. Containercmdletprovider. Getchildnamesdynamicparameters \*</span><span class="sxs-lookup"><span data-stu-id="865c2-126">System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- <span data-ttu-id="865c2-127">`Invoke-Item`: questo cmdlet consente all'utente di eseguire l'azione predefinita specificata dall'elemento.</span><span class="sxs-lookup"><span data-stu-id="865c2-127">`Invoke-Item`: This cmdlet allows the user to perform the default action specified by the item.</span></span> <span data-ttu-id="865c2-128">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) e [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .</span><span class="sxs-lookup"><span data-stu-id="865c2-128">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) and [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) methods.</span></span>

- <span data-ttu-id="865c2-129">`Move-Item`: questo cmdlet consente all'utente di spostare un elemento da un percorso a un altro.</span><span class="sxs-lookup"><span data-stu-id="865c2-129">`Move-Item`: This cmdlet allows the user to move an item from one location to another location.</span></span> <span data-ttu-id="865c2-130">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Navigationcmdletprovider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) e [System. Management. Automation. provider. Navigationcmdletprovider. Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s.</span><span class="sxs-lookup"><span data-stu-id="865c2-130">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) and [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s methods.</span></span>

- <span data-ttu-id="865c2-131">`New-ItemProperty`: questo cmdlet consente all'utente di creare un nuovo elemento nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="865c2-131">`New-ItemProperty`: This cmdlet allows the user to create a new item in the data store.</span></span>

- <span data-ttu-id="865c2-132">`Remove-Item`: questo cmdlet consente all'utente di rimuovere elementi dall'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="865c2-132">`Remove-Item`: This cmdlet allows the user to remove items from the data store.</span></span> <span data-ttu-id="865c2-133">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Containercmdletprovider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) e [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-133">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) and [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-134">`Rename-Item`: questo cmdlet consente all'utente di rinominare gli elementi nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="865c2-134">`Rename-Item`: This cmdlet allows the user to rename items in the data store.</span></span> <span data-ttu-id="865c2-135">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Containercmdletprovider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) e [System. Management. Automation. provider. Containercmdletprovider. Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-135">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) and [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-136">`Set-Item`: questo cmdlet consente all'utente di aggiornare i valori degli elementi nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="865c2-136">`Set-Item`: This cmdlet allows the user to update the values of items in the data store.</span></span> <span data-ttu-id="865c2-137">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) e [System. Management. Automation. provider. Itemcmdletprovider. Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-137">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) methods.</span></span>

### <a name="item-content-cmdlets"></a><span data-ttu-id="865c2-138">Cmdlet per contenuto elemento</span><span class="sxs-lookup"><span data-stu-id="865c2-138">Item content cmdlets</span></span>

- <span data-ttu-id="865c2-139">`Add-Content`: questo cmdlet consente all'utente di aggiungere contenuto a un elemento.</span><span class="sxs-lookup"><span data-stu-id="865c2-139">`Add-Content`: This cmdlet allows the user to add content to an item.</span></span>

- <span data-ttu-id="865c2-140">`Clear-Content`: questo cmdlet consente all'utente di eliminare contenuto da un elemento senza eliminare l'elemento.</span><span class="sxs-lookup"><span data-stu-id="865c2-140">`Clear-Content`: This cmdlet allows the user to delete content from an item without deleting the item.</span></span> <span data-ttu-id="865c2-141">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Icontentcmdletprovider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) e [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-141">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) and [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-142">`Get-Content`: questo cmdlet consente all'utente di recuperare il contenuto di un elemento.</span><span class="sxs-lookup"><span data-stu-id="865c2-142">`Get-Content`: This cmdlet allows the user to retrieve the content of an item.</span></span> <span data-ttu-id="865c2-143">Per supportare questo cmdlet, sovrascrivere [System. Management. Automation. provider. Icontentcmdletprovider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) e [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) Metodi.</span><span class="sxs-lookup"><span data-stu-id="865c2-143">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) and [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) methods.</span></span> <span data-ttu-id="865c2-144">Il metodo [System. Management. Automation. provider. Icontentcmdletprovider. GetContentReader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) restituisce un'interfaccia [System. Management. Automation. provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) che definisce i metodi usati per leggere il contenuto.</span><span class="sxs-lookup"><span data-stu-id="865c2-144">The [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method returns an [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interface that defines the methods used to read the content.</span></span>

- <span data-ttu-id="865c2-145">`Set-Content`: questo cmdlet consente all'utente di aggiornare il contenuto di un elemento.</span><span class="sxs-lookup"><span data-stu-id="865c2-145">`Set-Content`: This cmdlet allows the user to update the content of an item.</span></span> <span data-ttu-id="865c2-146">Per supportare questo cmdlet, sovrascrivere [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) e [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) Metodi.</span><span class="sxs-lookup"><span data-stu-id="865c2-146">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) and [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) methods.</span></span> <span data-ttu-id="865c2-147">Il metodo [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) restituisce un'interfaccia [System. Management. Automation. provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) che definisce i metodi usati per scrivere il contenuto.</span><span class="sxs-lookup"><span data-stu-id="865c2-147">The [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) method returns an [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interface that defines the methods used to write the content.</span></span>

### <a name="item-property-cmdlets"></a><span data-ttu-id="865c2-148">Cmdlet della proprietà Item</span><span class="sxs-lookup"><span data-stu-id="865c2-148">Item property cmdlets</span></span>

- <span data-ttu-id="865c2-149">`Clear-ItemProperty`: questo cmdlet consente all'utente di eliminare il valore di una proprietà.</span><span class="sxs-lookup"><span data-stu-id="865c2-149">`Clear-ItemProperty`: This cmdlet allows the user to delete the value of a property.</span></span> <span data-ttu-id="865c2-150">Per supportare questo cmdlet, sovrascrivere [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) e [System. Management. Automation. provider. Ipropertycmdletprovider. Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) Metodi.</span><span class="sxs-lookup"><span data-stu-id="865c2-150">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) and [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-151">`Copy-ItemProperty`: questo cmdlet consente all'utente di copiare una proprietà e il relativo valore da una posizione a un'altra.</span><span class="sxs-lookup"><span data-stu-id="865c2-151">`Copy-ItemProperty`: This cmdlet allows the user to copy a property and its value from one location to another.</span></span> <span data-ttu-id="865c2-152">Per supportare questo cmdlet, sovrascrivere [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) e [ Metodi System. Management. Automation. provider. Idynamicpropertycmdletprovider. Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-152">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) and [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-153">`Get-ItemProperty`: questo cmdlet recupera le proprietà di un elemento.</span><span class="sxs-lookup"><span data-stu-id="865c2-153">`Get-ItemProperty`: This cmdlet retrieves the properties of an item.</span></span> <span data-ttu-id="865c2-154">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) e [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-154">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) and [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-155">`Move-ItemProperty`: questo cmdlet consente all'utente di spostare una proprietà e il relativo valore da una posizione a un'altra.</span><span class="sxs-lookup"><span data-stu-id="865c2-155">`Move-ItemProperty`: This cmdlet allows the user to move a property and its value from one location to another.</span></span> <span data-ttu-id="865c2-156">Per supportare questo cmdlet, sovrascrivere [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) e [ Metodi System. Management. Automation. provider. Idynamicpropertycmdletprovider. Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-156">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) and [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-157">`New-ItemProperty`: questo cmdlet consente all'utente di creare una nuova proprietà e di impostarne il valore.</span><span class="sxs-lookup"><span data-stu-id="865c2-157">`New-ItemProperty`: This cmdlet allows the user to create a new property and set its value.</span></span> <span data-ttu-id="865c2-158">Per supportare questo cmdlet, sovrascrivere [System. Management. Automation. provider. Idynamicpropertycmdletprovider. newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) e [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)metodi.</span><span class="sxs-lookup"><span data-stu-id="865c2-158">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) and [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-159">`Remove-ItemProperty`: questo cmdlet consente all'utente di eliminare una proprietà e il relativo valore.</span><span class="sxs-lookup"><span data-stu-id="865c2-159">`Remove-ItemProperty`: This cmdlet allows the user to delete a property and its value.</span></span> <span data-ttu-id="865c2-160">Per supportare questo cmdlet, sovrascrivere [System. Management. Automation. provider. Idynamicpropertycmdletprovider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) e [ Metodi System. Management. Automation. provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-160">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) and [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-161">`Rename-ItemProperty`: questo cmdlet consente all'utente di modificare il nome di una proprietà.</span><span class="sxs-lookup"><span data-stu-id="865c2-161">`Rename-ItemProperty`: This cmdlet allows the user to change the name of a property.</span></span> <span data-ttu-id="865c2-162">Per supportare questo cmdlet, sovrascrivere [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) e [ Metodi System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-162">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) and [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) methods.</span></span>

- <span data-ttu-id="865c2-163">`Set-ItemProperty`: questo cmdlet consente all'utente di aggiornare le proprietà di un elemento.</span><span class="sxs-lookup"><span data-stu-id="865c2-163">`Set-ItemProperty`: This cmdlet allows the user to update the properties of an item.</span></span> <span data-ttu-id="865c2-164">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) e [System. Management. Automation. provider. Ipropertycmdletprovider. Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-164">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) and [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) methods.</span></span>

### <a name="location-cmdlets"></a><span data-ttu-id="865c2-165">Cmdlet Location</span><span class="sxs-lookup"><span data-stu-id="865c2-165">Location cmdlets</span></span>

- <span data-ttu-id="865c2-166">`Get-Location`: recupera le informazioni sul percorso di lavoro corrente.</span><span class="sxs-lookup"><span data-stu-id="865c2-166">`Get-Location`: Retrieves information about the current working location.</span></span> <span data-ttu-id="865c2-167">Non è necessario sovrascrivere alcun metodo per supportare questo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="865c2-167">You do not need to overwrite any methods to support this cmdlet.</span></span>

- <span data-ttu-id="865c2-168">`Pop-Location`: questo cmdlet imposta il percorso corrente sul percorso di cui è stato effettuato il push più di recente nello stack.</span><span class="sxs-lookup"><span data-stu-id="865c2-168">`Pop-Location`: This cmdlet changes the current location to the location most recently pushed onto the stack.</span></span> <span data-ttu-id="865c2-169">Non è necessario sovrascrivere alcun metodo per supportare questo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="865c2-169">You do not need to overwrite any methods to support this cmdlet.</span></span>

- <span data-ttu-id="865c2-170">`Push-Location`: questo cmdlet aggiunge il percorso corrente all'inizio di un elenco di percorsi (uno "stack").</span><span class="sxs-lookup"><span data-stu-id="865c2-170">`Push-Location`: This cmdlet adds the current location to the top of a list of locations (a "stack").</span></span> <span data-ttu-id="865c2-171">Non è necessario sovrascrivere alcun metodo per supportare questo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="865c2-171">You do not need to overwrite any methods to support this cmdlet.</span></span>

- <span data-ttu-id="865c2-172">`Set-Location`: questo cmdlet imposta il percorso di lavoro corrente su un percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="865c2-172">`Set-Location`: This cmdlet sets the current working location to a specified location.</span></span> <span data-ttu-id="865c2-173">Non è necessario sovrascrivere alcun metodo per supportare questo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="865c2-173">You do not need to overwrite any methods to support this cmdlet.</span></span>

### <a name="path-cmdlets"></a><span data-ttu-id="865c2-174">Cmdlet Path</span><span class="sxs-lookup"><span data-stu-id="865c2-174">Path cmdlets</span></span>

- <span data-ttu-id="865c2-175">`Join-Path`: questo cmdlet consente all'utente di combinare un segmento di percorso padre e figlio per creare un percorso interno del provider.</span><span class="sxs-lookup"><span data-stu-id="865c2-175">`Join-Path`: This cmdlet allows the user to combine a parent and child path segment to create a provider-internal path.</span></span> <span data-ttu-id="865c2-176">Per supportare questo cmdlet, sovrascrivere il metodo [System. Management. Automation. provider. Navigationcmdletprovider. makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .</span><span class="sxs-lookup"><span data-stu-id="865c2-176">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method.</span></span>

- <span data-ttu-id="865c2-177">`Convert-Path`: questo cmdlet converte un percorso da un percorso di Windows PowerShell a un percorso del provider di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="865c2-177">`Convert-Path`: This cmdlet converts a path from a Windows PowerShell path to a Windows PowerShell provider path.</span></span>

- <span data-ttu-id="865c2-178">`Split-Path`: restituisce la parte specificata di un percorso.</span><span class="sxs-lookup"><span data-stu-id="865c2-178">`Split-Path`: Returns the specified part of a path.</span></span>

- <span data-ttu-id="865c2-179">`Resolve-Path`: risolve i caratteri jolly in un percorso e visualizza il contenuto del percorso.</span><span class="sxs-lookup"><span data-stu-id="865c2-179">`Resolve-Path`: Resolves the wildcard characters in a path, and displays the path contents.</span></span>

- <span data-ttu-id="865c2-180">`Test-Path`: questo cmdlet determina se sono presenti tutti gli elementi di un percorso.</span><span class="sxs-lookup"><span data-stu-id="865c2-180">`Test-Path`: This cmdlet determines whether all elements of a path exist.</span></span> <span data-ttu-id="865c2-181">Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. itemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) e [System. Management. Automation. provider. Itemcmdletprovider. Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="865c2-181">To support this cmdlet, overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) and [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) methods.</span></span>

### <a name="psprovider-cmdlets"></a><span data-ttu-id="865c2-182">Cmdlet PSProvider</span><span class="sxs-lookup"><span data-stu-id="865c2-182">PSProvider cmdlets</span></span>

- <span data-ttu-id="865c2-183">`Get-PSProvider`: questo cmdlet restituisce informazioni sui provider disponibili nella sessione.</span><span class="sxs-lookup"><span data-stu-id="865c2-183">`Get-PSProvider`: This cmdlet returns information about the providers available in the session.</span></span> <span data-ttu-id="865c2-184">Non è necessario sovrascrivere alcun metodo per supportare questo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="865c2-184">You do not need to overwrite any methods to support this cmdlet.</span></span>