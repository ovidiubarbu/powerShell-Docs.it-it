---
title: Progettazione del Provider PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 518040df4df7260a974bfda252c606a051cc35ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856857"
---
# <a name="designing-your-windows-powershell-provider"></a>Progettazione del provider di Windows PowerShell

Se il prodotto o la configurazione espone un set di dati archiviati, ad esempio un database che l'utente dovrà di navigazione, è necessario implementare un provider di Windows PowerShell. Inoltre, se il prodotto fornisce un contenitore, anche se non è un contenitore più livelli, è opportuno implementare un provider di Windows PowerShell. Ad esempio, è possibile implementare un provider di contenitore di Windows PowerShell se il verbo cmdlet copia, spostamento, ridenominazione, nuovo o Remove adatto come un'operazione sui dati del prodotto o la configurazione.

## <a name="windows-powershell-paths-identify-your-provider"></a>Il Provider di identità di percorsi di Windows PowerShell

Il runtime di Windows PowerShell Usa i percorsi di Windows PowerShell per accedere al provider di Windows PowerShell appropriato. Quando un cmdlet specifica uno di questi percorsi, il runtime non saprà il provider da usare per accedere all'archivio dati associato. Questi percorsi sono percorsi drivequalified, completo di provider di percorsi, i percorsi di provider-direct e percorsi interna al provider. Ogni provider di Windows PowerShell deve supportare uno o più di questi percorsi.

Per altre informazioni sui percorsi di Windows PowerShell, vedere modalità di funzionamento di Windows PowerShell.

### <a name="defining-a-drive-qualified-path"></a>Definizione di un percorso completo di unità

Per consentire all'utente di accedere ai dati che si trova in un'unità fisica, il provider di Windows PowerShell deve supportare un percorso completo di unità. Il percorso inizia con il nome di unità seguito da due punti (:), ad esempio, mydrive:\abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Definizione di un percorso completo di Provider

Per consentire al runtime di Windows PowerShell inizializzare e annullare l'inizializzazione del provider, provider di Windows PowerShell deve supportare un percorso completo di provider. Ad esempio, file System::\\\uncshare\abc\bar è il percorso completo di provider per il provider filesystem fornito mediante Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Definizione di un percorso di Provider-Direct

Per consentire l'accesso remoto al provider di Windows PowerShell, è opportuno che un percorso di provider-direct per passare direttamente al provider di Windows PowerShell per la posizione corrente. Ad esempio, è possibile usare il provider di Windows PowerShell del Registro di sistema \\\server\regkeypath come un percorso di provider con accesso diretto.

### <a name="defining-a-provider-internal-path"></a>La definizione di un percorso interno-Provider

Per consentire i cmdlet del provider di accesso ai dati tramite application programming interface (API) non Windows PowerShell, il provider di Windows PowerShell deve supportare un percorso interna al provider. Questo percorso è indicato che segue il "::" il percorso completo di provider. Ad esempio, il percorso interna al provider per provider filesystem di Windows PowerShell è \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>La modifica dei dati archiviati

