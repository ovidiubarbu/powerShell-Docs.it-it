---
title: Creazione di un provider di elementi di Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: ad42b8de867f468e832380ab6a22a39b6d27d3c6
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417495"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Creazione di un provider di elementi di Windows PowerShell

In questo argomento viene descritto come creare un provider di Windows PowerShell in grado di modificare i dati in un archivio dati. In questo argomento, gli elementi dei dati nell'archivio vengono definiti "elementi" dell'archivio dati. Di conseguenza, un provider che può manipolare i dati nell'archivio viene definito provider di elementi di Windows PowerShell.

> [!NOTE]
> È possibile scaricare il C# file di origine (AccessDBSampleProvider03.cs) per questo provider utilizzando Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** .
>
> Per ulteriori informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

Il provider di elementi di Windows PowerShell descritto in questo argomento recupera gli elementi di dati da un database di Access. In questo caso, un "elemento" è una tabella nel database di Access o una riga in una tabella.

## <a name="defining-the-windows-powershell-item-provider-class"></a>Definizione della classe del provider di elementi di Windows PowerShell

Un provider di elementi di Windows PowerShell deve definire una classe .NET che deriva dalla classe di base [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Di seguito è riportata la definizione della classe per il provider di elementi descritto in questa sezione.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Si noti che in questa definizione di classe l'attributo [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) include due parametri. Il primo parametro specifica un nome descrittivo per il provider utilizzato da Windows PowerShell. Il secondo parametro specifica le funzionalità specifiche di Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando. Per questo provider non sono state aggiunte funzionalità specifiche di Windows PowerShell.

## <a name="defining-base-functionality"></a>Definizione della funzionalità di base

Come descritto in [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md), la classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) deriva da diverse altre classi che forniscono funzionalità diverse del provider. Un provider di elementi di Windows PowerShell deve quindi definire tutte le funzionalità fornite da tali classi.

Per ulteriori informazioni su come implementare la funzionalità per l'aggiunta di informazioni di inizializzazione specifiche della sessione e per il rilascio di risorse utilizzate dal provider, vedere [creazione di un provider di Windows PowerShell di base](./creating-a-basic-windows-powershell-provider.md). Tuttavia, la maggior parte dei provider, incluso il provider qui descritto, può utilizzare l'implementazione predefinita di questa funzionalità fornita da Windows PowerShell.

Prima che il provider di elementi di Windows PowerShell possa modificare gli elementi nell'archivio, deve implementare i metodi della classe di base [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) per accedere all'archivio dati. Per ulteriori informazioni sull'implementazione di questa classe, vedere [creazione di un provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Verifica della validità del percorso

Quando si cerca un elemento di dati, il runtime di Windows PowerShell fornisce un percorso di Windows PowerShell al provider, come definito nella sezione "concetti di PSPath" del [funzionamento di Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). Un provider di elementi di Windows PowerShell deve verificare la validità sintattica e semantica di qualsiasi percorso passato implementando il metodo [System. Management. Automation. provider. Itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) . Questo metodo restituisce `true` se il percorso è valido e `false` in caso contrario. Tenere presente che l'implementazione di questo metodo non deve verificare l'esistenza dell'elemento nel percorso, ma solo che il percorso sia sintatticamente e semanticamente corretto.

Di seguito è illustrata l'implementazione del metodo [System. Management. Automation. provider. Itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) per questo provider. Si noti che questa implementazione chiama un metodo helper NormalizePath per convertire tutti i separatori del percorso in uno uniforme.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Determinare se esiste un elemento

Dopo aver verificato il percorso, il runtime di Windows PowerShell deve determinare se esiste un elemento di dati in tale percorso. Per supportare questo tipo di query, il provider di elementi di Windows PowerShell implementa il metodo [System. Management. Automation. provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) . Questo metodo restituisce `true` un elemento viene trovato nel percorso specificato e `false` (impostazione predefinita) in caso contrario.

