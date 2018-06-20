---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Installazione di Windows PowerShell SDK
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953566"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installazione di Windows PowerShell SDK

L'argomento seguente descrive come installare PowerShell SDK in diverse versioni di Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installazione di Windows PowerShell 3.0 SDK in Windows 8 e Windows Server 2012

Windows PowerShell 3.0 viene installato automaticamente con Windows 8 e Windows Server 2012.
È inoltre possibile scaricare e installare gli assembly di riferimento per Windows PowerShell 3.0 come parte di Windows 8 SDK.
Questi assembly permettono di scrivere cmdlet, provider e programmi host per Windows PowerShell 3.0.
Quando si installa Windows SDK per Windows 8, gli assembly di Windows PowerShell vengono automaticamente installati nella cartella degli assembly di riferimento, in \Programmi (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.
Per altre informazioni, vedere il [sito di download di Windows 8 SDK](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).
Alcuni esempi di codice di Windows PowerShell sono disponibili anche in Dev Center.
Per altre informazioni, vedere la pagina degli esempi di codice per sistemi desktop nel [sito Dev Center](http://code.msdn.microsoft.com/windowsdesktop/).

Inoltre, Windows PowerShell 3.0 è compatibile con la versione precedente, Windows PowerShell 2.0 SDK, che include diversi esempi di codice.
Per altre informazioni su come scaricare Windows PowerShell 2.0 SDK, vedere di seguito.
Nota: benché gli esempi di codice della versione 2.0 siano compatibili con Windows 8 e Windows PowerShell 3.0, non è possibile installare Windows PowerShell 2.0 in una piattaforma Windows 8.

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installazione di Windows PowerShell 3.0 SDK in Windows 7 e Windows Server 2008 R2

In Windows 7 e Windows Server 2008 R2 PowerShell 2.0 è installato automaticamente.
In questi sistemi, inoltre, è possibile installare PowerShell 3.0.
Per altre informazioni, vedere [Installazione di Windows PowerShell](Installing-Windows-PowerShell.md).
Come descritto sopra, è possibile installare anche Windows 8 SDK in Windows 7 e Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installazione di Windows PowerShell 2.0 SDK in Windows 7, Vista, XP, Server 2003 e Server 2008

Windows PowerShell 2.0 SDK fornisce gli assembly di riferimento necessari per scrivere cmdlet, provider e applicazioni di hosting, nonché il codice di esempio C# che può essere usato come punto di partenza quando si inizia a scrivere il codice.

Per installare questo SDK, vedere [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).

## <a name="reference-assemblies"></a>Assembly di riferimento

Gli assembly di riferimento sono installati per impostazione predefinita nel percorso seguente: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> **Nota**: il codice compilato per gli assembly di Windows PowerShell 2.0 non può essere caricato nelle installazioni di Windows PowerShell 1.0.
>Al contrario, il codice compilato per gli assembly di Windows PowerShell 1.0 può essere caricato nelle installazioni di Windows PowerShell 2.0.

## <a name="samples"></a>Esempi

Gli esempi di codice sono installati per impostazione predefinita nel percorso seguente: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

La sezione seguente riporta una breve descrizione del funzionamento di ciascun esempio.

## <a name="cmdlet-samples"></a>Esempi di cmdlet
**GetProcessSample01**

Illustra come scrivere un semplice cmdlet che ottiene tutti i processi nel computer locale.

**GetProcessSample02**

Illustra come aggiungere parametri al cmdlet.
Il cmdlet accetta uno o più nomi di processo e restituisce i processi corrispondenti.

**GetProcessSample03**

Illustra come aggiungere parametri che accettano input dalla pipeline.

**GetProcessSample04**

Illustra come gestire errori non fatali.

**GetProcessSample05**

Illustra come visualizzare un elenco di processi specificati.

**SelectObject**

Illustra come scrivere un filtro per selezionare solo determinati oggetti.

**SelectString**

Illustra come cercare modelli specificati nei file.

**StopProcessSample01**

Illustra come implementare un parametro *PassThru* e come richiedere commenti degli utenti tramite chiamate ai metodi [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) e [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx).
Gli utenti specificano il parametro *PassThru* per forzare il cmdlet a restituire un oggetto.

**StopProcessSample02**

Illustra come arrestare un processo specifico.

**StopProcessSample03**

Illustra come dichiarare gli alias per i parametri e come supportare i caratteri jolly.

**StopProcessSample04**

Illustra come dichiarare i set di parametri, l'oggetto che il cmdlet accetta come input e come specificare il set di parametri predefinito da usare.

## <a name="remoting-samples"></a>Esempi di comunicazione remota

**RemoteRunspace01**

Illustra come creare uno spazio di esecuzione remota che viene usato per stabilire una connessione remota.

**RemoteRunspacePool01**

Illustra come creare un pool di spazi di esecuzione remota e come eseguire contemporaneamente più comandi usando questo pool.

**Serialization01**

Illustra come esaminare una classe .NET esistente e assicurarsi che le informazioni provenienti da specifiche proprietà pubbliche di questa classe vengano mantenute nella serializzazione/deserializzazione.

**Serialization02**

Illustra come esaminare una classe .NET esistente e assicurarsi che le informazioni provenienti dall'istanza di questa classe vengano mantenute nella serializzazione/deserializzazione quando non sono disponibili nelle proprietà pubbliche della classe.

**Serialization03**

Illustra come esaminare una classe .NET esistente e assicurarsi che le istanze di questa classe e delle classi derivate vengano deserializzate (riattivate) in oggetti .NET attivi.

## <a name="event-samples"></a>Esempi di evento

**Event01**

Illustra come creare un cmdlet per la registrazione di eventi da ObjectEventRegistrationBase.

**Event02**

Illustra come ricevere notifiche di eventi di Windows PowerShell generati nei computer remoti.
Usa l'evento PSEventReceived esposto tramite la classe [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx).

## <a name="hosting-application-samples"></a>Esempi di applicazioni di hosting

**Runspace01**

Illustra come usare la classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) per eseguire il cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) in modo sincrono.
Il cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) restituisce oggetti [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) per ogni processo in esecuzione nel computer locale.