Quando si esegue l'override di metodi che modificano l'archivio dati sottostante, chiamare sempre il [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metodo con la versione più aggiornata dell'elemento modificato da tale metodo. L'infrastruttura del provider determina se l'oggetto di elemento deve essere passato alla pipeline, ad esempio quando l'utente specifica il parametro - PassThru. Se l'elemento più aggiornata di recupero è una costosa operazione (percepirà), è possibile testare la proprietà Context.PassThru per stabilire se è effettivamente necessario scrivere l'elemento risulta.

## <a name="choose-a-base-class-for-your-provider"></a>Scegliere una classe di Base per il Provider

Windows PowerShell fornisce una serie di classi di base che è possibile usare per implementare il proprio provider di Windows PowerShell. Quando si progetta un provider, scegliere la classe di base, descritta in questa sezione, che è più adatta alle proprie esigenze.

Ogni classe di base di provider di Windows PowerShell rende disponibile un set di cmdlet. In questa sezione vengono descritti i cmdlet, ma non descrive i relativi parametri.

Usa lo stato della sessione, il runtime di Windows PowerShell rende diversi cmdlet percorso disponibile per alcuni provider di Windows PowerShell, ad esempio la `Get-Location`, `Set-Location`, `Pop-Location`, e `Push-Location` cmdlet. È possibile usare il `Get-Help` per ottenere informazioni su questi cmdlet di percorso.

### <a name="cmdletprovider-base-class"></a>Classe di base CmdletProvider

Il [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe definisce un provider di Windows PowerShell di base. Questa classe supporta la dichiarazione di provider e fornisce una serie di proprietà e metodi disponibili per tutti i provider Windows PowerShell. La classe viene richiamata dal `Get-PSProvider` cmdlet per elencare tutti i provider disponibili per una sessione. L'implementazione di questo cmdlet viene fornita mediante lo stato della sessione.

> [!NOTE]
> Provider di Windows PowerShell sono disponibili a tutti gli ambiti di lingua di Windows PowerShell.

### <a name="drivecmdletprovider-base-class"></a>Classe di base DriveCmdletProvider

Il [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe definisce un provider di unità di Windows PowerShell che supporta operazioni per l'aggiunta di nuove unità, la rimozione di unità esistente e l'inizializzazione di unità predefinite. Ad esempio, il provider FileSystem di Windows PowerShell consente di inizializzare le unità per tutti i volumi montati, ad esempio dischi rigidi e unità di dispositivo di CD/DVD.

Questa classe deriva dal [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe di base. Nella tabella seguente elenca i cmdlet esposti da questa classe. Oltre a quelle elencate, il `Get-PSDrive` cmdlet (esposti dallo stato della sessione) è un cmdlet correlato che viene usato per recuperare le unità disponibili.

|Cmdlet|Definizione|
|------------|----------------|
|`New-PSDrive`|Crea una nuova unità per la sessione e crea un flusso di informazioni sull'unità.|
|`Remove-PSDrive`|Rimuove un'unità nella sessione.|

### <a name="itemcmdletprovider-base-class"></a>Classe di base ItemCmdletProvider

Il [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe definisce un provider di Windows PowerShell che esegue operazioni per i singoli elementi dell'archivio dati e non assume qualsiasi contenitore o funzionalità di navigazione. Questa classe deriva dal [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe di base. Nella tabella seguente elenca i cmdlet esposti da questa classe.

|Cmdlet|Definizione|
|------------|----------------|
|`Clear-Item`|Cancella il contenuto corrente degli elementi nella posizione specificata e lo sostituisce con il valore "Cancella" specificato dal provider. Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|
|`Get-Item`|Recupera gli elementi dalla posizione specificata e trasmette gli oggetti risultanti.|
|`Invoke-Item`|Richiama l'azione predefinita per l'elemento nel percorso specificato.|
|`Set-Item`|Imposta un elemento nella posizione specificata con il valore indicato. Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|
|`Resolve-Path`|Risolve i caratteri jolly per un percorso di Windows PowerShell e le informazioni sul percorso di flussi.|
|`Test-Path`|Verifica per il percorso specificato e restituisce `true` se è presente e `false` in caso contrario. Questo cmdlet viene implementato per supportare le `IsContainer` parametro per il [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) (metodo).|

### <a name="containercmdletprovider-base-class"></a>Classe di base ContainerCmdletProvider

Il [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe definisce un provider di contenitore di Windows PowerShell che espone un contenitore, per gli elementi di archivio dati, all'utente. Tenere presente che è possibile utilizzare un provider di contenitore di Windows PowerShell solo quando è presente un contenitore (non i contenitori nidificati) con gli elementi in esso. Se sono presenti contenitori annidati, è necessario implementare un provider di navigazione di Windows PowerShell.

Questa classe deriva dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe di base. Nella tabella seguente definisce i cmdlet implementati da questa classe.

|Cmdlet|Definizione|
|------------|----------------|
|`Copy-Item`|Copia gli elementi da una posizione a un'altra. Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|
|`Get-Childitem`|Recupera gli elementi figlio in corrispondenza della posizione specificata e li trasmette come oggetti.|
|`New-Item`|Crea nuovi elementi nella posizione specificata e trasmette l'oggetto risultante.|
|`Remove-Item`|Rimuove gli elementi dalla posizione specificata.|
|`Rename-Item`|Rinomina un elemento in corrispondenza della posizione specificata. Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|

### <a name="navigationcmdletprovider-base-class"></a>Classe di base NavigationCmdletProvider

Il [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe definisce un provider di navigazione di Windows PowerShell che esegue operazioni per gli elementi che utilizzano più di un contenitore. Questa classe deriva dal [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe di base. Nella tabella seguente elenca i cmdlet esposti da questa classe.

|Cmdlet|Definizione|
|------------|----------------|
|Combinare-Path|Combina due percorsi in un singolo percorso, con un delimitatore di specifiche del provider tra i percorsi. Questo cmdlet crea un flusso di stringhe.|
|`Move-Item`|Sposta gli elementi nel percorso specificato. Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|

Cmdlet correlati è il cmdlet di analisi-Path base fornito mediante Windows PowerShell. Questo cmdlet può essere utilizzato per analizzare un percorso di Windows PowerShell per supportare il `Parent` parametro. Trasmette la stringa del percorso padre.

## <a name="select-provider-interfaces-to-support"></a>Selezionare le interfacce del Provider al supporto tecnico

Oltre alla derivazione da una delle classi di base di Windows PowerShell, il provider di Windows PowerShell può supportare altre funzionalità derivando da una o più delle seguenti interfacce del provider. Questa sezione definisce le interfacce e i cmdlet supportati da ognuno. Non descrive i parametri per i cmdlet di interfaccia supportata. Informazioni sui parametri di cmdlet è disponibile online tramite il `Get-Command` e `Get-Help` cmdlet.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

Il [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaccia definisce un provider di contenuti che esegue operazioni sul contenuto di un elemento di dati. Nella tabella seguente elenca i cmdlet esposti da questa interfaccia.

|Cmdlet|Definizione|
|------------|----------------|
|`Add-Content`|Aggiunge la lunghezza del valore indicato per il contenuto dell'elemento specificato. Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|
|`Clear-Content`|Imposta il contenuto dell'elemento specificato sul valore "Cancella". Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|
|`Get-Content`|Recupera il contenuto degli elementi specificati e trasmette gli oggetti risultanti.|
|`Set-Content`|Sostituisce il contenuto esistente per gli elementi specificati. Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

Il [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfaccia definisce un provider di Windows PowerShell di proprietà che esegue operazioni sulle proprietà degli elementi nell'archivio dati. Nella tabella seguente elenca i cmdlet esposti da questa interfaccia.

> [!NOTE]
> Il `Path` parametro su questi cmdlet indica un percorso di un elemento invece che identifica una proprietà.

|Cmdlet|Definizione|
|------------|----------------|
|`Clear-ItemProperty`|Imposta le proprietà degli elementi specificati per il valore "Cancella". Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|
|`Get-ItemProperty`|Recupera le proprietà dagli elementi specificati e trasmette gli oggetti risultanti.|
|`Set-ItemProperty`|Imposta le proprietà degli elementi specificati con i valori indicati. Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

Il [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interfaccia, derivato da [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), definisce un provider che specifica i parametri dinamici per i relativi cmdlet supportati. Questo tipo di provider gestisce le operazioni per cui le proprietà possono essere definite in fase di esecuzione, ad esempio, una nuova operazione di proprietà. Tali operazioni non sono possibili sugli elementi in modo statico dopo aver definito le proprietà. Nella tabella seguente elenca i cmdlet esposti da questa interfaccia.

|Cmdlet|Definizione|
|------------|----------------|
|`Copy-ItemProperty`|Copia una proprietà dall'elemento specificato in un altro elemento. Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|
|`Move-ItemProperty`|Sposta una proprietà dall'elemento specificato a un altro elemento. Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|
|`New-ItemProperty`|Crea una proprietà sugli elementi specificati e trasmette gli oggetti risultanti.|
|`Remove-ItemProperty`|Rimuove una proprietà per gli elementi specificati.|
|`Rename-ItemProperty`|Rinomina una proprietà degli elementi specificati. Questo cmdlet non passare un oggetto di output tramite la pipeline a meno che non relativo `PassThru` parametro è specificato.|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

Il [System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) interfaccia aggiunge funzionalità di descrittore di sicurezza a un provider. Questa interfaccia consente all'utente ottenere e impostare le informazioni sul descrittore di sicurezza per un elemento nell'archivio dati. Nella tabella seguente elenca i cmdlet esposti da questa interfaccia.

|Cmdlet|Definizione|
|------------|----------------|
|`Get-Acl`|Recupera le informazioni contenute in un elenco di controllo di accesso (ACL), che fa parte di un descrittore di sicurezza utilizzata per proteggere le risorse di sistema operativo, ad esempio, un file o un oggetto.|
|`Set-Acl`|Imposta le informazioni per un elenco ACL. È sotto forma di un'istanza di [System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) sugli elementi designati per il percorso specificato. Questo cmdlet è possibile impostare informazioni relative a file, chiavi e sottochiavi del Registro di sistema, o qualsiasi altro elemento del provider, se il provider di Windows PowerShell supporta l'impostazione delle informazioni di sicurezza.|

## <a name="see-also"></a>Vedere anche

[Creazione di provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Funzionamento di Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Funzionamento di Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)