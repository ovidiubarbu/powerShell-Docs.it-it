---
title: Tipi di provider | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 0a9bfe5dd0978ffce66db1b18ef4d82be6c1a7f2
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986651"
---
# <a name="provider-types"></a>Tipi di provider

I provider definiscono le funzionalità di base modificando il modo in cui i cmdlet del provider, forniti da PowerShell, eseguono le proprie azioni. I provider possono ad esempio utilizzare la funzionalità predefinita del `Get-Item` cmdlet oppure modificare il funzionamento del cmdlet durante il recupero di elementi dall'archivio dati. La funzionalità del provider descritta in questo documento include funzionalità definite mediante la sovrascrittura dei metodi da classi e interfacce specifiche del provider.

> [!NOTE]
> Per le funzionalità del provider predefinite da PowerShell, vedere funzionalità del [provider](/previous-versions//ee126189(v=vs.85)).

## <a name="drive-enabled-providers"></a>Provider abilitati per l'unità

I provider abilitati per l'unità specificano le unità predefinite disponibili per l'utente e consentono all'utente di aggiungere o rimuovere unità. Nella maggior parte dei casi, i provider sono provider abilitati per l'unità perché richiedono alcune unità predefinite per accedere all'archivio dati. Tuttavia, quando si scrive un provider personalizzato, è possibile o non si desidera consentire all'utente di creare e rimuovere unità.

Per creare un provider abilitato per l'unità, la classe del provider deve derivare dalla classe [System. Management. Automation. provider. DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) o da un'altra classe che deriva da tale classe. La classe **System. Management. Automation. provider. DriveCmdletProvider** definisce i metodi seguenti per implementare le unità predefinite del provider e supportare i `New-PSDrive` cmdlet e. `Remove-PSDrive` Nella maggior parte dei casi, per supportare un cmdlet del provider è necessario sovrascrivere il metodo chiamato dal motore di PowerShell per richiamare il cmdlet `NewDrive` , ad esempio `New-PSDrive` il metodo per il cmdlet, e, facoltativamente, è possibile sovrascrivere un `NewDriveDynamicParameters` secondo metodo, ad esempio , per aggiungere parametri dinamici al cmdlet.

- Il metodo [System. Management. Automation. provider. DriveCmdletProvider. InitializeDefaultDrives](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) definisce le unità predefinite che sono disponibili per l'utente ogni volta che viene usato il provider.

- I metodi [System. Management. Automation. provider. DriveCmdletProvider. nuovaunità](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System. Management. Automation. provider. DriveCmdletProvider. NewDriveDynamicParameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) definiscono il modo in cui il provider supporta il `New-PSDrive`cmdlet del provider. Questo cmdlet consente all'utente di creare unità per accedere all'archivio dati.

- Il metodo [System. Management. Automation. provider. DriveCmdletProvider. RemoveDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) definisce il modo in cui il `Remove-PSDrive` provider supporta il cmdlet provider. Questo cmdlet consente all'utente di rimuovere unità dall'archivio dati.

## <a name="item-enabled-providers"></a>Provider abilitati per gli elementi

I provider abilitati per gli elementi consentono all'utente di ottenere, impostare o cancellare gli elementi nell'archivio dati. Un "elemento" è un elemento dell'archivio dati a cui l'utente può accedere o gestire in modo indipendente. Per creare un provider abilitato per gli elementi, la classe del provider deve derivare dalla classe [System. Management. Automation. provider. ItemCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) o da un'altra classe che deriva da tale classe.

La classe **System. Management. Automation. provider. ItemCmdletProvider** definisce i metodi seguenti per implementare i cmdlet specifici del provider. Nella maggior parte dei casi, per supportare un cmdlet del provider è necessario sovrascrivere il metodo chiamato dal motore di PowerShell per richiamare il cmdlet `ClearItem` , ad esempio `Clear-Item` il metodo per il cmdlet, e, facoltativamente, è possibile sovrascrivere un `ClearItemDynamicParameters` secondo metodo, ad esempio , per aggiungere parametri dinamici al cmdlet.

- I metodi [System. Management. Automation. provider. ItemCmdletProvider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) e [System. Management. Automation. provider. ItemCmdletProvider. ClearItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) definiscono il modo in cui il provider supporta il `Clear-Item`cmdlet del provider. Questo cmdlet consente all'utente di rimuovere il valore di un elemento nell'archivio dati.

- I metodi [System. Management. Automation. provider. ItemCmdletProvider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System. Management. Automation. provider. ItemCmdletProvider. GetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) definiscono il modo in cui il `Get-Item` provider supporta il cmdlet del provider. Questo cmdlet consente all'utente di recuperare i dati dall'archivio dati.

- I metodi [System. Management. Automation. provider. ItemCmdletProvider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) e [System. Management. Automation. provider. ItemCmdletProvider. SetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) definiscono il modo in cui il `Set-Item` provider supporta il cmdlet del provider. Questo cmdlet consente all'utente di aggiornare i valori degli elementi nell'archivio dati.

- I metodi [System. Management. Automation. provider. Itemcmdletprovider. InvokeDefaultAction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) e [System. Management. Automation. provider. Itemcmdletprovider. InvokeDefaultActionDynamicParameters](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters) definiscono il modo in cui il provider supporta il `Invoke-Item` cmdlet provider. Questo cmdlet consente all'utente di eseguire l'azione predefinita specificata dall'elemento.

- I metodi [System. Management. Automation. provider. ItemCmdletProvider. itemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) e [System. Management. Automation. provider. ItemCmdletProvider. ItemExistsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) definiscono il modo in cui il provider supporta il `Test-Path`cmdlet del provider. Questo cmdlet consente all'utente di determinare se sono presenti tutti gli elementi di un percorso.

Oltre ai metodi usati per implementare i cmdlet del provider, la classe **System. Management. Automation. provider. ItemCmdletProvider** definisce anche i metodi seguenti:

- Il metodo [System. Management. Automation. provider. ItemCmdletProvider. ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) consente all'utente di usare caratteri jolly quando si specifica il percorso del provider.

- [System. Management. Automation. provider. ItemCmdletProvider. IsValidPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) viene usato per determinare se un percorso è sintatticamente e semanticamente valido per il provider.

## <a name="container-enabled-providers"></a>Provider abilitati per i contenitori

I provider abilitati per il contenitore consentono all'utente di gestire gli elementi che sono contenitori. Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune. Per creare un provider abilitato per il contenitore, la classe del provider deve derivare dalla classe [System. Management. Automation. provider. ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) o da un'altra classe che deriva da tale classe.

> [!IMPORTANT]
> I provider abilitati per i contenitori non possono accedere agli archivi dati che contengono contenitori nidificati. Se un elemento figlio di un contenitore è un altro contenitore, è necessario implementare un provider abilitato per la navigazione.

La classe **System. Management. Automation. provider. ContainerCmdletProvider** definisce i metodi seguenti per implementare i cmdlet specifici del provider. Nella maggior parte dei casi, per supportare un cmdlet del provider è necessario sovrascrivere il metodo chiamato dal motore di PowerShell per richiamare il cmdlet `CopyItem` , ad esempio `Copy-Item` il metodo per il cmdlet, e, facoltativamente, è possibile sovrascrivere un `CopyItemDynamicParameters` secondo metodo, ad esempio , per aggiungere parametri dinamici al cmdlet.

- I metodi [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) e [System. Management. Automation. provider. ContainerCmdletProvider. CopyItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) definiscono il modo in cui il provider supporta il `Copy-Item` cmdlet del provider. Questo cmdlet consente all'utente di copiare un elemento da una posizione a un'altra.

- I metodi [System. Management. Automation. provider. ContainerCmdletProvider.](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) getchilditems e [System. Management. Automation. provider. ContainerCmdletProvider. GetChildItemsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) definiscono il modo in cui il provider supporta il `Get-ChildItem` cmdlet provider. Questo cmdlet consente all'utente di recuperare gli elementi figlio dell'elemento padre.

- I metodi [System. Management. Automation. provider. ContainerCmdletProvider. GetChildNames](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) e [System. Management. Automation. provider. ContainerCmdletProvider. GetChildNamesDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) definiscono il modo in cui il provider supporta il `Get-ChildItem` cmdlet provider se viene `Name` specificato il relativo parametro.

- I metodi [System. Management. Automation. provider. ContainerCmdletProvider. NewItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) e [System. Management. Automation. provider. ContainerCmdletProvider. NewItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) definiscono il modo in cui il provider supporta il `New-Item` cmdlet del provider. Questo cmdlet consente all'utente di creare nuovi elementi nell'archivio dati.

- I metodi [System. Management. Automation. provider. ContainerCmdletProvider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) e [System. Management. Automation. provider. ContainerCmdletProvider. RemoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) definiscono il modo in cui il provider supporta il `Remove-Item` cmdlet del provider. Questo cmdlet consente all'utente di rimuovere elementi dall'archivio dati.

- I metodi [System. Management. Automation. provider. ContainerCmdletProvider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) e [System. Management. Automation. provider. ContainerCmdletProvider. RenameItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) definiscono il modo in cui il provider supporta il `Rename-Item` cmdlet del provider. Questo cmdlet consente all'utente di rinominare gli elementi nell'archivio dati.

Oltre ai metodi usati per implementare i cmdlet del provider, la classe **System. Management. Automation. provider. ContainerCmdletProvider** definisce anche i metodi seguenti:

- Il metodo [System. Management. Automation. provider. ContainerCmdletProvider. HasChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) può essere usato dalla classe provider per determinare se un elemento contiene elementi figlio.

- Il metodo [System. Management. Automation. provider. ContainerCmdletProvider. ConvertPath](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) può essere usato dalla classe provider per creare un nuovo percorso specifico del provider da un percorso specificato.

## <a name="navigation-enabled-providers"></a>Provider abilitati per la navigazione

I provider abilitati per la navigazione consentono all'utente di spostare gli elementi nell'archivio dati. Per creare un provider abilitato per la navigazione, la classe del provider deve derivare dalla classe [System. Management. Automation. provider. NavigationCmdletProvider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

La classe **System. Management. Automation. provider. NavigationCmdletProvider** definisce i metodi seguenti per implementare i cmdlet specifici del provider. Nella maggior parte dei casi, per supportare un cmdlet del provider è necessario sovrascrivere il metodo chiamato dal motore di PowerShell per richiamare il cmdlet `MoveItem` , ad esempio `Move-Item` il metodo per il cmdlet, e, facoltativamente, è possibile sovrascrivere un `MoveItemDynamicParameters` secondo metodo, ad esempio , per aggiungere parametri dinamici al cmdlet.

- I metodi [System. Management. Automation. provider. NavigationCmdletProvider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) e [System. Management. Automation. provider. NavigationCmdletProvider. MoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) definiscono il modo in cui il provider supporta il `Move-Item` cmdlet del provider. Questo cmdlet consente all'utente di spostare un elemento da una posizione nell'archivio a un'altra.

- Il metodo [System. Management. Automation. provider. NavigationCmdletProvider. makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) definisce il modo in cui il `Join-Path` provider supporta il cmdlet provider. Questo cmdlet consente all'utente di combinare un segmento di percorso padre e figlio per creare un percorso interno del provider.

Oltre ai metodi usati per implementare i cmdlet del provider, la classe **System. Management. Automation. provider. NavigationCmdletProvider** definisce anche i metodi seguenti:

- Il metodo [System. Management. Automation. provider. NavigationCmdletProvider.](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) getchildname estrae il nome del nodo figlio di un percorso.

- Il metodo [System. Management. Automation. provider. NavigationCmdletProvider. GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) estrae la parte padre di un percorso.

- Il metodo [System. Management. Automation. provider. NavigationCmdletProvider. IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) determina se l'elemento è un elemento contenitore. In questo contesto, un contenitore è un gruppo di elementi figlio sotto un elemento padre comune.

- Il metodo [System. Management. Automation. provider. NavigationCmdletProvider. NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) restituisce un percorso a un elemento relativo a un percorso di base specificato.

## <a name="content-enabled-providers"></a>Provider abilitati per il contenuto

I provider abilitati per il contenuto consentono all'utente di cancellare, ottenere o impostare il contenuto degli elementi in un archivio dati.
Ad esempio, il provider FileSystem consente di cancellare, ottenere e impostare il contenuto dei file nell'file system. Per creare un provider abilitato per il contenuto, la classe del provider deve implementare i metodi dell'interfaccia [System. Management. Automation. provider. IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

L'interfaccia **System. Management. Automation. provider. IContentCmdletProvider** definisce i metodi seguenti per implementare i cmdlet specifici del provider. Nella maggior parte dei casi, per supportare un cmdlet del provider è necessario sovrascrivere il metodo chiamato dal motore di PowerShell per richiamare il cmdlet `ClearContent` , ad esempio `Clear-Content` il metodo per il cmdlet, e, facoltativamente, è possibile sovrascrivere un `ClearContentDynamicParameters` secondo metodo, ad esempio , per aggiungere parametri dinamici al cmdlet.

- I metodi [System. Management. Automation. provider. IContentCmdletProvider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) e [System. Management. Automation. provider. IContentCmdletProvider. ClearContentDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) definiscono il modo in cui il provider supporta cmdlet `Clear-Content` del provider. Questo cmdlet consente all'utente di eliminare il contenuto di un elemento senza eliminare l'elemento.

- I metodi [System. Management. Automation. provider. IContentCmdletProvider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) e [System. Management. Automation. provider. IContentCmdletProvider. GetContentReaderDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) definiscono il modo in cui il provider supporta il `Get-Content` cmdlet provider. Questo cmdlet consente all'utente di recuperare il contenuto di un elemento. Il `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader` metodo restituisce un'interfaccia [System. Management. Automation. provider. IContentReader](/dotnet/api/System.Management.Automation.Provider.IContentReader) che definisce i metodi usati per leggere il contenuto.

- I metodi [System. Management. Automation. provider. IContentCmdletProvider. GetContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) e [System. Management. Automation. provider. IContentCmdletProvider. GetContentWriterDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) definiscono il modo in cui il provider supporta il `Set-Content` cmdlet provider. Questo cmdlet consente all'utente di aggiornare il contenuto di un elemento. Il `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter` metodo restituisce un'interfaccia [System. Management. Automation. provider. IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) che definisce i metodi utilizzati per scrivere il contenuto.

## <a name="property-enabled-providers"></a>Provider abilitati per la proprietà

I provider abilitati per la proprietà consentono all'utente di gestire le proprietà degli elementi nell'archivio dati.
Per creare un provider abilitato per la proprietà, la classe del provider deve implementare i metodi di [System. Management. Automation. provider. IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) e [System. Management. Automation. provider. IDynamicPropertyCmdletProvider ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)interfacce. Nella maggior parte dei casi, per supportare un cmdlet del provider è necessario sovrascrivere il metodo chiamato dal motore di PowerShell per richiamare il cmdlet `ClearProperty` , ad esempio il metodo per il cmdlet Clear-Property e, facoltativamente, è possibile sovrascrivere `ClearPropertyDynamicParameters` un secondo metodo, ad esempio , per aggiungere parametri dinamici al cmdlet.

L'interfaccia **System. Management. Automation. provider. IPropertyCmdletProvider** definisce i metodi seguenti per implementare i cmdlet specifici del provider:

- I metodi [System. Management. Automation. provider. IPropertyCmdletProvider. ClearProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) e [System. Management. Automation. provider. IPropertyCmdletProvider. ClearPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) definiscono il modo in cui il provider supporta il `Clear-ItemProperty` cmdlet provider. Questo cmdlet consente all'utente di eliminare il valore di una proprietà.

- I metodi [System. Management. Automation. provider. IPropertyCmdletProvider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) e [System. Management. Automation. provider. IPropertyCmdletProvider. GetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) definiscono il modo in cui il provider supporta cmdlet `Get-ItemProperty` del provider. Questo cmdlet consente all'utente di recuperare la proprietà di un elemento.

- I metodi [System. Management. Automation. provider. IPropertyCmdletProvider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) e [System. Management. Automation. provider. IPropertyCmdletProvider. SetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) definiscono il modo in cui il provider supporta cmdlet `Set-ItemProperty` del provider. Questo cmdlet consente all'utente di aggiornare le proprietà di un elemento.

  L'interfaccia **System. Management. Automation. provider. IDynamicPropertyCmdletProvider** definisce i metodi seguenti per implementare i cmdlet specifici del provider:

- I metodi [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. CopyProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) e [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. CopyPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) definiscono il modo in cui il provider supporta `Copy-ItemProperty` il cmdlet provider. Questo cmdlet consente all'utente di copiare una proprietà e il relativo valore da una posizione a un'altra.

- I metodi [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. MoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) e [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. MovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) definiscono il modo in cui il provider supporta `Move-ItemProperty` il cmdlet provider. Questo cmdlet consente all'utente di spostare una proprietà e il relativo valore da una posizione a un'altra.

- I metodi [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) e [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. NewPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) definiscono il modo in cui il provider supporta `New-ItemProperty` il cmdlet provider. Questo cmdlet consente all'utente di creare una nuova proprietà e di impostarne il valore.

- I metodi [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) e [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. RemovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) definiscono come il provider supporta il `Remove-ItemProperty` cmdlet. Questo cmdlet consente all'utente di eliminare una proprietà e il relativo valore.

- I metodi [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. RenameProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) e [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. RenamePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) definiscono come il provider supporta il `Rename-ItemProperty` cmdlet. Questo cmdlet consente all'utente di modificare il nome di una proprietà.

## <a name="see-also"></a>Vedere anche

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[Scrittura di un provider di Windows PowerShell](./writing-a-windows-powershell-provider.md)
