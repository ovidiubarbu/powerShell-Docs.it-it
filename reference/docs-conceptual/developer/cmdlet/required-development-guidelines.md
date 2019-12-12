---
title: Linee guida per lo sviluppo obbligatorie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: e68e43a91f9139e8d3dc636b5740121515aab2e6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369520"
---
# <a name="required-development-guidelines"></a>Linee guida sullo sviluppo necessarie

Quando si scrivono i cmdlet, è necessario seguire le linee guida seguenti. Sono separate da linee guida per la progettazione di cmdlet e linee guida per la scrittura del codice del cmdlet. Se non si seguono queste linee guida, i cmdlet potrebbero avere esito negativo e gli utenti potrebbero avere un'esperienza negativa quando usano i cmdlet.

## <a name="in-this-topic"></a>In questo argomento

### <a name="design-guidelines"></a>Linee guida per la progettazione

- [USA solo verbi approvati (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Nomi cmdlet: caratteri che non possono essere usati (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Nomi dei parametri che non possono essere usati (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Supporto richieste di conferma (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Parametro Force di supporto per sessioni interattive (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Oggetti di output del documento (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Linee guida del codice

- [Derivazione dal cmdlet o dalle classi PSCmdlet (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Specificare l'attributo del cmdlet (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Eseguire l'override di un metodo di elaborazione dell'input (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Specificare l'attributo OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Non mantenere gli handle per gli oggetti di output (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Gestione affidabile degli errori (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Usare un modulo di Windows PowerShell per distribuire i cmdlet (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Linee guida per la progettazione

È necessario seguire le linee guida seguenti quando si progettano i cmdlet per garantire un'esperienza utente coerente tra l'uso dei cmdlet e di altri cmdlet. Quando si individuano le linee guida per la progettazione applicabili alla propria situazione, assicurarsi di esaminare le linee guida del codice per le linee guida simili.

### <a name="use-only-approved-verbs-rd01"></a>USA solo verbi approvati (RD01)

Il verbo specificato nell'attributo del cmdlet deve provenire dal set di verbi riconosciuto fornito da Windows PowerShell. Non deve essere uno dei sinonimi proibiti. Usare le stringhe costanti definite dalle enumerazioni seguenti per specificare i verbi dei cmdlet:

- [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Per ulteriori informazioni sui nomi dei verbi approvati, vedere [verbi cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Gli utenti necessitano di un set di nomi di cmdlet individuabili e previsti. Usare il verbo appropriato in modo che l'utente possa eseguire una valutazione rapida del funzionamento di un cmdlet e individuare facilmente le funzionalità del sistema. Ad esempio, il comando della riga di comando seguente ottiene un elenco di tutti i comandi nel sistema i cui nomi iniziano con "Start": `get-command start-*`. Usare i sostantivi nei cmdlet per distinguere i cmdlet da altri cmdlet. Il sostantivo indica la risorsa in cui verrà eseguita l'operazione. L'operazione stessa è rappresentata dal verbo.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Nomi cmdlet: caratteri che non possono essere usati (RD02)

Quando si denominano i cmdlet, non usare uno dei caratteri speciali seguenti.

|Carattere|Name|
|---------------|----------|
|#|simbolo di cancelletto|
|,|comma (virgola)|
|()|parentesi|
|{}|graffe|
|[]|quadre|
|&|e commerciale|
|-|segno meno **:** il trattino può essere usato per separare il verbo dal sostantivo, ma non può essere usato all'interno del sostantivo o all'interno del verbo.|
|/|barra contrassegnata|
|\\| barra rovesciata|
|$|segno di dollaro|
|^|caret|
|;|punto e virgola|
|:|virgola|
|"|virgolette doppie|
|'|virgoletta singola|
|<>|parentesi angolari|
|&#124;|barra verticale|
|?|punto interrogativo|
|@|simbolo di chiocciola|
|`|apice inverso (grave accento)|
|*|asterisco|
|%|segno di percentuale|
|+|segno più|
|=|segno di uguale|
|~|tilde|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Nomi dei parametri che non possono essere usati (RD03)

Windows PowerShell fornisce un set comune di parametri a tutti i cmdlet, oltre a parametri aggiuntivi aggiunti in situazioni specifiche. Quando si progettano cmdlet personalizzati, non è possibile usare i nomi seguenti: Confirm, debug, ErrorAction, ErrorVariable, OutBuffer, OutVariable, WarningAction, WarningVariable, WhatIf, UseTransaction e Verbose. Per ulteriori informazioni su questi parametri, vedere [nomi di parametri comuni](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Supporto richieste di conferma (RD04)

Per i cmdlet che eseguono un'operazione che modifica il sistema, devono chiamare il metodo [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) per richiedere la conferma e, in casi speciali, chiamare il metodo [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . È necessario chiamare il metodo [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) solo dopo la chiamata del metodo [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .

Per effettuare queste chiamate, il cmdlet deve specificare che supporta le richieste di conferma impostando la parola chiave `SupportsShouldProcess` dell'attributo del cmdlet. Per ulteriori informazioni sull'impostazione di questo attributo, vedere [dichiarazione dell'attributo del cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Se l'attributo cmdlet della classe cmdlet indica che il cmdlet supporta le chiamate al metodo [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e il cmdlet non riesce a effettuare la chiamata al metodo [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , l'utente potrebbe modificare il sistema in modo imprevisto.

Usare il metodo [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) per tutte le modifiche del sistema. Una preferenza utente e il parametro `WhatIf` controllano il metodo [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Al contrario, la chiamata [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) esegue un controllo aggiuntivo per le modifiche potenzialmente pericolose. Questo metodo non è controllato da alcuna preferenza utente o dal parametro `WhatIf`. Se il cmdlet chiama il metodo [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , deve avere un parametro `Force` che ignora le chiamate a questi due metodi e che procede con l'operazione. Questo è importante perché consente l'uso del cmdlet in script e host non interattivi.

Se i cmdlet supportano queste chiamate, l'utente può determinare se l'azione deve essere effettivamente eseguita. Ad esempio, il cmdlet [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) chiama il metodo [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) prima di arrestare un set di processi critici, inclusi i processi System, Winlogon e Spoolsv.

Per ulteriori informazioni sul supporto di questi metodi, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Parametro Force di supporto per sessioni interattive (RD05)

Se il cmdlet viene usato in modo interattivo, fornire sempre un parametro Force per eseguire l'override delle azioni interattive, ad esempio i prompt o la lettura di righe di input. Questo è importante perché consente l'uso del cmdlet in script e host non interattivi. I metodi seguenti possono essere implementati da un host interattivo.

- [System. Management. Automation. host. PSHostUserInterface. prompt *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System. Management. Automation. host. Pshostuserinterface. PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System. Management. Automation. host. Ihostuisupportsmultiplechoiceselection. PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System. Management. Automation. host. Pshostuserinterface. PromptForCredential *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System. Management. Automation. host. Pshostuserinterface. ReadLine *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System. Management. Automation. host. Pshostuserinterface. ReadLineAsSecureString *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Oggetti di output del documento (RD06)

Windows PowerShell usa gli oggetti scritti nella pipeline. Per consentire agli utenti di sfruttare gli oggetti restituiti da ogni cmdlet, è necessario documentare gli oggetti restituiti ed è necessario documentare gli elementi per i quali vengono utilizzati i membri degli oggetti restituiti.

## <a name="code-guidelines"></a>Linee guida del codice

Quando si scrive il codice del cmdlet, è necessario seguire le linee guida seguenti. Quando si individua una linea guida per il codice che si applica alla propria situazione, assicurarsi di esaminare le linee guida per la progettazione di linee guida analoghe.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Derivazione dal cmdlet o dalle classi PSCmdlet (RC01)

Un cmdlet deve derivare dalla classe di base [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) o [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . I cmdlet che derivano dalla classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) non dipendono dal runtime di Windows PowerShell. Possono essere chiamati direttamente da qualsiasi linguaggio Microsoft .NET Framework. I cmdlet che derivano dalla classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) dipendono dal runtime di Windows PowerShell. Quindi, vengono eseguite all'interno di un spazio.

Tutte le classi di cmdlet implementate devono essere classi pubbliche. Per altre informazioni su queste classi di cmdlet, vedere [Cenni preliminari sui cmdlet](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Specificare l'attributo del cmdlet (RC02)

Affinché un cmdlet venga riconosciuto da Windows PowerShell, la relativa .NET Framework classe deve essere decorata con l'attributo cmdlet. Questo attributo specifica le funzionalità seguenti del cmdlet.

- Coppia verbo-e-sostantivo che identifica il cmdlet.

- Set di parametri predefinito utilizzato quando vengono specificati più set di parametri. Il set di parametri predefinito viene utilizzato quando Windows PowerShell non dispone di informazioni sufficienti per determinare il set di parametri da utilizzare.

- Indica se il cmdlet supporta le chiamate al metodo [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Questo metodo Visualizza un messaggio di conferma all'utente prima che il cmdlet apporta una modifica al sistema. Per ulteriori informazioni sul modo in cui vengono effettuate le richieste di conferma, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).

- Indica il livello di effetto (o gravità) dell'azione associata al messaggio di conferma. Nella maggior parte dei casi, è consigliabile usare il valore predefinito di media. Per ulteriori informazioni su come il livello di impatto influisca sulle richieste di conferma visualizzate all'utente, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).

Per ulteriori informazioni su come dichiarare l'attributo cmdlet, vedere [dichiarazione CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Eseguire l'override di un metodo di elaborazione dell'input (RC03)

Affinché il cmdlet partecipi all'ambiente di Windows PowerShell, deve eseguire l'override di almeno uno dei seguenti *metodi di elaborazione di input*.

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) questo metodo viene chiamato una sola volta e viene usato per fornire funzionalità di pre-elaborazione.

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) questo metodo viene chiamato più volte e viene usato per fornire funzionalità record per record.

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) questo metodo viene chiamato una sola volta e viene usato per fornire funzionalità di post-elaborazione.

### <a name="specify-the-outputtype-attribute-rc04"></a>Specificare l'attributo OutputType (RC04)

L'attributo OutputType, introdotto in Windows PowerShell 2,0, specifica il tipo di .NET Framework restituito dal cmdlet alla pipeline. Specificando il tipo di output dei cmdlet, è possibile rendere gli oggetti restituiti dal cmdlet più individuabili da altri cmdlet. Per ulteriori informazioni sull'decorazione della classe cmdlet con questo attributo, vedere [dichiarazione dell'attributo OutputType](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Non mantenere gli handle per gli oggetti di output (RC05)

Il cmdlet non deve conservare gli handle per gli oggetti passati al metodo [System. Management. Automation. cmdlet. WriteObject *](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Questi oggetti vengono passati al cmdlet successivo nella pipeline o utilizzati da uno script. Se si mantengono gli handle per gli oggetti, due entità sono proprietarie di ogni oggetto, causando errori.

### <a name="handle-errors-robustly-rc06"></a>Gestione affidabile degli errori (RC06)

Un ambiente di amministrazione rileva in modo intrinseco e apporta importanti modifiche al sistema che si sta amministrando. Pertanto, è fondamentale che i cmdlet gestiscano correttamente gli errori. Per ulteriori informazioni sui record degli errori, vedere [segnalazione errori Windows PowerShell](./error-reporting-concepts.md).

- Quando un errore impedisce a un cmdlet di continuare a elaborare altri record, si tratta di un errore fatale. Il cmdlet deve chiamare il metodo [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) che fa riferimento a un oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Se un'eccezione non viene rilevata dal cmdlet, il runtime di Windows PowerShell genera un errore fatale che contiene meno informazioni.

- Per un errore non irreversibile che non interrompe l'operazione sul record successivo proveniente dalla pipeline (ad esempio, un record prodotto da un processo diverso), il cmdlet deve chiamare il metodo [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) che fa riferimento a un oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Un esempio di errore non irreversibile è l'errore che si verifica se un determinato processo non viene arrestato. La chiamata del metodo [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) consente all'utente di eseguire in modo coerente le azioni richieste e di conservare le informazioni per determinate azioni che non riescono. Il cmdlet deve gestire ogni record nel modo più indipendente possibile.

- L'oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) a cui fanno riferimento i metodi [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) e [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) richiede un'eccezione al suo interno. Seguire le linee guida di progettazione .NET Framework quando si determina l'eccezione da usare. Se l'errore è semanticamente uguale a un'eccezione esistente, utilizzare tale eccezione o derivare da tale eccezione. In caso contrario, derivare una nuova eccezione o una nuova gerarchia di eccezioni direttamente dal tipo [System. Exception](/dotnet/api/System.Exception) .

Un oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) richiede inoltre una categoria di errore che raggruppa gli errori per l'utente. L'utente può visualizzare gli errori in base alla categoria impostando il valore della variabile `$ErrorView` Shell su CategoryView. Le categorie possibili sono definite dall'enumerazione [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) .

- Se un cmdlet crea un nuovo thread e il codice in esecuzione nel thread genera un'eccezione non gestita, Windows PowerShell non rileva l'errore e termina il processo.

- Se un oggetto dispone di codice nel relativo distruttore che causa un'eccezione non gestita, Windows PowerShell non rileverà l'errore e terminerà il processo. Questo errore si verifica anche se un oggetto chiama metodi Dispose che generano un'eccezione non gestita.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Usare un modulo di Windows PowerShell per distribuire i cmdlet (RC07)

Creare un modulo di Windows PowerShell per creare il pacchetto e distribuire i cmdlet. Il supporto per i moduli è stato introdotto in Windows PowerShell 2,0. È possibile usare gli assembly che contengono le classi di cmdlet direttamente come file di moduli binari (questo è molto utile quando si esegue il test dei cmdlet) oppure è possibile creare un manifesto del modulo che fa riferimento agli assembly di cmdlet. È anche possibile aggiungere assembly snap-in esistenti quando si usano i moduli. Per ulteriori informazioni sui moduli, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Vedere anche

[Linee guida per lo sviluppo fortemente consigliate](./strongly-encouraged-development-guidelines.md)

[Linee guida per lo sviluppo consultivo](./advisory-development-guidelines.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
