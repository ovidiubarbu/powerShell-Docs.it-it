---
title: Installazione di Windows PowerShell SDK
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: e7ca38377b3e6533eec1a70027f6de1a9fb3091b
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444500"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installazione di Windows PowerShell SDK

Si applica a: Windows PowerShell 2,0, Windows PowerShell 3,0

L'argomento seguente descrive come installare PowerShell SDK in diverse versioni di Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installazione di Windows PowerShell 3.0 SDK in Windows 8 e Windows Server 2012

Windows PowerShell 3.0 viene installato automaticamente con Windows 8 e Windows Server 2012. È inoltre possibile scaricare e installare gli assembly di riferimento per Windows PowerShell 3.0 come parte di Windows 8 SDK. Questi assembly permettono di scrivere cmdlet, provider e programmi host per Windows PowerShell 3.0. Quando si installa Windows SDK per Windows 8, gli assembly di Windows PowerShell vengono automaticamente installati nella cartella degli assembly di riferimento, in `\Program Files
(x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`. Per ulteriori informazioni, vedere il sito di download di Windows 8 SDK. Gli esempi di codice di Windows PowerShell sono disponibili anche nel centro di sviluppo di [Windows powershell 3,0 SDK Sample Pack](https://code.msdn.microsoft.com/Windows-PowerShell-30-SDK-9a34641d).

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installazione di Windows PowerShell 3.0 SDK in Windows 7 e Windows Server 2008 R2

In Windows 7 e Windows Server 2008 R2 PowerShell 2.0 è installato automaticamente. In questi sistemi, inoltre, è possibile installare PowerShell 3.0. È anche possibile installare Windows 8 SDK in Windows 7 e Windows Server 2008 R2 come descritto in precedenza.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installazione di Windows PowerShell 2.0 SDK in Windows 7, Vista, XP, Server 2003 e Server 2008

Windows PowerShell 2.0 SDK fornisce gli assembly di riferimento necessari per scrivere cmdlet, provider e applicazioni di hosting, nonché il codice di esempio C# che può essere usato come punto di partenza quando si inizia a scrivere il codice. È possibile scaricare gli esempi di codice da [https://www.microsoft.com/download/details.aspx?id=2560](https://www.microsoft.com/download/details.aspx?id=2560).

### <a name="reference-assemblies"></a>Assembly di riferimento

Gli assembly di riferimento sono installati per impostazione predefinita nel percorso seguente: `c:\Program Files\Reference
Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> [!NOTE]
>
> Il codice compilato per gli assembly di Windows PowerShell 2.0 non può essere caricato nelle installazioni di Windows PowerShell 1.0. Al contrario, il codice compilato per gli assembly di Windows PowerShell 1.0 può essere caricato nelle installazioni di Windows PowerShell 2.0.


### <a name="samples"></a>Esempi

Gli esempi di codice sono installati per impostazione predefinita nel percorso seguente: `C:\Program Files\Microsoft
SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`. La sezione seguente riporta una breve descrizione del funzionamento di ciascun esempio.

#### <a name="cmdlet-samples"></a>Esempi di cmdlet

- GetProcessSample01: Mostra come scrivere un semplice cmdlet che ottiene tutti i processi nel computer locale.
- GetProcessSample02: Mostra come aggiungere parametri al cmdlet. Il cmdlet accetta uno o più nomi di processo e restituisce i processi corrispondenti.
- GetProcessSample03: Mostra come aggiungere parametri che accettano input dalla pipeline.
- GetProcessSample04: Mostra come gestire errori non fatali.
- GetProcessSample05: Mostra come visualizzare un elenco di processi specificati.
- SelezionaOggetto: Mostra come scrivere un filtro per selezionare solo determinati oggetti.
- SelectString: Mostra come cercare i file per i modelli specificati.
- StopProcessSample01: Mostra come implementare un parametro PassThru e come richiedere commenti e suggerimenti degli utenti tramite chiamate ai metodi ShouldProcess e ShouldContinue. Gli utenti specificano il parametro PassThru quando vogliono forzare il cmdlet per la restituzione di un oggetto.
- StopProcessSample02: Mostra come arrestare un processo specifico.
- StopProcessSample03: Mostra come dichiarare gli alias per i parametri e come supportare i caratteri jolly.
- StopProcessSample04: Mostra come dichiarare i set di parametri, l'oggetto che il cmdlet accetta come input e come specificare il set di parametri predefinito da usare.

#### <a name="remoting-samples"></a>Esempi di comunicazione remota

- RemoteRunspace01: Mostra come creare un spazio remoto usato per stabilire una connessione remota.
- RemoteRunspacePool01: Mostra come costruire un pool di spazio remoto e come eseguire più comandi contemporaneamente usando questo pool.
- Serialization01: Mostra come esaminare una classe .NET esistente e assicurarsi che le informazioni provenienti dalle proprietà pubbliche selezionate di questa classe vengano mantenute durante la serializzazione/deserializzazione.
- Serialization02: Mostra come esaminare una classe .NET esistente e assicurarsi che le informazioni dell'istanza di questa classe vengano mantenute nella serializzazione/deserializzazione quando le informazioni non sono disponibili nelle proprietà pubbliche della classe.
- Serialization03: Mostra come esaminare una classe .NET esistente e assicurarsi che le istanze di questa classe e delle classi derivate vengano deserializzate (reidratate) in oggetti .NET attivi.

#### <a name="event-samples"></a>Esempi di evento

- Event01: Mostra come creare un cmdlet per la registrazione degli eventi mediante derivazione da ObjectEventRegistrationBase.
- Event02: Mostra come ricevere notifiche di eventi di Windows PowerShell generati su computer remoti. Usa l'evento PSEventReceived esposto tramite la classe spazio.

#### <a name="hosting-application-samples"></a>Esempi di applicazioni di hosting

- Runspace01: Mostra come usare la classe PowerShell per eseguire in modo sincrono il cmdlet `Get-Process`.
Il cmdlet `Get-Process` restituisce gli oggetti processo per ogni processo in esecuzione nel computer locale.
- Runspace02: Mostra come usare la classe PowerShell per eseguire in modo sincrono i cmdlet `Get-Process` e `Sort-Object`. Il cmdlet `Get-Process` restituisce gli oggetti processo per ogni processo in esecuzione nel computer locale e il `Sort-Object` Ordina gli oggetti in base alla relativa proprietà ID. I risultati di questi comandi vengono visualizzati usando un controllo DataGridView.
- Runspace03: Mostra come usare la classe PowerShell per eseguire uno script in modo sincrono e come gestire errori non fatali. Lo script riceve un elenco di nomi di processo e quindi recupera tali processi. I risultati dello script, compresi gli errori non fatali che si sono generati durante l'esecuzione dello script, vengono visualizzati in una finestra della console.
- Runspace04: Mostra come usare la classe PowerShell per eseguire i comandi e come intercettare gli errori fatali generati quando si eseguono i comandi. Vengono eseguiti due comandi e all'ultimo viene passato un argomento di parametro non valido. Di conseguenza, non viene restituito alcun oggetto e viene generato un errore non fatale.
- Runspace05: Mostra come aggiungere uno snap-in a un oggetto InitialSessionState in modo che il cmdlet dello snap-in sia disponibile quando viene aperto il spazio. Lo snap-in fornisce un cmdlet Get-proc (definito dall'esempio GetProcessSample01) che viene eseguito in modo sincrono tramite un oggetto PowerShell.
- Runspace06: Mostra come aggiungere un modulo a un oggetto InitialSessionState in modo che il modulo venga caricato quando viene aperto il spazio. Il modulo fornisce un cmdlet Get-proc (definito dall'esempio GetProcessSample02) che viene eseguito in modo sincrono tramite un oggetto PowerShell.
- Runspace07: Mostra come creare un spazio e quindi usare tale spazio per eseguire due cmdlet in modo sincrono tramite un oggetto PowerShell.
- Runspace08: Mostra come aggiungere comandi e argomenti alla pipeline di un oggetto PowerShell e come eseguire i comandi in modo sincrono.
- Runspace09: Mostra come aggiungere uno script alla pipeline di un oggetto PowerShell e come eseguire lo script in modo asincrono. Gli eventi vengono usati per gestire l'output dello script.
- Runspace10: Mostra come creare uno stato di sessione iniziale predefinito, come aggiungere un cmdlet a InitialSessionState, come creare un spazio che usa lo stato della sessione iniziale e come eseguire il comando usando un oggetto di PowerShell.
- Runspace11: Mostra come usare la classe ProxyCommand per creare un comando proxy che chiama un cmdlet esistente, ma limita il set di parametri disponibili. Il comando proxy viene quindi aggiunto a uno stato sessione iniziale usato per creare uno spazio di esecuzione vincolato. Ciò significa che l'utente può accedere alla funzionalità del cmdlet solo tramite il comando proxy.
- PowerShell01: Mostra come creare un spazio vincolato usando un oggetto InitialSessionState.
- PowerShell02: Mostra come usare un pool spazio per eseguire più comandi simultaneamente.

#### <a name="host-samples"></a>Esempi di host

- Host01: Mostra come implementare un'applicazione host che usa un host personalizzato. In questo esempio viene creato un spazio che usa l'host personalizzato e quindi viene usata l'API di PowerShell per eseguire uno script che chiama "Exit". L'applicazione host esamina l'output dello script e stampa i risultati.
- Host02: Mostra come scrivere un'applicazione host che usa il runtime di Windows PowerShell insieme a un'implementazione host personalizzata. L'applicazione host imposta le impostazioni cultura dell'host su tedesco, esegue il cmdlet `Get-Process` e Visualizza i risultati come verrebbero visualizzati usando pwrsh. exe e quindi stampa i dati e l'ora correnti in tedesco.
- Host03: Mostra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console.
- Host04: Mostra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console. L'applicazione host supporta anche la visualizzazione di messaggi di richiesta che consentono all'utente di specificare più opzioni.
- Host05: Mostra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console. Questa applicazione host supporta inoltre le chiamate a computer remoti utilizzando i cmdlet `Enter-PsSession` e `Exit-PsSession`.
- Host06: Mostra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console. Questo esempio usa inoltre le API del tokenizer per specificare il colore del testo immesso dall'utente.

#### <a name="provider-samples"></a>Esempi di provider

- AccessDBProviderSample01: Mostra come dichiarare una classe di provider che deriva direttamente dalla classe CmdletProvider. È incluso solo per motivi di completezza.

- AccessDBProviderSample02: Mostra come sovrascrivere i metodi nuovaunità e RemoveDrive per supportare le chiamate ai cmdlet `New-PSDrive` e `Remove-PSDrive`. La classe del provider in questo esempio deriva dalla classe DriveCmdletProvider.

- AccessDBProviderSample03: Mostra come sovrascrivere i metodi GetItem e SetItem per supportare le chiamate ai cmdlet `Get-Item` e `Set-Item`. La classe del provider in questo esempio deriva dalla classe ItemCmdletProvider.

- AccessDBProviderSample04: Mostra come sovrascrivere i metodi del contenitore per supportare le chiamate ai cmdlet `Copy-Item`, `Get-ChildItem`, `New-Item` e `Remove-Item`. Questi metodi devono essere implementati quando l'archivio dati contiene elementi che sono contenitori. Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune. La classe del provider in questo esempio deriva dalla classe ItemCmdletProvider.

- AccessDBProviderSample05: Mostra come sovrascrivere i metodi del contenitore per supportare le chiamate ai cmdlet `Move-Item` e `Join-Path`. Questi metodi devono essere implementati quando l'utente deve spostare elementi all'interno di un contenitore e se l'archivio dati contiene contenitori annidati. La classe del provider in questo esempio deriva dalla classe NavigationCmdletProvider.

- AccessDBProviderSample06: Mostra come sovrascrivere i metodi di contenuto per supportare le chiamate ai cmdlet `Clear-Content`, `Get-Content` e `Set-Content`. Questi metodi devono essere implementati quando l'utente deve gestire il contenuto degli elementi nell'archivio dati. La classe del provider in questo esempio deriva dalla classe NavigationCmdletProvider e implementa l'interfaccia IContentCmdletProvider.
