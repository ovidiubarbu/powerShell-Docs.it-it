---
title: Creazione di un provider di proprietà di Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: 9197f5635528e0f52cd08adde1c6bd69467725e8
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417476"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Creazione di un provider di proprietà di Windows PowerShell

In questo argomento viene descritto come creare un provider che consente all'utente di modificare le proprietà degli elementi in un archivio dati. Di conseguenza, questo tipo di provider viene definito provider di proprietà di Windows PowerShell. Ad esempio, il provider del registro di sistema fornito da Windows PowerShell gestisce i valori delle chiavi del registro di sistema come proprietà dell'elemento chiave del registro di sistema. Questo tipo di provider deve aggiungere l'interfaccia [System. Management. Automation. provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) all'implementazione della classe .NET.

> [!NOTE]
> Windows PowerShell fornisce un file di modello che è possibile usare per sviluppare un provider di Windows PowerShell. Il file TemplateProvider.cs è disponibile in Microsoft Windows Software Development Kit per Windows Vista e .NET Framework 3,0 componenti di Runtime. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> Il modello scaricato è disponibile nella directory **\<PowerShell samples >** . È necessario creare una copia di questo file e utilizzare la copia per creare un nuovo provider di Windows PowerShell, rimuovendo tutte le funzionalità non necessarie.
>
> Per ulteriori informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> I metodi del provider di proprietà devono scrivere tutti gli oggetti usando il metodo [System. Management. Automation. provider. CmdletProvider. Writepropertyobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) .

## <a name="defining-the-windows-powershell-provider"></a>Definizione del provider di Windows PowerShell

Un provider di proprietà deve creare una classe .NET che supporta l'interfaccia [System. Management. Automation. provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) . Di seguito è riportata la dichiarazione di classe predefinita dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Definizione della funzionalità di base

L'interfaccia [System. Management. Automation. provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) può essere associata a una qualsiasi delle classi base del provider, ad eccezione della classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Aggiungere la funzionalità di base richiesta dalla classe base in uso. Per ulteriori informazioni sulle classi di base, vedere [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Recupero di proprietà

Per recuperare le proprietà, il provider deve implementare il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) per supportare le chiamate dal cmdlet `Get-ItemProperty`. Questo metodo recupera le proprietà dell'elemento che si trova nel percorso interno del provider specificato (completo).

Il parametro `providerSpecificPickList` indica le proprietà da recuperare. Se questo parametro è `null` o vuoto, il metodo deve recuperare tutte le proprietà. Inoltre, [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) scrive un'istanza di un oggetto [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) che rappresenta un elenco di proprietà delle proprietà recuperate. Il metodo non deve restituire alcun elemento.

È consigliabile che l'implementazione di [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) supporti l'espansione con caratteri jolly dei nomi delle proprietà per ogni elemento nell'elenco di selezione. A tale scopo, usare la classe [System. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) per eseguire i criteri di ricerca con caratteri jolly.

Di seguito è riportata l'implementazione predefinita di [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Aspetti da ricordare sull'implementazione di GetProperty

Per l'implementazione di [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)è possibile che si verifichino le condizioni seguenti:

