---
title: Creazione di un provider di contenitori di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: 0b3ec95dde92644be07927a1d470fe97648c124c
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323509"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Creazione di un provider di contenitori di Windows PowerShell

In questo argomento viene descritto come creare un provider di Windows PowerShell in grado di funzionare in archivi dati a più livelli. Per questo tipo di archivio dati, il livello principale dell'archivio contiene gli elementi radice e ogni livello successivo viene definito nodo di elementi figlio. Consentendo all'utente di lavorare su questi nodi figlio, un utente può interagire gerarchicamente con l'archivio dati.

I provider che possono usare gli archivi dati a più livelli sono detti provider di contenitori di Windows PowerShell. Tuttavia, tenere presente che un provider di contenitori di Windows PowerShell può essere utilizzato solo quando è presente un contenitore (nessun contenitore annidato) con elementi. Se sono presenti contenitori annidati, è necessario implementare un provider di navigazione di Windows PowerShell. Per ulteriori informazioni sull'implementazione del provider di navigazione di Windows PowerShell, vedere [creazione di un provider di navigazione di Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> È possibile scaricare il C# file di origine (AccessDBSampleProvider04.cs) per questo provider utilizzando Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> I file di origine scaricati sono disponibili nell'  **\<>** directory degli esempi di PowerShell.
>
> Per ulteriori informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

Il provider di contenitori di Windows PowerShell descritto di seguito definisce il database come singolo contenitore, con le tabelle e le righe del database definite come elementi del contenitore.

> [!CAUTION]
> Tenere presente che questa progettazione presuppone che il database disponga di un campo con ID nome e che il tipo del campo sia LongInteger.

## <a name="defining-a-windows-powershell-container-provider-class"></a>Definizione di una classe del provider di contenitori di Windows PowerShell

Un provider di contenitori di Windows PowerShell deve definire una classe .NET che deriva dalla classe di base [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Ecco la definizione della classe per il provider di contenitori di Windows PowerShell descritta in questa sezione.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Si noti che in questa definizione di classe l'attributo [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) include due parametri. Il primo parametro specifica un nome descrittivo per il provider utilizzato da Windows PowerShell. Il secondo parametro specifica le funzionalità specifiche di Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando. Per questo provider non sono state aggiunte funzionalità specifiche di Windows PowerShell.

## <a name="defining-base-functionality"></a>Definizione della funzionalità di base

Come descritto in [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md), la classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) deriva da diverse altre classi che forniscono diverse funzionalità del provider. Un provider di contenitori di Windows PowerShell deve quindi definire tutte le funzionalità fornite da tali classi.

Per implementare la funzionalità per l'aggiunta di informazioni di inizializzazione specifiche della sessione e per il rilascio di risorse utilizzate dal provider, vedere [creazione di un provider di Windows PowerShell di base](./creating-a-basic-windows-powershell-provider.md). Tuttavia, la maggior parte dei provider (incluso il provider descritto qui) può usare l'implementazione predefinita di questa funzionalità fornita da Windows PowerShell.

