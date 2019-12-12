---
title: Verbi approvati per i comandi di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: 4475b3f5e15826efbe8bab867011985cd7e2e1ae
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72370030"
---
# <a name="approved-verbs-for-powershell-commands"></a>Verbi approvati per i comandi di PowerShell

PowerShell usa una coppia verbo-sostantivo per i nomi dei cmdlet e per le classi di Microsoft .NET Framework derivate.
Ad esempio, il cmdlet `Get-Command` fornito da PowerShell viene usato per recuperare tutti i comandi registrati in PowerShell.
Il verbo parte del nome identifica l'azione eseguita dal cmdlet.
La parte sostantiva del nome identifica l'entità in cui viene eseguita l'azione.

> [!NOTE]
> PowerShell usa il *verbo* del termine per descrivere una parola che implica un'azione anche se tale parola non è un verbo standard nella lingua inglese.
> Il termine *New* , ad esempio, è un nome di verbo di PowerShell valido perché implica un'azione anche se non è un verbo nella lingua inglese.

## <a name="verb-naming-rules"></a>Regole di denominazione dei verbi

Nell'elenco seguente vengono fornite le linee guida da considerare quando si sceglie il verbo per un nome di cmdlet:

* Quando si specifica il verbo, è consigliabile usare uno dei nomi di verbi predefiniti forniti da PowerShell (gli alias per questi verbi predefiniti sono inclusi nelle tabelle seguenti).
  Quando si utilizza un verbo predefinito, è possibile garantire la coerenza tra i cmdlet creati, i cmdlet forniti da PowerShell e i cmdlet progettati da altri utenti.

* Usare i verbi predefiniti per descrivere l'ambito generale dell'azione e usare i parametri per perfezionare ulteriormente l'azione del cmdlet.

* Per applicare la coerenza tra i cmdlet, non usare un sinonimo di un verbo approvato.

* Utilizzare solo il formato di ogni verbo elencato in questo argomento.
  Ad esempio, usare "Get", ma non usare "Get" o "Gets".

* Usare la convenzione Pascal per i verbi.
  In Pascal, la lettera iniziale di ogni parola è maiuscola, ad esempio "ForEach".

* Non usare i seguenti verbi o alias riservati.
  Questi verbi vengono usati dal linguaggio di PowerShell o dai cmdlet del caso speciale forniti da PowerShell.
  - ForEach (foreach)
  - Formato (f)
  - Gruppo (GP)
  - Ordinamento (SR)
  - Tee (te)
  - Dove (WH)

## <a name="similar-verbs-for-different-actions"></a>Verbi simili per azioni diverse

I verbi simili seguenti rappresentano azioni diverse.

### <a name="new-vs-set"></a>Nuovo rispetto a set
Il verbo `New` viene usato per creare una nuova risorsa.
Il verbo `Set` viene usato per modificare una risorsa esistente, creando eventualmente la risorsa, se non esiste, ad esempio il cmdlet `Set-Variable`.

### <a name="find-vs-search"></a>Trova e cerca
Il verbo `Find` viene usato per cercare un oggetto.
Il verbo `Search` viene usato per creare un riferimento a una risorsa in un contenitore.

### <a name="get-vs-read"></a>Ottenere e leggere
Il verbo `Get` viene usato per recuperare una risorsa, ad esempio un file.
Il verbo `Read` viene usato per ottenere informazioni da un'origine, ad esempio un file.

### <a name="invoke-vs-start"></a>Richiama e avvia
Il verbo `Invoke` viene usato per eseguire un'operazione che in genere è un'operazione sincrona, ad esempio l'esecuzione di un comando.
Il verbo `Start` viene usato per iniziare un'operazione che in genere è un'operazione asincrona, ad esempio l'avvio di un processo.

### <a name="ping-vs-test"></a>Ping rispetto a test
Usare il verbo `Test`.

## <a name="common-verbs"></a>Verbi comuni

PowerShell usa la classe di enumerazione [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) per definire azioni generiche che possono essere applicate a quasi tutti i cmdlet.
La tabella seguente elenca la maggior parte dei verbi definiti.

