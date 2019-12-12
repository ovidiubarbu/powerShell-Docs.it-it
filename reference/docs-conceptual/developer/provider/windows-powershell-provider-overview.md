---
title: Panoramica del provider di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 81f6c8cd75ccea9e711cd8f6d6daa6cca5a499a0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366290"
---
# <a name="windows-powershell-provider-overview"></a>Panoramica del provider di Windows PowerShell

Un provider di Windows PowerShell consente l'esposizione di qualsiasi archivio dati come un file system come se fosse un'unità montata. Il provider del registro di sistema incorporato, ad esempio, consente di spostarsi nel registro di sistema, come si naviga nell'unità `c` del computer. Un provider può anche eseguire l'override dei cmdlet di `Item`, ad esempio `Get-Item`, `Set-Item`e così via, in modo che i dati nell'archivio dati possano essere trattati come file e directory quando si naviga in una file system. Per ulteriori informazioni su provider e unità e sui provider predefiniti in Windows PowerShell, vedere [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Provider e unità

Un provider definisce la logica usata per accedere, esplorare e modificare un archivio dati, mentre un'unità specifica un punto di ingresso specifico per un archivio dati (o una parte di un archivio dati) di tipo definito dal provider. Il provider del registro di sistema, ad esempio, consente di accedere a hive e chiavi in un registro di sistema e le unità HKLM e HKCU specificano gli hive corrispondenti nel registro di sistema. Entrambe le unità HKLM e HKCU utilizzano il provider del registro di sistema.

Quando si scrive un provider, è possibile specificare unità predefinite che vengono create automaticamente quando il provider è disponibile. Si definisce anche un metodo per creare nuove unità che usano tale provider.

## <a name="type-of-providers"></a>Tipo di provider

Sono disponibili diversi tipi di provider, ognuno dei quali fornisce un livello di funzionalità diverso. Un provider viene implementato come una classe che deriva da uno dei discendenti della classe [System. Management. Automation. SessionStateCategory](/dotnet/api/system.management.automation.sessionstatecategory?view=pscore-6.2.0) **CmdletProvider** . Per informazioni sui diversi tipi di provider, vedere [tipi di provider](./provider-types.md).

## <a name="provider-cmdlets"></a>Cmdlet del provider

I provider possono implementare metodi che corrispondono ai cmdlet, creando comportamenti personalizzati per tali cmdlet quando vengono usati in un'unità per quel provider. A seconda del tipo di provider, sono disponibili diversi set di cmdlet. Per un elenco completo dei cmdlet disponibili per la personalizzazione nei provider, vedere [cmdlet del provider](./provider-cmdlets.md).

## <a name="provider-paths"></a>Percorsi provider

Gli utenti esplorano le unità del provider come file System. Per questo motivo, si aspettano che la sintassi dei percorsi corrisponda ai percorsi utilizzati per la navigazione file system. Quando un utente esegue un cmdlet del provider, specifica un percorso all'elemento a cui accedere. Il percorso specificato può essere interpretato in diversi modi. Un provider deve supportare uno o più dei tipi di percorso seguenti.

### <a name="drive-qualified-paths"></a>Percorsi qualificati dall'unità