Per ottenere l'accesso all'archivio dati, il provider deve implementare i metodi della classe di base [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Per ulteriori informazioni sull'implementazione di questi metodi, vedere [creazione di un provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Per modificare gli elementi di un archivio dati, ad esempio per ottenere, impostare e cancellare elementi, il provider deve implementare i metodi forniti dalla classe di base [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Per ulteriori informazioni sull'implementazione di questi metodi, vedere [creazione di un provider di elementi di Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Recupero di elementi figlio

Per recuperare un elemento figlio, il provider di contenitori di Windows PowerShell deve eseguire l'override del metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) per `Get-ChildItem` supportare le chiamate dal cmdlet. Questo metodo recupera gli elementi figlio dall'archivio dati e li scrive nella pipeline come oggetti. Se viene `recurse` specificato il parametro del cmdlet, il metodo recupera tutti gli elementi figlio indipendentemente dal livello in cui si trovano. Se il `recurse` parametro non è specificato, il metodo recupera solo un singolo livello di elementi figlio.

Di seguito è illustrata l'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) per questo provider. Si noti che questo metodo recupera gli elementi figlio in tutte le tabelle del database quando il percorso indica il database di Access e recupera gli elementi figlio dalle righe di tale tabella se il percorso indica una tabella di dati.

```csharp
protected override void GetChildItems(string path, bool recurse)
{
    // If path represented is a drive then the children in the path are
    // tables. Hence all tables in the drive represented will have to be
    // returned
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table, path, true);

            // if the specified item exists and recurse has been set then
            // all child items within it have to be obtained as well
            if (ItemExists(path) && recurse)
            {
                GetChildItems(path + pathSeparator + table.Name, recurse);
            }
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get the table name, row number and type of path from the
        // path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Obtain all the rows within the table
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);
            WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
        }
        else
        {
            // In this case, the path specified is not valid
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Aspetti da ricordare sull'implementazione di GetChildItem

Le condizioni seguenti possono essere valide per l'implementazione di [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Quando si definisce la classe provider, un provider di contenitori di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) deve garantire che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificate. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- L'implementazione di questo metodo deve prendere in considerazione qualsiasi forma di accesso all'elemento che potrebbe rendere visibile l'elemento all'utente. Ad esempio, se un utente ha accesso in scrittura a un file tramite il provider FileSystem (fornito da Windows PowerShell), ma non l'accesso in lettura, il file esiste ancora e [System. Management. Automation. provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) restituisce `true`. L'implementazione potrebbe richiedere il controllo di un elemento padre per verificare se è possibile enumerare l'elemento figlio.

- Quando si scrivono più elementi, il metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) può richiedere del tempo. È possibile progettare il provider per scrivere gli elementi usando il metodo [System. Management. Automation. provider. CmdletProvider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) uno alla volta. Utilizzando questa tecnica, gli elementi vengono presentati all'utente in un flusso.

- L'implementazione di [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) è responsabile della prevenzione della ricorsione infinita in presenza di collegamenti circolari e simili a. Per riflettere tale condizione è necessario che venga generata un'eccezione di terminazione appropriata.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Associazione di parametri dinamici al cmdlet Get-ChildItem

A volte `Get-ChildItem` il cmdlet che chiama [System. Management. Automation. provider. Containercmdletprovider. GetChildItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) richiede parametri aggiuntivi che vengono specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di contenitori di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) . Questo metodo recupera i parametri dinamici per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al `Get-ChildItem` cmdlet.

Questo provider di contenitori di Windows PowerShell non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Recupero dei nomi degli elementi figlio

Per recuperare i nomi degli elementi figlio, il provider di contenitori di Windows PowerShell deve eseguire l'override del metodo [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) per `Get-ChildItem` supportare le chiamate dal cmdlet quando il relativo `Name` parametro specificato. Questo metodo recupera i nomi degli elementi figlio per il percorso o i nomi degli elementi figlio specificati per tutti i contenitori `returnAllContainers` se viene specificato il parametro del cmdlet. Un nome figlio è la parte foglia di un percorso. Ad esempio, il nome figlio per il percorso c:\windows\system32\abc.dll è "ABC. dll". Il nome figlio per la directory c:\Windows\System32 è "system32".

Di seguito è illustrata l'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) per questo provider. Si noti che il metodo recupera i nomi di tabella se il percorso specificato indica il database di Access (unità) e i numeri di riga se il percorso indica una tabella.

```csharp
protected override void GetChildNames(string path,
                            ReturnContainers returnContainers)
{
    // If the path represented is a drive, then the child items are
    // tables. get the names of all the tables in the drive.
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table.Name, path, true);
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get type, table name and row number from path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Get all the rows in the table and then write out the
            // row numbers.
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row.RowNumber, path, false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);

            WriteItemObject(row.RowNumber, path, false);
        }
        else
        {
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildNames
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Aspetti da ricordare sull'implementazione di GetChildNames

Le condizioni seguenti possono essere valide per l'implementazione di [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Quando si definisce la classe provider, un provider di contenitori di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) deve garantire che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificate. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

  > [!NOTE]
  > Un'eccezione a questa regola si verifica quando `returnAllContainers` viene specificato il parametro del cmdlet. In questo caso, il metodo deve recuperare qualsiasi nome figlio per un contenitore, anche se non corrisponde ai valori di [System. Management. Automation. provider. CmdletProvider. Filter *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [ Proprietà System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)o [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono recuperare i nomi di oggetti che in genere sono nascosti all'utente a meno che non sia specificata la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) . Se il percorso specificato indica un contenitore, la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non è obbligatoria.

