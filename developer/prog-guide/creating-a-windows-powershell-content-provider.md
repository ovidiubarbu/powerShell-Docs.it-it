---
title: Creazione di un Provider di contenuto di PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: 1bccbfab55f4ba4476678b130bd9db91eed7df80
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795318"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Creazione di un provider di contenuti di Windows PowerShell

Questo argomento descrive come creare un provider di Windows PowerShell che consente all'utente di modificare il contenuto degli elementi in un archivio dati. Di conseguenza, un provider che consente di modificare il contenuto degli elementi viene considerato un provider di contenuti di Windows PowerShell.

> [!NOTE]
> È possibile scaricare il C# file di origine (AccessDBSampleProvider06.cs) per questo provider tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.
>
> Per altre informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [la progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

Nell'elenco seguente contiene le sezioni in questo argomento. Se non si ha familiarità con la scrittura di un provider di contenuti di Windows PowerShell, leggere le sezioni riportate nell'ordine in cui appaiono. Tuttavia, se si ha familiarità con la scrittura di un provider di contenuti di Windows PowerShell, passare direttamente alle informazioni necessarie.

- [Definizione della classe di Provider di Windows PowerShell contenuto](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [Definizione funzionalità di Base](#Define-Functionality-of-Base-Class)

- [Implementazione di un lettore di contenuti](#Implementing-a-Content-Reader)

- [Implementazione di un agente di scrittura del contenuto](#Implementing-a-Content-Writer)

- [Il recupero del lettore di contenuti](#Retrieving-the-Content-Reader)

- [Associare i parametri dinamici al `Get-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [Il recupero del Writer del contenuto](#Retrieving-the-Content-Writer)

- [Associazione di parametri dinamici al Add_Content e `Set-Content` cmdlet](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [La cancellazione del contenuto](#Clearing-Content)

- [Associare i parametri dinamici al `Clear-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [Esempio di codice](#Code-Sample)

- [Definizione di tipi di oggetto e formattazione](#defining-object-types-and-formatting)

- [Creazione del provider di Windows PowerShell](#Building-the-Windows-PowerShell-Provider)

- [Test di un provider Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a>Definire la classe di Provider di Windows PowerShell contenuto

Un provider di contenuti di Windows PowerShell è necessario creare una classe .NET che supporta il [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaccia. Ecco la definizione di classe per il provider dell'elemento descritto in questa sezione.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Si noti che in questa definizione di classe il [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attributo include due parametri. Il primo parametro specifica un nome descrittivo per il provider usato da Windows PowerShell. Il secondo parametro specifica le funzionalità specifiche di Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando. Per questo provider, non sono disponibili funzionalità specifiche di Windows PowerShell aggiunti.

## <a name="define-functionality-of-base-class"></a>Definire le funzionalità della classe di Base

Come descritto in [Provider di progettazione di Windows PowerShell](./designing-your-windows-powershell-provider.md), il [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe deriva da molte altre classi fornite funzionalità del provider diversa. Un provider di contenuti di Windows PowerShell, pertanto, in genere definisce tutte le funzionalità fornite da tali classi.

Per altre informazioni su come implementare la funzionalità per l'aggiunta di informazioni di inizializzazione specifiche della sessione e per il rilascio delle risorse usate dal provider, vedere [creazione di un PowerShell Provider di Windows base](./creating-a-basic-windows-powershell-provider.md). Tuttavia, la maggior parte dei provider, inclusi il provider descritto in questo caso, è possibile usare l'implementazione predefinita di questa funzionalità fornita da Windows PowerShell.

Per accedere all'archivio dati, il provider deve implementare i metodi del [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe di base. Per altre informazioni sull'implementazione di questi metodi, vedere [creazione di un Provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Per modificare gli elementi di un archivio dati, ad esempio il recupero, impostazione e cancellare elementi, il provider deve implementare i metodi forniti dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe di base. Per altre informazioni sull'implementazione di questi metodi, vedere [creazione di un Provider di Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Per usare gli archivi dati a più livelli, il provider deve implementare i metodi forniti dal [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe di base. Per altre informazioni sull'implementazione di questi metodi, vedere [creazione di un Provider di contenitore di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

Per supportare i comandi ricorsiva, contenitori nidificati e i percorsi relativi, il provider deve implementare il [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe di base. Questo provider di contenuti di Windows PowerShell possono inoltre consente di collegare [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaccia di [ System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe di base e pertanto deve implementare i metodi forniti da tale classe. Per altre informazioni, vedere l'implementazione di questi metodi, vedere [implementare un Provider di navigazione Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implementazione di un lettore di contenuti

Per leggere il contenuto da un elemento, un provider deve implementa una classe di lettore di contenuti che deriva da [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader). Il lettore di contenuti per questo provider consente l'accesso al contenuto di una riga in una tabella dati. Definisce la classe reader contenuto un **Read** metodo che recupera i dati della riga indicata e restituisce un elenco che rappresenta i dati, un **Seek** metodo che si sposta il lettore di contenuti, un  **Chiusura** metodo chiude il lettore di contenuti, e una **Dispose** (metodo).

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Implementazione di un agente di scrittura del contenuto

Per scrivere contenuto in un elemento, un provider deve implementare un contenuto writer classe deriva da [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter). Definisce la classe di writer contenuto un **scrivere** metodo che scrive il contenuto della riga specificata, un **Seek** metodo verrà spostato nel writer di contenuto, una **Chiudi** (metodo) che chiude il writer di contenuto e un **Dispose** (metodo).

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>Il recupero del lettore di contenuti

Per ottenere contenuto da un elemento, il provider deve implementare il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) per supportare il `Get-Content` cmdlet. Questo metodo restituisce il lettore di contenuti per l'elemento situato nel percorso specificato. L'oggetto lettore può quindi essere aperto per la lettura del contenuto.

Ecco l'implementazione di [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) per questo metodo per questo provider.

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

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Aspetti da ricordare sull'implementazione GetContentReader

Le condizioni seguenti possono applicare a un'implementazione di [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Quando si definisce la classe del provider, un provider di contenuti di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumerazione. In questi casi, l'implementazione del [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metodo è necessario assicurarsi che il percorso passato al metodo soddisfi i requisiti dell'oggetto specificato funzionalità. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Per impostazione predefinita, gli override di questo metodo non devono recuperare un lettore per gli oggetti che sono nascosti all'utente, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Deve essere scritto un errore se il percorso rappresenta un elemento è nascosto da parte dell'utente e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Associare i parametri dinamici per il Cmdlet Get-Content

Il `Get-Content` cmdlet potrebbero richiedere parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici, il provider di contenuti di Windows PowerShell deve implementare il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) (metodo). Questo metodo recupera i parametri dinamici per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere parametri al cmdlet.

Questo provider di contenitore di Windows PowerShell non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>Il recupero del Writer del contenuto

Per scrivere contenuto in un elemento, il provider deve implementare il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) per supportare le `Set-Content` e `Add-Content` cmdlet. Questo metodo restituisce il writer di contenuto per l'elemento situato nel percorso specificato.

Ecco l'implementazione di [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) per questo metodo.

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

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Aspetti da ricordare sull'implementazione GetContentWriter

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Quando si definisce la classe del provider, un provider di contenuti di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumerazione. In questi casi, l'implementazione del [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) metodo è necessario assicurarsi che il percorso passato al metodo soddisfi i requisiti dell'oggetto specificato funzionalità. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Per impostazione predefinita, gli override di questo metodo non devono recuperare un agente di scrittura per gli oggetti che sono nascosti all'utente, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Deve essere scritto un errore se il percorso rappresenta un elemento è nascosto da parte dell'utente e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Associare i parametri dinamici per i cmdlet Add-Content e Set-Content

Il `Add-Content` e `Set-Content` cmdlet potrebbero richiedere parametri dinamici aggiuntivi che vengono aggiunti a un runtime. Per fornire i parametri dinamici, il provider di contenuti di Windows PowerShell deve implementare il [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) gestire queste (metodo) parametri. Questo metodo recupera i parametri dinamici per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere parametri ai cmdlet.

Questo provider di contenitore di Windows PowerShell non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>La cancellazione del contenuto

Implementa il provider di contenuti di [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metodo supportare il `Clear-Content` cmdlet. Questo metodo rimuove il contenuto dell'elemento nel percorso specificato, ma lascia intatto l'elemento.

Ecco l'implementazione del [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metodo per questo provider.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Aspetti da ricordare sull'implementazione ClearContent

Le condizioni seguenti possono applicare a un'implementazione di [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Quando si definisce la classe del provider, un provider di contenuti di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumerazione. In questi casi, l'implementazione del [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metodo è necessario assicurarsi che il percorso passato al metodo soddisfi i requisiti dell'oggetto specificato funzionalità. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Per impostazione predefinita, gli override di questo metodo non cancellare il contenuto degli oggetti che sono nascosti all'utente, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Deve essere scritto un errore se il percorso rappresenta un elemento è nascosto da parte dell'utente e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `false`.

- L'implementazione del [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metodo deve chiamare [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificarne il valore restituito prima di apportare modifiche all'archivio dati. Questo metodo viene utilizzato per confermare l'esecuzione di un'operazione quando viene apportata una modifica all'archivio dati, ad esempio la cancellazione del contenuto. Il [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) metodo invia il nome della risorsa da modificare per l'utente, con il runtime di Windows PowerShell gestisce tutte le impostazioni della riga di comando o delle preferenze variabili per determinare che cosa deve essere visualizzata.

  Dopo la chiamata a [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, il [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metodo deve chiamare il [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (metodo). Questo metodo invia un messaggio all'utente per consentire il feedback verificare se l'operazione deve proseguire. La chiamata a [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) consente un controllo aggiuntivo per le modifiche del sistema potenzialmente pericolose.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Associare i parametri dinamici per il Cmdlet Clear-Content

Il `Clear-Content` cmdlet potrebbero richiedere parametri dinamici aggiuntivi che vengono aggiunti in fase di esecuzione. Per fornire i parametri dinamici, il provider di contenuti di Windows PowerShell deve implementare il [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) gestire queste (metodo) parametri. Questo metodo recupera i parametri per l'elemento nel percorso indicato. Questo metodo recupera i parametri dinamici per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere parametri al cmdlet.

Questo provider di contenitore di Windows PowerShell non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Esempio di codice

Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetto e formattazione

Durante la scrittura di un provider, potrebbe essere necessario aggiungere i membri per gli oggetti esistenti o definire nuovi oggetti. Quando questa operazione, è necessario creare un file di tipi che è possibile usare Windows PowerShell per identificare i membri dell'oggetto e un file di formato che definisce la modalità di visualizzazione dell'oggetto. Per altre informazioni, vedere [estendendo i tipi di oggetto e formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Creazione del Provider di Windows PowerShell

Visualizzare [come registrare i cmdlet, provider e ospitare applicazioni](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Test di un Provider Windows PowerShell

Quando il provider di Windows PowerShell è stato registrato con Windows PowerShell, è possibile eseguirne il test eseguendo il cmdlet supportati nella riga di comando. Ad esempio, testare il provider di contenuti di esempio.

Usare la `Get-Content` cmdlet per recuperare il contenuto dell'elemento specificato nella tabella di database nel percorso specificato per il `Path` parametro. Il `ReadCount` parametro specifica il numero di elementi per il lettore di contenuti definito da leggere (valore predefinito 1). Con la seguente voce del comando, il cmdlet recupera due righe (elementi) dalla tabella e viene visualizzato il relativo contenuto. Si noti che l'output di esempio seguente usa un database di Access fittizio.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
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

[Provider di progettazione di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estensione di tipi di oggetto e la formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementare un provider di navigazione Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)