Di seguito è illustrata l'implementazione del metodo [System. Management. Automation. provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) per questo provider. Si noti che questo metodo chiama i metodi helper PathIsDrive, ChunkPath e GetTable e usa un oggetto DatabaseTableInfo definito dal provider.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Aspetti da ricordare sull'implementazione di ItemExists

Per l'implementazione di [System. Management. Automation. provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)è possibile che si verifichino le condizioni seguenti:

- Quando si definisce la classe provider, un provider di elementi di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione del metodo [System. Management. Automation. provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) deve garantire che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificate. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- L'implementazione di questo metodo deve gestire qualsiasi tipo di accesso all'elemento che potrebbe rendere visibile l'elemento all'utente. Ad esempio, se un utente ha accesso in scrittura a un file tramite il provider FileSystem (fornito da Windows PowerShell), ma non l'accesso in lettura, il file esiste ancora e [System. Management. Automation. provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) restituisce `true`. L'implementazione potrebbe richiedere la verifica di un elemento padre per verificare se è possibile enumerare l'elemento figlio.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Associazione di parametri dinamici al cmdlet Test-Path

A volte il cmdlet `Test-Path` che chiama [System. Management. Automation. provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) richiede parametri aggiuntivi specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di elementi di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Itemcmdletprovider. Itemexistsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) . Questo metodo recupera i parametri dinamici per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al cmdlet `Test-Path`.

Questo provider di elementi di Windows PowerShell non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Recupero di un elemento

Per recuperare un elemento, il provider di elementi di Windows PowerShell deve eseguire l'override del metodo [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) per supportare le chiamate dal cmdlet `Get-Item`. Questo metodo scrive l'elemento usando il metodo [System. Management. Automation. provider. CmdletProvider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .

Di seguito è illustrata l'implementazione del metodo [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) per questo provider. Si noti che questo metodo usa i metodi helper GetTable e GetRow per recuperare elementi che sono tabelle nel database di Access o righe in una tabella di dati.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Aspetti da ricordare sull'implementazione di GetItem

Le condizioni seguenti possono essere valide per un'implementazione di [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Quando si definisce la classe provider, un provider di elementi di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione di [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) deve garantire che il percorso passato al metodo soddisfi tali requisiti. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono recuperare oggetti che in genere sono nascosti all'utente, a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. Ad esempio, il metodo [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) per il provider FileSystem controlla la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) prima di tentare di chiamare [System. Management. Automation. provider. CmdletProvider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) per i file nascosti o di sistema.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Associazione di parametri dinamici al cmdlet Get-Item

A volte il cmdlet `Get-Item` richiede parametri aggiuntivi specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di elementi di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) . Questo metodo recupera i parametri dinamici per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al cmdlet `Get-Item`.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Impostazione di un elemento

Per impostare un elemento, il provider di elementi di Windows PowerShell deve eseguire l'override del metodo [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) per supportare le chiamate dal cmdlet `Set-Item`. Questo metodo imposta il valore dell'elemento in corrispondenza del percorso specificato.

Questo provider non fornisce un override per il metodo [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) . Tuttavia, di seguito è riportata l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Aspetti da ricordare sull'implementazione di SetItem