- L'implementazione di [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) è responsabile della prevenzione della ricorsione infinita in presenza di collegamenti circolari e simili a. Per riflettere tale condizione è necessario che venga generata un'eccezione di terminazione appropriata.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Associazione di parametri dinamici al cmdlet Get-ChildItem (nome)

A volte `Get-ChildItem` il cmdlet (con `Name` il parametro) richiede parametri aggiuntivi specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di contenitori di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) . Questo metodo recupera i parametri dinamici per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a [System. Management. Automation. RuntimeDefinedParameterDictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)oggetto. Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al `Get-ChildItem` cmdlet.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Ridenominazione di elementi

Per rinominare un elemento, un provider di contenitori di Windows PowerShell deve eseguire l'override del metodo [System. Management. Automation. provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) per `Rename-Item` supportare le chiamate dal cmdlet. Questo metodo modifica il nome dell'elemento in corrispondenza del percorso specificato con il nuovo nome fornito. Il nuovo nome deve essere sempre relativo all'elemento padre (contenitore).

Questo provider non esegue l'override del metodo [System. Management. Automation. provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) . Tuttavia, di seguito è riportata l'implementazione predefinita.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Aspetti da ricordare sull'implementazione di RenameItem

Per l'implementazione di [System. Management. Automation. provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)è possibile che si verifichino le condizioni seguenti:

- Quando si definisce la classe provider, un provider di contenitori di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) deve garantire che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificate. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Il metodo [System. Management. Automation. provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) è destinato alla modifica del nome di un elemento e non per le operazioni di spostamento. L'implementazione del metodo deve scrivere un errore se il `newName` parametro contiene separatori di percorso o potrebbe altrimenti causare la modifica del percorso padre dell'elemento.

- Per impostazione predefinita, le sostituzioni di questo metodo non devono rinominare gli oggetti a meno che non sia specificata la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) . Se il percorso specificato indica un contenitore, la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non è obbligatoria.

- L'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) deve chiamare [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificare il relativo valore restituito prima apportare modifiche all'archivio dati. Questo metodo viene usato per confermare l'esecuzione di un'operazione quando viene apportata una modifica allo stato del sistema, ad esempio la ridenominazione dei file. [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) invia il nome della risorsa da modificare all'utente, con il runtime di Windows PowerShell che prende in considerazione le impostazioni della riga di comando o le variabili di preferenza per determinare elementi da visualizzare.

  Dopo che la chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, il metodo [System. Management. Automation. provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) deve chiamare il [Metodo Metodo System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Questo metodo invia un messaggio di conferma all'utente per consentire un ulteriore feedback per indicare se l'operazione deve essere continuata. Un provider deve chiamare [System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) come controllo aggiuntivo per le modifiche di sistema potenzialmente pericolose.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Associazione di parametri dinamici al cmdlet Rename-Item

A volte `Rename-Item` il cmdlet richiede parametri aggiuntivi che vengono specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di contenitori di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) . Questo metodo recupera i parametri per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al `Rename-Item` cmdlet.

Questo provider di contenitori non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Creazione di nuovi elementi

Per creare nuovi elementi, un provider di contenitori deve implementare il metodo [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) per supportare le `New-Item` chiamate dal cmdlet. Questo metodo crea un elemento di dati che si trova nel percorso specificato. Il `type` parametro del cmdlet contiene il tipo definito dal provider per il nuovo elemento. Ad esempio, il provider FileSystem usa un `type` parametro con un valore "file" o "directory". Il `newItemValue` parametro del cmdlet specifica un valore specifico del provider per il nuovo elemento.

Di seguito è illustrata l'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) per questo provider.

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>Aspetti da ricordare sull'implementazione di NewItem

Per l'implementazione di [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)è possibile che si verifichino le condizioni seguenti:

- Il metodo [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) deve eseguire un confronto senza distinzione tra maiuscole e minuscole della stringa `type` passata nel parametro. Deve inoltre consentire corrispondenze meno ambigue. Per i tipi "file" e "directory", ad esempio, è necessaria solo la prima lettera per evitare ambiguità. Se il `type` parametro indica un tipo che il provider non è in grado di creare, il metodo [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) deve scrivere un'eccezione ArgumentException con un messaggio che indica i tipi il provider può creare.

