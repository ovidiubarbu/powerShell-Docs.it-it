---
title: Linee guida per lo sviluppo fortemente consigliate | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369340"
---
# <a name="strongly-encouraged-development-guidelines"></a>Linee guida sullo sviluppo vivamente consigliate

Questa sezione descrive le linee guida da seguire quando si scrivono i cmdlet. Sono separate da linee guida per la progettazione di cmdlet e linee guida per la scrittura del codice del cmdlet. Si potrebbe notare che queste linee guida non sono applicabili a ogni scenario. Tuttavia, se si applicano e non si seguono queste linee guida, è possibile che gli utenti abbiano una scarsa esperienza quando usano i cmdlet.

## <a name="design-guidelines"></a>Linee guida per la progettazione

- [Usare un sostantivo specifico per un nome di cmdlet (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Usa il caso Pascal per i nomi di cmdlet (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Linee guida per la progettazione di parametri (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Inviare commenti e suggerimenti all'utente (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Creazione di un file della Guida per i cmdlet (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Linee guida del codice

- [Parametri di codifica (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Supporto per input della pipeline ben definito (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Scrivere record singoli nella pipeline (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Fare in modo che i cmdlet non facciano distinzione tra maiuscole e minuscole (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Linee guida per la progettazione

È necessario seguire le linee guida seguenti quando si progettano i cmdlet per garantire un'esperienza utente coerente tra l'uso dei cmdlet e di altri cmdlet. Quando si individuano le linee guida per la progettazione applicabili alla propria situazione, assicurarsi di esaminare le linee guida del codice per le linee guida simili.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Usare un sostantivo specifico per un nome di cmdlet (SD01)

I sostantivi utilizzati nella denominazione dei cmdlet devono essere molto specifici, in modo che l'utente possa individuare i cmdlet. Prefisso sostantivi generici come "Server" con una versione abbreviata del nome del prodotto. Se, ad esempio, un sostantivo fa riferimento a un server in cui è in esecuzione un'istanza di Microsoft SQL Server, utilizzare un sostantivo come "SQLServer". La combinazione di sostantivi specifici e l'elenco breve dei verbi approvati consentono all'utente di individuare e prevedere rapidamente le funzionalità evitando la duplicazione tra i nomi dei cmdlet.

Per migliorare l'esperienza utente, il sostantivo scelto per il nome di un cmdlet deve essere singolare. Ad esempio, usare il nome `Get-Process` anziché **Get-processes**. È consigliabile seguire questa regola per tutti i nomi di cmdlet, anche quando è probabile che un cmdlet agisca su più di un elemento.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Usa il caso Pascal per i nomi di cmdlet (SD02)

Usare il caso Pascal per i nomi dei parametri. In altre parole, capitalizzare la prima lettera del verbo e tutti i termini usati nel sostantivo. Ad esempio, "`Clear-ItemProperty`".

### <a name="parameter-design-guidelines-sd03"></a>Linee guida per la progettazione di parametri (SD03)

Un cmdlet richiede parametri che ricevono i dati su cui deve operare e parametri che indicano le informazioni utilizzate per determinare le caratteristiche dell'operazione. Ad esempio, un cmdlet potrebbe avere un `Name` parametro che riceve i dati dalla pipeline e il cmdlet potrebbe avere un `Force` parametro per indicare che il cmdlet può essere forzato a eseguire l'operazione. Non esiste alcun limite al numero di parametri che un cmdlet può definire.

#### <a name="use-standard-parameter-names"></a>Usa nomi di parametro standard

Il cmdlet deve usare nomi di parametro standard in modo che l'utente possa determinare rapidamente cosa significa un determinato parametro. Se è necessario un nome più specifico, usare un nome di parametro standard e quindi specificare un nome più specifico come alias. Ad esempio, il cmdlet `Get-Service` dispone di un parametro con un nome generico (`Name`) e un alias più specifico (`ServiceName`). Entrambi i termini possono essere utilizzati per specificare il parametro.

Per ulteriori informazioni sui nomi dei parametri e sui relativi tipi di dati, vedere il [nome del parametro del cmdlet e le linee guida sulle funzionalità](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Usa nomi di parametro singolari

Evitare l'utilizzo di nomi plurali per i parametri il cui valore è un singolo elemento. Sono inclusi i parametri che accettano matrici o elenchi perché l'utente potrebbe fornire una matrice o un elenco con un solo elemento.

I nomi di parametro plurale devono essere usati solo nei casi in cui il valore del parametro è sempre un valore a più elementi. In questi casi, il cmdlet deve verificare che siano specificati più elementi e che il cmdlet visualizzi un avviso all'utente se non vengono forniti più elementi.

#### <a name="use-pascal-case-for-parameter-names"></a>Usa il caso Pascal per i nomi di parametro

Usare il caso Pascal per i nomi dei parametri. In altre parole, è necessario capitalizzare la prima lettera di ogni parola nel nome del parametro, inclusa la prima lettera del nome. Ad esempio, il nome del parametro `ErrorAction` usa la maiuscola corretta. I nomi di parametro seguenti usano una maiuscola non corretta:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Parametri che accettano un elenco di opzioni

Esistono due modi per creare un parametro il cui valore può essere selezionato da un set di opzioni.

- Definire un tipo di enumerazione (o usare un tipo di enumerazione esistente) che specifichi i valori validi. Usare quindi il tipo di enumerazione per creare un parametro di quel tipo.

- Aggiungere l'attributo **ValidateSet** alla dichiarazione di parametro. Per ulteriori informazioni su questo attributo, vedere [dichiarazione dell'attributo ValidateSet](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Usare i tipi standard per i parametri

Per garantire la coerenza con altri cmdlet, usare i tipi standard per i parametri laddove possibile. Per ulteriori informazioni sui tipi che devono essere utilizzati per parametri diversi, vedere [tipi e nomi di parametri del cmdlet standard](./standard-cmdlet-parameter-names-and-types.md). In questo argomento vengono forniti collegamenti a diversi argomenti che descrivono i nomi e i tipi di .NET Framework per i gruppi di parametri standard, ad esempio "parametri attività".

#### <a name="use-strongly-typed-net-framework-types"></a>Usare tipi di .NET Framework fortemente tipizzati

I parametri devono essere definiti come tipi di .NET Framework per offrire una migliore convalida dei parametri. Ad esempio, i parametri limitati a un valore da un set di valori devono essere definiti come un tipo di enumerazione. Per supportare un valore di Uniform Resource Identifier (URI), definire il parametro come tipo [System. Uri](/dotnet/api/System.Uri) . Evitare i parametri di stringa di base per tutte le proprietà di testo in formato libero.

#### <a name="use-consistent-parameter-types"></a>Usare tipi di parametri coerenti

Quando lo stesso parametro viene usato da più cmdlet, usare sempre lo stesso tipo di parametro.  Se, ad esempio, il `Process` parametro è un tipo [System. Int16](/dotnet/api/System.Int16) per un cmdlet, non rendere il `Process` parametro per un altro cmdlet un tipo [System. UInt16](/dotnet/api/System.UInt16) .

#### <a name="parameters-that-take-true-and-false"></a>Parametri che accettano true e false

Se il parametro accetta solo `true` e `false`, definire il parametro come Type [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter). Un parametro switch viene trattato come `true` quando viene specificato in un comando. Se il parametro non è incluso in un comando, Windows PowerShell prende in considerazione il valore del parametro da `false`. Non definire parametri booleani.

Se il parametro deve distinguere tra 3 valori: $true, $false e "Unspecified", definire un parametro di tipo Nullable\<bool >.  La necessità di un terzo valore "non specificato" si verifica in genere quando il cmdlet può modificare una proprietà booleana di un oggetto. In questo caso "Unspecified" indica di non modificare il valore corrente della proprietà.

#### <a name="support-arrays-for-parameters"></a>Supportare matrici per i parametri

Spesso gli utenti devono eseguire la stessa operazione su più argomenti. Per questi utenti, un cmdlet deve accettare una matrice come input di parametro, in modo che un utente possa passare gli argomenti al parametro come variabile di Windows PowerShell. Ad esempio, il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) usa una matrice per le stringhe che identificano i nomi dei processi da recuperare.

#### <a name="support-the-passthru-parameter"></a>Supporto del parametro PassThru

Per impostazione predefinita, molti cmdlet che modificano il sistema, ad esempio il cmdlet [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) , fungono da "sink" per gli oggetti e non restituiscono alcun risultato. Questo cmdlet deve implementare il parametro `PassThru` per forzare la restituzione di un oggetto da parte del cmdlet. Quando viene specificato il parametro `PassThru`, il cmdlet restituisce un oggetto tramite una chiamata al metodo [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Ad esempio, il comando seguente interrompe il processo Calc e passa il processo risultante alla pipeline.

```powershell
Stop-Process calc -passthru
```

Nella maggior parte dei casi, i cmdlet Add, set e New devono supportare un parametro `PassThru`.

#### <a name="support-parameter-sets"></a>Supporta set di parametri

Un cmdlet è progettato per ottenere un singolo scopo. Tuttavia, è spesso disponibile più di un modo per descrivere l'operazione o la destinazione dell'operazione. Un processo, ad esempio, può essere identificato in base al nome, al relativo identificatore o a un oggetto processo. Il cmdlet deve supportare tutte le rappresentazioni ragionevoli delle relative destinazioni. In genere, il cmdlet soddisfa questo requisito specificando set di parametri (detti set di parametri) che operano insieme. Un singolo parametro può appartenere a un numero qualsiasi di set di parametri. Per ulteriori informazioni sui set di parametri, vedere [set di parametri del cmdlet](./cmdlet-parameter-sets.md).

Quando si specificano i set di parametri, impostare un solo parametro nella proprietà impostata su ValueFromPipeline. Per ulteriori informazioni su come dichiarare l'attributo **Parameter** , vedere [dichiarazione ParameterAttribute](./parameter-attribute-declaration.md).

Quando si utilizzano i set di parametri, il set di parametri predefinito viene definito dall'attributo del **cmdlet** . Il set di parametri predefinito deve includere i parametri che più probabilmente verranno usati in una sessione interattiva di Windows PowerShell. Per ulteriori informazioni su come dichiarare l'attributo **cmdlet** , vedere [dichiarazione CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Inviare commenti e suggerimenti all'utente (SD04)

Usare le linee guida in questa sezione per fornire commenti e suggerimenti all'utente. Questo feedback consente all'utente di essere a conoscenza di ciò che si sta verificando nel sistema e di prendere decisioni amministrative migliori.

Il runtime di Windows PowerShell consente a un utente di specificare come gestire l'output di ogni chiamata al metodo `Write` impostando una variabile di preferenza. L'utente può impostare diverse variabili di preferenza, inclusa una variabile che determina se il sistema deve visualizzare informazioni e una variabile che determina se il sistema deve eseguire una query sull'utente prima di intraprendere altre azioni.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Supportare i metodi WriteWarning, WriteVerbose e WriteDebug

Un cmdlet deve chiamare il metodo [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) quando il cmdlet sta per eseguire un'operazione che potrebbe avere un risultato imprevisto. Un cmdlet, ad esempio, deve chiamare questo metodo se il cmdlet sta per sovrascrivere un file di sola lettura.

Un cmdlet deve chiamare il metodo [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) quando l'utente richiede alcuni dettagli sulle operazioni svolte dal cmdlet. Un cmdlet, ad esempio, deve chiamare queste informazioni se l'autore del cmdlet ritiene che esistano scenari che potrebbero richiedere ulteriori informazioni sulle operazioni svolte dal cmdlet.

Il cmdlet deve chiamare il metodo [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) quando uno sviluppatore o un tecnico del supporto del prodotto deve comprendere cosa ha danneggiato l'operazione del cmdlet. Non è necessario che il cmdlet chiami il metodo [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) nello stesso codice che chiama il metodo [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) perché il parametro `Debug` presenta entrambi i set di informazioni.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>Supporto di WriteProgress per operazioni che importano molto tempo

Le operazioni del cmdlet che importano molto tempo per essere completate e che non possono essere eseguite in background dovrebbero supportare la creazione di report sullo stato di avanzamento tramite chiamate periodiche al metodo [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .

#### <a name="use-the-host-interfaces"></a>Usare le interfacce host

In alcuni casi, un cmdlet deve comunicare direttamente con l'utente anziché usando i diversi metodi Write o should supportati dalla classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . In questo caso, il cmdlet deve derivare dalla classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) e usare la proprietà [System. Management. Automation. PSCmdlet. host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) . Questa proprietà supporta diversi livelli di tipo di comunicazione, inclusi i tipi PromptForChoice, prompt e WriteLine/ReadLine. Al livello più specifico, fornisce anche metodi per leggere e scrivere singole chiavi e per gestire i buffer.

A meno che un cmdlet non sia specificamente progettato per generare un'interfaccia utente grafica (GUI), non deve ignorare l'host usando la proprietà [System. Management. Automation. PSCmdlet. host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) . Un esempio di cmdlet progettato per generare un'interfaccia utente grafica è il cmdlet [Out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) .

> [!NOTE]
> I cmdlet non devono usare l'API [System. console](/dotnet/api/System.Console) .

### <a name="create-a-cmdlet-help-file-sd05"></a>Creazione di un file della Guida per i cmdlet (SD05)

Per ogni assembly di cmdlet, creare un file Help. XML che contiene informazioni sul cmdlet. Queste informazioni includono una descrizione del cmdlet, descrizioni dei parametri del cmdlet, esempi di utilizzo del cmdlet e altro ancora.

## <a name="code-guidelines"></a>Linee guida del codice

Quando si codificano i cmdlet per garantire un'esperienza utente coerente con i cmdlet e altri cmdlet, è necessario attenersi alle linee guida seguenti. Quando si individua una linea guida per il codice che si applica alla propria situazione, assicurarsi di esaminare le linee guida per la progettazione di linee guida analoghe.

### <a name="coding-parameters-sc01"></a>Parametri di codifica (SC01)

Definire un parametro dichiarando una proprietà pubblica della classe cmdlet decorata con l'attributo **Parameter** . Non è necessario che i parametri siano membri statici della classe .NET Framework derivata per il cmdlet. Per altre informazioni su come dichiarare l'attributo **Parameter** , vedere [dichiarazione di attributo Parameter](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Supporto dei percorsi di Windows PowerShell

Il percorso di Windows PowerShell è il meccanismo per normalizzare l'accesso agli spazi dei nomi. Quando si assegna un percorso di Windows PowerShell a un parametro nel cmdlet, l'utente può definire un'unità personalizzata che funge da collegamento a un percorso specifico. Quando un utente designa tale unità, i dati archiviati, ad esempio i dati nel registro di sistema, possono essere usati in modo coerente.

Se il cmdlet consente all'utente di specificare un file o un'origine dati, deve definire un parametro di tipo [System. String](/dotnet/api/System.String). Se è supportata più di un'unità, il tipo deve essere una matrice. Il nome del parametro deve essere `Path`, con un alias di `PSPath`. Inoltre, il parametro `Path` deve supportare caratteri jolly. Se non è necessario il supporto per i caratteri jolly, definire un parametro `LiteralPath`.

Se i dati letti o scritti dal cmdlet devono essere un file, il cmdlet deve accettare l'input del percorso di Windows PowerShell e il cmdlet deve usare la proprietà [System. Management. Automation. SessionState. Path](/dotnet/api/System.Management.Automation.SessionState.Path) per tradurre i percorsi di Windows PowerShell in percorsi riconosciuti dal file System. I meccanismi specifici includono i metodi seguenti:

- [System. Management. Automation. PSCmdlet. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System. Management. Automation. PSCmdlet. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System. Management. Automation. PathIntrinsics. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System. Management. Automation. PathIntrinsics. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Se i dati letti o scritti dal cmdlet sono solo un set di stringhe anziché un file, il cmdlet deve utilizzare le informazioni sul contenuto del provider (`Content` membro) per la lettura e la scrittura. Queste informazioni vengono ottenute dalla proprietà [System. Management. Automation. provider. CmdletProvider. InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) . Questi meccanismi consentono ad altri archivi dati di partecipare alla lettura e alla scrittura dei dati.

#### <a name="support-wildcard-characters"></a>Supporto di caratteri jolly

Se possibile, un cmdlet deve supportare i caratteri jolly. Il supporto per i caratteri jolly si verifica in molte posizioni in un cmdlet, specialmente quando un parametro accetta una stringa per identificare un oggetto da un set di oggetti. Ad esempio, il cmdlet **Stop-proc** di esempio dell' [esercitazione StopProc](./stopproc-tutorial.md) definisce un parametro `Name` per gestire le stringhe che rappresentano i nomi dei processi. Questo parametro supporta i caratteri jolly in modo che l'utente possa specificare facilmente i processi da arrestare.

Quando è disponibile il supporto per i caratteri jolly, un'operazione di cmdlet in genere produce una matrice. In alcuni casi, non ha senso supportare una matrice perché l'utente potrebbe usare un solo elemento alla volta. Il cmdlet [set-location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) , ad esempio, non deve supportare una matrice perché l'utente sta impostando una sola posizione. In questo caso, il cmdlet supporta ancora caratteri jolly, ma forza la risoluzione in un'unica posizione.

Per ulteriori informazioni sui modelli di caratteri jolly, vedere [supporto di caratteri jolly nei parametri dei cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Definizione di oggetti

Questa sezione contiene le linee guida per la definizione di oggetti per i cmdlet e per l'estensione di oggetti esistenti.

##### <a name="define-standard-members"></a>Definire i membri standard

Definire i membri standard per estendere un tipo di oggetto in un file types. ps1xml personalizzato (usare il file di Windows PowerShell types. ps1xml come modello). I membri standard sono definiti da un nodo con il nome PSStandardMembers. Queste definizioni consentono ad altri cmdlet e al runtime di Windows PowerShell di usare l'oggetto in modo coerente.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Definire ObjectMembers da usare come parametri

Se si progetta un oggetto per un cmdlet, verificare che i relativi membri siano mappati direttamente ai parametri dei cmdlet che lo utilizzeranno. Questo mapping consente di inviare facilmente l'oggetto alla pipeline e di passare da un cmdlet all'altro.

Gli oggetti .NET Framework preesistenti restituiti dai cmdlet spesso non dispongono di membri importanti o pratici necessari per lo sviluppatore o l'utente di script. Questi membri mancanti possono essere particolarmente importanti per la visualizzazione e per creare i nomi dei membri corretti in modo che l'oggetto possa essere passato correttamente alla pipeline. Creare un file types. ps1xml personalizzato per documentare questi membri obbligatori. Quando si crea questo file, è consigliabile usare la convenzione di denominazione seguente: *< Your_Product_Name >* . Types. ps1xml.

Ad esempio, è possibile aggiungere una proprietà script `Mode` al tipo [System. io. FileInfo](/dotnet/api/System.IO.FileInfo) per visualizzare più chiaramente gli attributi di un file. Inoltre, è possibile aggiungere una proprietà alias `Count` al tipo [System. Array](/dotnet/api/System.Array) per consentire l'uso coerente del nome di tale proprietà (anziché `Length`).

##### <a name="implement-the-icomparable-interface"></a>Implementare l'interfaccia IComparable

Implementare un'interfaccia [System. IComparable](/dotnet/api/System.IComparable) in tutti gli oggetti di output. In questo modo è possibile inviare facilmente gli oggetti di output a diversi cmdlet di ordinamento e di analisi.

##### <a name="update-display-information"></a>Aggiornare le informazioni di visualizzazione

Se la visualizzazione di un oggetto non fornisce i risultati previsti, creare una\<personalizzata *> YourProductName*. File format. ps1xml per l'oggetto.

### <a name="support-well-defined-pipeline-input-sc02"></a>Supporto per input della pipeline ben definito (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implementare per la metà di una pipeline

Implementare un cmdlet presumendo che venga chiamato dal centro di una pipeline, ovvero che altri cmdlet producano l'input o ne utilizzino l'output. Si supponga, ad esempio, che il cmdlet `Get-Process`, perché genera dati, venga utilizzato solo come primo cmdlet in una pipeline. Tuttavia, poiché questo cmdlet è progettato per la metà di una pipeline, questo cmdlet consente ai cmdlet o ai dati precedenti nella pipeline di specificare i processi da recuperare.

#### <a name="support-input-from-the-pipeline"></a>Supportare l'input dalla pipeline

In ogni set di parametri per un cmdlet, includere almeno un parametro che supporta l'input dalla pipeline. Il supporto per l'input della pipeline consente all'utente di recuperare dati o oggetti, di inviarli al set di parametri corretto e di passare i risultati direttamente a un cmdlet.

Un parametro accetta input dalla pipeline se l'attributo del **parametro** include la parola chiave `ValueFromPipeline`, l'attributo della parola chiave `ValueFromPipelineByPropertyName` o entrambe le parole chiave nella relativa dichiarazione. Se nessuno dei parametri in un set di parametri supporta le parole chiave `ValueFromPipeline` o `ValueFromPipelineByPropertyName`, il cmdlet non può essere inserito in maniera significativa dopo un altro cmdlet, perché ignorerà qualsiasi input della pipeline.

#### <a name="support-the-processrecord-method"></a>Supporto del metodo ProcessRecord

Per accettare tutti i record dal cmdlet precedente nella pipeline, il cmdlet deve implementare il metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . Windows PowerShell chiama questo metodo più volte, una volta per ogni record inviato al cmdlet.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Scrivere record singoli nella pipeline (SC03)

Quando un cmdlet restituisce oggetti, il cmdlet deve scrivere gli oggetti immediatamente dopo la generazione. Il cmdlet non deve mantenerli in modo da memorizzarli nel buffer in una matrice combinata. I cmdlet che ricevono gli oggetti come input saranno in grado di elaborare, visualizzare o elaborare e visualizzare gli oggetti di output senza ritardo. Un cmdlet che genera gli oggetti di output uno alla volta deve chiamare il metodo [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Un cmdlet che genera oggetti di output in batch, ad esempio perché un'API sottostante restituisce una matrice di oggetti di output, deve chiamare il metodo [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) con il secondo parametro impostato su `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Fare in modo che i cmdlet non facciano distinzione tra maiuscole e minuscole (SC04)

Per impostazione predefinita, Windows PowerShell non fa distinzione tra maiuscole e minuscole. Tuttavia, poiché gestisce molti sistemi preesistenti, Windows PowerShell mantiene i casi per semplificare il funzionamento e la compatibilità. In altre parole, se un carattere viene fornito in lettere maiuscole, Windows PowerShell lo mantiene in lettere maiuscole. Per il corretto funzionamento dei sistemi, è necessario che un cmdlet segua questa convenzione. Se possibile, deve funzionare senza distinzione tra maiuscole e minuscole. Tuttavia, deve mantenere il caso originale per i cmdlet che si verificano in un secondo momento in un comando o nella pipeline.

## <a name="see-also"></a>Vedere anche

[Linee guida per lo sviluppo richieste](./required-development-guidelines.md)

[Linee guida per lo sviluppo consultivo](./advisory-development-guidelines.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
