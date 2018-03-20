---
ms.date: 2017-08-23
keywords: powershell,cmdlet
title: usare la console di windows powershell basata sul web
ms.openlocfilehash: a6c9812253309ba1225141cfd48d0f1c8b8785b5
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="use-the-web-based-windows-powershell-console"></a>Usare la console di Windows PowerShell basata sul Web

Ultimo aggiornamento: 24 giugno 2013

Si applica a: Windows Server 2012 R2, Windows Server 2012

Accesso Web Windows PowerShell consente agli utenti di accedere a un sito Web protetto per usare sessioni, cmdlet e script di Windows PowerShell per la gestione di un computer remoto.

La console di Windows PowerShell viene eseguita in un Web browser e può pertanto essere aperta da una vasta gamma di dispositivi client. È possibile usare quasi tutti i dispositivi con un Web browser.

La console di Windows PowerShell basata sul Web è destinata a un computer remoto specificato dagli utenti durante il processo di accesso. 

Questo argomento descrive come accedere e iniziare a usare la console di Accesso Web Windows PowerShell basata sul Web.

Questo argomento non descrive come usare o eseguire i cmdlet o gli script di Windows PowerShell. Per informazioni su come usare Windows PowerShell e le risorse di script, vedere la sezione [Vedere anche](#see-also) alla fine di questo argomento.

## <a name="supported-browsers-and-client-devices"></a>Browser e dispositivi client supportati

Accesso Web Windows PowerShell supporta i browser Internet seguenti. Anche se i browser per dispositivi mobili non sono ufficialmente supportati, molti potrebbero essere in grado di eseguire la console di Windows PowerShell basata sul Web. Anche gli altri browser che accettano cookie, eseguono JavaScript e aprono i siti Web HTTPS dovrebbero funzionare, ma non sono stati testati ufficialmente.

### <a name="supported-desktop-computer-browsers"></a>Browser per computer desktop supportati

- Windows Internet Explorer per Microsoft Windows 8.0, 9.0, 10.0 e 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m per Windows
- Apple Safari 5.1.2 per Windows
- Apple Safari 5.1.2 per Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Dispositivi mobili e browser sottoposti ai test minimi

- Windows Phone 7 e 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)
- Apple Safari 5.0.1 per sistema operativo iPhone
- Sistema operativo Apple Safari per iPad 2 5.0.1

### <a name="browser-requirements"></a>Requisiti del browser

Per usare la console di Accesso Web Windows PowerShell basata sul Web, i browser devono:

- Consentire i cookie dal sito Web del gateway di Accesso Web Windows PowerShell.
- Sia in grado di aprire e leggere le pagine HTTPS.
- Aprire ed eseguire siti Web che usano JavaScript.

## <a name="signing-in-to-windows-powershell-web-access"></a>Connessione ad Accesso Web Windows PowerShell

L'amministratore di Accesso Web Windows PowerShell deve specificare all'utente l'URL corrispondente all'indirizzo del sito Web del gateway di Accesso Web Windows PowerShell dell'organizzazione.
Per impostazione predefinita, l'indirizzo di questo sito Web è *https://\<nome_server\>/pswa*.

Prima di accedere ad Accesso Web Windows PowerShell, assicurarsi di avere il nome o l'indirizzo IP del computer remoto da gestire.
È necessario essere un utente autorizzato nel computer remoto, che deve essere configurato per consentire la gestione remota.
Per altre informazioni sulla configurazione del computer per consentire la gestione remota, vedere [Abilitare e usare i comandi remoti in Windows PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting).

Il metodo di configurazione del computer più semplice per consentire la gestione remota consiste nell'eseguire il cmdlet **Enable-PSRemoting -force** nel computer, in una sessione di Windows PowerShell aperta con diritti utente elevati, ovvero **Esegui come amministratore**.

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Per connettersi ad Accesso Web Windows PowerShell

1. Aprire il sito Web Accesso Web Windows PowerShell in una finestra o una scheda del browser Internet.