**Runspace02**

Illustra come usare la classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) per eseguire i cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) e [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) in modo sincrono.
Il cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) restituisce oggetti [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) per ogni processo in esecuzione nel computer locale e Sort-Object ordina gli oggetti in base alle loro proprietà [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx).
I risultati di questi comandi vengono visualizzati usando un controllo [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx).

**Runspace03**

Illustra come usare la classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) per eseguire uno script in modo sincrono e come gestire gli errori non fatali.
Lo script riceve un elenco di nomi di processo e quindi recupera tali processi.
I risultati dello script, compresi gli errori non fatali che si sono generati durante l'esecuzione dello script, vengono visualizzati in una finestra della console.

**Runspace04**

Illustra come usare la classe [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) per eseguire i comandi e come recuperare gli errori fatali generati durante l'esecuzione di comandi.
Vengono eseguiti due comandi e all'ultimo viene passato un argomento di parametro non valido.
Di conseguenza, non viene restituito alcun oggetto e viene generato un errore non fatale.

**Runspace05**

Illustra come aggiungere uno snap-in a un oggetto [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) in modo che il cmdlet dello snap-in sia disponibile quando viene aperto lo spazio di esecuzione.
Lo snap-in include un cmdlet Get-Process (definito dall'esempio [GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) che viene eseguito in modo sincrono tramite un oggetto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).

**Runspace06**

Illustra come aggiungere un modulo a un oggetto [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) in modo che il modulo venga caricato quando viene aperto lo spazio di esecuzione.
Il modulo include un cmdlet Get-Proc (definito dall'esempio [GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) che viene eseguito in modo sincrono tramite un oggetto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).

**Runspace07**

Illustra come creare uno spazio di esecuzione e quindi usare tale spazio di esecuzione per eseguire due cmdlet in modo sincrono tramite un oggetto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).

**Runspace08**

Illustra come aggiungere comandi e argomenti alla pipeline di un oggetto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) e come eseguire i comandi in modo sincrono.

**Runspace09**

