---
title: Linee guida sullo sviluppo advisory | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 871a74a084da3c7ec36767b7195461e0e7290cb9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056567"
---
# <a name="advisory-development-guidelines"></a>Linee guida sullo sviluppo consigliate

Questa sezione vengono descritte le linee guida che è opportuno considerare per garantire una buona esperienza di sviluppo e utenti. In alcuni casi si potrebbero applicare e in alcuni casi si potrebbe non.

## <a name="design-guidelines"></a>Linee guida di progettazione

- [Supporta un parametro InputObject (AD01)](./advisory-development-guidelines.md#AD01)

- [Supporto per il parametro Force (AD02)](./advisory-development-guidelines.md#AD02)

- [Gestire le credenziali tramite Windows PowerShell (AD03)](./advisory-development-guidelines.md#AD03)

- [Supporta i parametri di codifica (AD04)](./advisory-development-guidelines.md#AD04)

- [I cmdlet di prova devono restituire un valore booleano (AD05)](./advisory-development-guidelines.md#AD05)

## <a name="code-guidelines"></a>Linee guida dei codici

- [Seguire le convenzioni di denominazione classe Cmdlet (AC01)](./advisory-development-guidelines.md#AC01)

- [Se nessun Input della Pipeline esegue l'Override del metodo BeginProcessing (AC02)](./advisory-development-guidelines.md#AC02)

- [Per gestire le richieste di arresto, l'Override del metodo di StopProcessing (AC03)](./advisory-development-guidelines.md#AC03)

- [Implementare l'interfaccia IDisposable (AC04)](./advisory-development-guidelines.md#AC04)

- [Usare i tipi di parametro di facile integrazione con la serializzazione (AC05)](./advisory-development-guidelines.md#AC05)

- [Utilizzare SecureString per i dati sensibili (AC06)](./advisory-development-guidelines.md#AC06)

## <a name="design-guidelines"></a>Linee guida di progettazione

Le seguenti linee guida da considerare quando si progettano i cmdlet. Quando si individua un'indicazione di progettazione che si applica alle proprie esigenze, assicurarsi di esaminare le linee guida dei codici per le linee guida simili.

### <a name="support-an-inputobject-parameter-ad01"></a>Supporta un parametro InputObject (AD01)

Poiché Windows PowerShell funziona direttamente con gli oggetti di Microsoft .NET Framework, un oggetto .NET Framework è spesso disponibile che corrisponde esattamente il tipo di utente deve eseguono una particolare operazione. `InputObject` è il nome standard per un parametro che accetta un oggetto come input. Ad esempio, il codice di esempio **Stop-Process** cmdlet nel [StopProc esercitazione](./stopproc-tutorial.md) definisce un `InputObject` parametro del tipo di processo che supporta l'input dalla pipeline. L'utente può ottenere un set di oggetti processo, modificarli per selezionare esattamente gli oggetti per arrestare e quindi passarle per la **Stop-Process** cmdlet direttamente.

### <a name="support-the-force-parameter-ad02"></a>Supporto per il parametro Force (AD02)

In alcuni casi, un cmdlet deve impedire che l'utente esegue l'operazione richiesta. Un cmdlet di questo tipo deve supportare un `Force` parametro per consentire all'utente di eseguire l'override di tale protezione se l'utente disponga delle autorizzazioni per eseguire l'operazione.

Ad esempio, il [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet non rimuove in genere un file di sola lettura. Tuttavia, questo cmdlet supporta una `Force` parametro in modo che un utente può forzare la rimozione di un file di sola lettura. Se l'utente dispone già dell'autorizzazione per modificare l'attributo di sola lettura e l'utente rimuove il file, usare il `Force` parametro semplifica l'operazione. Tuttavia, se l'utente non dispone dell'autorizzazione per rimuovere il file, il `Force` parametro non ha alcun effetto.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Gestire le credenziali tramite Windows PowerShell (AD03)

Un cmdlet è necessario definire un `Credential` parametro per rappresentare le credenziali. Questo parametro deve essere di tipo [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) e deve essere definito mediante una dichiarazione di attributo di credenziali. Questo supporto automaticamente richiesto all'utente per il nome utente, la password o per entrambi quando una credenziale completa non viene fornita direttamente. Per altre informazioni sull'attributo credenziale, vedere [dichiarazione di attributo credenziale](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Supporta i parametri di codifica (AD04)

Se il cmdlet legge o scrive il testo da o verso un formato binario, ad esempio la scrittura o lettura da un file in un file System, quindi il cmdlet deve includere il parametro Encoding che specifica come il testo è codificato in formato binario.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>I cmdlet di prova devono restituire un valore booleano (AD05)

Cmdlet che eseguono i test con le relative risorse deve restituire un [System. Boolean](/dotnet/api/System.Boolean) tipo alla pipeline in modo che possono essere utilizzati nelle espressioni condizionali.

## <a name="code-guidelines"></a>Linee guida dei codici

Le linee guida seguenti devono essere considerate durante la scrittura di codice del cmdlet. Quando si rileva una situazione che si applica alle proprie esigenze, assicurarsi di esaminare le linee guida di progettazione per le linee guida simili.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Seguire le convenzioni di denominazione classe Cmdlet (AC01)

Dalle seguenti convenzioni di denominazione standard, i cmdlet di rendere più facilmente individuabili ed consentire all'utente di comprendere esattamente ciò che usano i cmdlet. Questa pratica è particolarmente importante per gli altri sviluppatori che usano Windows PowerShell perché i cmdlet sono i tipi pubblici.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Definire un Cmdlet nel Namespace corretto

In genere definire la classe per un cmdlet in uno spazio dei nomi .NET Framework che consente di accodare ". Comandi"per lo spazio dei nomi che rappresenta il prodotto in cui viene eseguito il cmdlet. Ad esempio, i cmdlet inclusi in Windows PowerShell sono definiti nel `Microsoft.PowerShell.Commands` dello spazio dei nomi.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Denominare la classe Cmdlet corrisponda al nome di Cmdlet

Quando si assegna un nome di classe .NET Framework che implementa un cmdlet, denominare la classe "*\<verbo >**\<sostantivo >**\<comando >*", in cui si sostituisce il  *\<Verbo >* e  *\<sostantivo >* segnaposto con il verbo e sostantivo utilizzato per il nome del cmdlet. Ad esempio, il [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet viene implementato in una classe denominata `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Se nessun Input della Pipeline esegue l'Override del metodo BeginProcessing (AC02)

Se il cmdlet non accetta input dalla pipeline, l'elaborazione deve essere implementata nel [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (metodo). Usare questo metodo consente a Windows PowerShell per mantenere l'ordine tra i cmdlet. Il primo cmdlet nella pipeline restituisce sempre gli oggetti prima i rimanenti cmdlet nella pipeline l'opportunità di avviare l'elaborazione.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Per gestire le richieste di arresto, l'Override del metodo di StopProcessing (AC03)

Eseguire l'override di [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) metodo in modo che il cmdlet può gestire segnale di arresto. Alcuni cmdlet richiedere molto tempo per completare il loro funzionamento e consentono molto tempo passa tra le chiamate al runtime di Windows PowerShell, ad esempio quando il cmdlet blocca il thread in chiamate RPC con esecuzione prolungata. Questo include i cmdlet che effettuano chiamate al [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metodo, al [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (metodo) e altri commenti e suggerimenti meccanismi che potrebbero richiedere molto tempo per il completamento. In questi casi l'utente potrebbe essere necessario inviare un segnale di arresto a questi cmdlet.

### <a name="implement-the-idisposable-interface-ac04"></a>Implementare l'interfaccia IDisposable (AC04)

Se il cmdlet include oggetti non vengono eliminati di (scritto per la pipeline) per il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo, il cmdlet potrebbe richiedere l'eliminazione dell'oggetto aggiuntive. Se, ad esempio, il cmdlet consente di aprire un handle di file nel relativo [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metodo e mantiene l'handle aprire per l'uso dal [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo, l'handle deve essere chiuso al termine dell'elaborazione.

Il runtime di Windows PowerShell non chiama sempre il [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (metodo). Ad esempio, il [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodo non può essere chiamato se il cmdlet viene annullato punto intermedio attraverso il suo funzionamento o se una terminazione errore si verifica in qualsiasi parte del cmdlet. Pertanto, la classe di .NET Framework per un cmdlet che richiede la pulizia degli oggetti deve implementare l'intero [System. IDisposable](/dotnet/api/System.IDisposable) criterio di interfaccia, inclusi il finalizzatore, in modo che il runtime di Windows PowerShell può chiamare entrambe le [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) e [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) metodi alla fine dell'elaborazione.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Usare i tipi di parametro di facile integrazione con la serializzazione (AC05)

Per supportare l'esecuzione del cmdlet in computer remoti, usare i tipi che possono essere facilmente serializzati nel computer client e quindi riattivazione su computer del server. I tipi seguenti sono facile integrazione con la serializzazione.

Tipi primitivi:

- Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32 e UInt64.

- Boolean, Guid, Byte [], intervallo di tempo, DateTime, Uri e versione.

- Char, String, XmlDocument.

Tipi rehydratable predefiniti:

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- PSCredential

- IPAddress, MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- DirectorySecurity, FileSecurity, RegistrySecurity

Altri tipi:

- StringaSicura

- Contenitori (elenchi e dizionari del tipo precedente)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Utilizzare SecureString per i dati sensibili (AC06)

Quando si gestiscono i dati sensibili sempre usare il [SecureString](/dotnet/api/System.Security.SecureString) tipo di dati. Ad esempio input di pipeline per i parametri, nonché la restituzione di dati sensibili alla pipeline.

## <a name="see-also"></a>Vedere anche

[Linee guida di sviluppo necessari](./required-development-guidelines.md)

[Linee guida sullo sviluppo vivamente consigliato](./strongly-encouraged-development-guidelines.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
