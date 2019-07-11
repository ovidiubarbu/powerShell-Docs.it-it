---
title: Cenni preliminari sul Provider PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 81f6c8cd75ccea9e711cd8f6d6daa6cca5a499a0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734857"
---
# <a name="windows-powershell-provider-overview"></a>Panoramica del provider di Windows PowerShell

Un provider di Windows PowerShell consente a qualsiasi archivio dati deve essere esposta come un file system come se fosse un'unità montata. Ad esempio, il provider del Registro di sistema predefinito consente di spostarsi nel Registro di sistema, ad esempio per esplorare il `c` unità del computer in uso. Un provider può anche eseguire l'override di `Item` i cmdlet (ad esempio, `Get-Item`, `Set-Item`e così via) tale che i dati nell'archivio dati possono essere considerati come i file e directory vengono considerate quando si passa un file system. Per altre informazioni sui provider e le unità e i provider predefiniti in Windows PowerShell, vedere [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>I provider e le unità

Un Provider definisce la logica che consente di accedere, esplorare e modificare un archivio dati, mentre un'unità specifica un punto di ingresso specifico a un archivio dati (o una parte di un archivio dati) che è del tipo definito dal provider. Ad esempio, il provider del Registro di sistema consente di accedere a hive e chiavi in un registro di sistema e le unità HKLM e HKCU specificare l'hive corrispondenti all'interno del Registro di sistema. Le unità HKLM e HKCU usano il provider del Registro di sistema.

Quando si scrive un provider, è possibile specificare le unità-unità di predefiniti che vengono create automaticamente quando il provider è disponibile. È anche possibile definire un metodo per creare nuove unità che utilizzano tale provider.

## <a name="type-of-providers"></a>Tipo di provider

Esistono diversi tipi di provider, ognuno dei quali fornisce un livello di funzionalità diverso. Un provider viene implementato come una classe che deriva da uno dei discendenti del [System.Management.Automation.SessionStateCategory](/dotnet/api/system.management.automation.sessionstatecategory?view=pscore-6.2.0) **CmdletProvider** classe. Per informazioni sui diversi tipi di provider, vedere [tipi di Provider](./provider-types.md).

## <a name="provider-cmdlets"></a>Cmdlet del provider

I provider possono implementare metodi che corrispondono ai cmdlet di creazione di comportamenti personalizzati per questi cmdlet quando utilizzato in un'unità per tale provider. A seconda del tipo di provider, sono disponibili diversi set di cmdlet. Per un elenco completo dei cmdlet disponibili per la personalizzazione prevista dai provider, vedere [cmdlet del Provider](./provider-cmdlets.md).

## <a name="provider-paths"></a>Percorsi di provider

Le unità del provider, ad esempio i file System di spostamento degli utenti. Per questo motivo, si aspettano la sintassi dei percorsi in modo che corrispondano ai percorsi usati nell'esplorazione del file system. Quando un utente esegue un cmdlet del provider, specifichino un percorso dell'elemento a cui accedere. Il percorso specificato può essere interpretato in diversi modi. Un provider deve supportare uno o più dei seguenti tipi di percorso.

### <a name="drive-qualified-paths"></a>Percorsi drivequalified

Un percorso completo di unità è una combinazione di nome dell'elemento, il contenitore e i sottocontenitori in cui si trova l'elemento e l'unità di Windows PowerShell tramite cui si accede all'elemento. (Le unità sono definite dal provider utilizzato per accedere all'archivio dati. Il percorso inizia con il nome di unità seguito da due punti (:). Ad esempio: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Percorsi di provider qualificati

Per consentire il motore di Windows PowerShell inizializzare e annullare l'inizializzazione del provider, il provider deve supportare un percorso completo di provider. Ad esempio, l'utente può inizializzare e annullare l'inizializzazione dal provider FileSystem al quanto definisce il percorso completo di provider seguente: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Percorsi di provider-direct

Per consentire l'accesso remoto al provider di Windows PowerShell, è opportuno che un percorso di provider-direct per passare direttamente al provider di Windows PowerShell per la posizione corrente. Ad esempio, è possibile usare il provider di Windows PowerShell del Registro di sistema `\\server\regkeypath` come un percorso di provider con accesso diretto.

### <a name="provider-internal-paths"></a>Percorsi di provider interno

Per consentire i cmdlet del provider di accesso ai dati tramite application programming interface (API) non Windows PowerShell, il provider di Windows PowerShell deve supportare un percorso interna al provider. Questo percorso è indicato che segue il "::" il percorso completo di provider. Ad esempio, il percorso interna al provider per provider filesystem di Windows PowerShell è `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Si esegue l'override di parametri del cmdlet

Il comportamento di alcuni cmdlet specifici del provider può essere sostituito da un provider. Per un elenco di parametri che possono essere sostituite e come eseguirne l'override nella classe del provider, vedere [parametri del cmdlet del Provider](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>Parametri dinamici

I provider possono definire i parametri dinamici che vengono aggiunti a un cmdlet del provider quando l'utente specifica un determinato valore per uno dei parametri statici del cmdlet. Un provider viene eseguita implementando uno o più metodi di parametri dinamici. Per un elenco di parametri del cmdlet che può essere utilizzato per aggiungere parametri dinamici e i metodi utilizzati per la relativa implementazione, vedere [parametri dinamici cmdlet Provider](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Funzionalità del provider

Il [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione definisce una serie di funzionalità che i provider possono supportare. Queste includono la possibilità di usare i caratteri jolly, filtrare gli elementi e supporta le transazioni. Per specificare le funzionalità per un provider, aggiungere un elenco di valori del [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione, combinato con operatore logico `OR` operazione, come il [ System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) proprietà (il secondo parametro dell'attributo) del [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attributo per la classe del provider. Ad esempio, l'attributo seguente specifica che il provider supporta le [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **ShouldProcess** e [ System.Management.Automation.Provider.ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **transazioni** funzionalità.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Guida dei cmdlet del provider

Quando si scrive un provider, è possibile implementare il proprio Help per i cmdlet del provider supportati. Ciò include un singolo argomento della Guida per ogni cmdlet del provider o più versioni di un argomento della Guida per i casi in cui agisce il cmdlet del provider in modo diverso in base all'utilizzo di parametri dinamici. Per supportare la Guida del cmdlet specifici provider, il provider deve implementare il [System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) interfaccia.

Il motore di Windows PowerShell chiama il [System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) metodo per visualizzare l'argomento della Guida per i cmdlet del provider. Il motore fornisce il nome del cmdlet per cui l'utente specificato durante l'esecuzione di `Get-Help` cmdlet e il percorso corrente dell'utente. Se il provider implementa versioni diverse dello stesso cmdlet di provider per le unità diverse, è necessario il percorso corrente. Il metodo deve restituire una stringa che contiene il codice XML per la Guida dei cmdlet.

Viene scritto il contenuto del file della Guida utilizzando PSMAML XML. Questo è lo stesso schema XML che viene usato per la scrittura di contenuto della Guida per cmdlet autonomo. Aggiunge il contenuto per il cmdlet personalizzato della Guida per il file della Guida per il provider di sotto di `CmdletHelpPaths` elemento. L'esempio seguente illustra il `command` (elemento) per un cmdlet solo provider che illustra come specificare il nome del cmdlet del provider che il provider. Supporta

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>Vedere anche

[Funzionalità del Provider di PowerShell di Windows](./provider-types.md)

[Cmdlet del provider](./provider-cmdlets.md)

[Scrittura di un Provider di Windows PowerShell](./writing-a-windows-powershell-provider.md)