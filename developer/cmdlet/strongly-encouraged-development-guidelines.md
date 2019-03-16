---
title: Vivamente consigliato linee guida sullo sviluppo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057723"
---
# <a name="strongly-encouraged-development-guidelines"></a>Linee guida sullo sviluppo vivamente consigliate

Questa sezione vengono descritte le linee guida da seguire quando si scrivono i cmdlet. Questi sono suddivisi in linee guida per la progettazione di cmdlet e le linee guida per la scrittura del codice di cmdlet. È possibile che queste linee guida non sono applicabili per ogni scenario. Tuttavia, se si applicano e non si seguono queste linee guida, gli utenti potrebbero essere un'esperienza deludente quando usano i cmdlet.

## <a name="design-guidelines"></a>Linee guida di progettazione

- [Usare un sostantivo specifico per un nome di Cmdlet (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Usare la convenzione Pascal maiuscole per i nomi dei Cmdlet (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Linee guida di progettazione di parametro (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Fornire commenti e suggerimenti all'utente (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Creare un File della Guida dei Cmdlet (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Linee guida dei codici

- [Parametri di codifica (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Supporta l'Input della Pipeline ben definito (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Scrivere un record singolo la pipeline (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Rendere i cmdlet di maiuscole e minuscole e maiuscole-mantenimento (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Linee guida di progettazione

Le seguenti linee guida da seguire quando si progettano i cmdlet per garantire un'esperienza utente coerente tra l'uso dei cmdlet e altri cmdlet. Quando si individua un'indicazione di progettazione che si applica alle proprie esigenze, assicurarsi di esaminare le linee guida dei codici per le linee guida simili.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Usare un sostantivo specifico per un nome di Cmdlet (SD01)

Sostantivi utilizzati nei nomi di cmdlet devono essere molto specifico in modo che l'utente può individuare i cmdlet. Prefisso sostantivi generici, ad esempio "server" con una versione abbreviata del nome del prodotto. Ad esempio, se un sostantivo fa riferimento a un server che esegue un'istanza di Microsoft SQL Server, usare un sostantivo, ad esempio "SQLServer". La combinazione di sostantivi specifici e il breve elenco dei verbi approvati consentono all'utente di individuare rapidamente e prevederne la funzionalità evitando la duplicazione tra i nomi dei cmdlet.

Per migliorare l'esperienza utente, il sostantivo scelti dall'utente per un nome di cmdlet dovrebbe essere singolare. Ad esempio, usare il nome `Get-Process` invece di **Get-processi**. È consigliabile attenersi a questa regola per tutti i nomi di cmdlet, anche quando un cmdlet è probabile che agiscono su più di un elemento.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Usare la convenzione Pascal maiuscole per i nomi dei Cmdlet (SD02)

La convenzione Pascal caso di utilizzo per i nomi dei parametri. In altre parole, converte in maiuscolo la prima lettera del verbo e tutti i termini usati nel sostantivo. Ad esempio, "`Clear-ItemProperty`".

### <a name="parameter-design-guidelines-sd03"></a>Linee guida di progettazione di parametro (SD03)

Un cmdlet necessita di parametri che ricevono i dati in cui deve operare e i parametri che indicano le informazioni utilizzate per determinare le caratteristiche dell'operazione. Ad esempio, potrebbe essere un cmdlet di un `Name` parametro che riceve dati dalla pipeline e il cmdlet potrebbe avere un `Force` parametro per indicare che è possibile forzare il cmdlet per eseguire l'operazione. Non sono previsti limiti al numero di parametri che è possibile definire un cmdlet.

#### <a name="use-standard-parameter-names"></a>Usare i nomi dei parametri Standard

Il cmdlet deve usare i nomi dei parametri standard in modo che l'utente può determinare rapidamente ciò che significa che un determinato parametro. Se è necessario un nome più specifico, usare un nome di parametro standard e quindi specificare un nome più specifico come alias. Ad esempio, il `Get-Service` cmdlet ha un parametro con un nome generico (`Name`) e un alias più specifico (`ServiceName`). Entrambi i termini sono utilizzabile per specificare il parametro.

Per altre informazioni sui nomi dei parametri e i relativi tipi di dati, vedere [nome del parametro di Cmdlet e linee guida per la funzionalità](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Usare i nomi dei parametri singolare

Evitare di usare nomi plurali per i parametri il cui valore è un singolo elemento. Questo include i parametri che accettano le matrici o elenchi perché l'utente potrebbe fornire una matrice o elenco con un solo elemento.

I nomi dei parametri plurale deve essere utilizzati solo nei casi in cui il valore del parametro è sempre un valore più elementi. In questi casi, il cmdlet deve verificare che vengono specificati più elementi e il cmdlet deve essere visualizzato un avviso all'utente se non vengono specificati più elementi.

#### <a name="use-pascal-case-for-parameter-names"></a>Usare la convenzione Pascal maiuscole per i nomi dei parametri

La convenzione Pascal caso di utilizzo per i nomi dei parametri. In altre parole, converte in maiuscolo la prima lettera di ogni parola nel nome del parametro, tra cui la prima lettera del nome. Ad esempio, il nome del parametro `ErrorAction` utilizza le maiuscole siano corrette. I nomi dei parametri seguenti usano l'uso delle maiuscole non corretto:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Parametri che accettano un elenco di opzioni

Esistono due modi per creare un parametro il cui valore può essere selezionati da un set di opzioni.

- Definire un tipo di enumerazione (o usare un tipo di enumerazione esistente) che specifica i valori validi. Quindi, usare il tipo di enumerazione per creare un parametro di quel tipo.

- Aggiungere il **ValidateSet** alla dichiarazione del parametro dell'attributo. Per altre informazioni su questo attributo, vedere [dichiarazione di attributo ValidateSet](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Utilizzare i tipi Standard per i parametri

Per garantire la coerenza con altri cmdlet, usare i tipi standard per i parametri di volte che ciò è possibile. Per altre informazioni sui tipi da usare per il parametro diversi, vedere [Standard i nomi dei parametri di Cmdlet e i tipi](./standard-cmdlet-parameter-names-and-types.md). In questo argomento vengono forniti collegamenti a diversi argomenti che descrivono i nomi e tipi di .NET Framework per i gruppi di parametri standard, ad esempio i parametri"attività".

#### <a name="use-strongly-typed-net-framework-types"></a>Utilizzare i tipi di Framework .NET fortemente tipizzati

I parametri devono essere definiti come tipi di .NET Framework per fornire una migliore convalida dei parametri. Ad esempio, i parametri che sono limitati a un valore da un set di valori devono essere definiti come un tipo di enumerazione. Per supportare un valore di Uniform Resource Identifier (URI), definire il parametro come un [System. URI](/dotnet/api/System.Uri) tipo. Evitare di parametri di base su stringhe per le proprietà tutto tranne testo libero.

#### <a name="use-consistent-parameter-types"></a>Usare i tipi di parametro coerenti

Se lo stesso parametro è utilizzato da più cmdlet, usare sempre lo stesso tipo di parametro.  Ad esempio, se il `Process` parametro è un [System.Int16](/dotnet/api/System.Int16) tipo per un cmdlet, non apportare il `Process` parametro per un altro cmdlet una [System.Uint16](/dotnet/api/System.UInt16) tipo.

#### <a name="parameters-that-take-true-and-false"></a>I parametri che accettano True e False

Se il parametro accetta solo `true` e `false`, definire il parametro di tipo [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter). Un parametro opzionale viene considerato come `true` quando viene specificato in un comando. Se il parametro non è incluso in un comando, Windows PowerShell considera il valore del parametro in modo `false`. Non definire i parametri booleani.

Se il parametro deve distinguere tra i 3 valori: "" non è specificato e, $false $true quindi definisce un parametro di tipo Nullable\<bool >.  La necessità di un 3rd, valore "non specificato" si verifica in genere quando il cmdlet è possibile modificare una proprietà booleana dell'oggetto. In questo caso "non specificato" indica di non modificare il valore corrente della proprietà.

#### <a name="support-arrays-for-parameters"></a>Supporta le matrici di parametri

Spesso, gli utenti devono eseguire la stessa operazione su più argomenti. Per i quali un cmdlet debba accettare una matrice come parametro di input in modo che un utente può passare gli argomenti nel parametro come una variabile di Windows PowerShell. Ad esempio, il [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet Usa una matrice di stringhe che identificano i nomi dei processi da recuperare.

#### <a name="support-the-passthru-parameter"></a>Supporta il parametro PassThru

Per impostazione predefinita, molti cmdlet che modificano il sistema, ad esempio la [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet, come "sink" per gli oggetti e non restituiscono un risultato. Questi cmdlet è necessario implementare il `PassThru` parametro per forzare il cmdlet per restituire un oggetto. Quando la `PassThru` parametro è specificato, il cmdlet restituisce un oggetto tramite una chiamata ai [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (metodo). Ad esempio, il comando seguente arresta il processo Calc e passa il processo risultante alla pipeline.

```powershell
Stop-Process calc -passthru
```

Nella maggior parte dei casi, i cmdlet Add, Set e New devono supportare un `PassThru` parametro.

#### <a name="support-parameter-sets"></a>Set di parametri di supporto

Un cmdlet è progettato per eseguire un unico scopo. Tuttavia, vi è spesso più di un modo per descrivere l'operazione o la destinazione dell'operazione. Ad esempio, un processo può essere identificato in base al nome, in base all'identificatore o da un oggetto processo. Il cmdlet deve supportare tutte le rappresentazioni ragionevole delle relative destinazioni. In genere, il cmdlet soddisfa questo requisito, specificando set di parametri (definiti come set di parametri) che vengono usati insieme. Un singolo parametro può appartenere a qualsiasi numero di set di parametri. Per altre informazioni sui set di parametri, vedere [imposta parametro di Cmdlet](./cmdlet-parameter-sets.md).

Quando si specificano set di parametri, impostare un solo parametro nel set da ValueFromPipeline. Per altre informazioni su come dichiarare la **parametri** dell'attributo, vedere [ParameterAttribute dichiarazione](./parameter-attribute-declaration.md).

Quando si utilizzano set di parametri, il set di parametri predefinito è definito per il **Cmdlet** attributo. Il set di parametri predefinito deve includere i parametri più probabili verranno utilizzati in una sessione interattiva di Windows PowerShell. Per altre informazioni su come dichiarare la **Cmdlet** dell'attributo, vedere [dichiarazione CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Fornire commenti e suggerimenti all'utente (SD04)

Usare le linee guida in questa sezione per fornire commenti e suggerimenti all'utente. Questi commenti e suggerimenti consente all'utente di essere a conoscenza di ciò che avviene nel sistema e al meglio le decisioni amministrativi.

Il runtime di Windows PowerShell consente agli utenti di specificare come gestire l'output di ogni chiamata al `Write` metodo impostando una variabile di preferenza. L'utente può impostare più variabili di preferenza, tra cui una variabile che determina se il sistema deve visualizzare le informazioni e una variabile che determina se il sistema deve eseguire una query all'utente prima di eseguire altre azioni.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Supporto di WriteWarning, WriteVerbose e metodi WriteDebug

Un cmdlet deve chiamare il [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metodo quando il cmdlet sta per eseguire un'operazione che potrebbe avere un risultato imprevisto. Ad esempio, un cmdlet deve chiamare questo metodo se il cmdlet deve sovrascrivere un file di sola lettura.

Un cmdlet deve chiamare il [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metodo quando l'utente richiede alcuni dettagli sulle operazioni eseguite il cmdlet. Ad esempio, un cmdlet deve chiamare queste informazioni se l'autore del cmdlet ritiene che non esistono scenari che potrebbero richiedere ulteriori informazioni su cosa sta facendo il cmdlet.

Il cmdlet deve chiamare il [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metodo quando un tecnico del supporto per gli sviluppatori o un prodotto è necessario comprendere ciò che ha danneggiato l'operazione di cmdlet. Non è necessario per il cmdlet per chiamare il [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metodo nello stesso codice che chiama il [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) (metodo) Poiché il `Debug` parametro presenta entrambi i set di informazioni.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>Supporto WriteProgress per operazioni che richiedono molto tempo

Operazioni del cmdlet che accettano un molto tempo e che non è possibile eseguire in background deve supportare lo stato di avanzamento reporting tramite eseguendo chiamate regolari al [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) (metodo).

#### <a name="use-the-host-interfaces"></a>Utilizzare le interfacce Host

In alcuni casi, un cmdlet deve comunicare direttamente con l'utente invece di usando i vari di scrittura o deve metodi supportati dal [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. In questo caso, il cmdlet deve derivare dal [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe e usare i [System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) proprietà. Questa proprietà supporta livelli diversi di tipo di comunicazione, inclusi i tipi PromptForChoice, prompt dei comandi e WriteLine/ReadLine. Livello più specifico, fornisce inoltre metodi per leggere e scrivere le singole chiavi e affrontare i buffer.

A meno che un cmdlet è progettato specificamente per generare un'interfaccia utente grafica (GUI), non dovrà ignorare l'host utilizzando la [System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) proprietà. Un esempio di un cmdlet che è progettato per generare un'interfaccia utente grafica è la [Out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) cmdlet.

> [!NOTE]
> I cmdlet non devono usare la [System. console](/dotnet/api/System.Console) API.

### <a name="create-a-cmdlet-help-file-sd05"></a>Creare un File della Guida dei Cmdlet (SD05)

Per ogni assembly di cmdlet, creare un file Help.xml che contiene informazioni sul cmdlet. Queste informazioni includono una descrizione del cmdlet, le descrizioni dei parametri del cmdlet, esempi di uso del cmdlet e altro ancora.

## <a name="code-guidelines"></a>Linee guida dei codici

Le seguenti linee guida da seguire quando si scrive codice cmdlet per garantire un'esperienza utente coerente tra l'uso dei cmdlet e altri cmdlet. Quando si rileva una situazione di codice che si applica alle proprie esigenze, assicurarsi di esaminare le linee guida di progettazione per le linee guida simili.

### <a name="coding-parameters-sc01"></a>Parametri di codifica (SC01)

Definire un parametro dichiarando una proprietà pubblica della classe del cmdlet che è decorata con il **parametro** attributo. Parametri non devono essere membri statici della classe derivata di .NET Framework per il cmdlet. Per altre informazioni su come dichiarare la **parametri** dell'attributo, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Supporto dei percorsi di Windows PowerShell

Il percorso di Windows PowerShell è il meccanismo per la normalizzazione dell'accesso agli spazi dei nomi. Quando si assegna un percorso di Windows PowerShell a un parametro nel cmdlet, l'utente può definire una classe personalizzata "unità" che agisce come un collegamento a un percorso specifico. Quando un utente specifica un'unità di questo tipo, i dati archiviati, ad esempio i dati nel Registro di sistema, è utilizzabile in modo coerente.

Se il cmdlet consente all'utente di specificare un file o un'origine dati, è necessario definire un parametro di tipo [System. String](/dotnet/api/System.String). Se più di una unità sia supportata, il tipo deve essere una matrice. Il nome del parametro deve essere `Path`, con un alias di `PSPath`. Inoltre, il `Path` parametro deve supportare i caratteri jolly. Se il supporto per i caratteri jolly non è necessario, definire un `LiteralPath` parametro.

Se i dati che il cmdlet legge o scrive deve essere un file, il cmdlet deve accettare l'input di percorso di Windows PowerShell e debba usare il cmdlet di [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path) proprietà per la conversione di Windows Percorsi di PowerShell in percorsi di file system riconosciuto da. I meccanismi specifici includono i seguenti metodi:

- [System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Se i dati che il cmdlet legge o scrive sono solo un set di stringhe invece di un file, il cmdlet deve usare le informazioni sul contenuto di provider (`Content` membro) per leggere e scrivere. Queste informazioni vengono ottenute dal [System.Management.Automation.Provider.CmdletProvider.InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) proprietà. Questi meccanismi offrono altri archivi dati a partecipare in lettura e scrittura dei dati.

#### <a name="support-wildcard-characters"></a>Supporta i caratteri jolly

Un cmdlet deve supportare i caratteri jolly se possibile. Supporto per i caratteri jolly si verifica in molte posizioni all'interno di un cmdlet (in particolare quando il parametro accetta una stringa per identificare un oggetto da un set di oggetti). Ad esempio, il codice di esempio **Stop-Process** cmdlet impedisce il [StopProc esercitazione](./stopproc-tutorial.md) definisce un `Name` parametro per gestire le stringhe che rappresentano i nomi dei processi. Questo parametro supporta i caratteri jolly in modo che l'utente può specificare facilmente i processi da arrestare.

Quando il supporto per caratteri jolly caratteri è disponibile, un'operazione di cmdlet è in genere produce una matrice. In alcuni casi non ha senso per supportare una matrice perché l'utente può usare solo un singolo elemento alla volta. Ad esempio, il [Set-Location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) cmdlet non è necessario supportare una matrice perché l'utente è l'impostazione solo un'unica posizione. In questo caso, il cmdlet supporta ancora i caratteri jolly, ma lo forza la risoluzione in un'unica posizione.

Per altre informazioni sui modelli di caratteri jolly, vedere [che supportano caratteri jolly nei parametri del Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Definizione di oggetti

In questa sezione contiene le linee guida per la definizione di oggetti per i cmdlet e per estendere gli oggetti esistenti.

##### <a name="define-standard-members"></a>Definire membri Standard

Definire membri standard per estendere un tipo di oggetto in un file Types.ps1xml personalizzato (usare il file Types.ps1xml di Windows PowerShell come un modello). Membri standard sono definiti da un nodo con il nome PSStandardMembers. Queste definizioni consentono il runtime di Windows PowerShell per lavorare con l'oggetto in modo coerente e altri cmdlet.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Definire ObjectMembers per essere usati come parametri

Se si sta progettando un oggetto per un cmdlet, assicurarsi che i relativi membri siano mappati direttamente ai parametri dei cmdlet che lo utilizzerà. Questo mapping consente all'oggetto da inviare con facilità la pipeline e deve essere passato da un cmdlet a altro.

Preesistenti gli oggetti di .NET Framework che vengono restituiti dai cmdlet spesso mancano alcuni membri importanti o pratici che sono necessari per lo sviluppatore di script o l'utente. I membri mancanti possono essere particolarmente importanti per la visualizzazione e per la creazione di nomi di membro corretto in modo che l'oggetto può essere passato in modo corretto per la pipeline. Creare un file Types ps1xml personalizzato per tenere traccia di questi membri obbligatori. Quando si crea questo file, è consigliabile la convenzione di denominazione seguente: *< Your_Product_Name >*. Types.ps1xml.

Ad esempio, è possibile aggiungere un `Mode` lo script di proprietà per il [FileInfo](/dotnet/api/System.IO.FileInfo) tipo per visualizzare gli attributi di un file in modo più chiaro. Inoltre, è possibile aggiungere un `Count` proprietà alias per il [System. Array](/dotnet/api/System.Array) tipo da consentire l'uso coerente di tale nome di proprietà (anziché `Length`).

##### <a name="implement-the-icomparable-interface"></a>Implementare l'interfaccia IComparable

Implementare una [System. IComparable](/dotnet/api/System.IComparable) interfaccia per tutti gli oggetti di output. In questo modo gli oggetti di output essere facilmente inviato tramite pipe ai cmdlet di analisi e ordinamento diverse.

##### <a name="update-display-information"></a>Aggiornare le informazioni di visualizzazione

Se la visualizzazione per un oggetto non fornisce i risultati previsti, creare una classe personalizzata  *\<YourProductName >*. File Format.ps1xml per quell'oggetto.

### <a name="support-well-defined-pipeline-input-sc02"></a>Supporta l'Input della Pipeline ben definito (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implementare per mezzo di una Pipeline

Implementare un cmdlet presupponendo che verrà chiamato dalla parte centrale di una pipeline (vale a dire, gli altri cmdlet verrà producono input o utilizzare l'output). Ad esempio, si potrebbe supporre che il `Get-Process` cmdlet, in quanto genera dati, viene usato solo come il primo cmdlet in una pipeline. Tuttavia, poiché questo cmdlet è progettato per mezzo di una pipeline, questo cmdlet consente i cmdlet precedenti o i dati nella pipeline per specificare i processi da recuperare.

#### <a name="support-input-from-the-pipeline"></a>Supporto Input dalla Pipeline

In ogni set di parametri per un cmdlet, includere almeno un parametro che supporta l'input dalla pipeline. Supporto per l'input della pipeline consente all'utente di recuperare dati o oggetti, inviarle al set di parametri corretti e passare i risultati direttamente a un cmdlet.

Ogni parametro accetta input dalla pipeline se la **parametro** attributo include il `ValueFromPipeline` parola chiave, il `ValueFromPipelineByPropertyName` attributo keyword, o entrambe le parole chiave nella sua dichiarazione. Se nessuno dei parametri in un parametro del set di supporto di `ValueFromPipeline` o `ValueFromPipelineByPropertyName` parole chiave, il cmdlet non possono chiaramente essere inserite dopo un altro cmdlet perché ignorerà qualsiasi input della pipeline.

#### <a name="support-the-processrecord-method"></a>Supporta il metodo ProcessRecord

Per accettare tutti i record del cmdlet precedente nella pipeline, il cmdlet deve implementare il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo). Windows PowerShell chiama questo metodo più volte, una volta per ogni record viene inviato al cmdlet.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Scrivere un record singolo la pipeline (SC03)

Quando un cmdlet restituisce gli oggetti, il cmdlet deve scrivere gli oggetti immediatamente mentre vengono generati. Il cmdlet non consigliabile mantenere li per loro un buffer in una matrice combinata. I cmdlet che riceve gli oggetti come input sarà quindi in grado di elaborare, visualizzare, o di elaborare e visualizzare gli oggetti di output senza ritardo. Gli oggetti di un cmdlet che genera l'output di uno alla volta deve chiamare il [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) (metodo). Un cmdlet che genera gli oggetti di output in batch (ad esempio, perché un'API sottostante restituisce una matrice di oggetti di output) deve chiamare il [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metodo con il secondo parametro impostato per `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Rendere i cmdlet di maiuscole e minuscole e maiuscole-mantenimento (SC04)

Per impostazione predefinita, Windows PowerShell è tra maiuscole e minuscole. Tuttavia, poiché deve gestire con molti sistemi preesistenti, Windows PowerShell consente di mantenere case per facilitare l'operazione e compatibilità. In altre parole, se viene specificato un carattere in lettere maiuscole, Windows PowerShell mantiene in lettere maiuscole. Per i sistemi in modo corretto, un cmdlet deve seguono questa convenzione. Se possibile, dovrebbe funzionano in modo tra maiuscole e minuscole. Tuttavia, dovrebbe, mantenere il caso originale per i cmdlet che si verificano in un secondo momento in un comando o nella pipeline.

## <a name="see-also"></a>Vedere anche

[Linee guida di sviluppo necessari](./required-development-guidelines.md)

[Linee guida sullo sviluppo di consulenza](./advisory-development-guidelines.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
