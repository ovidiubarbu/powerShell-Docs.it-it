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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854767"
---
# <a name="provider-cmdlets"></a>Cmdlet del provider

I cmdlet che l'utente può eseguire per gestire un archivio dati sono detti cmdlet del provider. Per supportare questi cmdlet, è necessario sovrascrivere alcuni dei metodi definiti da classi di provider di base e interfacce.

## <a name="provider-cmdlets"></a>Cmdlet del provider

Ecco i cmdlet del provider che possono essere eseguiti dall'utente:

### <a name="psdrive-cmdlets"></a>Cmdlet PSDrive

- `Get-PSDrive`: Questo cmdlet restituisce che le unità Windows PowerShell nella sessione corrente. Non è necessaria sovrascrivere i metodi per supportare questo cmdlet.

- `New-PSDrive`: Questo cmdlet consente all'utente di creare unità di Windows PowerShell per accedere all'archivio dati. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metodi.

- `Remove-PSDrive`: Questo cmdlet consente all'utente di rimuovere le unità Windows PowerShell accedono all'archivio dati. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) (metodo).

### <a name="item-cmdlets"></a>Cmdlet Item

- `Clear-Item`: Questo cmdlet consente all'utente di rimuovere il valore di un elemento nell'archivio dati. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) e [ System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) metodi.

- `Copy-Item`: Questo cmdlet consente all'utente di copiare un elemento da una posizione a un'altra. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) e [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) metodi.

- `Get-Item`: Questo cmdlet consente all'utente di recuperare dati dall'archivio dati. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metodi.

- `Get-ChildItem`: Questo cmdlet consente all'utente di recuperare gli elementi figlio dell'elemento padre. Per supportare questo cmdlet, sovrascrivere i metodi seguenti:

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: Questo cmdlet consente all'utente di eseguire l'azione predefinita specificata dall'elemento. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) e [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) metodi.

- `Move-Item`: Questo cmdlet consente all'utente di spostare un elemento da una posizione a un'altra posizione. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) e [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)metodi s.

- `New-ItemProperty`: Questo cmdlet consente all'utente di creare un nuovo elemento nell'archivio dati.

- `Remove-Item`: Questo cmdlet consente all'utente di rimuovere elementi dall'archivio dati. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) e [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) metodi.

- `Rename-Item`: Questo cmdlet consente di rinominare gli elementi nell'archivio dati. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) e [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) metodi.

- `Set-Item`: Questo cmdlet consente all'utente di aggiornare i valori degli elementi nell'archivio dati. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) metodi.

### <a name="item-content-cmdlets"></a>Cmdlet di contenuto Item

- `Add-Content`: Questo cmdlet consente all'utente di aggiungere contenuto a un elemento.

- `Clear-Content`: Questo cmdlet consente all'utente di eliminare il contenuto da un elemento senza eliminare l'elemento. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) e [ System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) metodi.

- `Get-Content`: Questo cmdlet consente all'utente di recuperare il contenuto di un elemento. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) e [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) metodi. Il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metodo restituisce un' [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interfaccia che definisce i metodi utilizzati per leggere il contenuto.

- `Set-Content`: Questo cmdlet consente all'utente di aggiornare il contenuto di un elemento. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) e [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) metodi. Il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) metodo restituisce un' [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interfaccia che definisce i metodi utilizzati per scrivere il contenuto.

### <a name="item-property-cmdlets"></a>Cmdlet di proprietà Item

- `Clear-ItemProperty`: Questo cmdlet consente all'utente di eliminare il valore di una proprietà. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) e [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) metodi.

- `Copy-ItemProperty`: Questo cmdlet consente all'utente di copiare una proprietà e il relativo valore da una posizione a un'altra. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) metodi.

- `Get-ItemProperty`: Questo cmdlet recupera le proprietà di un elemento. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) e [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) metodi.

- `Move-ItemProperty`: Questo cmdlet consente all'utente di spostare una proprietà e il relativo valore da una posizione a un'altra. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) metodi.

- `New-ItemProperty`: Questo cmdlet consente all'utente di creare una nuova proprietà e impostarne il valore. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) metodi.

- `Remove-ItemProperty`: Questo cmdlet consente all'utente di eliminare una proprietà e il relativo valore. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) metodi.

- `Rename-ItemProperty`: Questo cmdlet consente all'utente di modificare il nome di una proprietà. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) metodi.

- `Set-ItemProperty`: Questo cmdlet consente all'utente di aggiornare le proprietà di un elemento. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) e [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) metodi.

### <a name="location-cmdlets"></a>Cmdlet Location

- `Get-Location`: Recupera informazioni sul percorso di lavoro corrente. Non è necessaria sovrascrivere i metodi per supportare questo cmdlet.

- `Pop-Location`: Questo cmdlet modifica il percorso corrente nel percorso di più di recente nello stack. Non è necessaria sovrascrivere i metodi per supportare questo cmdlet.

- `Push-Location`: Questo cmdlet aggiunge il percorso corrente all'inizio di un elenco di percorsi ("stack"). Non è necessaria sovrascrivere i metodi per supportare questo cmdlet.

- `Set-Location`: Questo cmdlet imposta il percorso di lavoro corrente in una posizione specificata. Non è necessaria sovrascrivere i metodi per supportare questo cmdlet.

### <a name="path-cmdlets"></a>Cmdlet Path

- `Join-Path`: Questo cmdlet consente di combinare un segmento di percorso padre e figlio per creare un tracciato interna al provider. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) (metodo).

- `Convert-Path`: Questo cmdlet converte un percorso di un percorso di Windows PowerShell in un percorso di provider di Windows PowerShell.

- `Split-Path`: Restituisce la parte specificata di un percorso.

- `Resolve-Path`: Risolve i caratteri jolly in un percorso e visualizza il contenuto del percorso.

- `Test-Path`: Questo cmdlet determina l'esistono di tutti gli elementi di un percorso. Per supportare questo cmdlet, sovrascrivere la [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) e [ System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) metodi.

### <a name="psprovider-cmdlets"></a>Cmdlet PSProvider

- `Get-PSProvider`: Questo cmdlet restituisce informazioni sui provider disponibili nella sessione. Non è necessaria sovrascrivere i metodi per supportare questo cmdlet.