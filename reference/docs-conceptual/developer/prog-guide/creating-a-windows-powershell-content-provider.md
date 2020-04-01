---
title: Creazione di un provider di contenuti di Windows PowerShell
ms.date: 09/13/2016
ms.topic: article
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
ms.openlocfilehash: 149ddb5becf2e0237973e535323ddf8b03b86f24
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500830"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Creazione di un provider di contenuti di Windows PowerShell

In questo argomento viene descritto come creare un provider di Windows PowerShell che consente all'utente di modificare il contenuto degli elementi in un archivio dati. Di conseguenza, un provider che può manipolare il contenuto degli elementi viene definito provider di contenuti Windows PowerShell.

> [!NOTE]
> È possibile scaricare il C# file di origine (AccessDBSampleProvider06.cs) per questo provider utilizzando Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** . Per ulteriori informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="define-the-windows-powershell-content-provider-class"></a>Definire la classe del provider di contenuti Windows PowerShell

Un provider di contenuti Windows PowerShell deve creare una classe .NET che supporta l'interfaccia [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) . Di seguito è riportata la definizione della classe per il provider di elementi descritto in questa sezione.

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Si noti che in questa definizione di classe l'attributo [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) include due parametri. Il primo parametro specifica un nome descrittivo per il provider utilizzato da Windows PowerShell. Il secondo parametro specifica le funzionalità specifiche di Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando. Per questo provider non sono state aggiunte funzionalità specifiche di Windows PowerShell.

## <a name="define-functionality-of-base-class"></a>Definire la funzionalità della classe di base

Come descritto in [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md), la classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) deriva da diverse altre classi che forniscono funzionalità diverse del provider. Un provider di contenuti Windows PowerShell, pertanto, definisce in genere tutte le funzionalità fornite da tali classi.

Per ulteriori informazioni su come implementare la funzionalità per l'aggiunta di informazioni di inizializzazione specifiche della sessione e per il rilascio di risorse utilizzate dal provider, vedere [creazione di un provider di Windows PowerShell di base](./creating-a-basic-windows-powershell-provider.md).
Tuttavia, la maggior parte dei provider, incluso il provider qui descritto, può utilizzare l'implementazione predefinita di questa funzionalità fornita da Windows PowerShell.