1. Nella pagina di accesso di Accesso Web Windows PowerShell specificare il nome utente e la password di rete e il nome del computer che si vuole gestire e del quale si è un utente autorizzato. Se l'amministratore di Accesso Web Windows PowerShell ha specificato di usare un URI in un server del sito o un server proxy personalizzato invece di un nome computer, selezionare **URI connessione** nel campo **Tipo di connessione** e quindi specificare l'URI.

    > ![Nota](images/Note.jpeg) **Nota**:
    >
    > - Se il computer di destinazione fa parte di un gruppo di lavoro, usare la sintassi seguente per specificare il nome utente e accedere al computer: `<workgroup_name>\<user_name>`
    > - Se il computer di destinazione è il server gateway, è possibile specificare `localhost` nel campo Nome computer
    > - Se il computer di destinazione è il server gateway e il server gateway fa parte di un gruppo di lavoro, è necessario usare `<workgroup name>\<user_name>` nel campo Nome utente. È possibile usare `localhost` nel campo Nome computer.

1. La sezione **Impostazioni di connessione facoltative** è relativa ai requisiti di autorizzazione del computer remoto che si vuole gestire. Per altre informazioni sui parametri equivalenti alle impostazioni di connessione facoltative, vedere la guida del cmdlet [Enter-PSSession](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession).

    In genere, le credenziali che si usano per il passaggio attraverso il gateway di Accesso Web Windows PowerShell sono le stesse riconosciute dal computer remoto che si vuole gestire. Se tuttavia si preferisce usare credenziali diverse per gestire il computer remoto specificato nel passaggio 2, espandere la sezione **Impostazioni di connessione facoltative** e fornire le credenziali alternative. In caso contrario, andare al passaggio 6.

1. Se l'amministratore di Accesso Web Windows PowerShell ha creato una configurazione di sessione personalizzata per gli utenti di Accesso Web Windows PowerShell, digitare il nome della configurazione di sessione nel campo **Nome configurazione**. Per altre informazioni sulle configurazioni di sessione, vedere [about_Session_Configurations](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Mantenere il valore di **Tipo di autenticazione** impostato su **Predefinito**, a meno che l'amministratore di Accesso Web Windows PowerShell non abbia fornito istruzioni per procedere diversamente.

1. Fare clic su **Accedi**.

## <a name="signing-out-and-timing-out"></a>Disconnessione e timeout

Una qualsiasi delle operazioni seguenti causa la disconnessione dell'utente da una sessione di Windows PowerShell basata sul Web.

- Fare clic su **Disconnetti** nell'angolo in basso a destra della console. Solo Windows Server 2012

- Fare clic su **Salva** o **Esci** nell'angolo in basso a destra della console (solo Windows Server 2012 R2). Se si fa clic su **Salva**, la sessione di Accesso Web Windows PowerShell viene salvata e chiusa. È possibile riconnettersi alla sessione in un secondo momento. Quando si accede di nuovo ad Accesso Web Windows PowerShell, viene visualizzato un elenco delle sessioni salvate. È possibile selezionare una sessione salvata e riconnettersi o avviare una nuova sessione. Il numero massimo di sessioni aperte consentito agli utenti, sia salvate che attive, viene configurato dall'amministratore del gateway.

    Se si fa clic su **Esci**, la sessione di Accesso Web Windows PowerShell viene disconnessa senza essere salvata.

- Provare ad accedere per gestire un computer remoto diverso nella stessa sessione del browser o in una nuova scheda della stessa sessione del browser. Questo approccio non è applicabile se il server gateway esegue Windows Server 2012 R2. L'esecuzione di Accesso Web Windows PowerShell in Windows Server 2012 R2 consente più sessioni utente in nuove schede della stessa sessione del browser. Per altre informazioni su come usare più sessioni attive nello stesso computer, vedere Connessione a più computer di destinazione contemporaneamente. nella sezione [Limitazioni della console basata sul Web](#limitations-of-the-web-based-console) di questo argomento.

