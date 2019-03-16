---
title: Linee guida di sviluppo necessarie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: 3f6bcd2e4ef4d9c404b3a5deeaa9f25d3fa42ec1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056516"
---
# <a name="required-development-guidelines"></a>Linee guida sullo sviluppo necessarie

Le linee guida seguenti devono essere seguite quando si scrivono i cmdlet. Questi sono suddivisi in linee guida per la progettazione di cmdlet e le linee guida per la scrittura del codice di cmdlet. Se non si seguono queste linee guida, il cmdlet potrebbe non riuscire e agli utenti potrebbero essere un'esperienza deludente quando usano i cmdlet.

## <a name="in-this-topic"></a>In questo argomento

### <a name="design-guidelines"></a>Linee guida di progettazione

- [Usare solo i verbi (RD01) approvate](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Nomi dei cmdlet: Caratteri non possono essere usati (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [I nomi dei parametri non possono essere usati (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Supporta le richieste di conferma (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Parametro Force supporto per le sessioni interattive (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Oggetti di documento di Output (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Linee guida dei codici

- [Derivare dalle classi PSCmdlet (RC01) o Cmdlet](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Specificare l'attributo Cmdlet (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Eseguire l'override di un metodo (RC03) di elaborazione dell'Input](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Specificare l'attributo OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Non mantengono handle di oggetti di Output (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Gestire gli errori in modo affidabile (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Usare un modulo di Windows PowerShell per distribuire i cmdlet (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Linee guida di progettazione

Le linee guida seguenti devono essere seguite quando si progettano i cmdlet per garantire un'esperienza utente coerente tra l'uso dei cmdlet e altri cmdlet. Quando si individua un'indicazione di progettazione che si applica alle proprie esigenze, assicurarsi di esaminare le linee guida dei codici per le linee guida simili.

### <a name="use-only-approved-verbs-rd01"></a>Usare solo i verbi (RD01) approvate

Il verbo specificato nell'attributo Cmdlet deve provenire dal set di riconosciuto dei verbi di Windows PowerShell. Non deve essere uno dei sinonimi non consentiti. Usare le stringhe costanti definiti per le enumerazioni seguenti per specificare i verbi di cmdlet:

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Per altre informazioni sui nomi di verbo approvato, vedere [verbi dei Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Gli utenti necessitano di un set di nomi di cmdlet individuabili e previsto. Usare il verbo appropriato in modo che l'utente può eseguire una rapida valutazione delle operazioni eseguite da un cmdlet e individuare facilmente le funzionalità del sistema. Ad esempio, la riga di comando seguente ottiene un elenco di tutti i comandi nel sistema i cui nomi iniziano con "start": `get-command start-*`. Usare i sostantivi dei cmdlet per distinguere i cmdlet da altri cmdlet. Il sostantivo indica la risorsa in cui verrà eseguita l'operazione. L'operazione stessa è rappresentato dal verbo.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Nomi dei cmdlet: Caratteri non possono essere usati (RD02)

Quando si assegna un nome cmdlet, non usare i caratteri speciali seguenti.

|Carattere|Nome|
|---------------|----------|
|#|simbolo di cancelletto|
|,|Virgola|
|()|Parentesi|
|{}|apparecchio per i denti|
|[]|parentesi|
|&|e commerciale|
|-|trattino **Nota:**  Il trattino può essere utilizzato per separare il verbo dal sostantivo, ma non può essere usato entro il sostantivo o entro il verbo.|
|/|barra|
|\|backslash|
|$|Segno di dollaro|
|^|Punto di inserimento|
|;|Punto e virgola|
|:|I due punti|
|"|segno di virgolette doppie|
|'|virgoletta singola|
|<>|parentesi angolari|
|&#124;|barra verticale|
|?|punto interrogativo|
|@|simbolo di chiocciola|
|' | eseguire il backup dei segni di graduazione (accento grave)|
|*|Asterisco|
|%|Segno di percentuale|
|+|Segno di addizione|
|=|Segno di uguale|
|~|Tilde|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>I nomi dei parametri non possono essere usati (RD03)

Windows PowerShell fornisce un insieme comune di parametri a tutti i cmdlet e parametri aggiuntivi che vengono aggiunti in situazioni specifiche. Durante la progettazione dei cmdlet personalizzati è possibile utilizzare i nomi seguenti: Verificare che, Debug, ErrorAction, ErrorVariable, OutVariable OutBuffer, WarningAction, WarningVariable, WhatIf, UseTransaction e dettagliato. Per altre informazioni su questi parametri, vedere [i nomi dei parametri comuni](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Supporta le richieste di conferma (RD04)

Per i cmdlet che eseguono un'operazione che modifichi il sistema, chiamano il [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo per richiedere conferma e in alcuni casi speciali chiamare il [ System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (metodo). (Il [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodo deve essere chiamato solo dopo il [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) viene chiamato il metodo.)

Per effettuare queste chiamate deve specificare il cmdlet che supporta le richieste di conferma, impostando il `SupportsShouldProcess` (parola chiave) dell'attributo Cmdlet. Per altre informazioni sull'impostazione di questo attributo, vedere [dichiarazione di attributo Cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Se l'attributo Cmdlet della classe del cmdlet indica che il cmdlet supporta le chiamate per il [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo e il cmdlet non riesce a effettuare la chiamata al [ System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo, l'utente è stato possibile modificare il sistema in modo imprevisto.

Usare la [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo per qualsiasi modifica di sistema. Una preferenza utente e la `WhatIf` controllo del parametro di [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (metodo). Al contrario, il [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) chiamata esegue un controllo aggiuntivo per apportare modifiche potenzialmente pericolose. Questo metodo non è controllato da eventuali preferenze dell'utente o il `WhatIf` parametro. Se viene chiamato il cmdlet di [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodo, è necessario un `Force` parametro che consente di ignorare le chiamate a questi due metodi e che viene eseguita l'operazione. Questo è importante perché consente il cmdlet da utilizzare nell'host e gli script non interattiva.

Se i cmdlet supportano queste chiamate, l'utente può determinare se l'azione deve essere effettivamente eseguita. Ad esempio, il [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) chiamate cmdlet la [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodo prima che venga interrotta una serie di processi critici, incluso il sistema, Winlogon, e Processi Spoolsv.

Per altre informazioni sul supporto di questi metodi, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Parametro Force supporto per le sessioni interattive (RD05)

Se il cmdlet viene usato in modo interattivo, sempre fornire un parametro Force per ignorare le azioni interattive, ad esempio istruzioni o leggere le righe di input). Questo è importante perché consente il cmdlet da utilizzare nell'host e gli script non interattiva. I metodi seguenti possono essere implementati da un host interattivo.

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Oggetti di documento di Output (RD06)

Windows PowerShell Usa gli oggetti che vengono scritte nella pipeline. Affinché gli utenti a sfruttare i vantaggi degli oggetti restituiti da ogni cmdlet, è necessario documentare gli oggetti che vengono restituiti e devono documentare ciò che i membri di tali oggetti restituiti vengono utilizzati per.

## <a name="code-guidelines"></a>Linee guida dei codici

Le linee guida seguenti devono essere seguite quando la scrittura di codice del cmdlet. Quando si rileva una situazione di codice che si applica alle proprie esigenze, assicurarsi di esaminare le linee guida di progettazione per le linee guida simili.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Derivare dalle classi PSCmdlet (RC01) o Cmdlet

Un cmdlet deve derivare dal [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) oppure [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe di base. I cmdlet che derivano dal [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe non basarsi sul runtime di Windows PowerShell. Possono essere chiamati direttamente da qualsiasi linguaggio Microsoft .NET Framework. I cmdlet che derivano dal [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe dipendono dal runtime di Windows PowerShell. Pertanto, vengono eseguite all'interno di uno spazio di esecuzione.

Tutte le classi di cmdlet implementati devono essere classi pubbliche. Per altre informazioni su queste classi di cmdlet, vedere [Panoramica su Cmdlet](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Specificare l'attributo Cmdlet (RC02)

Per un cmdlet essere riconosciuti da Windows PowerShell, la relativa classe di .NET Framework deve essere decorata con l'attributo Cmdlet. Questo attributo specifica le funzionalità seguenti del cmdlet.

- La coppia di verbo e nome che identifica il cmdlet.

- Il set di parametri predefinito che viene usato quando si specificano più set di parametri. Il set di parametri predefinito viene utilizzato quando Windows PowerShell non dispone di informazioni sufficienti per determinare quale serie di parametri da usare.

- Indica se il cmdlet supporta le chiamate per il [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (metodo). Questo metodo visualizza un messaggio di conferma all'utente prima che il cmdlet apporta una modifica al sistema. Per altre informazioni sul modo in cui le richieste di conferma vengono eseguite, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).

- Indicare il livello di impatto (o livello di gravità) dell'azione associata al messaggio di conferma. Nella maggior parte dei casi, usare il valore predefinito Medium. Per altre informazioni sull'influenza il livello di impatto sulle richieste di conferma visualizzate all'utente, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).

Per altre informazioni su come dichiarare l'attributo cmdlet, vedere [dichiarazione CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Eseguire l'override di un metodo (RC03) di elaborazione dell'Input

Per il cmdlet di partecipare nell'ambiente di Windows PowerShell, è necessario eseguire l'override almeno uno dei seguenti *metodi di elaborazione di input*.

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) questo metodo viene chiamato una sola volta e viene usato per fornire funzionalità di pre-elaborazione.

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) questo metodo viene chiamato più volte e viene usato per fornire funzionalità di record per record.

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) questo metodo viene chiamato una sola volta e viene usato per fornire funzionalità di post-elaborazione.

### <a name="specify-the-outputtype-attribute-rc04"></a>Specificare l'attributo OutputType (RC04)

L'attributo OutputType (introdotta in Windows PowerShell 2.0) specifica il tipo di .NET Framework che il cmdlet restituisce alla pipeline. Specificando il tipo di output del cmdlet rendere gli oggetti restituiti dal cmdlet più facilmente individuabili da altri cmdlet. Per altre informazioni sulla decorazione di classe del cmdlet con questo attributo, vedere [dichiarazione di attributo OutputType](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Non mantengono handle di oggetti di Output (RC05)

Il cmdlet non devono conservare tutti gli handle per gli oggetti che vengono passati per il [System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (metodo). Questi oggetti vengono passati al cmdlet successivo nella pipeline o vengono usati da uno script. Se si mantengono gli handle di oggetti, due entità proprietario di ogni oggetto, che fa in modo che gli errori.

### <a name="handle-errors-robustly-rc06"></a>Gestire gli errori in modo affidabile (RC06)

Un ambiente di amministrazione intrinsecamente rileva ed effettua importanti modifiche al sistema che si sta amministrando. Pertanto, è fondamentale che i cmdlet di gestiscono correttamente gli errori. Per altre informazioni sui record di errore, vedere [segnalazione errori Windows PowerShell](./error-reporting-concepts.md).

- Quando un errore impedisce a un cmdlet di continuare a elaborare altri record, è un errore irreversibile. È necessario chiamare il cmdlet di [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metodo che fa riferimento a un [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetto. Se non viene intercettata un'eccezione dal cmdlet, il runtime di Windows PowerShell genera un errore irreversibile che contiene meno informazioni.

- Per un errore non fatale che non si arresta operazione al successivo record provenienti dalla pipeline (ad esempio, un record prodotto da un processo diverso), il cmdlet è necessario chiamare il [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodo che fa riferimento a un [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetto. Un esempio di un errore non fatale è l'errore che si verifica se un determinato processo non riesce ad arrestare. Chiama il [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodo consente all'utente di eseguire in modo coerente le azioni richieste e conservare le informazioni per determinate azioni che non riescono. Il cmdlet consente di gestire ogni record più indipendente possibile.

- Il [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetto cui fa riferimento il [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) e [ System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodi richiede un'eccezione alla cui base. Seguire le indicazioni per la progettazione di .NET Framework quando è possibile determinare l'eccezione da utilizzare. Se l'errore è semanticamente identico un'eccezione esistente, usare tale eccezione o derivare da tale eccezione. In caso contrario, derivare una nuova eccezione o gerarchia delle eccezioni direttamente dai [System. Exception](/dotnet/api/System.Exception) tipo.

Un' [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetto richiede anche una categoria di errore che raggruppa gli errori dell'utente. L'utente può visualizzare gli errori in base alla categoria impostando il valore della `$ErrorView` variabile della shell per CategoryView. Le possibili categorie vengono definite per il [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumerazione.

- Se un cmdlet crea un nuovo thread e se il codice che è in esecuzione in tale thread genera un'eccezione non gestita, Windows PowerShell non rileva l'errore e terminerà il processo.

- Se un oggetto dispone di codice nel relativo distruttore che genera un'eccezione non gestita, Windows PowerShell non rileva l'errore e terminerà il processo. Ciò si verifica anche se un oggetto chiama i metodi Dispose che causano un'eccezione non gestita.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Usare un modulo di Windows PowerShell per distribuire i cmdlet (RC07)

Creare un modulo di Windows PowerShell per creare un pacchetto e distribuire i cmdlet. Supporto per i moduli è stato introdotto in Windows PowerShell 2.0. È possibile usare gli assembly che contengono le classi di cmdlet direttamente come file del modulo binario (questo è molto utile durante il test dei cmdlet) oppure è possibile creare un manifesto del modulo che fa riferimento all'assembly di cmdlet. (È possibile anche aggiungere assembly con lo snap-in esistenti quando si usano moduli.) Per altre informazioni sui moduli, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Vedere anche

[Linee guida sullo sviluppo vivamente consigliato](./strongly-encouraged-development-guidelines.md)

[Linee guida sullo sviluppo di consulenza](./advisory-development-guidelines.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
