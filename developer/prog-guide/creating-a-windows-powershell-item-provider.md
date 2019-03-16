---
title: Creazione di un Provider Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: f2c9e10f0dc392399cf062500b7f28b3d1c07f6e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055122"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Creazione di un provider di elementi di Windows PowerShell

Questo argomento descrive come creare un provider di Windows PowerShell che consente di modificare i dati in un archivio dati. In questo argomento, vengono definiti gli elementi di dati nell'archivio per archiviare gli "elementi" dei dati. Di conseguenza, un provider che consente di modificare i dati nell'archivio viene considerato un provider di Windows PowerShell.

> [!NOTE]
> È possibile scaricare il C# file di origine (AccessDBSampleProvider03.cs) per questo provider tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.
>
> Per altre informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [la progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

Il provider di elementi di Windows PowerShell descritto in questo argomento Ottiene gli elementi di dati da un database di Access. In questo caso, un "elemento" è una tabella del database di Access o una riga in una tabella.

Nell'elenco seguente contiene le sezioni in questo argomento. Se non si ha familiarità con la scrittura di un provider di Windows PowerShell, leggere le sezioni riportate nell'ordine in cui appaiono. Tuttavia, se si ha familiarità con la scrittura di un provider di Windows PowerShell, passare direttamente alle informazioni che è necessario:

- [Definizione della classe di Provider di Windows PowerShell elemento](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [Definizione funzionalità di Base](#Defining-Base-Functionality)

- [Verifica la validità di percorso](#Checking-for-Path-Validity)

- [Determinare se esiste un elemento](#Determining-if-an-Item-Exists)

- [Associare i parametri dinamici al `Test-Path` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [Il recupero di un elemento](#Retrieving-an-Item)

- [Associare i parametri dinamici al `Get-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [Impostazione di un elemento](#Setting-an-Item)

- [Associare i parametri dinamici al `Set-Item` Cmdlet](#Retrieving-Dynamic-Parameters-for-SetItem)

- [La cancellazione di un elemento](#Clearing-an-Item)

- [Associare i parametri dinamici per il Cmdlet Clear-Item](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [Esecuzione di un'azione predefinita per un elemento](#Performing-a-Default-Action-for-an-Item)

- [Recupero dei parametri dinamici per InvokeDefaultAction](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [Implementazione di classi e metodi di supporto](#Implementing-Helper-Methods-and-Classes)

- [Esempio di codice](#Code-Sample)

- [Definizione di tipi di oggetto e formattazione](#Defining-Object-Types-and-Formatting)

- [Creazione del Provider di Windows PowerShell](#Building-the-Windows-PowerShell-provider)

- [Test di un Provider Windows PowerShell](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>Definizione della classe di Provider di Windows PowerShell elemento

Un provider di Windows PowerShell è necessario definire una classe .NET che deriva dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe di base. Di seguito è la definizione di classe per il provider dell'elemento descritto in questa sezione.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Si noti che in questa definizione di classe il [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attributo include due parametri. Il primo parametro specifica un nome descrittivo per il provider usato da Windows PowerShell. Il secondo parametro specifica le funzionalità specifiche di Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando. Per questo provider, non sono disponibili funzionalità specifiche di Windows PowerShell aggiunti.

## <a name="defining-base-functionality"></a>Definizione funzionalità di Base

Come descritto in [Provider di progettazione di Windows PowerShell](./designing-your-windows-powershell-provider.md), il [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe deriva da molte altre classi fornite diverse funzionalità del provider. Un provider di Windows PowerShell, pertanto, è necessario definire tutte le funzionalità fornite da tali classi.

Per altre informazioni su come implementare la funzionalità per l'aggiunta di informazioni di inizializzazione specifiche della sessione e per rilasciare le risorse utilizzate dal provider, vedere [creazione di un PowerShell Provider di Windows base](./creating-a-basic-windows-powershell-provider.md). Tuttavia, la maggior parte dei provider, inclusi il provider descritto in questo caso, è possibile usare l'implementazione predefinita di questa funzionalità fornita da Windows PowerShell.

Prima che il provider di Windows PowerShell è possibile modificare gli elementi nell'archivio, deve implementare i metodi del [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe per accedere all'archivio dati di base. Per altre informazioni sull'implementazione di questa classe, vedere [creazione di un Provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Verifica la validità di percorso

Quando si cerca un elemento di dati, il runtime di Windows PowerShell offre un sistema di un percorso di Windows PowerShell per il provider, come definito nella sezione "Concetti PSPath" del [modalità di funzionamento di Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). Un provider di Windows PowerShell è necessario verificare la validità sintattica e semantica di qualsiasi percorso passato mediante l'implementazione di [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) (metodo). Questo metodo restituisce `true` se il percorso sia valido, e `false` in caso contrario. Essere consapevoli che l'implementazione di questo metodo non deve verificare l'esistenza dell'elemento nel percorso, ma solo che il percorso sia sintatticamente e semanticamente corretto.

Ecco l'implementazione del [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metodo per questo provider. Si noti che questa implementazione chiama un metodo helper NormalizePath per convertire tutti i separatori del percorso a uno uniforme.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Determinare se esiste un elemento

Dopo aver verificato il percorso, il runtime di Windows PowerShell è necessario determinare se esiste un elemento di dati in tale percorso. Per supportare questo tipo di query, il provider di Windows PowerShell implementa il [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) (metodo). Questo metodo restituisce `true` un elemento viene trovato nel percorso specificato e `false` (predefinito) in caso contrario.

Ecco l'implementazione del [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metodo per questo provider. Si noti che questo metodo chiama i metodi helper PathIsDrive ChunkPath e GetTable che usa un provider definito oggetto DatabaseTableInfo.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Aspetti da ricordare sull'implementazione ItemExists

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Quando si definisce la classe del provider, un provider di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumerazione. In questi casi, l'implementazione del [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metodo è necessario assicurarsi che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificato. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- L'implementazione di questo metodo deve gestire qualsiasi tipo di accesso all'elemento che potrebbe rendere visibili all'utente l'elemento. Ad esempio, se un utente ha accesso in scrittura a un file tramite il provider FileSystem (fornito da Windows PowerShell), ma non l'accesso in lettura, il file esista ancora e [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) restituisce `true`. L'implementazione potrebbe richiedere la verifica di un elemento padre per vedere se l'elemento figlio può essere enumerata.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Associare i parametri dinamici per il Cmdlet Test-Path

In alcuni casi il `Test-Path` cmdlet che chiama [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) richiede parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici di PowerShell di Windows provider di elementi deve implementare il [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) (metodo). Questo metodo recupera i parametri dinamici per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere i parametri di `Test-Path` cmdlet.

Questo provider di Windows PowerShell non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Il recupero di un elemento

Per recuperare un elemento, il provider di Windows PowerShell è necessario eseguire l'override [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metodo per supportare le chiamate dal `Get-Item` cmdlet. Questo metodo scrive l'elemento mediante il [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) (metodo).

Ecco l'implementazione del [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metodo per questo provider. Si noti che questo metodo Usa i metodi helper GetTable e GetRow per recuperare gli elementi che sono le tabelle del database di Access o righe in una tabella di dati.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Aspetti da ricordare sull'implementazione GetItem

Le condizioni seguenti possono applicare a un'implementazione di [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Quando si definisce la classe del provider, un provider di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumerazione. In questi casi, l'implementazione di [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) necessario assicurarsi che il percorso passato al metodo soddisfi tali requisiti. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Per impostazione predefinita, gli override di questo metodo non devono recuperare gli oggetti che sono in genere nascoste all'utente, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Ad esempio, il [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metodo per i controlli di provider FileSystem di [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) proprietà prima di chiamare [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) per nascosto o file di sistema.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Associare i parametri dinamici per il Cmdlet Get-Item

In alcuni casi il `Get-Item` cmdlet richiede parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici di PowerShell di Windows provider di elementi deve implementare il [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) (metodo). Questo metodo recupera i parametri dinamici per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere i parametri di `Get-Item` cmdlet.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Impostazione di un elemento

Per impostare un elemento, il provider di Windows PowerShell è necessario eseguire l'override di [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metodo per supportare le chiamate dal `Set-Item` cmdlet. Questo metodo imposta il valore dell'elemento nel percorso specificato.

Questo provider non è incluso un override per il [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) (metodo). Tuttavia, di seguito è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Aspetti da ricordare sull'implementazione SetItem

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Quando si definisce la classe del provider, un provider di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumerazione. In questi casi, l'implementazione di [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) necessario assicurarsi che il percorso passato al metodo soddisfi tali requisiti. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Per impostazione predefinita, gli override di questo metodo devono non impostata o scrivere gli oggetti che sono nascosti all'utente, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Deve essere inviato un errore il [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metodo, se il percorso rappresenta un elemento nascosto e [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `false`.

- L'implementazione del [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metodo deve chiamare [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)e verificare il valore restituito corrispondente prima di apportare modifiche all'archivio dati. Questo metodo viene utilizzato per confermare l'esecuzione di un'operazione quando viene apportata una modifica all'archivio dati, ad esempio, l'eliminazione di file. Il [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) metodo invia il nome della risorsa da modificare per l'utente, con il runtime di Windows PowerShell prendendo in considerazione tutte le impostazioni della riga di comando o variabili di preferenza nella determinazione di ciò che deve essere visualizzato.

  Dopo la chiamata a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, il [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)il metodo deve chiamare il [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (metodo). Questo metodo invia un messaggio all'utente per consentire il feedback verificare se l'operazione deve proseguire. La chiamata a [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) consente un controllo aggiuntivo per le modifiche del sistema potenzialmente pericolose.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Recupero dei parametri dinamici per SetItem

In alcuni casi il `Set-Item` cmdlet richiede parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici di PowerShell di Windows provider di elementi deve implementare il [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) (metodo). Questo metodo recupera i parametri dinamici per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere i parametri di `Set-Item` cmdlet.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>La cancellazione di un elemento

Per cancellare un elemento, il provider di Windows PowerShell implementa il [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) metodo per supportare le chiamate dal `Clear-Item` cmdlet. Questo metodo cancella l'elemento di dati nel percorso specificato.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Aspetti da ricordare sull'implementazione ClearItem

Le condizioni seguenti possono applicare a un'implementazione di [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Quando si definisce la classe del provider, un provider di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumerazione. In questi casi, l'implementazione di [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) necessario assicurarsi che il percorso passato al metodo soddisfi tali requisiti. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Per impostazione predefinita, gli override di questo metodo devono non impostata o scrivere gli oggetti che sono nascosti all'utente, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Deve essere inviato un errore il [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metodo, se il percorso rappresenta un elemento è nascosto da parte dell'utente e [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `false`.

- L'implementazione del [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metodo deve chiamare [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)e verificare il valore restituito corrispondente prima di apportare modifiche all'archivio dati. Questo metodo viene utilizzato per confermare l'esecuzione di un'operazione quando viene apportata una modifica all'archivio dati, ad esempio, l'eliminazione di file. Il [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) metodo invia il nome della risorsa per essere modificato per l'utente, con il runtime di Windows PowerShell e gestire tutte le impostazioni della riga di comando o delle preferenze variabili per determinare che cosa deve essere visualizzata.

  Dopo la chiamata a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, il [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)il metodo deve chiamare il [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (metodo). Questo metodo invia un messaggio all'utente per consentire il feedback verificare se l'operazione deve proseguire. La chiamata a [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) consente un controllo aggiuntivo per le modifiche del sistema potenzialmente pericolose.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Recuperare i parametri dinamici per ClearItem

In alcuni casi il `Clear-Item` cmdlet richiede parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici di PowerShell di Windows provider di elementi deve implementare il [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) (metodo). Questo metodo recupera i parametri dinamici per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere i parametri di `Clear-Item` cmdlet.

Questo provider di elementi non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Esecuzione di un'azione predefinita per un elemento

Può implementare un provider di Windows PowerShell il [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) metodo per supportare le chiamate dal `Invoke-Item` cmdlet, che consente al provider per eseguire un'azione predefinita per l'elemento nel percorso specificato. Ad esempio, il provider FileSystem potrebbe utilizzare questo metodo per una chiamata a ShellExecute per un elemento specifico.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Aspetti da ricordare sull'implementazione InvokeDefaultAction

Le condizioni seguenti possono applicare a un'implementazione di [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Quando si definisce la classe del provider, un provider di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumerazione. In questi casi, l'implementazione di [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) necessario assicurarsi che il percorso passato al metodo soddisfi tali requisiti. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Per impostazione predefinita, gli override di questo metodo devono non impostata o scrivere gli oggetti nascosti all'utente, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Deve essere inviato un errore il [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metodo, se il percorso rappresenta un elemento è nascosto da parte dell'utente e [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Recuperare i parametri dinamici per InvokeDefaultAction

In alcuni casi il `Invoke-Item` cmdlet richiede parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici di PowerShell di Windows provider di elementi deve implementare il [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) (metodo). Questo metodo recupera i parametri dinamici per l'elemento nel percorso indicato e restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere i parametri dinamici per il `Invoke-Item` cmdlet.

Questo provider di elementi non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implementazione di classi e metodi di supporto

Questo provider di elementi implementa diversi metodi helper e le classi utilizzate da parte del pubblico eseguire l'override di metodi definiti da Windows PowerShell. Il codice per questi metodi helper e le classi vengono visualizzati nei [esempio di codice](#Code-Sample) sezione.

### <a name="normalizepath-method"></a>Metodo NormalizePath

Questo provider di elementi implementa un metodo helper NormalizePath per assicurarsi che il percorso abbia un formato coerente. Il formato specificato Usa una barra rovesciata (\\) come separatore.

### <a name="pathisdrive-method"></a>Metodo PathIsDrive

Questo provider di elementi implementa un metodo helper PathIsDrive per determinare se il percorso specificato è effettivamente il nome dell'unità.

### <a name="chunkpath-method"></a>Metodo ChunkPath

Questo provider di elementi implementa un metodo helper ChunkPath che suddivide il percorso specificato in modo che il provider possa identificare i singoli elementi. Restituisce che una matrice è costituito da elementi di percorso.

### <a name="gettable-method"></a>Metodo getTable

Questo provider di elementi implementa il metodo helper GetTables che restituisce un oggetto DatabaseTableInfo che rappresenta le informazioni sulla tabella specificata nella chiamata.

### <a name="getrow-method"></a>Metodo GetRow

Il [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metodo di questo provider elemento chiama il metodo helper GetRows. Questo metodo di supporto recupera un oggetto DatabaseRowInfo che rappresenta le informazioni sulla riga specificata nella tabella.

### <a name="databasetableinfo-class"></a>Classe DatabaseTableInfo

Il provider di questo elemento definisce una classe DatabaseTableInfo che rappresenta una raccolta di informazioni in una tabella di dati nel database. Questa classe è simile al [DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) classe.

Il provider di esempio definisce un metodo DatabaseTableInfo.GetTables che restituisce una raccolta di oggetti informazioni di tabella che definisce le tabelle nel database. Questo metodo include un blocco try/catch per garantire che qualsiasi errore di database viene visualizzato come riga con le voci di zero.

### <a name="databaserowinfo-class"></a>Classe DatabaseRowInfo

Questo provider di elementi definisce la classe helper DatabaseRowInfo che rappresenta una riga in una tabella del database. Questa classe è simile al [FileInfo](/dotnet/api/System.IO.FileInfo) classe.

Il provider di esempio definisce un metodo DatabaseRowInfo.GetRows per restituire una raccolta di oggetti informazioni di riga per la tabella specificata. Questo metodo include un blocco try/catch per intercettare le eccezioni. Gli eventuali errori comporterà alcuna informazione di riga.

## <a name="code-sample"></a>Esempio di codice

Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetto e formattazione

Durante la scrittura di un provider, potrebbe essere necessario aggiungere i membri per gli oggetti esistenti o definire nuovi oggetti. Al termine, creare un file di tipi che è possibile usare Windows PowerShell per identificare i membri dell'oggetto e un file di formato che definisce la modalità di visualizzazione dell'oggetto. Per altre informazioni, vedere [estendendo i tipi di oggetto e formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Creazione del provider di Windows PowerShell

Visualizzare [come registrare i cmdlet, provider e ospitare applicazioni](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Test di un provider Windows PowerShell

Quando questo provider di Windows PowerShell viene registrato con Windows PowerShell, è possibile solo test di base e funzionalità del provider di unità. Per testare la modifica di elementi, è inoltre necessario implementare la funzionalità contenitore descritto nella [implementazione di un Provider di contenitore di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Creazione di provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Progettazione di provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estensione di tipi di oggetto e la formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Funzionamento di Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Creazione di un provider di contenitori Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Creazione di un provider di unità Windows PowerShell](./creating-a-windows-powershell-drive-provider.md)

[Come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)