- 20 minuti di inattività della sessione. L'amministratore del gateway può personalizzare il periodo di timeout di inattività. Per altre informazioni, vedere [Gestione delle sessioni](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

    - Se si viene disconnessi da una sessione nella console basata sul Web a causa di un errore di rete o di un altro arresto o errore non pianificato e non perché la sessione è stata volutamente chiusa, la sessione di Accesso Web Windows PowerShell rimane in esecuzione e connessa al computer di destinazione, finché non sarà trascorso il periodo di timeout sul lato client. Per impostazione predefinita, questo periodo di timeout è di 20 minuti e viene configurato dall'amministratore del gateway. La sessione viene disconnessa trascorsi i 20 minuti predefiniti o dopo il periodo di timeout specificato dall'amministratore del gateway, a seconda del valore inferiore.

        Se il server gateway esegue Windows Server 2012 R2, Accesso Web Windows PowerShell consente agli utenti di riconnettersi alle sessioni salvate in un secondo momento, ma non si possono visualizzare le sessioni salvate o riconnettersi finché non sarà trascorso il periodo di timeout specificato dall'amministratore del gateway.

- Chiudere la finestra o la scheda del browser.

- Disattivare il dispositivo client in cui è in esecuzione il browser o disconnettersi dalla rete.

- Esecuzione del comando **Esci** nella console Web. Questo comando non funziona se la configurazione della sessione a cui si è connessi è configurata per supportare la modalità [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) o si trova in uno spazio di esecuzione con restrizioni.

Per accedere di nuovo, riaprire la pagina Web di Accesso Web Windows PowerShell ed eseguire l'accesso con la procedura descritta in [Connessione ad Accesso Web Windows PowerShell](#signing-in-to-windows-powershell-web-access) in questo argomento.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Differenze nella console di Windows PowerShell basata sul Web

Dopo l'accesso a Accesso Web Windows PowerShell, viene aperta una console di Windows PowerShell basata sul Web nella finestra o in una scheda del browser. La console è connessa al computer remoto specificato durante il processo di accesso, di conseguenza nella console possono essere usati solo i cmdlet o gli script di Windows PowerShell disponibili nel computer remoto. Questa sezione descrive altre limitazioni delle console di Accesso Web Windows PowerShell e le differenze tra le console di Accesso Web Windows PowerShell e la console di **PowerShell.exe** installata.

### <a name="functional-disparity-with-powershellexe"></a>Disparità funzionale con PowerShell.exe

Quasi tutte le funzionalità host di Windows PowerShell sono disponibili nella console di Accesso Web Windows PowerShell basata sul Web.

- Visualizzazioni di avanzamento annidate.

  Accesso Web Windows PowerShell presenta un'interfaccia utente grafica di avanzamento per i cmdlet, che segnala lo stato di avanzamento, visualizzando però solo le informazioni di primo livello.

- Modifica del colore di input.

  Il colore di input, sia primo piano che di sfondo, non può essere modificato. Lo stile dei messaggi di output, di avviso, dettagliati e di errore possono essere tutti gestiti con l'esecuzione di uno script.

- PSHostRawUserInterface.

  Accesso Web Windows PowerShell è implementato nella gestione remota di Windows PowerShell e usa uno spazio di esecuzione remoto. Accesso Web Windows PowerShell non implementa alcuni metodi in questa interfaccia, ad esempio, tutti i comandi che scrivono nella console di Windows. I comandi come **PowerTab** non funzionano in Accesso Web Windows PowerShell.

- Tasti funzione.

  Accesso Web Windows PowerShell non supporta alcuni tasti funzione, in molti casi perché i comandi sono riservati dal browser.

### <a name="unsupported-shortcut-keys"></a>Tasti di scelta rapida non supportati