Per accedere all'archivio dati, il provider deve implementare i metodi della classe di base [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Per ulteriori informazioni sull'implementazione di questi metodi, vedere [creazione di un provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Per modificare gli elementi di un archivio dati, ad esempio per ottenere, impostare e cancellare elementi, il provider deve implementare i metodi forniti dalla classe di base [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Per ulteriori informazioni sull'implementazione di questi metodi, vedere [creazione di un provider di elementi di Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Per lavorare su archivi dati a più livelli, il provider deve implementare i metodi forniti dalla classe di base [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Per ulteriori informazioni sull'implementazione di questi metodi, vedere [creazione di un provider di contenitori di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

Per supportare i comandi ricorsivi, i contenitori annidati e i percorsi relativi, il provider deve implementare la classe di base [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Questo provider di contenuti di Windows PowerShell, inoltre, può collegare l'interfaccia [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) alla classe di base [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) e pertanto deve implementare i metodi forniti da tale classe. Per ulteriori informazioni, vedere Implementazione di questi metodi, vedere [implementare un provider di Windows PowerShell per la navigazione](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implementazione di un lettore di contenuti

Per leggere il contenuto da un elemento, un provider deve implementare una classe di lettura contenuto che deriva da [System. Management. Automation. provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader).
Il lettore di contenuto per questo provider consente l'accesso al contenuto di una riga in una tabella di dati. La classe Content Reader definisce un metodo **Read** che recupera i dati dalla riga indicata e restituisce un elenco che rappresenta tali dati, un metodo **Seek** che sposta il lettore di contenuto, un metodo **Close** che chiude il lettore di contenuto e un metodo **Dispose** .

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241
"AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Implementazione di un writer di contenuto

Per scrivere contenuto in un elemento, un provider deve implementare una classe del writer del contenuto deriva da [System. Management. Automation. provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter).
La classe Content Writer definisce un metodo **Write** che scrive il contenuto della riga specificato, un metodo **Seek** che sposta il writer del contenuto, un metodo **Close** che chiude il writer del contenuto e un metodo **Dispose** .

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>Recupero del lettore di contenuto

Per ottenere contenuto da un elemento, il provider deve implementare [System. Management. Automation. provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) per supportare il cmdlet `Get-Content`. Questo metodo restituisce il lettore di contenuto per l'elemento che si trova nel percorso specificato. L'oggetto Reader può quindi essere aperto per leggere il contenuto.

Di seguito è illustrata l'implementazione di [System. Management. Automation. provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) per questo metodo per questo provider.

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Aspetti da ricordare sull'implementazione di GetContentReader

Le condizioni seguenti possono essere valide per un'implementazione di [System. Management. Automation. provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Quando si definisce la classe provider, un provider di contenuti di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione del metodo [System. Management. Automation. provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) deve garantire che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificate. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono recuperare un Reader per gli oggetti nascosti all'utente, a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. È necessario scrivere un errore se il percorso rappresenta un elemento nascosto dall'utente e [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostato su `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Associazione di parametri dinamici al cmdlet Get-Content

Il cmdlet `Get-Content` potrebbe richiedere parametri aggiuntivi specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di contenuti di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) . Questo metodo recupera i parametri dinamici per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al cmdlet.

Questo provider di contenitori di Windows PowerShell non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>Recupero del writer di contenuto

Per scrivere contenuto in un elemento, il provider deve implementare [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) per supportare i cmdlet `Set-Content` e `Add-Content`. Questo metodo restituisce il writer di contenuto per l'elemento che si trova nel percorso specificato.

Di seguito è illustrata l'implementazione di [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) per questo metodo.

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Aspetti da ricordare sull'implementazione di GetContentWriter

Per l'implementazione di [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)è possibile che si verifichino le condizioni seguenti:

- Quando si definisce la classe provider, un provider di contenuti di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione del metodo [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) deve garantire che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificate. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono recuperare un writer per gli oggetti che sono nascosti all'utente a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. È necessario scrivere un errore se il percorso rappresenta un elemento nascosto dall'utente e [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostato su `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Associazione di parametri dinamici ai cmdlet Add-Content e set-content

I cmdlet `Add-Content` e `Set-Content` possono richiedere parametri dinamici aggiuntivi che aggiungono un Runtime. Per fornire questi parametri dinamici, il provider di contenuti di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) per gestire questi parametri. Questo metodo recupera i parametri dinamici per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri ai cmdlet.

Questo provider di contenitori di Windows PowerShell non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>Cancellazione di contenuto

Il provider di contenuti implementa il metodo [System. Management. Automation. provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) per supportare il cmdlet `Clear-Content`. Questo metodo rimuove il contenuto dell'elemento nel percorso specificato, ma lascia intatto l'elemento.

Di seguito è illustrata l'implementazione del metodo [System. Management. Automation. provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) per questo provider.

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Aspetti da ricordare sull'implementazione di ClearContent

Le condizioni seguenti possono essere valide per un'implementazione di [System. Management. Automation. provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Quando si definisce la classe provider, un provider di contenuti di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione del metodo [System. Management. Automation. provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) deve garantire che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificate. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono cancellare il contenuto degli oggetti nascosti all'utente, a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. È necessario scrivere un errore se il percorso rappresenta un elemento nascosto dall'utente e [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostato su `false`.

- L'implementazione del metodo [System. Management. Automation. provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) deve chiamare [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificare il relativo valore restituito prima di apportare eventuali modifiche all'archivio dati. Questo metodo viene usato per confermare l'esecuzione di un'operazione quando viene apportata una modifica all'archivio dati, ad esempio la cancellazione di contenuto. Il metodo [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) invia il nome della risorsa da modificare all'utente, con il runtime di Windows PowerShell che gestisce le impostazioni della riga di comando o le variabili di preferenza per determinare gli elementi da visualizzare.

  Dopo che la chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, il metodo [System. Management. Automation. provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) deve chiamare il metodo [System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Questo metodo invia un messaggio all'utente per consentire il feedback per verificare se l'operazione deve essere continuata. La chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) consente un ulteriore controllo della presenza di modifiche di sistema potenzialmente pericolose.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Associazione di parametri dinamici al cmdlet Clear-Content

Il cmdlet `Clear-Content` potrebbe richiedere parametri dinamici aggiuntivi aggiunti in fase di esecuzione. Per fornire questi parametri dinamici, il provider di contenuti di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) per gestire questi parametri. Questo metodo recupera i parametri per l'elemento in corrispondenza del percorso indicato. Questo metodo recupera i parametri dinamici per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al cmdlet.

Questo provider di contenitori di Windows PowerShell non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Codice di esempio

Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetti e formattazione

Quando si scrive un provider, potrebbe essere necessario aggiungere membri a oggetti esistenti o definire nuovi oggetti. Al termine di questa operazione, è necessario creare un file di tipi che Windows PowerShell può utilizzare per identificare i membri dell'oggetto e un file di formato che definisce la modalità di visualizzazione dell'oggetto. Per ulteriori informazioni, vedere [estensione di tipi di oggetti e formattazione](/previous-versions/ms714665(v=vs.85)).

## <a name="building-the-windows-powershell-provider"></a>Compilazione del provider di Windows PowerShell

Vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>Test del provider di Windows PowerShell

Quando il provider di Windows PowerShell è stato registrato con Windows PowerShell, è possibile testarlo eseguendo i cmdlet supportati dalla riga di comando. Ad esempio, testare il provider di contenuti di esempio.

Usare il cmdlet `Get-Content` per recuperare il contenuto dell'elemento specificato nella tabella di database nel percorso specificato dal parametro `Path`. Il parametro `ReadCount` specifica il numero di elementi per il lettore di contenuto definito da leggere (valore predefinito 1). Con la voce di comando seguente, il cmdlet recupera due righe (elementi) dalla tabella e ne Visualizza il contenuto. Si noti che l'output di esempio seguente usa un database di Access fittizio.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```Output
ID        : 1
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
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>Vedere anche

[Creazione di provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Progettare il provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85))

[Implementare un provider di Windows PowerShell per la navigazione](./creating-a-windows-powershell-navigation-provider.md)

[Come registrare cmdlet, provider e applicazioni host](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)
