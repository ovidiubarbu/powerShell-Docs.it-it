---
title: Installazione di Windows PowerShell SDK
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853957"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installazione di Windows PowerShell SDK

Si applica a: Windows PowerShell 2.0, Windows PowerShell 3.0

L'argomento seguente descrive come installare PowerShell SDK in diverse versioni di Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installazione di Windows PowerShell 3.0 SDK in Windows 8 e Windows Server 2012

Windows PowerShell 3.0 viene installato automaticamente con Windows 8 e Windows Server 2012. È inoltre possibile scaricare e installare gli assembly di riferimento per Windows PowerShell 3.0 come parte di Windows 8 SDK. Questi assembly permettono di scrivere cmdlet, provider e programmi host per Windows PowerShell 3.0. Quando si installa Windows SDK per Windows 8, gli assembly di Windows PowerShell vengono automaticamente installati nella cartella degli assembly di riferimento, in \Programmi (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0. Per altre informazioni, vedere Windows 8 SDK nel sito di download. Alcuni esempi di codice di Windows PowerShell sono disponibili anche in Dev Center.
Per altre informazioni, vedere la pagina di esempio di codice per sistemi Desktop nel sito di Dev center.

Inoltre, Windows PowerShell 3.0 è compatibile con la versione precedente, Windows PowerShell 2.0 SDK, che include diversi esempi di codice. Per altre informazioni su come scaricare Windows PowerShell 2.0 SDK, vedere di seguito. Nota: benché gli esempi di codice della versione 2.0 siano compatibili con Windows 8 e Windows PowerShell 3.0, non è possibile installare Windows PowerShell 2.0 in una piattaforma Windows 8.

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installazione di Windows PowerShell 3.0 SDK in Windows 7 e Windows Server 2008 R2

In Windows 7 e Windows Server 2008 R2 PowerShell 2.0 è installato automaticamente. In questi sistemi, inoltre, è possibile installare PowerShell 3.0. (Per altre informazioni, vedere Installazione di Windows PowerShell.). Come descritto sopra, è possibile installare anche Windows 8 SDK in Windows 7 e Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installazione di Windows PowerShell 2.0 SDK in Windows 7, Vista, XP, Server 2003 e Server 2008

Windows PowerShell 2.0 SDK fornisce gli assembly di riferimento necessari per scrivere cmdlet, provider e applicazioni di hosting, nonché il codice di esempio C# che può essere usato come punto di partenza quando si inizia a scrivere il codice.

Per installare questo SDK, vedere Windows PowerShell 2.0 SDK.

### <a name="reference-assemblies"></a>Assembly di riferimento

Impostazione predefinita, gli assembly di riferimento vengono installati nel percorso seguente: c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0.

> [!NOTE]
>
> Il codice compilato per gli assembly di Windows PowerShell 2.0 non può essere caricato nelle installazioni di Windows PowerShell 1.0. Al contrario, il codice compilato per gli assembly di Windows PowerShell 1.0 può essere caricato nelle installazioni di Windows PowerShell 2.0.


### <a name="samples"></a>Esempi

Per impostazione predefinita, gli esempi di codice vengono installati nel percorso seguente: C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\. La sezione seguente riporta una breve descrizione del funzionamento di ciascun esempio.

#### <a name="cmdlet-samples"></a>Esempi di cmdlet

- GetProcessSample01 - illustra come scrivere un semplice cmdlet che ottiene tutti i processi nel computer locale.
- GetProcessSample02 - Mostra come aggiungere parametri al cmdlet. Il cmdlet accetta uno o più nomi di processo e restituisce i processi corrispondenti.
- GetProcessSample03 - Mostra come aggiungere parametri che accettano input dalla pipeline.
- GetProcessSample04 - Mostra come gestire gli errori non fatali.
- GetProcessSample05 - illustra come visualizzare un elenco di processi specificati.
- SelectObject - illustra come scrivere un filtro per selezionare solo determinati oggetti.
- SelectString - Mostra come cercare file per modelli specificati.
- StopProcessSample01 - illustra come implementare un parametro PassThru e come richiedere commenti degli utenti tramite chiamate ai metodi ShouldContinue e ShouldProcess. Gli utenti specificano il parametro PassThru quando vogliono forzare il cmdlet per restituire un oggetto,
- StopProcessSample02 - Mostra come arrestare un processo specifico.
- StopProcessSample03 - illustra come dichiarare alias per i parametri e come supportare i caratteri jolly.
- StopProcessSample04 - illustra come dichiarare set di parametri, l'oggetto che il cmdlet accetta come input e come specificare il parametro predefinito impostato per l'utilizzo.

#### <a name="remoting-samples"></a>Esempi di comunicazione remota

- RemoteRunspace01 - Mostra come creare uno spazio di esecuzione remota che consente di stabilire una connessione remota.
- RemoteRunspacePool01 - Mostra come creare un pool di spazio di esecuzione remoto e come eseguire contemporaneamente più comandi usando questo pool.
- Serialization01 - illustra come esaminare una classe .NET esistente e assicurarsi che le informazioni da specifiche proprietà pubbliche di questa classe vengano mantenute nella serializzazione/deserializzazione.
- Serialization02 - illustra come esaminare una classe .NET esistente e assicurarsi che le informazioni dall'istanza di questa classe vengano mantenute nella serializzazione/deserializzazione quando le informazioni non sono disponibili nelle proprietà pubbliche della classe.
- Serialization03 - illustra come esaminare una classe .NET esistente e assicurarsi che le istanze di questa classe e delle classi derivate vengano deserializzate (riattivate) in oggetti .NET attivi.

#### <a name="event-samples"></a>Esempi di evento

- Event01 - Mostra come creare un cmdlet per la registrazione di eventi da ObjectEventRegistrationBase.
- Event02 - Mostra come viene illustrato come ricevere le notifiche degli eventi di Windows PowerShell generati nei computer remoti. Usa l'evento PSEventReceived esposto tramite la classe dello spazio di esecuzione.

#### <a name="hosting-application-samples"></a>Esempi di applicazioni di hosting

- Runspace01 - illustra come usare la classe di PowerShell per eseguire il `Get-Process` cmdlet in modo sincrono.
Il `Get-Process` cmdlet restituisce gli oggetti di processo per ogni processo in esecuzione nel computer locale.
- Runspace02 - illustra come usare la classe di PowerShell per eseguire la `Get-Process` e `Sort-Object` cmdlet in modo sincrono. Il `Get-Process` cmdlet restituisce gli oggetti di processo per ogni processo in esecuzione nel computer locale e il `Sort-Object` Ordina gli oggetti in base alla relativa proprietà Id. I risultati di questi comandi vengono visualizzati utilizzando un controllo DataGridView.
- Runspace03 - illustra come usare la classe di PowerShell per eseguire uno script in modo sincrono e come gestire gli errori non fatali. Lo script riceve un elenco di nomi di processo e quindi recupera tali processi. I risultati dello script, compresi gli errori non fatali che si sono generati durante l'esecuzione dello script, vengono visualizzati in una finestra della console.
- Runspace04 - illustra come usare la classe di PowerShell per eseguire i comandi e come intercettare gli errori generati durante l'esecuzione di comandi di terminazione. Vengono eseguiti due comandi e all'ultimo viene passato un argomento di parametro non valido. Di conseguenza, non viene restituito alcun oggetto e viene generato un errore non fatale.
- Runspace05 - Mostra come aggiungere uno snap-in a un oggetto InitialSessionState in modo che il cmdlet dello snap-in è disponibile quando viene aperto lo spazio di esecuzione. Lo snap-in fornisce un cmdlet Get-Proc (definito dall'esempio GetProcessSample01) che viene eseguito in modo sincrono usando un oggetto di PowerShell.
- Runspace06 - Mostra come aggiungere un modulo a un oggetto InitialSessionState in modo che il modulo venga caricato quando viene aperto lo spazio di esecuzione. Il modulo include un cmdlet Get-Proc (definito dall'esempio GetProcessSample02) che viene eseguito in modo sincrono usando un oggetto di PowerShell.
- Runspace07 - illustra come creare uno spazio di esecuzione e quindi usare tale spazio di esecuzione per eseguire due cmdlet in modo sincrono usando un oggetto di PowerShell.
- Runspace08 - Mostra come aggiungere comandi e argomenti alla pipeline di un oggetto di PowerShell e su come eseguire i comandi in modo sincrono.
- Runspace09 - Mostra come aggiungere uno script alla pipeline di un oggetto di PowerShell e su come eseguire lo script in modo asincrono. Gli eventi vengono usati per gestire l'output dello script.
- Runspace10 - Mostra come creare uno stato sessione iniziale predefinito, come aggiungere un cmdlet al InitialSessionState, come creare uno spazio di esecuzione che usa lo stato sessione iniziale e come eseguire il comando utilizzando un oggetto di PowerShell.
- Runspace11 - illustra come usare la classe ProxyCommand per creare un comando proxy che chiama un cmdlet esistente, ma limita il set di parametri disponibili. Il comando proxy viene quindi aggiunto a uno stato sessione iniziale usato per creare uno spazio di esecuzione vincolato. Ciò significa che l'utente può accedere alla funzionalità del cmdlet solo tramite il comando proxy.
- PowerShell01 - Mostra come creare uno spazio di esecuzione vincolato usando un oggetto InitialSessionState.
- PowerShell02 - Mostra come usare un pool di spazi di esecuzione per eseguire più comandi contemporaneamente.

#### <a name="host-samples"></a>Esempi di host

- Host01 - Mostra come implementare un'applicazione host che usa un host personalizzato. In questo esempio che viene creato uno spazio di esecuzione che usa l'host personalizzato e quindi l'API di PowerShell viene usata per eseguire uno script che chiama "exit". L'applicazione host esamina l'output dello script e stampa i risultati.
- Host02 - illustra come scrivere un'applicazione host che usa il runtime di Windows PowerShell insieme a un'implementazione host personalizzata. L'applicazione host imposta le impostazioni cultura host sul tedesco, viene eseguito il `Get-Process` cmdlet e visualizza i risultati come li vedrebbe utilizzando pwrsh.exe e quindi stampa i dati correnti e l'ora in tedesco.
- Host03 - illustra come compilare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console.
- Host04 - illustra come compilare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console. L'applicazione host supporta anche la visualizzazione di messaggi di richiesta che consentono all'utente di specificare più opzioni.
- Host05 - illustra come compilare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console. Questa applicazione host supporta anche le chiamate a computer remoti usando il `Enter-PsSession` e `Exit-PsSession` cmdlet.
- Host06 - illustra come compilare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console. Questo esempio usa inoltre le API del tokenizer per specificare il colore del testo immesso dall'utente.

#### <a name="provider-samples"></a>Esempi di provider

- AccessDBProviderSample01 - Mostra come dichiarare una classe di provider che deriva direttamente dalla classe CmdletProvider. È incluso solo per motivi di completezza.

- AccessDBProviderSample02 - Mostra come sovrascrivere i metodi NewDrive e RemoveDrive per supportare le chiamate per il `New-PSDrive` e `Remove-PSDrive` cmdlet. La classe provider in questo esempio deriva dalla classe DriveCmdletProvider.

- AccessDBProviderSample03 - Mostra come sovrascrivere i metodi GetItem e SetItem per supportare le chiamate per il `Get-Item` e `Set-Item` cmdlet. La classe provider in questo esempio deriva dalla classe ItemCmdletProvider.

- AccessDBProviderSample04 - Mostra come sovrascrivere metodi contenitore per supportare le chiamate per il `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlet. Questi metodi devono essere implementati quando l'archivio dati contiene elementi che sono contenitori. Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune. La classe provider in questo esempio deriva dalla classe ItemCmdletProvider.

- AccessDBProviderSample05 - Mostra come sovrascrivere metodi contenitore per supportare le chiamate per il `Move-Item` e `Join-Path` cmdlet. Questi metodi devono essere implementati quando l'utente deve spostare elementi all'interno di un contenitore e se l'archivio dati contiene contenitori annidati. La classe provider in questo esempio deriva dalla classe NavigationCmdletProvider.

- AccessDBProviderSample06 - Mostra come sovrascrivere i metodi per supportare le chiamate per il `Clear-Content`, `Get-Content`, e `Set-Content` cmdlet. Questi metodi devono essere implementati quando l'utente deve gestire il contenuto degli elementi nell'archivio dati. La classe provider in questo esempio deriva dalla classe NavigationCmdletProvider e implementa l'interfaccia IContentCmdletProvider.