Illustra come aggiungere uno script alla pipeline di un oggetto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) e come eseguire lo script in modo asincrono.
Gli eventi vengono usati per gestire l'output dello script.

**Runspace10**

Illustra come creare uno stato di sessione iniziale predefinito, come aggiungere un cmdlet a [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), come creare uno spazio di esecuzione che usa lo stato sessione iniziale e come eseguire il comando usando un oggetto [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx).

**Runspace11**

Illustra come usare la classe [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) per creare un comando proxy che chiama un cmdlet esistente, ma limita il set di parametri disponibili.
Il comando proxy viene quindi aggiunto a uno stato sessione iniziale usato per creare uno spazio di esecuzione vincolato.
Ciò significa che l'utente può accedere alla funzionalità del cmdlet solo tramite il comando proxy.

**PowerShell01**

Illustra come creare uno spazio di esecuzione vincolato usando un oggetto [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx).

**PowerShell02**

Illustra come usare un pool di spazi di esecuzione per eseguire più comandi contemporaneamente.

## <a name="host-samples"></a>Esempi di host

**Host01**

Illustra come implementare un'applicazione host che usa un host personalizzato.
In questo esempio viene creato uno spazio di esecuzione che usa l'host personalizzato e quindi viene usata l'API [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) per eseguire uno script che chiama "exit".
L'applicazione host esamina l'output dello script e stampa i risultati.

**Host02**

Illustra come scrivere un'applicazione host che usa il runtime di Windows PowerShell insieme a un'implementazione host personalizzata.
L'applicazione host imposta le impostazioni cultura dell'host per la lingua tedesca, esegue il cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) e visualizza i risultati allo stesso modo di quando si usa pwrsh.exe e quindi stampa i dati e l'ora correnti in tedesco.

**Host03**

Illustra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi visualizza i risultati nella console.

**Host04**

Illustra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi visualizza i risultati nella console.
L'applicazione host supporta anche la visualizzazione di messaggi di richiesta che consentono all'utente di specificare più opzioni.

**Host05**

Illustra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi visualizza i risultati nella console.
L'applicazione host supporta anche le chiamate a computer remoti tramite i cmdlet [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) e [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212).

**Host06**

Illustra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi visualizza i risultati nella console.
Questo esempio usa inoltre le API del tokenizer per specificare il colore del testo immesso dall'utente.

## <a name="provider-samples"></a>Esempi di provider

**AccessDBProviderSample01**

Illustra come dichiarare una classe di provider che deriva direttamente dalla classe [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx).
È incluso solo per motivi di completezza.

**AccessDBProviderSample02**

Illustra come sovrascrivere i metodi [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) e [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) per il supporto alle chiamate ai cmdlet New-PSDrive e Remove-PSDrive.
La classe del provider in questo esempio deriva dalla classe [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx).

**AccessDBProviderSample03**

Illustra come sovrascrivere i metodi [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) e [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) per il supporto alle chiamate ai cmdlet Get-Item e Set-Item.
La classe del provider in questo esempio deriva dalla classe [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx).

**AccessDBProviderSample04**

Illustra come sovrascrivere i metodi contenitore per il supporto alle chiamate ai cmdlet Copy-Item, Get-ChildItem, New-Item e Remove-Item.
Questi metodi devono essere implementati quando l'archivio dati contiene elementi che sono contenitori.
Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune.
La classe del provider in questo esempio deriva dalla classe [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx).

**AccessDBProviderSample05**

Illustra come sovrascrivere i metodi contenitore per il supporto alle chiamate ai cmdlet Move-Item e Join-Path.
Questi metodi devono essere implementati quando l'utente deve spostare elementi all'interno di un contenitore e se l'archivio dati contiene contenitori annidati.
La classe del provider in questo esempio deriva dalla classe [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx).

**AccessDBProviderSample06**

Illustra come sovrascrivere i metodi contenuto per il supporto alle chiamate ai cmdlet Clear-Content, Get-Content e Set-Content.
Questi metodi devono essere implementati quando l'utente deve gestire il contenuto degli elementi nell'archivio dati.
La classe del provider in questo esempio deriva dalla classe [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) che implementa l'interfaccia [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx).