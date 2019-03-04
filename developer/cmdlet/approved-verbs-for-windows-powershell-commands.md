---
title: I verbi approvati per i comandi di PowerShell | Microsoft Docs
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
ms.openlocfilehash: d8a0561d6fbb4447a691c434e0518e3e16ce41e7
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56863667"
---
# <a name="approved-verbs-for-powershell-commands"></a>Verbi approvati per i comandi di PowerShell

PowerShell Usa una coppia di verbo-sostantivo per i nomi dei cmdlet e le relative classi derivate di Microsoft .NET Framework.
Ad esempio, il `Get-Command` cmdlet di PowerShell viene usato per recuperare tutti i comandi che sono registrati in PowerShell.
La parte verbale del nome identifica l'azione eseguita dal cmdlet.
La parte del sostantivo del nome identifica l'entità su cui viene eseguita l'azione.

> [!NOTE]
> PowerShell Usa il termine *verbo* per descrivere una parola che implica un'azione anche se tale parola non è un verbo standard in lingua inglese.
> Ad esempio, il termine *New* è il nome di un verbo PowerShell valido perché implica un'azione anche se non è un verbo in lingua inglese.

## <a name="verb-naming-rules"></a>Regole di denominazione verbo

Nell'elenco seguente vengono fornite linee guida da considerare quando si sceglie il verbo per nome di un cmdlet:

* Quando si specifica il verbo, è consigliabile usare uno dei nomi di verbo predefiniti forniti da PowerShell (alias per questi verbi predefiniti sono inclusi nelle tabelle seguenti).
  Quando si usa un verbo predefiniti, garantire la coerenza tra i cmdlet creati, i cmdlet forniti da PowerShell e i cmdlet progettati da altri utenti.

* Usare i verbi predefiniti per descrivere l'ambito generale dell'azione e utilizzare i parametri per limitare ulteriormente l'azione del cmdlet.

* Per garantire la coerenza tra i cmdlet, non utilizzare un sinonimo di un verbo approvato.

* Usare solo la forma di ogni verbo elencato in questo argomento.
  Ad esempio, usare "Get", ma non usare "Introduzione" o "Ottiene".

* Utilizzare la convenzione Pascal maiuscole e minuscole per i verbi.
  Nella convenzione Pascal maiuscole e minuscole la lettera iniziale di ogni parola è scritto in lettere maiuscole, ad esempio "ForEach".

* Non usare i seguenti verbi riservati o gli alias.
  Questi comandi vengono usati dal linguaggio di PowerShell o dai cmdlet di case speciale di PowerShell.
  - ForEach (foreach)
  - Formato (f)
  - Gruppo di (protezione generale)
  - Sort (sr)
  - Tee (to)
  - In cui (CO)

## <a name="similar-verbs-for-different-actions"></a>Verbi simili per diverse azioni

Simili ai seguenti verbi rappresentano diverse azioni.

### <a name="new-vs-set"></a>Nuovo Visual Studio. Imposta
Il `New` verbi viene utilizzato per creare una nuova risorsa.
Il `Set` verbo viene usato per modificare una risorsa esistente, creando facoltativamente la risorsa se non esiste, ad esempio il `Set-Variable` cmdlet.

### <a name="find-vs-search"></a>Trovare Visual Studio. Ricerca
Il `Find` verbo viene utilizzato per cercare un oggetto.
Il `Search` verbi viene utilizzato per creare un riferimento a una risorsa in un contenitore.

### <a name="get-vs-read"></a>Ottenere Visual Studio. Lettura
Il `Get` verbo viene usato per recuperare una risorsa, ad esempio un file.
Il `Read` verbo viene usata per ottenere informazioni da un'origine, ad esempio un file.

### <a name="invoke-vs-start"></a>Richiamare Visual Studio. Avviare
Il `Invoke` verbo viene usato per eseguire un'operazione che è in genere un'operazione sincrona, ad esempio l'esecuzione di un comando.
Il `Start` verbo utilizzato per avviare un'operazione che è in genere un'operazione asincrona, ad esempio avvio di un processo.

### <a name="ping-vs-test"></a>Visual Studio di ping. Test
Usare il `Test` verbo.

## <a name="common-verbs"></a>Verbi comuni

PowerShell Usa il [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) classe di enumerazione per definire azioni generiche applicabili a quasi tutti i cmdlet.
La tabella seguente elenca la maggior parte dei verbi definiti.