- Quando si definisce la classe provider, un provider di proprietà di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione del metodo [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) deve garantire che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificate. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono recuperare un Reader per gli oggetti nascosti all'utente, a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. È necessario scrivere un errore se il percorso rappresenta un elemento nascosto dall'utente e [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostato su `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Associazione di parametri dinamici al cmdlet Get-ItemProperty

Il cmdlet `Get-ItemProperty` potrebbe richiedere parametri aggiuntivi specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di proprietà di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) . Il parametro `path` indica un percorso interno completo del provider, mentre il parametro `providerSpecificPickList` specifica le proprietà specifiche del provider immesse nella riga di comando. Questo parametro può essere `null` o vuoto se le proprietà vengono reindirizzate al cmdlet. In questo caso, questo metodo restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Il runtime di Windows PowerShell usa l'oggetto restituito per aggiungere i parametri al cmdlet.

Di seguito è riportata l'implementazione predefinita di [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Impostazione delle proprietà

Per impostare le proprietà, il provider di proprietà di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) per supportare le chiamate dal cmdlet `Set-ItemProperty`. Questo metodo imposta una o più proprietà dell'elemento nel percorso specificato e sovrascrive le proprietà fornite come richiesto. [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) scrive anche un'istanza di un oggetto [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) che rappresenta un elenco di proprietà delle proprietà aggiornate.

Di seguito è riportata l'implementazione predefinita di [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Aspetti da ricordare sull'implementazione di Set-ItemProperty

Per un'implementazione di [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)è possibile che si verifichino le condizioni seguenti:

- Quando si definisce la classe provider, un provider di proprietà di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione del metodo [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) deve garantire che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificate. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono recuperare un Reader per gli oggetti nascosti all'utente, a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. È necessario scrivere un errore se il percorso rappresenta un elemento nascosto dall'utente e [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostato su `false`.

- L'implementazione del metodo [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) deve chiamare [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificare il relativo valore restituito prima di apportare modifiche all'archivio dati. Questo metodo viene usato per confermare l'esecuzione di un'operazione quando viene apportata una modifica allo stato del sistema, ad esempio la ridenominazione dei file. [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) invia il nome della risorsa da modificare all'utente, con il runtime di Windows PowerShell e gestendo le impostazioni della riga di comando o le variabili di preferenza per determinare gli elementi da visualizzare.

  Dopo che la chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, se possono essere apportate modifiche di sistema potenzialmente pericolose, il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) deve chiamare il metodo [System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Questo metodo invia un messaggio di conferma all'utente per consentire un ulteriore feedback per indicare che l'operazione deve essere continuata.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Associazione di parametri dinamici per il cmdlet Set-ItemProperty

Il cmdlet `Set-ItemProperty` potrebbe richiedere parametri aggiuntivi specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di proprietà di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) . Questo metodo restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Se non è necessario aggiungere parametri dinamici, è possibile che venga restituito il valore `null`.

Di seguito è riportata l'implementazione predefinita di [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Cancellazione delle proprietà

Per cancellare le proprietà, il provider di proprietà di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) per supportare le chiamate dal cmdlet `Clear-ItemProperty`. Questo metodo imposta una o più proprietà per l'elemento che si trova nel percorso specificato.

Di seguito è riportata l'implementazione predefinita di [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Cosa ricordare sull'implementazione di ClearProperty

Per l'implementazione di [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)è possibile che si verifichino le condizioni seguenti:

- Quando si definisce la classe provider, un provider di proprietà di Windows PowerShell può dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questi casi, l'implementazione del metodo [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) deve garantire che il percorso passato al metodo soddisfi i requisiti delle funzionalità specificate. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, le proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [System. Management. Automation. provider. CmdletProvider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Per impostazione predefinita, le sostituzioni di questo metodo non devono recuperare un Reader per gli oggetti nascosti all'utente, a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. È necessario scrivere un errore se il percorso rappresenta un elemento nascosto dall'utente e [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostato su `false`.

- L'implementazione del metodo [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) deve chiamare [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificare il relativo valore restituito prima di apportare eventuali modifiche all'archivio dati. Questo metodo viene usato per confermare l'esecuzione di un'operazione prima che venga apportata una modifica allo stato del sistema, ad esempio la cancellazione di contenuto. [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) invia il nome della risorsa da modificare all'utente, con il runtime di Windows PowerShell che prende in considerazione le impostazioni della riga di comando o le variabili di preferenza per determinare gli elementi da visualizzare.

  Dopo che la chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, se possono essere apportate modifiche di sistema potenzialmente pericolose, il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) deve chiamare il metodo [System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Questo metodo invia un messaggio di conferma all'utente per consentire un ulteriore feedback per indicare che l'operazione potenzialmente pericolosa deve continuare.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Associazione di parametri dinamici al cmdlet Clear-ItemProperty

Il cmdlet `Clear-ItemProperty` potrebbe richiedere parametri aggiuntivi specificati dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di proprietà di Windows PowerShell deve implementare il metodo [System. Management. Automation. provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) . Questo metodo restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Se non è necessario aggiungere parametri dinamici, è possibile che venga restituito il valore `null`.

Di seguito è riportata l'implementazione predefinita di [System. Management. Automation. provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) dal file TemplateProvider.cs fornito da Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Compilazione del provider di Windows PowerShell

Vedere [come registrare i cmdlet, i provider e le applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Vedere anche

[Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Progettare il provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estensione di tipi di oggetti e formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Come registrare cmdlet, provider e applicazioni host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)
