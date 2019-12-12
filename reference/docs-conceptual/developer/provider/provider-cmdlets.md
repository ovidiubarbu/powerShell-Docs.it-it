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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359980"
---
# <a name="provider-cmdlets"></a>Cmdlet del provider

I cmdlet che l'utente può eseguire per gestire un archivio dati sono detti cmdlet del provider. Per supportare questi cmdlet, è necessario sovrascrivere alcuni dei metodi definiti dalle classi e dalle interfacce del provider di base.

## <a name="provider-cmdlets"></a>Cmdlet del provider

Ecco i cmdlet del provider che possono essere eseguiti dall'utente:

### <a name="psdrive-cmdlets"></a>Cmdlet PSDrive

- `Get-PSDrive`: questo cmdlet restituisce le unità di Windows PowerShell nella sessione corrente. Non è necessario sovrascrivere alcun metodo per supportare questo cmdlet.

- `New-PSDrive`: questo cmdlet consente all'utente di creare unità di Windows PowerShell per accedere all'archivio dati. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System. Management. Automation. provider. Drivecmdletprovider. Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

- `Remove-PSDrive`: questo cmdlet consente all'utente di rimuovere le unità di Windows PowerShell che accedono all'archivio dati. Per supportare questo cmdlet, sovrascrivere il metodo [System. Management. Automation. provider. Drivecmdletprovider. Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .

### <a name="item-cmdlets"></a>Cmdlet Item

- `Clear-Item`: questo cmdlet consente all'utente di rimuovere il valore di un elemento nell'archivio dati. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) e [System. Management. Automation. provider. Itemcmdletprovider. Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .

- `Copy-Item`: questo cmdlet consente all'utente di copiare un elemento da una posizione a un'altra. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Containercmdletprovider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) e [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

- `Get-Item`: questo cmdlet consente all'utente di recuperare i dati dall'archivio dati. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

- `Get-ChildItem`: questo cmdlet consente all'utente di recuperare gli elementi figlio dell'elemento padre. Per supportare questo cmdlet, sovrascrivere i metodi seguenti:

  - [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System. Management. Automation. provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System. Management. Automation. provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: questo cmdlet consente all'utente di eseguire l'azione predefinita specificata dall'elemento. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) e [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

- `Move-Item`: questo cmdlet consente all'utente di spostare un elemento da un percorso a un altro. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Navigationcmdletprovider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) e [System. Management. Automation. provider. Navigationcmdletprovider. Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s.

- `New-ItemProperty`: questo cmdlet consente all'utente di creare un nuovo elemento nell'archivio dati.

- `Remove-Item`: questo cmdlet consente all'utente di rimuovere elementi dall'archivio dati. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Containercmdletprovider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) e [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .

- `Rename-Item`: questo cmdlet consente all'utente di rinominare gli elementi nell'archivio dati. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Containercmdletprovider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) e [System. Management. Automation. provider. Containercmdletprovider. Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) .

- `Set-Item`: questo cmdlet consente all'utente di aggiornare i valori degli elementi nell'archivio dati. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) e [System. Management. Automation. provider. Itemcmdletprovider. Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) .

### <a name="item-content-cmdlets"></a>Cmdlet per contenuto elemento

- `Add-Content`: questo cmdlet consente all'utente di aggiungere contenuto a un elemento.

- `Clear-Content`: questo cmdlet consente all'utente di eliminare contenuto da un elemento senza eliminare l'elemento. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Icontentcmdletprovider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) e [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) .

- `Get-Content`: questo cmdlet consente all'utente di recuperare il contenuto di un elemento. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Icontentcmdletprovider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) e [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) . Il metodo [System. Management. Automation. provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) restituisce un'interfaccia [System. Management. Automation. provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) che definisce i metodi usati per leggere il contenuto.

- `Set-Content`: questo cmdlet consente all'utente di aggiornare il contenuto di un elemento. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) e [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) . Il metodo [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) restituisce un'interfaccia [System. Management. Automation. provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) che definisce i metodi usati per scrivere il contenuto.

### <a name="item-property-cmdlets"></a>Cmdlet della proprietà Item

- `Clear-ItemProperty`: questo cmdlet consente all'utente di eliminare il valore di una proprietà. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) e [System. Management. Automation. provider. Ipropertycmdletprovider. Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) .

- `Copy-ItemProperty`: questo cmdlet consente all'utente di copiare una proprietà e il relativo valore da una posizione a un'altra. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) e [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) .

- `Get-ItemProperty`: questo cmdlet recupera le proprietà di un elemento. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) e [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

- `Move-ItemProperty`: questo cmdlet consente all'utente di spostare una proprietà e il relativo valore da una posizione a un'altra. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) e [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) .

- `New-ItemProperty`: questo cmdlet consente all'utente di creare una nuova proprietà e di impostarne il valore. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Idynamicpropertycmdletprovider. newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) e [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) .

- `Remove-ItemProperty`: questo cmdlet consente all'utente di eliminare una proprietà e il relativo valore. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Idynamicpropertycmdletprovider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) e [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .

- `Rename-ItemProperty`: questo cmdlet consente all'utente di modificare il nome di una proprietà. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) e [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) .

- `Set-ItemProperty`: questo cmdlet consente all'utente di aggiornare le proprietà di un elemento. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) e [System. Management. Automation. provider. Ipropertycmdletprovider. Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

### <a name="location-cmdlets"></a>Cmdlet Location

- `Get-Location`: recupera le informazioni sul percorso di lavoro corrente. Non è necessario sovrascrivere alcun metodo per supportare questo cmdlet.

- `Pop-Location`: questo cmdlet imposta il percorso corrente sul percorso di cui è stato effettuato il push più di recente nello stack. Non è necessario sovrascrivere alcun metodo per supportare questo cmdlet.

- `Push-Location`: questo cmdlet aggiunge il percorso corrente all'inizio di un elenco di percorsi (uno "stack"). Non è necessario sovrascrivere alcun metodo per supportare questo cmdlet.

- `Set-Location`: questo cmdlet imposta il percorso di lavoro corrente su un percorso specificato. Non è necessario sovrascrivere alcun metodo per supportare questo cmdlet.

### <a name="path-cmdlets"></a>Cmdlet Path

- `Join-Path`: questo cmdlet consente all'utente di combinare un segmento di percorso padre e figlio per creare un percorso interno del provider. Per supportare questo cmdlet, sovrascrivere il metodo [System. Management. Automation. provider. Navigationcmdletprovider. makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .

- `Convert-Path`: questo cmdlet converte un percorso da un percorso di Windows PowerShell a un percorso del provider di Windows PowerShell.

- `Split-Path`: restituisce la parte specificata di un percorso.

- `Resolve-Path`: risolve i caratteri jolly in un percorso e visualizza il contenuto del percorso.

- `Test-Path`: questo cmdlet determina se sono presenti tutti gli elementi di un percorso. Per supportare questo cmdlet, sovrascrivere i metodi [System. Management. Automation. provider. Itemcmdletprovider. itemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) e [System. Management. Automation. provider. Itemcmdletprovider. Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) .

### <a name="psprovider-cmdlets"></a>Cmdlet PSProvider

- `Get-PSProvider`: questo cmdlet restituisce informazioni sui provider disponibili nella sessione. Non è necessario sovrascrivere alcun metodo per supportare questo cmdlet.