- Per il `newItemValue` parametro, l'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) è consigliata per accettare almeno le stringhe. Deve inoltre accettare il tipo di oggetto recuperato dal metodo [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) per lo stesso percorso. Il metodo [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) può usare il metodo [System. Management. Automation. LanguagePrimitives. ConvertTo *](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) per convertire i tipi nel tipo desiderato.

- L'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) deve chiamare [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificare il relativo valore restituito prima apportare modifiche all'archivio dati. Dopo la chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce true, il metodo [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) deve chiamare il [Metodo System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metodo come controllo aggiuntivo per le modifiche di sistema potenzialmente pericolose.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Associazione di parametri dinamici al cmdlet New-Item

A volte `New-Item` il cmdlet richiede parametri aggiuntivi che vengono specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di contenitori deve implementare il metodo [System. Management. Automation. provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) . Questo metodo recupera i parametri per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al `New-Item` cmdlet.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Rimozione di elementi

Per rimuovere gli elementi, il provider di Windows PowerShell deve eseguire l'override del metodo [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) per `Remove-Item` supportare le chiamate dal cmdlet. Questo metodo elimina un elemento dall'archivio dati nel percorso specificato. Se il `recurse` parametro `Remove-Item` del cmdlet è impostato su `true`, il metodo rimuove tutti gli elementi figlio indipendentemente dal relativo livello. Se il parametro è impostato su `false`, il metodo rimuove solo un singolo elemento nel percorso specificato.

Questo provider non supporta la rimozione di elementi. Tuttavia, il codice seguente è l'implementazione predefinita di [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Aspetti da ricordare sull'implementazione di RemoveItem

Per l'implementazione di [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)è possibile che si verifichino le condizioni seguenti:

- Quando si definisce la classe provider, un provider di contenitori di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) deve garantire che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificate. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono rimuovere oggetti, a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su true. Se il percorso specificato indica un contenitore, la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non è obbligatoria.

- L'implementazione di [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) è responsabile della prevenzione della ricorsione infinita in presenza di collegamenti circolari e simili a. Per riflettere tale condizione è necessario che venga generata un'eccezione di terminazione appropriata.