Le condizioni seguenti possono essere valide per l'implementazione di [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Quando si definisce la classe provider, un provider di elementi di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione di [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) deve garantire che il percorso passato al metodo soddisfi tali requisiti. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono impostare o scrivere oggetti nascosti all'utente, a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. È necessario inviare un errore al metodo [System. Management. Automation. provider. CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) se il percorso rappresenta un elemento nascosto e [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostato su `false`.

- L'implementazione del metodo [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) deve chiamare [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificare il relativo valore restituito prima di apportare modifiche all'archivio dati. Questo metodo viene usato per confermare l'esecuzione di un'operazione quando viene apportata una modifica all'archivio dati, ad esempio l'eliminazione di file. Il metodo [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) invia il nome della risorsa da modificare all'utente, con il runtime di Windows PowerShell che prende in considerazione le impostazioni della riga di comando o le variabili di preferenza per determinare gli elementi da visualizzare.

  Dopo che la chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, il metodo [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) deve chiamare il metodo [System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Questo metodo invia un messaggio all'utente per consentire il feedback per verificare se l'operazione deve essere continuata. La chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) consente un ulteriore controllo della presenza di modifiche di sistema potenzialmente pericolose.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Recupero di parametri dinamici per SetItem

A volte il cmdlet `Set-Item` richiede parametri aggiuntivi specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di elementi di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) . Questo metodo recupera i parametri dinamici per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al cmdlet `Set-Item`.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Cancellazione di un elemento

Per cancellare un elemento, il provider di elementi di Windows PowerShell implementa il metodo [System. Management. Automation. provider. Itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) per supportare le chiamate dal cmdlet `Clear-Item`. Questo metodo cancella l'elemento dati nel percorso specificato.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Aspetti da ricordare sull'implementazione di ClearItem

Le condizioni seguenti possono essere valide per un'implementazione di [System. Management. Automation. provider. Itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Quando si definisce la classe provider, un provider di elementi di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione di [System. Management. Automation. provider. Itemcmdletprovider. ClearItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) deve garantire che il percorso passato al metodo soddisfi tali requisiti. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono impostare o scrivere oggetti nascosti all'utente, a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. È necessario inviare un errore al metodo [System. Management. Automation. provider. CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) se il percorso rappresenta un elemento nascosto dall'utente e [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostato su `false`.

- L'implementazione del metodo [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) deve chiamare [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificare il relativo valore restituito prima di apportare modifiche all'archivio dati. Questo metodo viene usato per confermare l'esecuzione di un'operazione quando viene apportata una modifica all'archivio dati, ad esempio l'eliminazione di file. Il metodo [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) invia il nome della risorsa da modificare all'utente con il runtime di Windows PowerShell e gestisce le impostazioni della riga di comando o le variabili di preferenza per determinare gli elementi da visualizzare.

  Dopo che la chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, il metodo [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) deve chiamare il metodo [System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Questo metodo invia un messaggio all'utente per consentire il feedback per verificare se l'operazione deve essere continuata. La chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) consente un ulteriore controllo della presenza di modifiche di sistema potenzialmente pericolose.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Recuperare i parametri dinamici per ClearItem

A volte il cmdlet `Clear-Item` richiede parametri aggiuntivi specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di elementi di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) . Questo metodo recupera i parametri dinamici per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al cmdlet `Clear-Item`.

Questo provider di elementi non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Esecuzione di un'azione predefinita per un elemento

Un provider di elementi di Windows PowerShell può implementare il metodo [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) per supportare le chiamate dal cmdlet `Invoke-Item`, che consente al provider di eseguire un'azione predefinita per l'elemento nel percorso specificato. Ad esempio, il provider FileSystem può utilizzare questo metodo per chiamare ShellExecute per un elemento specifico.

Questo provider non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Aspetti da ricordare sull'implementazione di InvokeDefaultAction

Le condizioni seguenti possono essere valide per un'implementazione di [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Quando si definisce la classe provider, un provider di elementi di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione di [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) deve garantire che il percorso passato al metodo soddisfi tali requisiti. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono impostare o scrivere oggetti nascosti dall'utente a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. È necessario inviare un errore al metodo [System. Management. Automation. provider. CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) se il percorso rappresenta un elemento nascosto dall'utente e [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostato su `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Recuperare i parametri dinamici per InvokeDefaultAction

A volte il cmdlet `Invoke-Item` richiede parametri aggiuntivi specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di elementi di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) . Questo metodo recupera i parametri dinamici per l'elemento in corrispondenza del percorso indicato e restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri dinamici al cmdlet `Invoke-Item`.