Tasto funzione | Azione
-- | --
CTRL+C | In Accesso Web Windows PowerShell **CTRL+C** viene usato dal browser per copiare il contenuto. La console fornisce un pulsante **Annulla** e gli utenti possono anche usare **CTRL+Q** per annullare i comandi.
ALT+BARRA SPAZ.+E+L | Scorre il buffer dello schermo.
ALT+BARRA SPAZ.+E+F | Cerca il testo nel buffer dello schermo.
ALT+BARRA SPAZ.+E+K | Seleziona il testo da copiare dal buffer dello schermo.
ALT+BARRA SPAZ.+E+P | Incolla il contenuto degli Appunti nella console di Windows PowerShell.
ALT+BARRA SPAZ.+C | Chiude la console di Windows PowerShell.
CTRL+INTERR | Forza la chiusura della finestra di Windows PowerShell.
CTRL+HOME | Elimina dall'inizio della riga di comando corrente.
CTRL+FINE | Elimina fino alla fine della riga di comando.
F1 | Sposta il cursore di un carattere a destra nella riga di comando.
F2 | Crea un nuovo comando copiando l'ultimo comando fino al carattere digitato.
F3 | Completa la riga di comando con il contenuto dell'ultima riga di comando.
F4 | Elimina i caratteri dalla posizione del cursore.
F5 | Scorre all'indietro nella cronologia del comando. Per accedere ai comandi nella cronologia dei comandi in Accesso Web Windows PowerShell, fare clic sui pulsanti di scorrimento **Cronologia** disponibili nella console basata sul Web.
F7 | Seleziona in modo interattivo un comando dalla cronologia dei comandi.
F8 | Analizza la cronologia visualizzando i comandi che corrispondono al testo corrente.
F9 | Esegue un comando numerato specifico dalla cronologia.
PGSU | Esegue il primo comando nella cronologia.
PGGIÙ | Esegue l'ultimo comando nella cronologia.
ALT+F7 | Cancella l'elenco della cronologia dei comandi.

### <a name="limitations-of-the-web-based-console"></a>Limitazioni della console basata sul Web

- Doppio hop

    Se si prova a creare una nuova sessione o a usarla con Accesso Web Windows PowerShell, si potrebbe riscontrare una limitazione al doppio hop, ovvero la connessione a un secondo computer dalla prima connessione. Accesso Web Windows PowerShell usa uno spazio di esecuzione remoto e attualmente **PowerShell.exe** non consente di stabilire una connessione remota a un secondo computer da uno spazio di esecuzione remoto. Se si prova a connettersi a un secondo computer remoto da una connessione esistente usando il cmdlet **Enter-PSSession**, potrebbero essere generati diversi errori, ad esempio un messaggio simile a "Non è possibile ottenere risorse di rete".

    Per evitare errori relativi al doppio hop, l'amministratore deve configurare l'autenticazione CredSSP nell'ambiente di rete dell'organizzazione. Per altre informazioni sulla configurazione dell'autenticazione CredSSP, vedere il blog relativo a [CredSSP per la comunicazione remota con un secondo hop](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) nel sito Web Microsoft. È anche possibile fornire credenziali esplicite quando si vuole gestire un secondo computer remoto. È improbabile che le credenziali implicite consentano il secondo hop.

- Comunicazione remota

    Accesso Web Windows PowerShell usa e ha le stesse limitazioni di una sessione remota di Windows PowerShell. I comandi che chiamano direttamente le API della console di Windows, ad esempio quelle per gli editor basati su console o i programmi di menu basati su testo, non funzionano perché i comandi non leggono o scrivono su pipe standard di input, output e di errore. Di conseguenza, i comandi che avviano un file eseguibile, ad esempio **notepad.exe**, o che visualizzano un'interfaccia utente grafica, ad esempio `OpenGridView` o `ogv`, non funzionano. Questo comportamento influenza l'esperienza utente, perché sembra che Accesso Web Windows PowerShell non risponda al comando.

- Completamento tramite TAB

    Il completamento tramite tasto TAB non funziona in una configurazione di sessione con uno spazio di esecuzione con restrizioni o in modalità **NoLanguage**. Anche se gli amministratori possono configurare una sessione per supportare il completamento tramite tasto TAB, è sconsigliato per motivi di sicurezza, perché può esporre le informazioni seguenti a utenti non autorizzati.

    - Percorsi interni del file system

    - Cartelle condivise in computer interni

    - Variabili nello spazio di esecuzione

    - Tipi caricati o spazi dei nomi di .NET Framework

    - Variabili di ambiente