Un percorso qualificato dall'unità è una combinazione del nome dell'elemento, del contenitore e dei sottocontenitori in cui si trova l'elemento e dell'unità di Windows PowerShell tramite cui viene eseguito l'accesso all'elemento. (Le unità sono definite dal provider utilizzato per accedere all'archivio dati. Questo percorso inizia con il nome dell'unità seguito da due punti (:). Ad esempio: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Percorsi qualificati dal provider

Per consentire al motore di Windows PowerShell di inizializzare e annullare l'inizializzazione del provider, il provider deve supportare un percorso qualificato dal provider. L'utente può, ad esempio, inizializzare e annullare l'inizializzazione del provider FileSystem perché definisce il percorso qualificato dal provider seguente: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Percorsi diretti del provider

Per consentire l'accesso remoto al provider di Windows PowerShell, deve supportare un percorso diretto del provider da passare direttamente al provider di Windows PowerShell per il percorso corrente. Ad esempio, il provider del registro di sistema di Windows PowerShell può usare `\\server\regkeypath` come percorso diretto del provider.

### <a name="provider-internal-paths"></a>Percorsi interni del provider

Per consentire al cmdlet del provider di accedere ai dati usando le API (Application Programming Interface) non Windows PowerShell, il provider di Windows PowerShell deve supportare un percorso interno del provider. Questo percorso è indicato dopo "::" nel percorso qualificato dal provider. Ad esempio, il percorso interno del provider per il provider FileSystem di Windows PowerShell è `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Override dei parametri dei cmdlet

Il comportamento di alcuni cmdlet specifici del provider può essere sostituito da un provider. Per un elenco di parametri che possono essere sottoposti a override e come eseguirne l'override nella classe del provider, vedere [parametri del cmdlet del provider](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>Parametri dinamici

I provider possono definire parametri dinamici che vengono aggiunti a un cmdlet del provider quando l'utente specifica un determinato valore per uno dei parametri statici del cmdlet. Un provider esegue questa operazione implementando uno o più metodi di parametri dinamici. Per un elenco di parametri del cmdlet che possono essere usati per aggiungere parametri dinamici e i metodi usati per implementarli, vedere [parametri dinamici dei cmdlet del provider](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Funzionalità del provider

L'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) definisce un certo numero di funzionalità che i provider sono in grado di supportare. Che includono la possibilità di utilizzare caratteri jolly, filtrare gli elementi e supportare le transazioni. Per specificare le funzionalità per un provider, aggiungere un elenco di valori dell'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) , combinati con un'operazione di `OR` logica, come la proprietà [System. Management. Automation. provider. CmdletProviderAttribute. ProviderCapabilities *](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) (il secondo parametro dell'attributo) dell'attributo [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) per la classe del provider. Ad esempio, l'attributo seguente specifica che il provider supporta le funzionalità delle **transazioni** [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **ShouldProcess** e [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) .

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Guida per i cmdlet del provider

Quando si scrive un provider, è possibile implementare una guida personalizzata per i cmdlet del provider supportati. È incluso un singolo argomento della Guida per ogni cmdlet del provider o più versioni di un argomento della Guida per i casi in cui il cmdlet del provider agisce in modo diverso in base all'utilizzo di parametri dinamici. Per supportare la guida specifica del cmdlet del provider, è necessario che il provider implementi l'interfaccia [System. Management. Automation. provider. Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) .

Il motore di Windows PowerShell chiama il metodo [System. Management. Automation. provider. Icmdletprovidersupportshelp. Gethelpmaml *](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) per visualizzare l'argomento della Guida per i cmdlet del provider. Il motore fornisce il nome del cmdlet specificato dall'utente durante l'esecuzione del cmdlet `Get-Help` e il percorso corrente dell'utente. Il percorso corrente è obbligatorio se il provider implementa versioni diverse dello stesso cmdlet provider per unità diverse. Il metodo deve restituire una stringa che contiene il codice XML per la guida del cmdlet.

Il contenuto del file della guida viene scritto utilizzando il codice XML PSMAML. Si tratta dello stesso XML Schema usato per scrivere il contenuto della Guida per i cmdlet autonomi. Aggiungere il contenuto per la guida del cmdlet personalizzato al file della Guida per il provider nell'elemento `CmdletHelpPaths`. Nell'esempio seguente viene illustrato l'elemento `command` per un singolo cmdlet del provider e viene illustrato come specificare il nome del cmdlet del provider. supporta

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

[Funzionalità del provider di Windows PowerShell](./provider-types.md)

[Cmdlet del provider](./provider-cmdlets.md)

[Scrittura di un provider di Windows PowerShell](./writing-a-windows-powershell-provider.md)