|Verbo (alias)|Azione|Commenti|
|--------------------|------------|--------------|
|[Add](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Aggiunge una risorsa a un contenitore o associa un elemento a un altro elemento. Ad esempio, il `Add-Content` cmdlet aggiunge il contenuto in un file. Questo verbo viene abbinato `Remove`.|Per questa azione, non usare verbi ad esempio di Append, collegamento e concatenazione, o inserire.|
|[Cancella](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Rimuove tutte le risorse da un contenitore, ma non elimina il contenitore. Ad esempio, il `Clear-Content` cmdlet rimuove il contenuto di un file ma non elimina il file.|Per questa azione, non usare verbi ad esempio lo scaricamento, cancellazione, versione, Rimuovi il contrassegno, Unset o Rendi null.|
|[Chiudi](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|Modifica lo stato di una risorsa per renderla accessibile, non disponibile o inutilizzabile. Questo verbo è associato a `Open.`||
|[Copy](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|Copia una risorsa a un altro nome o a un altro contenitore. Ad esempio, il `Copy-Item` cmdlet che consente di accedere ai dati archiviati copia un elemento da una posizione nell'archivio dati in un'altra posizione.|Per questa azione, non usare verbi come duplicato, clonare, eseguire la replica o sincronizzazione.|
|[Immettere](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Specifica un'azione che consente all'utente di spostare in una risorsa. Ad esempio, il `Enter-PSSession` cmdlet inserisce l'utente in una sessione interattiva. Questo verbo viene abbinato `Exit`.|Per questa azione, non usare verbi ad esempio Push o in.|
|[Uscita](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|Imposta l'ambiente corrente o il contesto nel contesto degli ultimi file usati. Ad esempio, il `Exit-PSSession` cmdlet inserisce l'utente della sessione che è stato usato per avviare la sessione interattiva. Questo verbo viene abbinato `Enter`.|Per questa azione, non usare verbi ad esempio Pop o Out.|
|[Trovare](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Cerca un oggetto in un contenitore è sconosciuto, impliciti, facoltativo o specificato.||
|[Formato](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Dispone gli oggetti in un formato specificato o layout.||
|[Ottenere](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Specifica un'azione che consente di recuperare una risorsa. Questo verbo viene abbinato `Set`.|Per questa azione, non usare verbi ad esempio lettura, Open, Cat, tipo, Dir, ottenere, Dump, acquisizione, esaminare, trova o Cerca questa azione.|
|[Nascondi](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Effettua una risorsa non rilevabili. Ad esempio, un cmdlet il cui nome include il verbo Nascondi può nascondere un servizio da un utente. Questo verbo viene abbinato `Show`.|Per questa azione, non utilizzare un verbo, ad esempio blocco.|
|[Join](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Combina le risorse in una risorsa. Ad esempio, il `Join-Path` cmdlet combina un percorso con uno dei relativi percorsi figlio per creare un unico percorso. Questo verbo viene abbinato `Split`.|Per questa azione, non usare verbi come combinare, Unite, Connect o associare.|
|[Blocco](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|Consente di proteggere una risorsa. Questo verbo viene abbinato `Unlock`.|Per questa azione, non usare verbi ad esempio limitare o sicura.|
|[Move](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Sposta una risorsa da una posizione a altra. Ad esempio, il `Move-Item` cmdlet sposta un elemento da una posizione nell'archivio dati in un'altra posizione.|Per questa azione, non usare verbi ad esempio trasferimento, il nome o la migrazione.|
|[Nuovo](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Crea una risorsa. (Il `Set` verbo utilizzabili durante la creazione di una risorsa che include i dati, ad esempio il `Set-Variable` cmdlet.)|Per questa azione, non usare verbi ad esempio Create, generare, compilazione, verificare o Allocate.|
|[Apri](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|Modifica lo stato di una risorsa per renderla accessibile, disponibili o utilizzabile. Questo verbo viene abbinato `Close`.||
|[Ottimizzare](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Aumenta l'efficacia di una risorsa.||
|[POP](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Rimuove un elemento dall'inizio dello stack. Ad esempio, il `Pop-Location` cmdlet imposta il percorso corrente nel percorso che è stato inserito più di recente nello stack.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|Aggiunge un elemento all'inizio di uno stack. Ad esempio, il `Push-Location` cmdlet inserisce il percorso corrente nello stack.||
|[Fase di rollforward](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Reimposta una risorsa allo stato in cui è stato annullato.||
|[Rimuovere](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Elimina una risorsa da un contenitore. Ad esempio, il `Remove-Variable` cmdlet Elimina una variabile e il relativo valore. Questo verbo viene abbinato `Add`.|Per questa azione, non usare verbi di questo tipo in chiaro, le operazioni Taglia, Dispose, variabile Discard o cancellare.|
|[Rinominare](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn)|Modifica il nome di una risorsa. Ad esempio, il `Rename-Item` cmdlet, che viene usato per accedere ai dati archiviati, modifica il nome di un elemento nell'archivio dati.|Per questa azione, non utilizzare un verbo, ad esempio modifica.|
|[Reimpostare](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|Imposta una risorsa allo stato originale.||
|[Ricerca](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|Crea un riferimento a una risorsa in un contenitore.|Per questa azione, non usare verbi ad esempio trova o Cerca.|
|[Selezionare](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|Individua una risorsa in un contenitore. Ad esempio, il `Select-String` cmdlet Trova testo in stringhe e file.|Per questa azione, non usare verbi ad esempio trova o Cerca.|
|[Impostare](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Sostituisce i dati in una risorsa esistente o crea una risorsa che contiene alcuni dati. Ad esempio, il `Set-Date` cmdlet modifica l'ora di sistema nel computer locale. (Il `New` verbo è anche utilizzabile per creare una risorsa.) Questo verbo viene abbinato `Get`.|Per questa azione, non usare verbi ad esempio di scrittura, Reset, assegna o configurare.|
|[Mostra](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|Rende visibili all'utente una risorsa. Questo verbo viene abbinato `Hide`.|Per questa azione, non usare verbi come visualizzazione o producono.|
|[Ignora](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|Consente di ignorare uno o più risorse o i punti in una sequenza.|Per questa azione, non utilizzare un verbo, ad esempio Bypass o di salto.|
|[Suddivisione](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|Separa le parti di una risorsa. Ad esempio, il `Split-Path` cmdlet restituisce le parti diverse di un percorso. Questo verbo viene abbinato `Join`.|Per questa azione, non utilizzare un verbo tali separato.|
|[Passaggio](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|Passa al successivo punto o risorse in una sequenza.||
|[Commutatore](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|Specifica un'azione che alterna tra due risorse, ad esempio modificare tra due posizioni, le responsabilità o gli stati.||
|[Annulla](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (annullamento)|Imposta una risorsa allo stato precedente.||
|[Sbloccare](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (Regno Unito)|Rilascia una risorsa bloccata. Questo verbo viene abbinato `Lock`.|Per questa azione, non usare verbi come versione, Unrestrict o senza protezione.|
|[Espressioni di controllo](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|Continuamente controlla o di monitoraggio di una risorsa per le modifiche.||

## <a name="communications-verbs"></a>Le comunicazioni verbi

PowerShell Usa il [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) classe per definire le azioni applicabili alle comunicazioni.
La tabella seguente elenca la maggior parte dei verbi definiti.

|Verbo (alias)|Azione|Commenti|
|--------------------|------------|--------------|
|[Connettere](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|Crea un collegamento tra un'origine e destinazione. Questo verbo viene abbinato `Disconnect`.|Per questa azione, non usare verbi ad esempio Join o Telnet.|
|[Disconnettere](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|Interrompe il collegamento tra un'origine e destinazione. Questo verbo viene abbinato `Connect`.|Per questa azione, non usare verbi quali Break o disconnessione.|
|[Lettura](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|Acquisisce informazioni da un'origine. Questo verbo viene abbinato `Write`.|Per questa azione, non usare verbi ad esempio acquisizione, prompt dei comandi, o ottenere.|
|[Receive](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|Accetta le informazioni inviate da un'origine. Questo verbo viene abbinato `Send`.|Per questa azione, non usare verbi ad esempio lettura, accetta, o Visualizza.|
|[Inviare](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|Invia informazioni a una destinazione. Questo verbo viene abbinato `Receive`.|Per questa azione, non usare verbi ad esempio Put, trasmissione, stampa o Fax.|
|[Scrivere](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (SCR)|Aggiunge informazioni a una destinazione. Questo verbo viene abbinato `Read`.|Per questa azione, non usare verbi ad esempio Put o stampa.|

## <a name="data-verbs"></a>Verbi di dati

PowerShell Usa il [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) classe per definire le azioni applicabili per la gestione dei dati.
La tabella seguente elenca la maggior parte dei verbi definiti.

|Nome del verbo (alias)|Azione|Commenti|
|-------------------------|------------|--------------|
|[Backup](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|Archivia i dati per la replica.|Per questa azione, non usare verbi come salvare, Burn, eseguire la replica o sincronizzazione.|
|[Checkpoint](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|Crea uno snapshot dello stato corrente dei dati o della relativa configurazione.|Per questa azione, non utilizzare un verbo, ad esempio differenze.|
|[Confrontare](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|Valuta i dati da una risorsa in base a quelli di un'altra risorsa.|Per questa azione, non utilizzare un verbo, ad esempio differenze.|
|[Comprimere](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Compatta i dati di una risorsa. Coppie con `Expand`.|Per questa azione, non utilizzare un verbo, ad esempio Compact.|
|[Convertire](/dotnet/api/System.Management.Automation.VerbsData.Convert) (Visualizzatore di concorrenza)|Modifica i dati da una rappresentazione a un altro quando il cmdlet supporta la conversione bidirezionale o quando il cmdlet supporta la conversione tra più tipi di dati.|Per questa azione, non usare verbi ad esempio modificare, ridimensionare, o Resample.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|Converte un tipo primario di input (il sostantivo cmdlet indica l'input) in uno o più tipi di output supportati.|Per questa azione, non usare verbi ad esempio l'esportazione, Output o Out.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|Converte da uno o più tipi di input a un tipo di output primario (il sostantivo cmdlet indica il tipo di output).|Per questa azione, non usare verbi ad esempio l'importazione, Input, o In.|
|[Smontare](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|Scollega un'entità denominata da un percorso. Questo verbo viene abbinato `Mount`.|Per questa azione, non usare verbi ad esempio Smonta o Scollega.|
|[Modifica](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Modifica dati esistenti aggiungendo o rimuovendo contenuto.|Per questa azione, non usare verbi ad esempio modifica, aggiornamento o modifica per questa azione.|
|[Espandere](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Consente di ripristinare i dati di una risorsa che è stata compressa allo stato originale. Questo verbo viene abbinato `Compress`.|Per questa azione, non usare verbi come esploso o.|
|[Esportare](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|Incapsula l'input principale in un archivio dati permanente, ad esempio un file o in un formato di interscambio. Questo verbo viene abbinato `Import`.|Per questa azione, non usare verbi quali Backup o di estrazione.|
|[Gruppo](/dotnet/api/System.Management.Automation.VerbsData.Group) (criteri di gruppo)|Organizza o associa una o più risorse.|Per questa azione, non usare verbi ad esempio aggregazione, Disponi, associazione, o mettere in correlazione.|
|[Importazione](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|Crea una risorsa da dati archiviati in un archivio dati permanente (ad esempio un file) o in un formato di interscambio. Ad esempio, il `Import-CSV` cmdlet Importa dati da un file con valori delimitati da virgole (CSV) in oggetti che possono essere utilizzati da altri cmdlet. Questo verbo viene abbinato `Export`.|Per questa azione, non usare verbi ad esempio BulkLoad o caricamento.|
|[Inizializzare](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Prepara una risorsa per l'uso e lo imposta su uno stato predefinito.|Per questa azione, non usare verbi come cancellazione, Init, rinnovo, ricompilazione, reinizializzare o il programma di installazione.|
|[Limite](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Applica i vincoli a una risorsa.|Per questa azione, non utilizzare un verbo, ad esempio Quota.|
|[Merge](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Crea una singola risorsa di più risorse.|Per questa azione, non usare verbi ad esempio Join o combinare.|
|[Mount](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|Associa un'entità denominata in un percorso. Questo verbo viene abbinato `Dismount`.|Per questa azione, non usare il verbo Connect.|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Invia i dati all'esterno dell'ambiente. Ad esempio, il `Out-Printer` cmdlet invia dati a una stampante.||
|[Publish](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|Rende disponibile ad altri utenti una risorsa. Questo verbo viene abbinato `Unpublish`.|Per questa azione, non usare verbi ad esempio distribuzione, versione, o installare.|
|[Ripristinare](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|Imposta una risorsa in uno stato predefinito, ad esempio uno stato impostato da `Checkpoint`. Ad esempio, il `Restore-Computer` cmdlet avvia un ripristino del sistema nel computer locale.|Per questa azione, non usare verbi ad esempio Repair, Return, annullamento o correzione.|
|[Salvare](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|Consente di mantenere i dati per evitare la perdita.||
|[Sincronizzazione](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|Garantisce che due o più risorse sono nello stesso stato.|Per questa azione, non usare verbi ad esempio eseguire la replica, soggetti a coercizione, o corrispondenti.|
|[Annullare la pubblicazione](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (ub)|Rende una risorsa non disponibile ad altri utenti. Questo verbo viene abbinato `Publish`.|Per questa azione, non usare verbi ad esempio di disinstallazione, ripristino, o nascondere.|
|[Aggiornamento](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|Offre una risorsa aggiornata per mantenere relativo stato, la precisione, della conformità o conformità. Ad esempio, il `Update-FormatData` cmdlet Aggiorna e aggiunge file di formattazione per la console di PowerShell corrente.|Per questa azione, non usare verbi ad esempio il ricalcolo di rinnovo, l'aggiornamento o la reindicizzazione.|

## <a name="diagnostic-verbs"></a>Verbi di diagnostica

PowerShell Usa il [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) classe per definire le azioni applicabili alla diagnostica.
La tabella seguente elenca la maggior parte dei verbi definiti.

|Verbo (alias)|Azione|Commenti|
|--------------------|------------|--------------|
|[Debug](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|Esamina una risorsa per diagnosticare i problemi operativi.|Per questa azione, non utilizzare un verbo, ad esempio Esegui diagnosi.|
|[Misura](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|Identifica le risorse utilizzate da un'operazione specifica o recupera le statistiche su una risorsa.|Per questa azione, non usare verbi ad esempio Calculate, determinare o Analyze.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|Usare il `Test` verbo.||
|[Repair](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|Ripristina una risorsa a una condizione utilizzabile|Per questa azione, non usare verbi come correggere il problema o ripristino.|
|[Risolvere](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|Esegue il mapping di una rappresentazione in forma abbreviata di una risorsa in una rappresentazione più completa.|Per questa azione, non usare verbi ad esempio l'espansione o determinare.|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Verifica l'operazione o per la coerenza di una risorsa.|Per questa azione, non usare verbi ad esempio Esegui diagnosi, analizza, recupero o verifica.|
|[Traccia](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|Registra le attività di una risorsa.|Per questa azione, non usare verbi ad esempio Track, seguire, controlla, o un'analisi.|

## <a name="lifecycle-verbs"></a>Verbi del ciclo di vita

PowerShell Usa il [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) classe per definire le azioni che si applicano al ciclo di vita di una risorsa.
La tabella seguente elenca la maggior parte dei verbi definiti.

|Verbo (alias)|Azione|Commenti|
|--------------------|------------|--------------|
|[Approvare](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|Conferma o accetta lo stato di una risorsa o un processo.||
|[L'asserzione](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (esempio)|Modalità automatica dello stato di una risorsa.|Per questa azione, non utilizzare un verbo, ad esempio Certify.|
|[Compilare](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|Crea un elemento (in genere un file binario o documento) all'esterno di un set di file di input (in genere il codice sorgente o documenti dichiarativi)|Questo verbo è stata aggiunta in PowerShell v6|
|[Completa](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|Un'operazione è terminata.||
|[Confirm](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|Invia un acknowledgement, verifica o convalida lo stato di una risorsa o un processo.|Per questa azione, non usare verbi ad esempio riconoscimento, Accetto, Certify, convalida o verificare.|
|[Deny](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|Rifiuta, oggetti, si blocca o oppone lo stato di una risorsa o un processo.|Per questa azione, non usare verbi quali blocco, oggetto, rifiutare o rifiutare.|
|[Distribuire](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|Invia un'applicazione, un sito Web o una soluzione a una destinazione remota [s] in modo che un consumer di tale soluzione possibile accedervi dopo la distribuzione è stata completata|Questo verbo è stata aggiunta in PowerShell v6|
|[Disabilitare](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Configura una risorsa a uno stato non disponibile o inattivo. Ad esempio, il `Disable-PSBreakpoint` cmdlet rende inattiva un punto di interruzione. Questo verbo viene abbinato `Enable`.|Per questa azione, non usare verbi ad esempio Halt o nascondere.|
|[Abilitare](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Configura una risorsa a uno stato non disponibile o attiva. Ad esempio, il `Enable-PSBreakpoint` cmdlet rende attiva un punto di interruzione. Questo verbo viene abbinato `Disable`.|Per questa azione, non usare verbi quali avvio o Begin.|
|[Installare](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (è)|Inserisce una risorsa in un percorso e facoltativamente lo inizializza. Questo verbo viene abbinato `Uninstall`.|Per questa azione, eseguire operazioni non un verbo di utilizzo, ad esempio il programma di installazione.|
|[Invoke](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Esegue un'azione, ad esempio l'esecuzione di un comando o un metodo.|Per questa azione, non usare verbi ad esempio esecuzione o avviare.|
|[Registrare](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|Crea una voce per una risorsa in un repository, ad esempio un database. Questo verbo viene abbinato `Unregister`.||
|[Richiedere](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (rq)|Richiede una risorsa o richiede le autorizzazioni.||
|[Riavviare](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|Arresta un'operazione e quindi avvia nuovamente. Ad esempio, il `Restart-Service` cmdlet arresta e quindi avvia un servizio.|Per questa azione, non utilizzare un verbo, ad esempio riciclo.|
|[Riprendi](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (UR)|Avvia un'operazione che è stata sospesa. Ad esempio, il `Resume-Service` cmdlet avvia un servizio che è stata sospesa. Questo verbo viene abbinato `Suspend`.||
|[Avviare](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Avvia un'operazione. Ad esempio, il `Start-Service` cmdlet avvia un servizio. Questo verbo viene abbinato `Stop`.|Per questa azione, non usare verbi come avvio, avvio o avvio.|
|[Arrestare](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|Interrompe un'attività. Questo verbo viene abbinato `Start`.|Per questa azione, non usare verbi ad esempio finale, Kill, Terminate, o annullare.|
|[Submit](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|Presenta una risorsa per l'approvazione.|Per questa azione, non utilizzare un verbo, ad esempio Post.|
|[Sospendere](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|Sospende un'attività. Ad esempio, il `Suspend-Service` cmdlet sospende un servizio. Questo verbo viene abbinato `Resume`.|Per questa azione, non utilizzare un verbo, ad esempio sospendere.|
|[Disinstallare](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|Rimuove una risorsa da un percorso indicato. Questo verbo viene abbinato `Install`.||
|[Annullare la registrazione](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (i)|Rimuove la voce di una risorsa da un repository. Questo verbo viene abbinato `Register`.|Per questa azione, non utilizzare un verbo, ad esempio Remove.|
|[Attesa](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Sospende un'operazione fino a quando non si verifica un evento specificato. Ad esempio, il `Wait-Job` cmdlet sospende le operazioni fino a quando uno o più processi in background sono state completate.|Per questa azione, non usare verbi come sospensione o Sospendi.|

## <a name="security-verbs"></a>Verbi di sicurezza

PowerShell Usa il [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) classe per definire le azioni applicabili alla sicurezza.
La tabella seguente elenca la maggior parte dei verbi definiti.

|Verbo (alias)|Azione|Commenti|
|--------------------|------------|--------------|
|[Blocco](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|Limita l'accesso a una risorsa. Questo verbo viene abbinato `Unblock`.|Per questa azione, non usare verbi ad esempio Impedisci, limite o Deny.|
|[GRANT](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Consente l'accesso a una risorsa. Questo verbo viene abbinato `Revoke`.|Per questa azione, non usare verbi ad esempio Consenti o abilitare.|
|[Proteggere](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|Consente di proteggere una risorsa attacco o di perdita. Questo verbo viene abbinato `Unprotect`.|Per questa azione, non usare verbi ad esempio Encrypt, misura di sicurezza o sigillo.|
|[Revocare](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (rk)|Specifica un'azione che non consente l'accesso a una risorsa. Questo verbo viene abbinato `Grant`.|Per questa azione, non usare verbi ad esempio rimuovere o disabilitare.|
|[Sbloccare](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|Rimuove le restrizioni a una risorsa. Questo verbo viene abbinato `Block`.|Per questa azione, non usare verbi ad esempio chiaro o Allow.|
|[Rimuovere la protezione](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (massimo)|Rimuove le misure di sicurezza da una risorsa che sono state aggiunte per impedirne l'attacco o di perdita. Questo verbo viene abbinato `Protect`.|Per questa azione, non usare verbi ad esempio Unseal o decrittografare.|

## <a name="other-verbs"></a>Altri verbi

PowerShell Usa il [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) classe per definire i nomi canonici verbo che non rientrano in una categoria di nome verbo specifici, ad esempio il comune, le comunicazioni, i dati, del ciclo di vita o nomi di verbi di sicurezza verbi.

|Verbo (alias)|Azione|Commenti|
|--------------------|------------|--------------|
|[Usare](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Usa oppure include una risorsa per ottenere un risultato.||

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Dichiarazione di cmdlet](./cmdlet-class-declaration.md)

[Guida per programmatori di Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