Questo provider di elementi non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di questo metodo.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implementazione di metodi e classi helper

Questo provider di elementi implementa diversi metodi e classi helper usati dai metodi di override pubblici definiti da Windows PowerShell. Il codice per questi metodi e classi helper è illustrato nella sezione di [esempio di codice](#code-sample) .

### <a name="normalizepath-method"></a>Metodo NormalizePath

Questo provider di elementi implementa un metodo helper NormalizePath per verificare che il percorso abbia un formato coerente. Il formato specificato usa una barra rovesciata (\\) come separatore.

### <a name="pathisdrive-method"></a>Metodo PathIsDrive

Questo provider di elementi implementa un metodo helper PathIsDrive per determinare se il percorso specificato è effettivamente il nome dell'unità.

### <a name="chunkpath-method"></a>Metodo ChunkPath

Questo provider di elementi implementa un metodo helper ChunkPath che suddivide il percorso specificato in modo che il provider possa identificare i singoli elementi. Restituisce una matrice composta dagli elementi Path.

### <a name="gettable-method"></a>GetTable (metodo)

Questo provider di elementi implementa il metodo helper getTables che restituisce un oggetto DatabaseTableInfo che rappresenta le informazioni sulla tabella specificata nella chiamata.

### <a name="getrow-method"></a>Metodo GetRow

Il metodo [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) di questo provider di elementi chiama il metodo helper GetRows. Questo metodo helper recupera un oggetto DatabaseRowInfo che rappresenta le informazioni sulla riga specificata nella tabella.

### <a name="databasetableinfo-class"></a>Classe DatabaseTableInfo

Questo provider di elementi definisce una classe DatabaseTableInfo che rappresenta una raccolta di informazioni in una tabella di dati del database. Questa classe è simile alla classe [System. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .

Il provider di elementi di esempio definisce un metodo DatabaseTableInfo. getTables che restituisce una raccolta di oggetti informazioni tabella che definiscono le tabelle nel database. Questo metodo include un blocco try/catch per assicurarsi che qualsiasi errore del database venga visualizzato come una riga con zero voci.

### <a name="databaserowinfo-class"></a>Classe DatabaseRowInfo

Questo provider di elementi definisce la classe helper DatabaseRowInfo che rappresenta una riga in una tabella del database. Questa classe è simile alla classe [System. io. FileInfo](/dotnet/api/System.IO.FileInfo) .

Il provider di esempio definisce un metodo DatabaseRowInfo. GetRows per restituire una raccolta di oggetti informazioni sulla riga per la tabella specificata. Questo metodo include un blocco try/catch per intercettare le eccezioni. Eventuali errori non comporteranno alcuna informazione sulle righe.

## <a name="code-sample"></a>Esempio di codice

Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetti e formattazione

Quando si scrive un provider, potrebbe essere necessario aggiungere membri a oggetti esistenti o definire nuovi oggetti. Al termine, creare un file di tipi che Windows PowerShell può usare per identificare i membri dell'oggetto e un file di formato che definisce la modalità di visualizzazione dell'oggetto. Per ulteriori informazioni su, vedere [estensione di tipi di oggetti e formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Compilazione del provider di Windows PowerShell

Vedere [come registrare i cmdlet, i provider e le applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Test del provider di Windows PowerShell

Quando questo provider di elementi di Windows PowerShell viene registrato con Windows PowerShell, è possibile testare solo le funzionalità di base e di unità del provider. Per testare la manipolazione degli elementi, è necessario implementare anche la funzionalità del contenitore descritta in [implementazione di un provider di Windows PowerShell per contenitori](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Creazione di provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estensione di tipi di oggetti e formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Funzionamento di Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Creazione di un provider di Windows PowerShell per contenitori](./creating-a-windows-powershell-container-provider.md)

[Creazione di un provider di Windows PowerShell per unità](./creating-a-windows-powershell-drive-provider.md)

[Come registrare cmdlet, provider e applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)
