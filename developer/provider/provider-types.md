---
title: Tipi di provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 25b604621c90f1aa88bc1eea365e47db66e98c3d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858407"
---
# <a name="provider-types"></a>Tipi di provider

Provider per definire le funzionalità di base, come i cmdlet del provider (forniti da Windows PowerShell) eseguono le azioni di modifica. Ad esempio, i provider possono utilizzare la funzionalità predefinita del `Get-Item` cmdlet oppure è possibile modificare come tale cmdlet viene eseguito durante il recupero di elementi dall'archivio dati. La funzionalità del provider descritte in questo argomento include la funzionalità definita da sovrascrivere i metodi dalle interfacce e classi di base di provider specifico.

> [!NOTE]
> Per le funzionalità di provider che sono già definite da Windows PowerShell, vedere [funzionalità supportate dai Provider](http://msdn.microsoft.com/en-us/864e4807-554a-4016-80ea-bf643a090fc6).

## <a name="drive-enabled-providers"></a>Provider di Drive-abilitata

Provider di Drive-abilitata per specificare le unità predefinite disponibili per l'utente e consentono all'utente di aggiungere o rimuovere le unità. Nella maggior parte dei casi, i provider sono basate su unità provider perché richiedono alcune unità predefinita per accedere all'archivio dati. Tuttavia, quando si scrive il proprio provider potrebbe o potrebbe non voler consentire all'utente di creare e rimuovere le unità.

Per creare un provider abilitati all'uso di unità, la classe del provider deve derivare dal [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe o un'altra classe che deriva da tale classe. Il [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe definisce i metodi seguenti per implementare le unità predefinite del provider e il supporto di `New-PSDrive` e `Remove-PSDrive` cmdlet. Nella maggior parte dei casi, per supportare un cmdlet del provider è necessario sovrascrivere il metodo che chiama il motore di Windows PowerShell per richiamare il cmdlet, ad esempio la `NewDrive` metodo per il `New-PSDrive` cmdlet e, facoltativamente, è possibile sovrascrivere un secondo metodo, ad esempio `NewDriveDynamicParameters`, per l'aggiunta di parametri dinamici al cmdlet.

- Il [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metodo consente di definire le unità predefinite che sono disponibili per l'utente ogni volta che viene utilizzato il provider.

- Il [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metodi definisce come il provider supporta il `New-PSDrive` cmdlet del provider. Questo cmdlet consente all'utente di creare le unità per accedere all'archivio dati.

- Il [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metodo definisce come il provider supporta il `Remove-PSDrive` cmdlet del provider. Questo cmdlet consente all'utente di rimuovere le unità dall'archivio dati.

## <a name="item-enabled-providers"></a>Elemento abilitato provider

Elemento abilitato provider consentono all'utente di ottenere, impostare o cancellare gli elementi nell'archivio dati. Un "elemento" è un elemento dell'archivio dati che l'utente possa accedere o gestire in modo indipendente. Per creare un provider elemento abilitato, la classe del provider deve derivare dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe o un'altra classe che deriva da tale classe.

Il [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe definisce i metodi seguenti per l'implementazione di cmdlet del provider specifico. Nella maggior parte dei casi, per supportare un cmdlet del provider è necessario sovrascrivere il metodo che chiama il motore di Windows PowerShell per richiamare il cmdlet, ad esempio la `ClearItem` metodo per il `Clear-Item` cmdlet e, facoltativamente, è possibile sovrascrivere un secondo metodo, ad esempio `ClearItemDynamicParameters`, per l'aggiunta di parametri dinamici al cmdlet.

- Il [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) metodi definire come il provider supporta il `Clear-Item` cmdlet del provider. Questo cmdlet consente all'utente di rimuovere il valore di un elemento nell'archivio dati.

- Il [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metodi definiscono come il provider supporta il `Get-Item` cmdlet del provider. Questo cmdlet consente all'utente di recuperare dati dall'archivio dati.

- Il [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) e [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) metodi definiscono come il provider supporta il `Set-Item` cmdlet del provider. Questo cmdlet consente all'utente di aggiornare i valori degli elementi nell'archivio dati.

- Il [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) e [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) metodi definire come il provider supporta il `Invoke-Item` cmdlet del provider. Questo cmdlet consente all'utente di eseguire l'azione predefinita specificata dall'elemento.

- Il [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) e [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) metodi definire come il provider supporta il `Test-Path` cmdlet del provider. Questo cmdlet consente all'utente di stabilire se sono presenti tutti gli elementi di un percorso.

  Oltre ai metodi usati per implementare i cmdlet del provider, il [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe definisce anche i metodi seguenti:

- Il [System.Management.Automation.Provider.Itemcmdletprovider.Expandpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) metodo consente all'utente di usare caratteri jolly quando si specifica il percorso del provider.

- Il [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) viene usato per determinare se un percorso è sintatticamente e semanticamente valido per il provider.

## <a name="container-enabled-providers"></a>Provider di contenitore abilitato

Provider di contenitore abilitato consente all'utente gestire gli elementi che sono contenitori. Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune. Per creare un provider di contenitore abilitato, la classe del provider deve derivare dal [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe o un'altra classe che deriva da tale classe.

> [!IMPORTANT]
> Provider di contenitore abilitato non è possibile accedere agli archivi di dati che contengono i contenitori nidificati. Se un elemento figlio di un contenitore è un altro contenitore, è necessario implementare un provider abilitati all'uso di navigazione.

Il [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe definisce i metodi seguenti per l'implementazione di cmdlet del provider specifico. Nella maggior parte dei casi, per supportare un cmdlet del provider è necessario sovrascrivere il metodo che chiama il motore di Windows PowerShell per richiamare il cmdlet, ad esempio la `CopyItem` metodo per il `Copy-Item` cmdlet e, facoltativamente, è possibile sovrascrivere un secondo metodo, ad esempio `CopyItemDynamicParameters`, per l'aggiunta di parametri dinamici al cmdlet.

- Il [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) e [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) metodi definiscono come il provider supporta il `Copy-Item` cmdlet del provider. Questo cmdlet consente all'utente di copiare un elemento da una posizione a un'altra.

- Il [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) e [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) metodi definiscono come il provider supporta il `Get-ChildItem` cmdlet del provider. Questo cmdlet consente all'utente di recuperare gli elementi figlio dell'elemento padre.

- Il [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) e [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) metodi definiscono come il provider supporta la `Get-ChildItem` cmdlet del provider se relativo `Name` parametro è specificato.

- Il [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) e [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) metodi definiscono come il provider supporta il `New-Item` cmdlet del provider. Questo cmdlet consente all'utente di creare nuovi elementi nell'archivio dati.

- Il [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) e [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) metodi definiscono come il provider supporta il `Remove-Item` cmdlet del provider. Questo cmdlet consente all'utente di rimuovere elementi dall'archivio dati.

- Il [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) e [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) metodi definiscono come il provider supporta il `Rename-Item` cmdlet del provider. Questo cmdlet consente di rinominare gli elementi nell'archivio dati.

  Oltre ai metodi usati per implementare i cmdlet del provider, il [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe definisce anche i metodi seguenti:

- Il [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) metodo può essere usato dalla classe del provider per determinare se un elemento include gli elementi figlio.

- Il [System.Management.Automation.Provider.Containercmdletprovider.Convertpath*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) metodo può essere utilizzato dalla classe provider per creare un nuovo percorso specifico del provider da un percorso specificato.

## <a name="navigation-enabled-providers"></a>Provider di navigazione abilitata

Provider di navigazione abilitata consente all'utente di spostare gli elementi nell'archivio dati. Per creare un provider di navigazione abilitata, la classe del provider deve derivare dal [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.

Il [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe definisce i metodi seguenti per l'implementazione di cmdlet del provider specifico. Nella maggior parte dei casi, per supportare un cmdlet del provider è necessario sovrascrivere il metodo che chiama il motore di Windows PowerShell per richiamare il cmdlet, ad esempio la `MoveItem` metodo per il `Move-Item` cmdlet e, facoltativamente, è possibile sovrascrivere un secondo metodo, ad esempio `MoveItemDynamicParameters`, per l'aggiunta di parametri dinamici al cmdlet.

- Il [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) e [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) metodi definiscono come il provider supporta il `Move-Item` cmdlet del provider. Questo cmdlet consente all'utente di spostare un elemento da una posizione nell'archivio in un'altra posizione.

- Il [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metodo definisce come il provider supporta il `Join-Path` cmdlet del provider. Questo cmdlet consente di combinare un segmento di percorso padre e figlio per creare un tracciato interna al provider.

  Oltre ai metodi usati per implementare i cmdlet del provider, il [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe definisce anche i metodi seguenti:

- Il [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metodo estrae il nome del nodo figlio di un percorso.

- Il [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metodo estrae la parte padre di un percorso.

- Il [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) metodo determina se l'elemento è un elemento contenitore. In questo contesto, un contenitore è un gruppo di elementi figlio sotto un elemento padre comune.

- Il [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) metodo restituisce un percorso di un elemento che è relativo a un percorso di base specificato.

## <a name="content-enabled-providers"></a>Provider di contenuto abilitato

Provider di contenuto abilitato consentono all'utente di cancellare, ottenere o impostare il contenuto degli elementi in un archivio dati. Ad esempio, il provider FileSystem consente di cancellare, ottenere e impostare il contenuto del file nel file system. Per creare un provider di contenuti abilitato, la classe del provider deve implementare i metodi del [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaccia.

Il [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaccia definisce i metodi seguenti per l'implementazione di cmdlet del provider specifico. Nella maggior parte dei casi, per supportare un cmdlet del provider è necessario sovrascrivere il metodo che chiama il motore di Windows PowerShell per richiamare il cmdlet, ad esempio la `ClearContent` metodo per il `Clear-Content` cmdlet e, facoltativamente, è possibile sovrascrivere un secondo metodo, ad esempio `ClearContentDynamicParameters`, per l'aggiunta di parametri dinamici al cmdlet.

- Il [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) e [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)metodi definiscono come il provider supporta il `Clear-Content` cmdlet del provider. Questo cmdlet consente all'utente di eliminare il contenuto di un elemento senza eliminare l'elemento.

- Il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) e [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) metodi definiscono come il provider supporta il `Get-Content` cmdlet del provider. Questo cmdlet consente all'utente di recuperare il contenuto di un elemento. Il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metodo restituisce un' [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interfaccia che definisce i metodi utilizzati per leggere il contenuto.

- Il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) e [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) metodi definiscono come il provider supporta il `Set-Content` cmdlet del provider. Questo cmdlet consente all'utente di aggiornare il contenuto di un elemento. Il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) metodo restituisce un' [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interfaccia che definisce i metodi utilizzati per scrivere il contenuto.

## <a name="property-enabled-providers"></a>Provider di proprietà-abilitata

Provider di proprietà abilitata consente all'utente gestire le proprietà degli elementi nell'archivio dati. Per creare un provider di proprietà abilitata, la classe del provider deve implementare i metodi del [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interfacce. Nella maggior parte dei casi, per supportare un cmdlet del provider è necessario sovrascrivere il metodo che chiama il motore di Windows PowerShell per richiamare il cmdlet, ad esempio il `ClearProperty` metodo per il cmdlet Clear-proprietà e, facoltativamente, è possibile sovrascrivere un secondo metodo, ad esempio `ClearPropertyDynamicParameters`, per l'aggiunta di parametri dinamici al cmdlet.

Il [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfaccia definisce i metodi seguenti per l'implementazione di cmdlet del provider specifici:

- Il [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) e [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) metodi definiscono come il provider supporta il `Clear-ItemProperty` cmdlet del provider. Questo cmdlet consente all'utente di eliminare il valore di una proprietà.

- Il [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) e [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)metodi definiscono come il provider supporta il `Get-ItemProperty` cmdlet del provider. Questo cmdlet consente all'utente di recuperare la proprietà di un elemento.

- Il [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) e [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)metodi definiscono come il provider supporta il `Set-ItemProperty` cmdlet del provider. Questo cmdlet consente all'utente di aggiornare le proprietà di un elemento.

  Il [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interfaccia definisce i metodi seguenti per l'implementazione di cmdlet del provider specifici:

- Il [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) metodi definiscono come il provider supporta il `Copy-ItemProperty` cmdlet del provider. Questo cmdlet consente all'utente di copiare una proprietà e il relativo valore da una posizione a un'altra.

- Il [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) metodi definiscono come il provider supporta il `Move-ItemProperty` cmdlet del provider. Questo cmdlet consente all'utente di spostare una proprietà e il relativo valore da una posizione a un'altra.

- Il [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) metodi definiscono come il provider supporta il `New-ItemProperty` cmdlet del provider. Questo cmdlet consente all'utente di creare una nuova proprietà e impostarne il valore.

- Il [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) metodi definiscono come il provider supporta il `Remove-ItemProperty` cmdlet. Questo cmdlet consente all'utente di eliminare una proprietà e il relativo valore.

- Il [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) e [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) metodi definiscono come il provider supporta il `Rename-ItemProperty` cmdlet. Questo cmdlet consente all'utente di modificare il nome di una proprietà.

## <a name="see-also"></a>Vedere anche

[Scrittura di un Provider di Windows PowerShell](./writing-a-windows-powershell-provider.md)