- Sessione **NoLanguage** o uno spazio di esecuzione con restrizioni

    Gli utenti connessi a una configurazione di sessione **NoLanguage** o a uno spazio di esecuzione con restrizioni in Accesso Web Windows PowerShell non possono eseguire il comando **Esci** per terminare la sessione. Per disconnettersi, gli utenti devono fare clic su **Disconnetti** nella pagina della console.

- Connessione a più computer di destinazione contemporaneamente.

    Se il server gateway esegue Windows Server 2012, Accesso Web Windows PowerShell consente solo una connessione a un computer remoto per ogni sessione del browser. Non consente agli utenti di accedere una sola volta e connettersi a più computer remoti usando schede separate del browser. Quando si apre una nuova scheda o una nuova finestra del browser, Accesso Web Windows PowerShell chiede di disconnettere la sessione corrente e avviare una nuova sessione, per potersi connettere al computer remoto nuovo o esistente. Se si vogliono stabilire due o più sessioni separate per computer remoti diversi, in Internet Explorer è disponibile una funzionalità che consente tuttavia di creare una nuova sessione. Per avviare una nuova sessione del browser in Internet Explorer, premere **ALT**, aprire il menu **File** e scegliere **Nuova sessione**. Aprire quindi il sito Web di Accesso Web Windows PowerShell nella nuova sessione ed eseguire l'accesso a un altro computer remoto.

    Quando il gateway di Accesso Web Windows PowerShell è in esecuzione in Windows Server 2012 R2, gli utenti possono aprire più connessioni a computer remoti in schede del browser diverse. Per aprire più connessioni a un computer remoto con la console di Windows PowerShell basata sul Web, verificare con l'amministratore del gateway di Accesso Web Windows PowerShell se questa funzionalità è supportata dal server gateway.

- Sessioni di Windows PowerShell persistenti (riconnessione).

    Dopo il timeout del gateway di Accesso Web Windows PowerShell, la connessione remota tra il gateway e il computer di destinazione viene chiusa. L'elaborazione degli eventuali cmdlet e script in corso viene arrestata. È consigliabile usare l'infrastruttura **-Job** di Windows PowerShell quando si eseguono attività di lunga durata, in modo da avviare i processi, disconnettersi dal computer e riconnettersi in seguito mantenendo i processi persistenti. Un altro vantaggio dell'uso dei cmdlet **-Job** è la possibilità di avviarli con Accesso Web Windows PowerShell, di disconnettersi e riconnettersi successivamente sia con Accesso Web Windows PowerShell che con un altro host, ad esempio Windows PowerShell Integrated Scripting Environment (ISE).

- Ridimensionamento della console.

    La finestra della console di **PowerShell.exe** può essere ridimensionata nei tre modi seguenti.

    - Trascinare e adattare le dimensioni della finestra della console con il mouse.

    - Modificare le proprietà di altezza e larghezza tramite un'interfaccia utente grafica per le proprietà della console.

    - Modificare l'altezza e la larghezza delle finestre della console con un cmdlet.

        La finestra della console per Accesso Web Windows PowerShell può essere configurata con i cmdlet, come indicato di seguito. Nell'esempio seguente un utente modifica la larghezza della console di Accesso Web Windows PowerShell in **20**.

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        Si può modificare l'altezza della console in modo simile.

        Altri esempi per personalizzare la visualizzazione della console sono disponibili nel [Blog del Team di Windows PowerShell](http://blogs.msdn.com/b/powershell/).

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento per i cmdlet di Windows PowerShell](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
- [Windows PowerShell su Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
- [Archivio di Script Center su Technet](http://gallery.technet.microsoft.com/scriptcenter)
- [Script Center: blog "Hey, Scripting Guy!"](https://technet.microsoft.com/scriptcenter)
- [Blog del team di Windows PowerShell](http://blogs.msdn.com/b/powershell/)