|Verbo (alias)|Azione|Commenti|
|--------------------|------------|--------------|
|[Aggiungi](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Aggiunge una risorsa a un contenitore o connette un elemento a un altro elemento. Ad esempio, il cmdlet `Add-Content` aggiunge contenuto a un file. Questo verbo è associato a `Remove`.|Per questa azione, non usare verbi come Append, allegate, concatenate o INSERT.|
|[Cancella](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Rimuove tutte le risorse da un contenitore, ma non elimina il contenitore. Ad esempio, il cmdlet `Clear-Content` rimuove il contenuto di un file ma non elimina il file.|Per questa azione, non usare verbi come Flush, erase, release, UNMARK, annullato o Annulla.|
|[Chiudi](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (CS)|Modifica lo stato di una risorsa per renderla inaccessibile, non disponibile o inutilizzabile. Questo verbo è associato a `Open.`||
|[Copia](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (CP)|Copia una risorsa in un altro nome o in un altro contenitore. Ad esempio, il cmdlet `Copy-Item` usato per accedere ai dati archiviati copia un elemento da una posizione nell'archivio dati in un'altra posizione.|Per questa azione, non usare verbi come duplicato, clonazione, replica o sincronizzazione.|
|[Immetti](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Specifica un'azione che consente all'utente di spostarsi in una risorsa. Ad esempio, il cmdlet `Enter-PSSession` inserisce l'utente in una sessione interattiva. Questo verbo è associato a `Exit`.|Per questa azione, non usare verbi come push o into.|
|[Esci](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|Imposta l'ambiente o il contesto corrente sul contesto utilizzato più di recente. Ad esempio, il cmdlet `Exit-PSSession` inserisce l'utente nella sessione utilizzata per avviare la sessione interattiva. Questo verbo è associato a `Enter`.|Per questa azione, non usare verbi come pop o out.|
|[Trova](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (FD)|Cerca un oggetto in un contenitore sconosciuto, implicito, facoltativo o specificato.||
|[Formato](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Dispone gli oggetti in un form o un layout specificato.||
|[Get](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Specifica un'azione che recupera una risorsa. Questo verbo è associato a `Set`.|Per questa azione, non usare verbi come Read, Open, cat, Type, dir, ottenere, dump, Acquire, examine, Find o search.|
|[Nascondi](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Rende una risorsa non rilevabile. Ad esempio, un cmdlet il cui nome include il verbo Hide potrebbe nascondere un servizio di un utente. Questo verbo è associato a `Show`.|Per questa azione, non usare un verbo come Block.|
|[Join](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Combina le risorse in un'unica risorsa. Ad esempio, il cmdlet `Join-Path` combina un percorso con uno dei percorsi figlio per creare un singolo percorso. Questo verbo è associato a `Split`.|Per questa azione, non usare i verbi, ad esempio combinare, unire, connettere o associare.|
|[Blocco](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (LK)|Protegge una risorsa. Questo verbo è associato a `Unlock`.|Per questa azione, non usare i verbi, ad esempio Restrict o Secure.|
|[Sposta](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Sposta una risorsa da una posizione a un'altra. Ad esempio, il cmdlet `Move-Item` sposta un elemento da una posizione nell'archivio dati in un'altra posizione.|Per questa azione, non usare verbi come trasferimento, nome o migrazione.|
|[Nuovo](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Crea una risorsa. Il verbo `Set` può essere utilizzato anche quando si crea una risorsa che include dati, ad esempio il cmdlet `Set-Variable`.|Per questa azione, non usare verbi come create, generate, Build, make o allocate.|
|[Apri](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|Modifica lo stato di una risorsa per renderla accessibile, disponibile o utilizzabile. Questo verbo è associato a `Close`.||
|[Ottimizza](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (OM)|Aumenta l'efficacia di una risorsa.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Rimuove un elemento dall'inizio di uno stack. Ad esempio, il cmdlet `Pop-Location` imposta il percorso corrente sul percorso di cui è stato effettuato il push più di recente nello stack.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (unità di elaborazione)|Aggiunge un elemento all'inizio di uno stack. Ad esempio, il cmdlet `Push-Location` effettua il push del percorso corrente nello stack.||
|[Ripeti](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Reimposta una risorsa sullo stato che è stato annullato.||
|[Rimuovi](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Elimina una risorsa da un contenitore. Ad esempio, il cmdlet `Remove-Variable` Elimina una variabile e il relativo valore. Questo verbo è associato a `Add`.|Per questa azione, non usare verbi come Clear, Cut, Dispose, scarto o Erase.|
|[Rinomina](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (RN)|Modifica il nome di una risorsa. Ad esempio, il cmdlet `Rename-Item`, utilizzato per accedere ai dati archiviati, modifica il nome di un elemento nell'archivio dati.|Per questa azione, non usare un verbo, ad esempio Change.|
|[Reimposta](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (RS)|Consente di ripristinare lo stato originale di una risorsa.||
|[Cerca](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (SR)|Crea un riferimento a una risorsa in un contenitore.|Per questa azione, non usare verbi come Find o locate.|
|[Select](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (SC)|Individua una risorsa in un contenitore. Ad esempio, il cmdlet `Select-String` trova il testo in stringhe e file.|Per questa azione, non usare verbi come Find o locate.|
|[Set](/dotnet/api/System.Management.Automation.VerbsCommon.Set) /i|Sostituisce i dati in una risorsa esistente o crea una risorsa che contiene alcuni dati. Ad esempio, il cmdlet `Set-Date` modifica l'ora di sistema nel computer locale. Per creare una risorsa, è anche possibile usare il verbo `New`. Questo verbo è associato a `Get`.|Per questa azione, non usare verbi quali Write, reset, Assign o Configure.|
|[Mostra](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (SH)|Rende visibile una risorsa all'utente. Questo verbo è associato a `Hide`.|Per questa azione, non usare verbi come la visualizzazione o la produzione.|
|[Ignora](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (SK)|Ignora una o più risorse o punti in una sequenza.|Per questa azione, non usare un verbo, ad esempio bypass o Jump.|
|[Divisione](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (SL)|Separa le parti di una risorsa. Ad esempio, il cmdlet `Split-Path` restituisce parti diverse di un percorso. Questo verbo è associato a `Join`.|Per questa azione, non usare un verbo come separato.|
|[Passaggio](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (St)|Passa al punto o alla risorsa successiva in una sequenza.||
|[Switch](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (SW)|Specifica un'azione che si alterna tra due risorse, ad esempio per passare da una posizione all'altra, responsabilità o Stati.||
|[Annulla (annullamento](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) )|Imposta una risorsa sullo stato precedente.||
|[Sblocco](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (Regno Unito)|Rilascia una risorsa bloccata. Questo verbo è associato a `Lock`.|Per questa azione, non usare verbi quali release, unrestrict o unsecure.|
|[Watch](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (WC)|Controlla o monitora continuamente una risorsa per le modifiche.||

## <a name="communications-verbs"></a>Verbi di comunicazione

PowerShell usa la classe [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) per definire le azioni che si applicano alle comunicazioni.
La tabella seguente elenca la maggior parte dei verbi definiti.

|Verbo (alias)|Azione|Commenti|
|--------------------|------------|--------------|
|[Connetti](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (CC)|Crea un collegamento tra un'origine e una destinazione. Questo verbo è associato a `Disconnect`.|Per questa azione, non usare verbi come join o Telnet.|
|[Disconnetti](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (DC)|Interrompe il collegamento tra un'origine e una destinazione. Questo verbo è associato a `Connect`.|Per questa azione, non usare verbi come break o disconnessione.|
|[Lettura](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (Rd)|Acquisisce informazioni da un'origine. Questo verbo è associato a `Write`.|Per questa azione, non usare verbi come acquisizione, prompt o Get.|
|[Ricezione](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (RC)|Accetta le informazioni inviate da un'origine. Questo verbo è associato a `Send`.|Per questa azione, non usare verbi come Read, Accept o PEEK.|
|[Invia](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (SD)|Recapita le informazioni a una destinazione. Questo verbo è associato a `Receive`.|Per questa azione, non usare verbi come put, broadcast, mail o fax.|
|[Scrittura](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (WR)|Aggiunge informazioni a una destinazione. Questo verbo è associato a `Read`.|Per questa azione, non usare verbi come put o Print.|

## <a name="data-verbs"></a>Verbi di dati

PowerShell usa la classe [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData) per definire le azioni che si applicano alla gestione dei dati.
La tabella seguente elenca la maggior parte dei verbi definiti.

|Nome del verbo (alias)|Azione|Commenti|
|-------------------------|------------|--------------|
|[Backup](/dotnet/api/System.Management.Automation.VerbsData.Backup) (BA)|Archivia i dati eseguendo la replica.|Per questa azione, non usare i verbi, ad esempio Save, Burn, replicate o Sync.|
|[Checkpoint](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (CH)|Crea uno snapshot dello stato corrente dei dati o della relativa configurazione.|Per questa azione, non usare un verbo come diff.|
|[Confronta](/dotnet/api/System.Management.Automation.VerbsData.Compare) (CR)|Valuta i dati di una risorsa in base ai dati di un'altra risorsa.|Per questa azione, non usare un verbo come diff.|
|[Comprimi](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Compatta i dati di una risorsa. Coppie con `Expand`.|Per questa azione, non usare un verbo, ad esempio Compact.|
|[Converti](/dotnet/api/System.Management.Automation.VerbsData.Convert) (CV)|Modifica i dati da una rappresentazione a un'altra quando il cmdlet supporta la conversione bidirezionale o quando il cmdlet supporta la conversione tra più tipi di dati.|Per questa azione, non usare i verbi, ad esempio modifica, ridimensionamento o ricampionamento.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (CF)|Converte un tipo di input primario (il nome del cmdlet indica l'input) in uno o più tipi di output supportati.|Per questa azione, non usare verbi quali Export, output o out.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (CT)|Esegue la conversione da uno o più tipi di input a un tipo di output primario (il nome del cmdlet indica il tipo di output).|Per questa azione, non usare verbi come Import, input o in.|
|[Smontaggio](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (DM)|Scollega un'entità denominata da un percorso. Questo verbo è associato a `Mount`.|Per questa azione, non usare verbi come unmount o Unlink.|
|[Modifica](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Modifica i dati esistenti aggiungendo o rimuovendo contenuto.|Per questa azione, non usare i verbi, ad esempio modifica, aggiornamento o modifica.|
|[Espandi](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Ripristina i dati di una risorsa che è stata compressa nello stato originale. Questo verbo è associato a `Compress`.|Per questa azione, non usare verbi come Esplodi o decomprimere.|
|[Esporta](/dotnet/api/System.Management.Automation.VerbsData.Export) (EP)|Incapsula l'input primario in un archivio dati persistente, ad esempio un file, o in un formato di interscambio. Questo verbo è associato a `Import`.|Per questa azione, non usare verbi come Extract o backup.|
|[Gruppo](/dotnet/api/System.Management.Automation.VerbsData.Group) (GP)|Dispone o associa una o più risorse.|Per questa azione, non usare verbi come aggregate, Arrange, associate o correlate.|
|[Importazione](/dotnet/api/System.Management.Automation.VerbsData.Import) (IP)|Crea una risorsa da dati archiviati in un archivio dati permanente (ad esempio un file) o in un formato di interscambio. Ad esempio, il cmdlet `Import-CSV` importa i dati da un file con valori delimitati da virgole (CSV) a oggetti che possono essere usati da altri cmdlet. Questo verbo è associato a `Export`.|Per questa azione, non usare verbi come BulkLoad o Load.|
|[Initialize](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Prepara una risorsa per l'uso e la imposta su uno stato predefinito.|Per questa azione, non usare verbi come Erase, init, Renew, Rebuild, Reinitialize o Setup.|
|[Limite](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Applica vincoli a una risorsa.|Per questa azione, non usare un verbo, ad esempio quota.|
|[Unisci](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Crea una singola risorsa da più risorse.|Per questa azione, non usare verbi come combine o join.|
|[Montaggio](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|Connette un'entità denominata a una posizione. Questo verbo è associato a `Dismount`.|Per questa azione, non usare il verbo Connect.|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Invia i dati all'esterno dell'ambiente. Ad esempio, il cmdlet `Out-Printer` invia dati a una stampante.||
|[Pubblica](/dotnet/api/System.Management.Automation.VerbsData.Publish) (PB)|Rende disponibile una risorsa per altri utenti. Questo verbo è associato a `Unpublish`.|Per questa azione, non usare i verbi come la distribuzione, la versione o l'installazione.|
|[Ripristino](/dotnet/api/System.Management.Automation.VerbsData.Restore) (RR)|Imposta una risorsa su uno stato predefinito, ad esempio uno stato impostato da `Checkpoint`. Ad esempio, il cmdlet `Restore-Computer` avvia un ripristino di sistema nel computer locale.|Per questa azione, non usare verbi come Repair, return, Undo o Fix.|
|[Salva](/dotnet/api/System.Management.Automation.VerbsData.Save) (SV)|Conserva i dati per evitare perdite.||
|[Sincronizzazione](/dotnet/api/System.Management.Automation.VerbsData.Sync) (SY)|Assicura che due o più risorse si trovino nello stesso stato.|Per questa azione, non usare verbi come replicate, coercizione o match.|
|[Annulla pubblicazione](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (UB)|Rende una risorsa non disponibile per altri utenti. Questo verbo è associato a `Publish`.|Per questa azione, non usare verbi come Disinstalla, Annulla o Nascondi.|
|[Aggiornamento](/dotnet/api/System.Management.Automation.VerbsData.Update) (UD)|Porta aggiornata una risorsa per mantenerne lo stato, l'accuratezza, la conformità o la conformità. Ad esempio, il cmdlet `Update-FormatData` aggiorna e aggiunge i file di formattazione alla console di PowerShell corrente.|Per questa azione, non usare verbi come Refresh, Renew, ricalcola o REINDEX.|

## <a name="diagnostic-verbs"></a>Verbi di diagnostica

PowerShell usa la classe [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) per definire le azioni che si applicano alla diagnostica.
La tabella seguente elenca la maggior parte dei verbi definiti.

|Verbo (alias)|Azione|Commenti|
|--------------------|------------|--------------|
|[Debug](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (DB)|Esamina una risorsa per diagnosticare i problemi operativi.|Per questa azione, non usare un verbo come la diagnosi.|
|[Misura](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (MS)|Identifica le risorse utilizzate da un'operazione specificata o recupera le statistiche relative a una risorsa.|Per questa azione, non usare verbi come Calculate, determine o Analyze.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (PI)|Usare il verbo `Test`.||
|[Ripristino](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (RP)|Ripristina una risorsa in una condizione utilizzabile|Per questa azione, non usare verbi come Fix o Restore.|
|[Risolvi](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (RV)|Esegue il mapping di una rappresentazione abbreviata di una risorsa a una rappresentazione più completa.|Per questa azione, non usare verbi come Expand o Determine.|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Verifica l'operazione o la coerenza di una risorsa.|Per questa azione, non usare verbi quali diagnosi, analisi, recupero o verifica.|
|[Traccia](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (TR)|Tiene traccia delle attività di una risorsa.|Per questa azione, non usare verbi come Track, follow, ispezionate o dig.|

## <a name="lifecycle-verbs"></a>Verbi del ciclo di vita

PowerShell usa la classe [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) per definire le azioni che si applicano al ciclo di vita di una risorsa.
La tabella seguente elenca la maggior parte dei verbi definiti.

|Verbo (alias)|Azione|Commenti|
|--------------------|------------|--------------|
|[Approva](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (AP)|Conferma o accetta lo stato di una risorsa o di un processo.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (As)|Afferma lo stato di una risorsa.|Per questa azione, non usare un verbo come certificate.|
|[Compilazione](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (BD)|Crea un elemento, in genere un file binario o un documento, da un set di file di input, in genere codice sorgente o documenti dichiarativi.|Questo verbo è stato aggiunto in PowerShell V6|
|[Operazione completata](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (CP)|Conclude un'operazione.||
|[Conferma](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (CN)|Conferma, verifica o convalida lo stato di una risorsa o di un processo.|Per questa azione, non usare verbi come riconoscimento, accettazione, certificazione, convalida o verifica.|
|[Nega](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (DN)|Rifiuta, oggetti, blocchi o si oppone allo stato di una risorsa o di un processo.|Per questa azione, non usare verbi come Block, Object, Reject o Reject.|
|[Distribuzione](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (DP)|Invia un'applicazione, un sito Web o una soluzione a una destinazione remota [s] in modo che un utente di tale soluzione possa accedervi dopo il completamento della distribuzione|Questo verbo è stato aggiunto in PowerShell V6|
|[Disabilita](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Configura una risorsa in uno stato non disponibile o inattivo. Ad esempio, il cmdlet `Disable-PSBreakpoint` rende inattivo un punto di interruzione. Questo verbo è associato a `Enable`.|Per questa azione, non usare verbi come Halt o Hide.|
|[Abilita](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Configura una risorsa in uno stato disponibile o attivo. Ad esempio, il cmdlet `Enable-PSBreakpoint` rende attivo un punto di interruzione. Questo verbo è associato a `Disable`.|Per questa azione, non usare verbi come Start o Begin.|
|[Installa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (is)|Inserisce una risorsa in un percorso e, facoltativamente, la Inizializza. Questo verbo è associato a `Uninstall`.|Per questa azione, non usare un verbo di utilizzo quale il programma di installazione.|
|[Richiama](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Esegue un'azione, ad esempio l'esecuzione di un comando o di un metodo.|Per questa azione, non usare verbi come Run o Start.|
|[Registra](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (RG)|Crea una voce per una risorsa in un repository, ad esempio un database. Questo verbo è associato a `Unregister`.||
|[Richiesta](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (RQ)|Richiede una risorsa o chiede le autorizzazioni.||
|[Riavvia](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (RT)|Arresta un'operazione, quindi la avvia nuovamente. Ad esempio, il cmdlet `Restart-Service` arresta e quindi avvia un servizio.|Per questa azione, non usare un verbo come il riciclo.|
|[Riprendi](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (UR)|Avvia un'operazione sospesa. Ad esempio, il cmdlet `Resume-Service` avvia un servizio che è stato sospeso. Questo verbo è associato a `Suspend`.||
|[Avvio](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (SA)|Avvia un'operazione. Ad esempio, il cmdlet `Start-Service` avvia un servizio. Questo verbo è associato a `Stop`.|Per questa azione, non usare verbi come avvio, avvio o avvio.|
|[Arresta](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (SP)|Interrompe un'attività. Questo verbo è associato a `Start`.|Per questa azione, non usare verbi come end, Kill, terminate o Cancel.|
|[Invia](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (SB)|Presenta una risorsa per l'approvazione.|Per questa azione, non usare un verbo come post.|
|[Sospendi](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (SS)|Sospende un'attività. Ad esempio, il cmdlet `Suspend-Service` sospende un servizio. Questo verbo è associato a `Resume`.|Per questa azione, non usare un verbo quale pause.|
|[Disinstalla](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (Stati Uniti)|Rimuove una risorsa da una posizione indicata. Questo verbo è associato a `Install`.||
|[Annulla registrazione](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (UR)|Rimuove la voce per una risorsa da un repository. Questo verbo è associato a `Register`.|Per questa azione, non usare un verbo come Remove.|
|[Attesa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Sospende un'operazione fino a quando non si verifica un evento specificato. Ad esempio, il cmdlet `Wait-Job` sospende le operazioni fino al completamento di uno o più processi in background.|Per questa azione, non usare verbi quali sospensione o sospensione.|

## <a name="security-verbs"></a>Verbi di sicurezza

PowerShell usa la classe [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) per definire le azioni che si applicano alla sicurezza.
La tabella seguente elenca la maggior parte dei verbi definiti.

|Verbo (alias)|Azione|Commenti|
|--------------------|------------|--------------|
|[Blocca](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (BL)|Limita l'accesso a una risorsa. Questo verbo è associato a `Unblock`.|Per questa azione, non usare verbi come Impedisci, limita o nega.|
|[Concessione](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Consente l'accesso a una risorsa. Questo verbo è associato a `Revoke`.|Per questa azione, non usare verbi come allow o Enable.|
|[Proteggi](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (PT)|Protegge una risorsa da attacchi o perdite. Questo verbo è associato a `Unprotect`.|Per questa azione, non usare verbi come Encrypt, SafeGuard o Seal.|
|[Revoke](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (RK)|Specifica un'azione che non consente l'accesso a una risorsa. Questo verbo è associato a `Grant`.|Per questa azione, non usare verbi come Remove o Disable.|
|[Sblocco](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (UL)|Rimuove le restrizioni a una risorsa. Questo verbo è associato a `Block`.|Per questa azione, non usare verbi come Clear o Allow.|
|[Rimuovere la protezione](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (su)|Rimuove le misure di sicurezza da una risorsa aggiunta per impedirne l'attacco o la perdita. Questo verbo è associato a `Protect`.|Per questa azione, non usare verbi come Decrypt o Unseal.|

## <a name="other-verbs"></a>Altri verbi

PowerShell usa la classe [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) per definire i nomi di verbi canonico che non rientrano in una categoria specifica del nome del verbo, ad esempio i verbi comuni, di comunicazione, di dati, del ciclo di vita o dei verbi di sicurezza.

|Verbo (alias)|Azione|Commenti|
|--------------------|------------|--------------|
|[USA](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|USA o include una risorsa per eseguire un'operazione.||

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Dichiarazione di cmdlet](./cmdlet-class-declaration.md)

[Guida per programmatori di Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md)

[SDK della shell di Windows PowerShell](../windows-powershell-reference.md)
