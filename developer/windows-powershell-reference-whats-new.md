---
title: Riferimento di Windows PowerShell - novità
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080527"
---
# <a name="whats-new"></a>Novità

Windows PowerShell 2.0 offre le seguenti nuove funzionalità per l'uso durante la scrittura di cmdlet, provider e applicazioni host.

## <a name="modules"></a>Moduli

È ora possibile creare un pacchetto e distribuire soluzioni di Windows PowerShell usando i moduli. I moduli consentono di partizione, organizzare e astraggono del codice di Windows PowerShell in unità indipendente e riutilizzabile. Per altre informazioni sui moduli, vedere la scrittura di un modulo di Windows PowerShell.

## <a name="the-powershell-class"></a>La classe di PowerShell

La classe di PowerShell fornisce una soluzione più semplice per la creazione di applicazioni, detta applicazioni host, che a livello di codice eseguono i comandi. Questa classe consente di creare una pipeline di comandi, specificare lo spazio di esecuzione che consente di eseguire i comandi e specificare richiamare i comandi in modo sincrono o asincrono.

## <a name="the-runspacepool-class"></a>La classe RunspacePool

I pool di spazi di esecuzione consentono di creare più spazi di esecuzione utilizzando un'unica chiamata. Il metodo CreateRunspacePool fornisce diversi overload che può essere utilizzato per creare spazi di esecuzione che hanno le stesse funzionalità, ad esempio l'host stesso, lo stato della sessione iniziale e le informazioni di connessione.

## <a name="the-initialsessionstate-class"></a>La classe InitialSessionState

La classe InitialSessionState consente di creare una configurazione di stato di sessione che viene usata quando viene aperto uno spazio di esecuzione. È possibile creare una configurazione personalizzata, una configurazione predefinita che include i comandi forniti dal mshshort e una configurazione i cui comandi sono limitati in base alle funzionalità della sessione.

## <a name="remote-runspaces"></a>Spazi di esecuzione remota

È ora possibile creare spazi di esecuzione che può essere aperto in computer remoti, che consente di eseguire comandi nel computer remoto e raccogliere i risultati in locale. Per creare uno spazio di esecuzione remota, è necessario specificare informazioni di connessione remota quando si crea lo spazio di esecuzione. Vedere i metodi CreateRunspace e CreateRunspacePool per alcuni esempi. Le informazioni di connessione sono definite dalla classe RunspaceConnectionInfo.

## <a name="private-runspace-elements"></a>Elementi privati dello spazio di esecuzione

È ora possibile creare spazi di esecuzione a cui elementi sono pubblici o privati. In questo modo è possibile creare spazi di esecuzione cui elementi sono disponibili per lo spazio di esecuzione, ma non sono disponibili all'utente. Vedere la classe ConstrainedSessionStateEntry per scoprire quali elementi di spazio di esecuzione possono essere reso privati.

## <a name="runspace-threading-modes-and-apartment-state"></a>Spazio di esecuzione le modalità e stato dell'apartment del threading

È ora possibile specificare la modalità thread vengono creati e usati quando si eseguono comandi in uno spazio di esecuzione. Visualizzare le proprietà System.Management.Automation.Runspaces.Runspace.ThreadOptions e System.Management.Automation.Runspaces.RunspacePool.ThreadOptions.

È ora possibile ottenere lo stato dell'apartment di thread utilizzati per eseguire i comandi in uno spazio di esecuzione. Visualizzare le proprietà System.Management.Automation.Runspaces.Runspace.ApartmentState e System.Management.Automation.Runspaces.RunspacePool.ApartmentState.

## <a name="transaction-cmdlets"></a>Cmdlet delle transazioni

È ora possibile creare i cmdlet che possono essere usati all'interno di una transazione. Quando un cmdlet viene usato in una transazione, le azioni sono temporanee e possono essere accettate o rifiutate tramite i cmdlet delle transazioni forniti da Windows PowerShell.

Per altre informazioni sulle transazioni, vedere modalità di supporto delle transazioni.

## <a name="transaction-provider"></a>Provider delle transazioni

È ora possibile creare i provider che possono essere usati all'interno di una transazione. Analogamente ai cmdlet, quando viene utilizzato un provider in una transazione, le azioni sono temporanee e possono essere accettate o rifiutate tramite i cmdlet delle transazioni forniti da Windows PowerShell.

Per altre informazioni su come specificare il supporto per la transazione all'interno di una classe di provider, vedere la proprietà System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities.

## <a name="job-cmdlets"></a>Cmdlet di processo

È ora possibile scrivere i cmdlet che è possono eseguire le azioni come processo. Questi processi vengono eseguiti in background senza l'interazione con la sessione corrente. Per altre informazioni su come Windows PowerShell supporta i processi, vedere i processi in Background.

## <a name="cmdlet-output-types"></a>Tipi di output di cmdlet

È ora possibile specificare i tipi di .NET Framework che vengono restituiti tramite il cmdlet dichiarando l'attributo OutputType durante la scrittura dei cmdlet. Questa operazione consentirà ad altri utenti di determinare il tipo di oggetti vengono restituiti da un cmdlet, esaminando la proprietà OutputType del cmdlet.

## <a name="event-support"></a>Supporto per gli eventi

È ora possibile scrivere i cmdlet che aggiungono e utilizzano gli eventi. Vedere la classe PSEvent.

## <a name="proxy-commands"></a>Comandi proxy

È ora possibile scrivere i comandi di proxy che possono essere usati per eseguire un altro comando. Un comando proxy consente di controllare quali funzionalità del cmdlet origine è disponibile per l'utente. Ad esempio, è possibile creare un comando proxy che rimuove un parametro che viene fornito dal comando di origine. Vedere la classe ProxyCommand.

## <a name="multiple-choice-prompts"></a>Più scelta richieste

È ora possibile scrivere applicazioni che possono fornire messaggi di richiesta che consentono all'utente di selezionare più opzioni. Vedere l'interfaccia IHostUISupportsMultipleChoiceSelection

## <a name="interactive-sessions"></a>Sessioni interattive

È ora possibile scrivere applicazioni che possono avviare e arrestare una sessione interattiva in un computer remoto.
Vedere l'interfaccia IHostSupportsInteractiveSession.

## <a name="custom-cmdlet-help-for-providers"></a>Guida personalizzata sui Cmdlet per i provider

È ora possibile creare argomenti della Guida personalizzati per i cmdlet del provider. Guida sui cmdlet personalizzati possono illustrano il funzionamento di cmdlet provider percorso e il documento speciali funzionalità, tra cui i parametri dinamici che consente di aggiungere il provider al cmdlet.
