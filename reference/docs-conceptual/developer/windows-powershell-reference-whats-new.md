---
title: Informazioni di riferimento su Windows PowerShell-novità
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366090"
---
# <a name="whats-new"></a>Novità

Windows PowerShell 2,0 fornisce le seguenti nuove funzionalità da utilizzare per la scrittura di cmdlet, provider e applicazioni host.

## <a name="modules"></a>Moduli

È ora possibile creare pacchetti e distribuire le soluzioni di Windows PowerShell usando i moduli. I moduli consentono di partizionare, organizzare ed estrarre il codice di Windows PowerShell in unità autosufficienti e riutilizzabili. Per ulteriori informazioni sui moduli, vedere scrittura di un modulo di Windows PowerShell.

## <a name="the-powershell-class"></a>Classe PowerShell

La classe PowerShell offre una soluzione più semplice per la creazione di applicazioni, denominate applicazioni host, che eseguono comandi a livello di codice. Questa classe consente di creare una pipeline di comandi, specificare il valore di spazio usato per eseguire i comandi e specificare di richiamare i comandi in modo sincrono o asincrono.

## <a name="the-runspacepool-class"></a>Classe RunspacePool

I pool di spazio consentono di creare più Runspaces usando una singola chiamata. Il metodo CreateRunspacePool fornisce diversi overload che possono essere usati per creare Runspaces con le stesse funzionalità, ad esempio lo stesso host, lo stato iniziale della sessione e le informazioni di connessione.

## <a name="the-initialsessionstate-class"></a>Classe InitialSessionState

La classe InitialSessionState consente di creare una configurazione dello stato della sessione usata quando viene aperto un spazio. È possibile creare una configurazione personalizzata, una configurazione predefinita che include i comandi forniti da mshshort e una configurazione i cui comandi sono limitati in base alle funzionalità della sessione.

## <a name="remote-runspaces"></a>Runspaces remoto

È ora possibile creare Runspaces che possono essere aperti in computer remoti, consentendo di eseguire comandi nel computer remoto e di raccogliere i risultati in locale. Per creare una spazio remota, è necessario specificare le informazioni sulla connessione remota durante la creazione di spazio. Per esempi, vedere i metodi CreateRunspace e CreateRunspacePool. Le informazioni di connessione sono definite dalla classe RunspaceConnectionInfo.

## <a name="private-runspace-elements"></a>Elementi spazio privati

È ora possibile creare Runspaces i cui elementi sono pubblici o privati. Ciò consente di creare Runspaces i cui elementi sono disponibili per spazio, ma non sono disponibili per l'utente. Vedere la classe ConstrainedSessionStateEntry per individuare gli elementi di spazio che possono essere resi privati.

## <a name="runspace-threading-modes-and-apartment-state"></a>Modalità di Threading spazio e stato Apartment

È ora possibile specificare il modo in cui i thread vengono creati e usati durante l'esecuzione di comandi in un spazio. Vedere le proprietà System. Management. Automation. Runspaces. spazio. ThreadOptions e System. Management. Automation. Runspaces. RunspacePool. ThreadOptions.

È ora possibile ottenere lo stato dell'Apartment dei thread usati per eseguire i comandi in un spazio. Vedere le proprietà System. Management. Automation. Runspaces. spazio. ApartmentState e System. Management. Automation. Runspaces. RunspacePool. ApartmentState.

## <a name="transaction-cmdlets"></a>Cmdlet Transaction

È ora possibile creare cmdlet che possono essere usati all'interno di una transazione. Quando un cmdlet viene utilizzato in una transazione, le relative azioni sono temporanee e possono essere accettate o rifiutate dai cmdlet di transazione forniti da Windows PowerShell.

Per ulteriori informazioni sulle transazioni, vedere come supportare le transazioni.

## <a name="transaction-provider"></a>Provider di transazioni

È ora possibile creare provider che possono essere utilizzati all'interno di una transazione. Analogamente ai cmdlet, quando un provider viene utilizzato in una transazione, le relative azioni sono temporanee e possono essere accettate o rifiutate dai cmdlet di transazione forniti da Windows PowerShell.

Per ulteriori informazioni sulla specifica del supporto per la transazione all'interno di una classe di provider, vedere la proprietà System. Management. Automation. provider. CmdletProviderAttribute. ProviderCapabilities.

## <a name="job-cmdlets"></a>Cmdlet Job

È ora possibile scrivere cmdlet che possono eseguire l'azione come un processo. Questi processi vengono eseguiti in background senza interagire con la sessione corrente. Per ulteriori informazioni sul supporto dei processi in Windows PowerShell, vedere processi in background.

## <a name="cmdlet-output-types"></a>Tipi di output del cmdlet

È ora possibile specificare i tipi di .NET Framework restituiti dai cmdlet dichiarando l'attributo OutputType quando si scrivono i cmdlet. Ciò consentirà ad altri utenti di determinare il tipo di oggetti restituiti da un cmdlet esaminando la proprietà OutputType del cmdlet.

## <a name="event-support"></a>Supporto degli eventi

È ora possibile scrivere cmdlet che aggiungono e utilizzano eventi. Vedere la classe PSEvent.

## <a name="proxy-commands"></a>Comandi proxy

È ora possibile scrivere comandi proxy che possono essere usati per eseguire un altro comando. Un comando proxy consente di controllare la funzionalità del cmdlet di origine disponibile per l'utente. Ad esempio, è possibile creare un comando proxy che rimuove un parametro fornito dal comando di origine. Vedere la classe ProxyCommand.

## <a name="multiple-choice-prompts"></a>Richieste a più scelte

È ora possibile scrivere applicazioni in grado di fornire richieste che consentono all'utente di selezionare più opzioni. Vedere l'interfaccia IHostUISupportsMultipleChoiceSelection

## <a name="interactive-sessions"></a>Sessioni interattive

È ora possibile scrivere applicazioni in grado di avviare e arrestare una sessione interattiva in un computer remoto.
Vedere l'interfaccia IHostSupportsInteractiveSession.

## <a name="custom-cmdlet-help-for-providers"></a>Guida per i cmdlet personalizzati per i provider

È ora possibile creare argomenti della Guida personalizzati per i cmdlet del provider. Gli argomenti della guida sui cmdlet personalizzati possono spiegare il funzionamento del cmdlet nel percorso del provider e documentare le funzionalità speciali, inclusi i parametri dinamici aggiunti dal provider al cmdlet.
