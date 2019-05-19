---
title: Creazione di un Provider di contenitore di Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: 9e7da13ff559e802d52df475f2a555baeeeef983
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855190"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Creazione di un provider di contenitori di Windows PowerShell

In questo argomento viene descritto come creare un provider di Windows PowerShell che possa usare gli archivi dati a più livelli. Per questo tipo di archivio dati, il livello principale dell'archivio contiene gli elementi radice e ogni livello successivo viene considerato come un nodo di elementi figlio. Tramite l'archivio dati, consentendo all'utente di lavorare su questi nodi figlio, un utente può interagire in modo gerarchico.

I provider compatibile con gli archivi dati a più livelli sono dette provider di contenitore di Windows PowerShell. Tuttavia, tenere presente che è possibile utilizzare un provider di contenitore di Windows PowerShell solo quando è presente un contenitore (non i contenitori nidificati) con gli elementi in esso. Se sono presenti contenitori annidati, è necessario implementare un provider di navigazione di Windows PowerShell. Per altre informazioni sull'implementazione del provider di navigazione di Windows PowerShell, vedere [creazione di un Provider di navigazione di Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> È possibile scaricare il C# file di origine (AccessDBSampleProvider04.cs) per questo provider tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.
>
> Per altre informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [la progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

Il provider di contenitore di Windows PowerShell descritto di seguito definisce il database come relativo contenitore singolo, con le tabelle e le righe del database definiti come elementi del contenitore.

> [!CAUTION]
> Tenere presente che questa progettazione si presuppone che un database con un campo con l'ID del nome e che il tipo del campo è LongInteger.

## <a name="defining-a-windows-powershell-container-provider-class"></a>Definizione di una classe di Provider contenitore di Windows PowerShell

Un provider di contenitore di Windows PowerShell è necessario definire una classe .NET che deriva dal [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe di base. Ecco la definizione di classe per il provider di contenitore di Windows PowerShell descritti in questa sezione.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Si noti che in questa definizione di classe il [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attributo include due parametri. Il primo parametro specifica un nome descrittivo per il provider usato da Windows PowerShell. Il secondo parametro specifica le funzionalità specifiche di Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando. Per questo provider, non sono disponibili funzionalità specifiche di Windows PowerShell che vengono aggiunti.

## <a name="defining-base-functionality"></a>Definizione funzionalità di Base

Come descritto in [la progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md), il [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe deriva da molte altre classi fornite funzionalità del provider diversa. Un provider di contenitore di Windows PowerShell, pertanto, deve definire tutte le funzionalità fornite da tali classi.

Per implementare la funzionalità per l'aggiunta di informazioni di inizializzazione specifiche della sessione e per il rilascio delle risorse usate dal provider, vedere [creazione di un PowerShell Provider di Windows base](./creating-a-basic-windows-powershell-provider.md). Tuttavia, la maggior parte dei fornitori (tra cui il provider descritto di seguito) è possono usare l'implementazione predefinita di questa funzionalità fornita da Windows PowerShell.

Per ottenere l'accesso all'archivio dati, il provider deve implementare i metodi del [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe di base. Per altre informazioni sull'implementazione di questi metodi, vedere [creazione di un Provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Per modificare gli elementi di un archivio dati, ad esempio il recupero, impostazione e cancellare elementi, il provider deve implementare i metodi forniti dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe di base. Per altre informazioni sull'implementazione di questi metodi, vedere [creazione di un Provider di Windows PowerShell elemento](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Recupero degli elementi figlio

Per recuperare un elemento figlio, il provider di contenitore di Windows PowerShell è necessario eseguire l'override di [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metodo per supportare le chiamate dal `Get-ChildItem` cmdlet. Questo metodo recupera gli elementi figlio dall'archivio dati e li scrive alla pipeline come oggetti. Se il `recurse` parametro del cmdlet è specificato, il metodo recupera tutti gli elementi figlio indipendentemente dal livello sono a. Se il `recurse` parametro viene omesso, il metodo recupera un solo livello degli elementi figlio.

Ecco l'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metodo per questo provider. Si noti che questo metodo recupera gli elementi figlio in tutte le tabelle di database quando il percorso indica il database di Access e recupera gli elementi figlio dalle righe della tabella se il percorso indica una tabella di dati.

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

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Aspetti da ricordare sull'implementazione GetChildItems

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Quando si definisce la classe del provider, un provider di contenitore di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione. In questi casi, l'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) deve garantire che il percorso passato al metodo soddisfi i requisiti della classe specificata (metodo) funzionalità. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- L'implementazione di questo metodo deve tenere conto alcuna forma di accesso per l'elemento che potrebbe rendere visibili all'utente l'elemento. Ad esempio, se un utente ha accesso in scrittura a un file tramite il provider FileSystem (fornito da Windows PowerShell), ma non l'accesso in lettura, il file esista ancora e [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) restituisce `true`. L'implementazione potrebbe richiedere la verifica di un elemento padre per vedere se l'elemento figlio può essere enumerata.

- Durante la scrittura di più elementi, il [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metodo può richiedere alcuni minuti. È possibile progettare il provider per scrivere gli elementi usando il [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metodo uno alla volta. Utilizzando questa tecnica presenta gli elementi per l'utente in un flusso.

- L'implementazione di [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) è responsabile del divieto una ricorsione infinita quando sono presenti collegamenti circolari e così via. Un'eccezione di terminazione appropriata deve essere generata in modo da riflettere tale condizione.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Associare i parametri dinamici per il Cmdlet Get-ChildItem

In alcuni casi il `Get-ChildItem` cmdlet che chiama [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) richiede parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici, il provider di contenitore di Windows PowerShell deve implementare il [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) (metodo). Questo metodo recupera i parametri dinamici per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere i parametri di `Get-ChildItem` cmdlet.

Questo provider di contenitore di Windows PowerShell non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Il recupero dei nomi di elementi figlio

Per recuperare i nomi degli elementi figlio, il provider di contenitore di Windows PowerShell è necessario eseguire l'override di [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metodo per supportare le chiamate dalle `Get-ChildItem`cmdlet quando relativo `Name` parametro è specificato. Questo metodo recupera i nomi degli elementi figlio per i percorso o figlio elemento i nomi specificati per tutti i contenitori se il `returnAllContainers` parametro del cmdlet è specificato. La porzione di foglia di un percorso è un nome di figlio. Ad esempio, il nome figlio c:\windows\system32\abc.dll il percorso è "abc. dll". Il nome del figlio per la directory c:\windows\system32 è "system32".

Ecco l'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metodo per questo provider. Si noti che il metodo recupera i nomi di tabella, se il percorso specificato indica i database di Access (unità) e i numeri di riga se il percorso indica una tabella.

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

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Aspetti da ricordare sull'implementazione GetChildNames

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Quando si definisce la classe del provider, un provider di contenitore di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione. In questi casi, l'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) deve garantire che il percorso passato al metodo soddisfi i requisiti della classe specificata (metodo) funzionalità. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

  > [!NOTE]
  > Si verifica un'eccezione a questa regola quando le `returnAllContainers` parametro del cmdlet è specificato. In questo caso, il metodo deve recuperare qualsiasi nome figlio per un contenitore, anche se non corrispondono ai valori di [System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), oppure [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) proprietà.

- Per impostazione predefinita, gli override di questo metodo non devono recuperare i nomi degli oggetti che sono in genere nascoste all'utente, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è specificata la proprietà. Se il percorso specificato indica un contenitore, il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) proprietà non è necessaria.

- L'implementazione di [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) è responsabile del divieto una ricorsione infinita quando sono presenti collegamenti circolari e così via. Un'eccezione di terminazione appropriata deve essere generata in modo da riflettere tale condizione.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Associare i parametri dinamici per il Cmdlet Get-ChildItem (nome)

In alcuni casi il `Get-ChildItem` cmdlet (con il `Name` parametro) richiede parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici, il provider di contenitore di Windows PowerShell deve implementare il [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) (metodo). Questo metodo recupera i parametri dinamici per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere i parametri di `Get-ChildItem` cmdlet.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Ridenominazione di elementi

Per rinominare un elemento, è necessario eseguire l'override di un provider di contenitore di Windows PowerShell il [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metodo per supportare le chiamate dal `Rename-Item` cmdlet. Questo metodo modifica il nome dell'elemento nel percorso specificato per il nuovo nome fornito. Il nuovo nome deve essere sempre rispetto all'elemento padre (contenitore).

Questo provider non esegue l'override di [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) (metodo). Tuttavia, di seguito è l'implementazione predefinita.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Aspetti da ricordare sull'implementazione RenameItem

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Quando si definisce la classe del provider, un provider di contenitore di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione. In questi casi, l'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) deve garantire che il percorso passato al metodo soddisfi i requisiti della classe specificata (metodo) funzionalità. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Il [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metodo è stato progettato per la modifica del nome di un solo elemento e non per le operazioni di spostamento. L'implementazione del metodo deve scrivere un errore se il `newName` parametro contiene separatori del percorso o in caso contrario, potrebbe causare l'elemento per modificarne il percorso padre.

- Per impostazione predefinita, gli override di questo metodo devono non rinominare oggetti, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è specificata la proprietà. Se il percorso specificato indica un contenitore, il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) proprietà non è necessaria.

- L'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metodo deve chiamare [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e controllare il valore restituito corrispondente prima di apportare modifiche all'archivio dati. Questo metodo viene utilizzato per confermare l'esecuzione di un'operazione quando viene apportata una modifica lo stato del sistema, ad esempio, la ridenominazione dei file. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) invia il nome della risorsa da modificare per l'utente, con il runtime di Windows PowerShell prendendo in considerazione eventuali impostazioni riga di comando o variabili di preferenza in determinare ciò che deve essere visualizzato.

  Dopo la chiamata a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, il [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metodo deve chiamare il [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (metodo). Questo metodo invia un messaggio di un messaggio di conferma all'utente per consentire ulteriori commenti e suggerimenti a dire se l'operazione deve proseguire. Un provider deve chiamare [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) come verifica aggiuntiva per le modifiche del sistema potenzialmente pericolose.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Associare i parametri dinamici per il Cmdlet Rename-Item

In alcuni casi il `Rename-Item` cmdlet richiede parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici, provider di contenitore di Windows PowerShell deve implementare il [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) (metodo). Questo metodo recupera i parametri per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere i parametri di `Rename-Item` cmdlet.

Questo provider di contenitore non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Creazione di nuovi elementi

Per creare nuovi elementi, è necessario implementare un provider di contenitore di [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metodo per supportare le chiamate dal `New-Item` cmdlet. Questo metodo crea un elemento di dati che si trova nel percorso specificato. Il `type` parametro del cmdlet contiene il tipo definito dal provider per il nuovo elemento. Ad esempio, il provider FileSystem utilizza un `type` parametro con il valore "file" o "directory". Il `newItemValue` parametro del cmdlet consente di specificare un valore specifico del provider per il nuovo elemento.

Ecco l'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metodo per questo provider.

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

#### <a name="things-to-remember-about-implementing-newitem"></a>Aspetti da ricordare sull'implementazione NewItem

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Il [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metodo deve eseguire un confronto tra maiuscole e minuscole della stringa passata il `type` parametro. Deve inoltre consentire corrispondenze meno ambigue. Per i tipi "file" e "directory", ad esempio, solo la prima lettera è necessario per risolvere l'ambiguità. Se il `type` parametro indica un tipo non è possibile creare il provider, il [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metodo deve scrivere un'eccezione ArgumentException con un messaggio il provider che indicano i tipi può creare.

- Per il `newItemValue` parametro, l'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metodo è consigliato per accettare stringhe come minimo. È anche necessario accettare il tipo di oggetto che viene recuperato dal [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metodo per lo stesso percorso. Il [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metodo può utilizzare il [System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) metodo per convertire i tipi di tipo desiderato.

- L'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metodo deve chiamare [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e controllare il valore restituito corrispondente prima di apportare modifiche all'archivio dati. Dopo la chiamata a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce true, il [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) il metodo deve chiamare il [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metodo come un ulteriore controllo per le modifiche del sistema potenzialmente pericolose.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Associare i parametri dinamici per il Cmdlet New-Item

In alcuni casi il `New-Item` cmdlet richiede parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici, il provider di contenitore deve implementare il [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) (metodo). Questo metodo recupera i parametri per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere i parametri di `New-Item` cmdlet.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Rimozione di elementi

Per rimuovere gli elementi, il provider di Windows PowerShell è necessario eseguire l'override di [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metodo per supportare le chiamate dal `Remove-Item` cmdlet. Questo metodo consente di eliminare un elemento dall'archivio dati nel percorso specificato. Se il `recurse` parametro il `Remove-Item` cmdlet è impostata su `true`, il metodo rimuove tutti gli elementi figlio, indipendentemente dal relativo livello. Se il parametro è impostato su `false`, il metodo rimuove solo un singolo elemento nel percorso specificato.

Questo provider non supporta la rimozione di elementi. Tuttavia, il codice seguente è l'implementazione predefinita di [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Aspetti da ricordare sull'implementazione RemoveItem

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Quando si definisce la classe del provider, un provider di contenitore di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione. In questi casi, l'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) deve garantire che il percorso passato al metodo soddisfi i requisiti della classe specificata (metodo) funzionalità. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Per impostazione predefinita, gli override di questo metodo non necessario rimuovere gli oggetti, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) viene impostata su true. Se il percorso specificato indica un contenitore, il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) proprietà non è necessaria.

- L'implementazione di [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) è responsabile del divieto una ricorsione infinita quando sono presenti collegamenti circolari e così via. Un'eccezione di terminazione appropriata deve essere generata in modo da riflettere tale condizione.

- L'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metodo deve chiamare [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e controllare il valore restituito corrispondente prima di apportare modifiche all'archivio dati. Dopo la chiamata a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, il [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metodo deve chiamare il [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metodo come un ulteriore controllo per le modifiche del sistema potenzialmente pericolose.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Associare i parametri dinamici per il Cmdlet Remove-Item

In alcuni casi il `Remove-Item` cmdlet richiede parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici, il provider di contenitore deve implementare il [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) metodo per gestire questi parametri. Questo metodo recupera i parametri dinamici per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere i parametri di `Remove-Item` cmdlet.

Questo provider di contenitore non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>L'esecuzione di query per gli elementi figlio

Per verificare se esistono elementi figlio nel percorso specificato, il provider di contenitore di Windows PowerShell è necessario eseguire l'override di [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) (metodo). Questo metodo restituisce `true` se l'elemento dispone di figli, e `false` in caso contrario. Per un percorso null o vuoto, il metodo prende in considerazione tutti gli elementi nell'archivio dati come elementi figlio e restituisce `true`.

Ecco l'override per il [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) (metodo). Se sono presenti più di due parti di percorso create dal metodo helper ChunkPath, il metodo restituisce `false`, dal momento che sono definiti solo un contenitore del database e un contenitore della tabella. Per altre informazioni su questo metodo di supporto, vedere il metodo ChunkPath viene illustrato in [creazione di un Provider di Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Aspetti da ricordare sull'implementazione HasChildItems

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Se il contenitore espone una radice che contiene interessanti punti di montaggio, l'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) metodo dovrebbe restituire `true`quando un valore null o una stringa vuota viene passata per il percorso.

## <a name="copying-items"></a>Copia di elementi

Per copiare gli elementi, il provider di contenitore deve implementare il [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metodo per supportare le chiamate dal `Copy-Item` cmdlet. Questo metodo consente di copiare un elemento di dati dalla posizione indicata dal `path` del cmdlet nel percorso indicato dal parametro di `copyPath` parametro. Se il `recurse` viene specificato, il metodo di copia tutti i contenitori secondari. Se il parametro viene omesso, il metodo di copia un solo livello di elementi.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Aspetti da ricordare sull'implementazione di CopyItem

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Quando si definisce la classe del provider, un provider di contenitore di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione. In questi casi, l'implementazione del [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) deve garantire che il percorso passato al metodo soddisfi i requisiti della classe specificata (metodo) funzionalità. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Per impostazione predefinita, gli override di questo metodo non necessario copiare gli oggetti tramite gli oggetti esistenti, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Ad esempio, il provider FileSystem non copierà c:\temp\abc.txt tramite un file esistente c:\abc.txt a meno che non la [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Se il percorso specificato nella `copyPath` parametro è presente e indica un contenitore, il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) proprietà non è necessaria. In questo caso, [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) deve copiare l'elemento indicato dalle `path` parametro per il contenitore indicato dal `copyPath` parametro come elemento figlio.

- L'implementazione di [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) è responsabile del divieto una ricorsione infinita quando sono presenti collegamenti circolari e così via. Un'eccezione di terminazione appropriata deve essere generata in modo da riflettere tale condizione.

- L'implementazione del [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metodo deve chiamare [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e controllare il valore restituito corrispondente prima di apportare modifiche all'archivio dati. Dopo la chiamata a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce true, il [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) il metodo deve chiamare il [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metodo come un ulteriore controllo per le modifiche del sistema potenzialmente pericolose. Per altre informazioni sulla chiamata di questi metodi, vedere [rinominare elementi](#renaming-items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Associare i parametri dinamici per il Cmdlet Copy-Item

In alcuni casi il `Copy-Item` cmdlet richiede parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici, il provider di contenitore di Windows PowerShell deve implementare il [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) gestire queste (metodo) parametri. Questo metodo recupera i parametri per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere i parametri di `Copy-Item` cmdlet.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Esempio di codice

Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Creazione del Provider di Windows PowerShell

Visualizzare [come registrare i cmdlet, provider e ospitare applicazioni](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Test di un Provider Windows PowerShell

Quando il provider di Windows PowerShell è stato registrato con Windows PowerShell, è possibile eseguirne il test eseguendo il cmdlet supportati nella riga di comando. Tenere presente che l'output di esempio seguente usa un database di Access fittizio.

1. Eseguire il `Get-ChildItem` cmdlet per recuperare l'elenco degli elementi figlio da una tabella Customers nel database di Access.

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

2. Eseguire il `Get-ChildItem` cmdlet per recuperare i dati di una tabella.

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

3. A questo punto usare il `Get-Item` cmdlet per recuperare gli elementi alla riga 0 nella tabella dati.

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

4. Riutilizzare `Get-Item` per recuperare i dati per gli elementi nella riga 0.

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

5. A questo punto usare il `New-Item` cmdlet per aggiungere una riga a una tabella esistente. Il `Path` parametro specifica il percorso completo alla riga e deve indicare un numero di riga che è maggiore del numero di righe nella tabella esistente. Il `Type` parametro indica "riga" per specificare che il tipo di elemento da aggiungere. Infine, il `Value` parametro specifica un elenco delimitato da virgole di valori di colonna per la riga.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Verificare la correttezza della nuova operazione di elemento come indicato di seguito.

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

[Progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Implementazione di un Provider di Windows PowerShell](./creating-a-windows-powershell-item-provider.md)

[Implementazione di un Provider di navigazione Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)