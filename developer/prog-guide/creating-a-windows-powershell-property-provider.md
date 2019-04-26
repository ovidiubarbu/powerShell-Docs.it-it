---
title: Creazione di un Provider di proprietà di PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: 6ec0752a9ae06c5c2cdd1a1851caeeff52d8eb74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081836"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Creazione di un provider di proprietà di Windows PowerShell

Questo argomento descrive come creare un provider che consente all'utente di modificare le proprietà degli elementi in un archivio dati. Di conseguenza, questo tipo di provider viene considerato un provider di proprietà di Windows PowerShell. Ad esempio, il provider del Registro di sistema fornito dai valori di chiave del Registro di sistema di Windows PowerShell gestisce come proprietà dell'elemento chiave del Registro di sistema. Questo tipo di provider è necessario aggiungere il [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfaccia per l'implementazione della classe .NET.

> [!NOTE]
> Windows PowerShell fornisce un file di modello che è possibile usare per sviluppare un provider di Windows PowerShell. Il file TemplateProvider.cs è disponibile su Microsoft Windows Software Development Kit per Windows Vista e i componenti Runtime di .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Il modello scaricato è disponibile nel  **\<esempi di PowerShell >** directory. È consigliabile creare una copia di questo file e usare la copia per la creazione di un nuovo provider di Windows PowerShell, la rimozione di tutte le funzionalità non è necessario.
>
> Per altre informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [la progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> I metodi del provider di proprietà devono scrivere tutti gli oggetti utilizzando il [System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) (metodo).

Nell'elenco seguente contiene le sezioni in questo argomento. Se non si ha familiarità con la scrittura di un provider di proprietà di Windows PowerShell, leggere queste informazioni nell'ordine in cui viene visualizzato. Tuttavia, se si ha familiarità con la scrittura di un provider di proprietà di Windows PowerShell, passare direttamente alle informazioni necessarie.

- [Che definisce il Provider PowerShell per Windows](#Defining-the-Windows-PowerShell-provider)

- [Definizione funzionalità di Base](#Defining-Base-Functionality)

- [Recupero delle proprietà](#Retrieving-Properties)

- [Associare i parametri dinamici al `Get-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ItemProperty-Cmdlet)

- [Impostazione delle proprietà](#Setting-Properties)

- [Associare i parametri dinamici al `Set-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-for-the-Set-ItemProperty-Cmdlet)

- [La cancellazione di una proprietà](#Clearing-Properties)

- [Associare i parametri dinamici al `Clear-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-ItemProperty-Cmdlet)

- [Creazione del Provider di Windows PowerShell](#Building-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-provider"></a>Che definisce il provider di Windows PowerShell

Un provider di proprietà necessario creare una classe .NET che supporta il [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfaccia. Ecco la dichiarazione di classe predefinita dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Definizione funzionalità di Base

Il [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfaccia può essere collegata a una delle classi di base di provider, ad eccezione del [ System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe. Aggiungere la funzionalità di base richiesto dalla classe di base in uso. Per altre informazioni sulle classi di base, vedere [la progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Recupero delle proprietà

Per recuperare le proprietà, il provider deve implementare il [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) metodo per supportare le chiamate dal `Get-ItemProperty` cmdlet. Questo metodo recupera le proprietà dell'elemento presente nel percorso interna al provider specificato (completo).

Il `providerSpecificPickList` parametro indica quale proprietà da recuperare. Se questo parametro è `null` o vuoto, il metodo deve recuperare tutte le proprietà. È inoltre [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) scrive un'istanza di un [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) oggetto che rappresenta un contenitore delle proprietà delle proprietà recuperata. Il metodo deve restituire alcun valore.

È consigliabile che l'implementazione di [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) supporta l'espansione di caratteri jolly di nomi di proprietà per ogni elemento nell'elenco di selezione. A questo scopo, usare il [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) classe per eseguire i criteri di ricerca con caratteri jolly.

Ecco l'implementazione predefinita di [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Aspetti da ricordare sull'implementazione GetProperty

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Quando si definisce la classe del provider, un provider di proprietà di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione. In questi casi, l'implementazione del [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) deve garantire che il percorso passato al metodo soddisfi i requisiti della classe specificata (metodo) funzionalità. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Per impostazione predefinita, gli override di questo metodo non devono recuperare un lettore per gli oggetti che sono nascosti all'utente, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Deve essere scritto un errore se il percorso rappresenta un elemento è nascosto da parte dell'utente e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Associare i parametri dinamici per il Cmdlet Get-ItemProperty

Il `Get-ItemProperty` cmdlet potrebbero richiedere parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici, il provider di proprietà di Windows PowerShell deve implementare il [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) (metodo). Il `path` parametro indica un percorso di provider interno completo, mentre il `providerSpecificPickList` parametro specifica le proprietà specifiche del provider inserite nella riga di comando. Questo parametro potrebbe essere `null` o vuoto se le proprietà vengono inviati tramite pipe al cmdlet. In questo caso, questo metodo restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il runtime di Windows PowerShell Usa l'oggetto restituito per aggiungere parametri al cmdlet.

Ecco l'implementazione predefinita di [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Impostazione delle proprietà

Per impostare le proprietà, il provider di proprietà di Windows PowerShell deve implementare il [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metodo per supportare le chiamate dal `Set-ItemProperty` cmdlet. Questo metodo imposta una o più proprietà dell'elemento nel percorso specificato e sovrascrive la proprietà fornita in base alle esigenze. [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) scrive anche un'istanza di un [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) oggetto che rappresenta un contenitore delle proprietà di aggiornato proprietà.

Ecco l'implementazione predefinita di [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Aspetti da ricordare sull'implementazione di Set-ItemProperty

Le condizioni seguenti possono applicare a un'implementazione di [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Quando si definisce la classe del provider, un provider di proprietà di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione. In questi casi, l'implementazione del [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metodo è necessario assicurarsi che il percorso passato al metodo soddisfi i requisiti dell'oggetto specificato funzionalità. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Per impostazione predefinita, gli override di questo metodo non devono recuperare un lettore per gli oggetti che sono nascosti all'utente, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Deve essere scritto un errore se il percorso rappresenta un elemento è nascosto da parte dell'utente e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `false`.

- L'implementazione del [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metodo deve chiamare [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificare il valore restituito corrispondente prima di apportare modifiche all'archivio dati. Questo metodo viene utilizzato per confermare l'esecuzione di un'operazione quando viene apportata una modifica lo stato del sistema, ad esempio, la ridenominazione dei file. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) invia il nome della risorsa da modificare per l'utente, con il runtime di Windows PowerShell e la gestione delle impostazioni della riga di comando o variabili di preferenza nella determinazione che cosa deve essere visualizzata.

  Dopo la chiamata a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, se è possibile apportare modifiche di sistema potenzialmente pericolose, il [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metodo deve chiamare il [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (metodo). Questo metodo invia un messaggio di conferma all'utente per consentire ulteriori commenti e suggerimenti indicare che l'operazione deve proseguire.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Associare i parametri dinamici per il Cmdlet Set-ItemProperty

Il `Set-ItemProperty` cmdlet potrebbero richiedere parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici, il provider di proprietà di Windows PowerShell deve implementare il [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) (metodo). Questo metodo restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il `null` valore può essere restituito se nessun parametro dinamico devono essere aggiunti.

Ecco l'implementazione predefinita di [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>La cancellazione di proprietà

Per cancellare le proprietà, il provider di proprietà di Windows PowerShell deve implementare il [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) metodo per supportare le chiamate dal `Clear-ItemProperty` cmdlet. Questo metodo imposta una o più proprietà per l'elemento situato nel percorso specificato.

Ecco l'implementazione predefinita di [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Cosa da ricordare sull'implementazione ClearProperty

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Quando si definisce la classe del provider, un provider di proprietà di Windows PowerShell potrebbe dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione. In questi casi, l'implementazione del [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) deve garantire che il percorso passato al metodo soddisfi i requisiti della classe specificata (metodo) funzionalità. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) proprietà.

- Per impostazione predefinita, gli override di questo metodo non devono recuperare un lettore per gli oggetti che sono nascosti all'utente, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Deve essere scritto un errore se il percorso rappresenta un elemento è nascosto da parte dell'utente e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `false`.

- L'implementazione del [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) metodo deve chiamare [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificarne il valore restituito prima di apportare modifiche all'archivio dati. Questo metodo viene utilizzato per confermare l'esecuzione di un'operazione prima che viene apportata una modifica lo stato del sistema, ad esempio la cancellazione del contenuto. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) invia il nome della risorsa da modificare per l'utente, con il runtime di Windows PowerShell prendendo in considerazione eventuali impostazioni riga di comando o variabili di preferenza in determinare ciò che deve essere visualizzato.

  Dopo la chiamata a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, se è possibile apportare modifiche di sistema potenzialmente pericolose, il [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) metodo deve chiamare il [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (metodo). Questo metodo invia un messaggio di conferma all'utente per consentire ulteriori commenti e suggerimenti indicare che è opportuno continuare l'operazione potenzialmente pericoloso.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Associare i parametri dinamici per il Cmdlet Clear-ItemProperty

Il `Clear-ItemProperty` cmdlet potrebbero richiedere parametri aggiuntivi che vengono specificati in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici, il provider di proprietà di Windows PowerShell deve implementare il [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) (metodo). Questo metodo restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto. Il `null` valore può essere restituito se nessun parametro dinamico devono essere aggiunti.

Ecco l'implementazione predefinita di [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Creazione del provider di Windows PowerShell

Visualizzare [come registrare i cmdlet, provider e ospitare applicazioni](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Vedere anche

[Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Provider di progettazione di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estensione di tipi di oggetto e la formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)