- L'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) deve chiamare [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificare il relativo valore restituito prima apportare modifiche all'archivio dati. Dopo che la chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, il metodo [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) deve chiamare il [Metodo System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metodo come controllo aggiuntivo per le modifiche di sistema potenzialmente pericolose.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Associazione di parametri dinamici al cmdlet Remove-Item

A volte `Remove-Item` il cmdlet richiede parametri aggiuntivi che vengono specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di contenitori deve implementare il metodo [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) per gestire questi parametri. Questo metodo recupera i parametri dinamici per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a [System. Management. Automation. RuntimeDefinedParameterDictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)oggetto. Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al `Remove-Item` cmdlet.

Questo provider di contenitori non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Esecuzione di query per gli elementi figlio

Per verificare se esistono elementi figlio nel percorso specificato, il provider di contenitori di Windows PowerShell deve eseguire l'override del metodo [System. Management. Automation. provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) . Questo metodo restituisce `true` se l'elemento ha elementi figlio e `false` in caso contrario. Per un percorso null o vuoto, il metodo considera gli elementi dell'archivio dati come elementi figlio e restituisce `true`.

Di seguito è riportato l'override per il metodo [System. Management. Automation. provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) . Se sono presenti più di due parti del percorso create dal metodo helper ChunkPath, il metodo restituisce `false`, poiché vengono definiti solo un contenitore di database e un contenitore di tabelle. Per ulteriori informazioni su questo metodo helper, vedere il metodo ChunkPath descritto in creazione di [un provider di elementi di Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Aspetti da ricordare sull'implementazione di HasChildItems

Per l'implementazione di [System. Management. Automation. provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)è possibile che si verifichino le condizioni seguenti:

- Se il provider del contenitore espone una radice che contiene punti di montaggio interessanti, l'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) deve `true` restituire quando un valore null o un oggetto viene passata una stringa vuota per il percorso.

## <a name="copying-items"></a>Copia di elementi

Per copiare gli elementi, il provider di contenitori deve implementare il metodo [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) per supportare le `Copy-Item` chiamate dal cmdlet. Questo metodo copia un elemento dati dal percorso indicato dal `path` parametro del cmdlet alla posizione indicata `copyPath` dal parametro. Se il `recurse` parametro viene specificato, il metodo copia tutti i contenitori secondari. Se il parametro non è specificato, il metodo copia solo un singolo livello di elementi.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Aspetti da ricordare sull'implementazione di CopyItem

Le condizioni seguenti possono essere valide per l'implementazione di [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Quando si definisce la classe provider, un provider di contenitori di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione del metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) deve garantire che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificate. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono copiare oggetti sugli oggetti esistenti a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. Ad esempio, il provider FileSystem non copierà c:\temp\abc.txt su un file c:\abc.txt esistente a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia `true`impostata su. Se il percorso specificato nel `copyPath` parametro esiste e indica un contenitore, la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non è obbligatoria. In questo caso [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) deve copiare l'elemento indicato dal `path` parametro nel `copyPath` contenitore indicato dal parametro come figlio.

- L'implementazione di [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) è responsabile della prevenzione della ricorsione infinita in presenza di collegamenti circolari e simili a. Per riflettere tale condizione è necessario che venga generata un'eccezione di terminazione appropriata.

- L'implementazione del metodo [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) deve chiamare [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificare il relativo valore restituito prima apportare modifiche all'archivio dati. Dopo la chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce true, il metodo [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) deve chiamare il [Metodo System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metodo come controllo aggiuntivo per le modifiche di sistema potenzialmente pericolose. Per ulteriori informazioni sulla chiamata di questi metodi, vedere [rinominare gli elementi](#renaming-items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Associazione di parametri dinamici al cmdlet Copy-Item

A volte `Copy-Item` il cmdlet richiede parametri aggiuntivi che vengono specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di contenitori di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) per gestire questi parametri. Questo metodo recupera i parametri per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al `Copy-Item` cmdlet.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Esempio di codice

Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Compilazione del provider di Windows PowerShell

Vedere [come registrare i cmdlet, i provider e le applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Test del provider di Windows PowerShell

Quando il provider di Windows PowerShell è stato registrato con Windows PowerShell, è possibile testarlo eseguendo i cmdlet supportati dalla riga di comando. Tenere presente che l'output di esempio seguente usa un database di Access fittizio.

1. Eseguire il `Get-ChildItem` cmdlet per recuperare l'elenco di elementi figlio da una tabella Customers nel database di Access.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   Viene visualizzato l'output seguente.

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. Eseguire di `Get-ChildItem` nuovo il cmdlet per recuperare i dati di una tabella.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   Viene visualizzato l'output seguente.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. A questo punto `Get-Item` , usare il cmdlet per recuperare gli elementi alla riga 0 nella tabella dati.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   Viene visualizzato l'output seguente.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. Riuso `Get-Item` per recuperare i dati per gli elementi nella riga 0.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   Viene visualizzato l'output seguente.

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. A questo punto `New-Item` , usare il cmdlet per aggiungere una riga a una tabella esistente. Il `Path` parametro specifica il percorso completo della riga e deve indicare un numero di riga maggiore del numero di righe esistente nella tabella. Il `Type` parametro indica "Row" per specificare il tipo di elemento da aggiungere. Infine, il `Value` parametro specifica un elenco delimitato da virgole di valori di colonna per la riga.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Verificare la correttezza dell'operazione del nuovo elemento come indicato di seguito.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   Viene visualizzato l'output seguente.

   ```output
   ID        : 3
   FirstName : Eric
   LastName  : Gruber
   Email     : ericgruber@fabrikam.com
   Title     : President
   Company   : Fabrikam
   WorkPhone : (425) 555-0100
   Address   : 4567 Main Street
   City      : Buffalo
   State     : NY
   Zip       : 98052
   Country   : USA
   ```

## <a name="see-also"></a>Vedere anche

[Creazione di provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Implementazione di un provider di Windows PowerShell per elementi](./creating-a-windows-powershell-item-provider.md)

[Implementazione di un provider di Windows PowerShell per la navigazione](./creating-a-windows-powershell-navigation-provider.md)

[Come registrare cmdlet, provider e applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)