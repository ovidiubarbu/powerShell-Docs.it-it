---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Novità di Windows PowerShell 5.0
ms.openlocfilehash: 08775c1767f1d9d18dafab39d188db152073e69d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417579"
---
# <a name="whats-new-in-windows-powershell-50"></a>Novità di Windows PowerShell 5.0

Windows PowerShell 5.0 include nuove funzionalità significative che ne estendono e migliorano l'uso e consentono di controllare e gestire gli ambienti Windows in modo più semplice e completo.

Windows PowerShell 5.0 è compatibile con le versioni precedenti. Cmdlet, provider, moduli, snap-in, script, funzioni e profili progettati per Windows PowerShell 4.0, Windows PowerShell 3.0 e Windows PowerShell 2.0 in genere funzionano in Windows PowerShell 5.0 senza modifiche.

## <a name="installing-windows-powershell"></a>Installazione di Windows PowerShell

Windows PowerShell 5.0 viene installato per impostazione predefinita in Windows Server 2016 Technical Preview e Windows 10.

Per installare Windows PowerShell 5.0 in Windows Server 2012 R2, Windows 8.1 Enterprise o Windows 8.1 Pro, scaricare e installare [Windows Management Framework 5.0](https://aka.ms/wmf5download). Prima di installare Windows Management Framework 5.0, leggere i dettagli sul download e soddisfare tutti i requisiti di sistema.

## <a name="in-this-topic"></a>Contenuto dell'argomento

- [Aggiornamenti di Windows PowerShell 4.0 DSC in KB 3000850](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Nuove funzionalità di Windows PowerShell 5.0](#new-features-in-windows-powershell-50)
- [Nuove funzionalità di Windows PowerShell 4.0](#new-features-in-windows-powershell-40)
- [Nuove funzionalità di Windows PowerShell 3.0](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Aggiornamenti di Windows PowerShell 4.0 nell'aggiornamento cumulativo di novembre 2014 (KB 3000850)

Molti aggiornamenti e miglioramenti per Windows PowerShell Desired State Configuration (DSC) in Windows PowerShell 4.0 sono disponibili nell'[aggiornamento cumulativo di novembre 2014 per Windows RT 8.1, Windows 8.1 e Windows Server 2012 R2](https://support.microsoft.com/kb/3000850/) (KB 3000850). È possibile determinare se l'aggiornamento KB 3000850 è installato nel sistema eseguendo `Get-Hotfix -Id KB3000850` in Windows PowerShell.

- Aggiornamenti per i cmdlet esistenti nel modulo [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx)
  - [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) è più veloce (soprattutto in ISE).
  - [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) ha un nuovo parametro, -UseExisting, che consente di riapplicare l'ultima configurazione applicata.
  - [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) -Force è stato corretto.
  - [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx) visualizza più informazioni utili sullo stato del motore.
  - [Test-DscConfiguration](https://technet.microsoft.com/library/dn407382.aspx) restituisce ora il nome del computer insieme a True o False.
  - [New-DscChecksum](https://technet.microsoft.com/library/dn521622.aspx) supporta ora i percorsi UNC.

- Nuovi cmdlet nel modulo [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx)
  - [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541(v=wps.630).aspx):  Esegue un controllo del server di pull su richiesta.
  - [Stop-DscConfiguration](https://technet.microsoft.com/library/mt143542(v=wps.630).aspx):  Arresta una configurazione già in esecuzione.
  - [Remove-DscConfigurationDocument](https://technet.microsoft.com/library/mt143544(v=wps.630).aspx):  Consente di rimuovere i documenti di configurazione nelle varie fasi (in sospeso, precedente o corrente).

- Miglioramenti del linguaggio
  - DependsOn supporta ora risorse composite.
  - DependsOn supporta ora numeri nei nomi di istanze delle risorse.
  - Le espressioni sui nodi con risultato vuoto non generano più errori.
  - È stato corretto un errore che si verifica se un'espressione sui nodi restituisce un valore vuoto.
  - Le configurazioni che chiamano configurazioni ora funzionano nella console di Windows PowerShell.

- Miglioramenti della modalità pull
  - La modalità pull supporta ora tutti i file ZIP.
  - **AllowModuleOverwrite** funziona ora correttamente.

- Miglioramenti della resilienza
  - La nuova proprietà **DebugMode** consente di ricaricare i moduli delle risorse.
  - Se si verifica un errore di configurazione, il file pending.mof non viene eliminato.
  - Gestione configurazione locale offre ora maggiore resilienza in caso di danneggiamento delle impostazioni di metaconfigurazione.

- Miglioramenti della diagnostica
  - Viene visualizzato un avviso quando Gestione configurazione locale imposta il timer su impostazioni diverse da quelle specificate.
  - I file di log degli errori contengono ora lo stack di chiamate per le risorse di Windows PowerShell.

- Miglioramenti della flessibilità
  - La risorsa LocalConfigurationManager ha una nuova proprietà **ActionAfterReboot**.
    - ContinueConfiguration (valore predefinito): Riprende automaticamente una configurazione dopo il riavvio di un nodo di destinazione.
    - StopConfiguration: Non riprende automaticamente una configurazione dopo il riavvio di un nodo.
  - L'esecuzione di un controllo di coerenza può ora avvenire più spesso di un'operazione PULL o viceversa.
  - Supporto per il controllo delle versioni:  DSC ora può riconoscere un documento che è stato generato in un client più recente (incluso in [WMF 5.0](https://aka.ms/wmf5download)).

- Miglioramenti di prevenzione degli errori
  - La versione del modulo viene ora imposta prima dell'applicazione di una configurazione.
  - **DebugPreference** viene ora impostato correttamente per le chiamate di Get-, Set- o Test-TargetResource.

- Miglioramenti della gestione delle credenziali
  - Viene ora usato un certificato, se vengono specificate sia la proprietà **Certificate** che **PSDscAllowPlainTextPassword**.
  - Le credenziali vengono decrittografate, anche per Get-TargetResource.
  - Le credenziali della metaconfigurazione vengono crittografate e decrittografate.
  - Le credenziali PSCredential vengono ora decrittografate quando sono incluse in un oggetto incorporato.

- Miglioramenti apportati alle risorse predefinite
  - Risorsa Package
    - Non installa più il pacchetto errato (da origini locali o Web).
    - Ora supporta HTTPS.
  - È ora disponibile il supporto di HTTPS nella [risorsa Package](https://technet.microsoft.com/library/dn282132.aspx).
  - La [risorsa Archive](https://technet.microsoft.com/library/dn249917.aspx) ora supporta le credenziali.

## <a name="new-features-in-windows-powershell-50"></a>Nuove funzionalità di Windows PowerShell 5.0

- [Nuove funzionalità di Windows PowerShell](#new-features-in-windows-powershell)
- [Nuove funzionalità di Windows PowerShell Desired State Configuration](#new-features-in-windows-powershell-desired-state-configuration)
- [Nuove funzionalità di Windows PowerShell ISE](#new-features-in-windows-powershell-ise)
- [Nuove funzionalità dei servizi Web di Windows PowerShell](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Correzioni di bug importanti in Windows PowerShell 5.0](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Nuove funzionalità di Windows PowerShell

- A partire da Windows PowerShell 5.0 è possibile sviluppare usando le classi, con sintassi e semantica formali simili ad altri linguaggi di programmazione orientati agli oggetti. Le parole chiave **Class**, **Enum** ed altre sono state aggiunte al linguaggio di Windows PowerShell per supportare la nuova funzionalità. Per altre informazioni sull'utilizzo delle classi, vedere about_Classes.

- Windows PowerShell 5.0 introduce un nuovo flusso di informazioni strutturate per trasmettere dati strutturati tra uno script e i relativi chiamanti o l'ambiente di host. È ora possibile usare Write-Host per immettere l'output nel flusso di informazioni. I flussi di informazioni funzionano anche per PowerShell.Streams, processi, processi pianificati e flussi di lavoro. Le funzionalità seguenti supportano il flusso di informazioni.
  - Un nuovo cmdlet Write-Information che consente di specificare in che modo Windows PowerShell gestisce i dati del flusso di informazioni per un comando. Write-Host è un wrapper per Write-Information. Write-Information è anche un'attività di flusso di lavoro supportata.
  - Due nuovi parametri comuni, InformationVariable e InformationAction, consentono di determinare come vengono visualizzati i flussi di informazioni da un comando. I valori validi per InformationAction sono SilentlyContinue, Stop, Continue, Inquire, Ignore o Suspend. SilentlyContinue è il valore predefinito. InformationVariable specifica una stringa come nome di una variabile in cui si vogliono salvare i dati Write-Host da un comando.
  - Una nuova variabile di preferenza, InformationPreference, che specifica la preferenza predefinita per i dati del flusso di informazioni in una sessione di Windows PowerShell. Il valore predefinito è SilentlyContinue.
  - Sono stati aggiunti due nuovi parametri comuni per il flusso di lavoro, PSInformation e InformationAction.
  - Quando si usa il comando Format-Table, le colonne della tabella vengono ora formattate automaticamente valutando i primi 300 ms di dati che passano attraverso il flusso.

- In collaborazione con [Microsoft Research](https://research.microsoft.com/) è stato aggiunto il nuovo cmdlet ConvertFrom-String. ConvertFrom-String consente di estrarre e analizzare oggetti strutturati dal contenuto di stringhe di testo. Per altre informazioni, vedere ConvertFrom-String.
- Il nuovo cmdlet Convert-String formatta automaticamente il testo in base a un esempio fornito nel parametro -Example.
- Il nuovo modulo Microsoft.PowerShell.Archive include cmdlet che consentono di comprimere file e cartelle in file di archivio (noti anche come file ZIP), estrarre file da file ZIP esistenti e aggiornare i file ZIP con le versioni più recenti dei file compressi al loro interno.
- Il nuovo modulo PackageManagement consente di individuare e installare pacchetti software su Internet. Il modulo PackageManagement (precedentemente noto come OneGet) è un modulo di gestione, o multiplexer, di gestori di pacchetti esistenti, noti anche come provider di pacchetti, che riunisce la gestione dei pacchetti di Windows in una singola interfaccia di Windows PowerShell.
- Il nuovo modulo PowerShellGet consente di trovare, installare, pubblicare e aggiornare i moduli e le risorse DSC in [PowerShell Gallery](https://www.powershellgallery.com/) o in un repository di moduli interno che è possibile configurare eseguendo il cmdlet Register-PSRepository.
- È stata aggiunta una nuova parola chiave del linguaggio, **Hidden**, per specificare che un membro (una proprietà o un metodo) non viene visualizzato per impostazione predefinita nei risultati di Get-Member (a meno che non si aggiunga il parametro -Force). Anche le proprietà o i metodi contrassegnati come nascosti non vengono visualizzati nei risultati di IntelliSense, a meno che non ci si trovi in un contesto in cui il membro deve essere visibile. Ad esempio, la variabile automatica $This dovrebbe visualizzare i membri nascosti nel metodo della classe.
- I cmdlet New-Item, Remove-Item e Get-ChildItem sono stati migliorati per supportare la creazione e gestione di [collegamenti simbolici](https://en.wikipedia.org/wiki/Symbolic_link). Il parametro **-ItemType** per New-Item accetta il nuovo valore **SymbolicLink**. Per creare collegamenti simbolici, è ora sufficiente una sola riga con il cmdlet New-Item.
- Get-ChildItem include ora il nuovo parametro -Depth da usare con il parametro -Recurse per limitare la ricorsione. Ad esempio, Get-ChildItem -Recurse -Depth 2 restituisce risultati dalla cartella corrente, da tutte le cartelle figlio all'interno della cartella corrente e da tutte le cartelle all'interno delle cartelle figlio.
- Copy-Item consente ora di copiare file o cartelle da una sessione di Windows PowerShell a un'altra. Ciò significa che è possibile copiare i file in sessioni connesse a computer remoti, inclusi i computer che eseguono [Nano Server](https://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx) e quindi non hanno altre interfacce. Per copiare file, specificare gli ID di PSSession come valore per i nuovi parametri -FromSession e -ToSession e aggiungere -Path e -Destination per specificare rispettivamente il percorso e la destinazione. Ad esempio, Copy-Item -Path c:\\file.txt -ToSession $s -Destination d:\\cartellaDestinazione.
- La funzionalità di trascrizione di Windows PowerShell è stata migliorata per consentirne l'applicazione a tutte le applicazioni di hosting, ad esempio, Windows PowerShell ISE, e non solo all'host della console, **powershell.exe**. Le opzioni per la trascrizione, inclusa l'abilitazione di una trascrizione a livello di sistema, possono essere configurate abilitando l'impostazione di Criteri di gruppo **Attiva trascrizione di PowerShell** in Modelli amministrativi/Componenti di Windows/Windows PowerShell.
- Una nuova funzionalità di traccia dettagliata degli script consente di monitorare e analizzare nel dettaglio l'uso degli script di Windows PowerShell in un sistema. Dopo aver abilitato la traccia dettagliata degli script, Windows PowerShell registra tutti i blocchi di script nel registro eventi ETW (Event Tracing for Windows), **Microsoft-Windows-PowerShell/Operational**.
- A partire da Windows PowerShell 5.0, i nuovi cmdlet CMS (Cryptographic Message Syntax) supportano la crittografia e la decrittografia del contenuto con il formato standard IETF per la protezione crittografica dei messaggi, come documentato in [RFC5652](https://tools.ietf.org/html/rfc5652). I cmdlet Get-CmsMessage, Protect-CmsMessage e Unprotect-CmsMessage sono stati aggiunti al modulo [Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh849807.aspx).
- I nuovi cmdlet nel modulo [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx), Get-Runspace, Debug-Runspace, Get-RunspaceDebug, Enable-RunspaceDebug e Disable-RunspaceDebug, consentono di impostare le opzioni di debug in uno spazio di esecuzione e di avviare e arrestare il debug in uno spazio di esecuzione. Per eseguire il debug di spazi di esecuzione arbitrari, ovvero gli spazi di esecuzione che non corrispondono allo spazio di esecuzione predefinito per una console di Windows PowerShell o una sessione di Windows PowerShell ISE, Windows PowerShell consente di impostare punti di interruzione in uno script e fare in modo che i punti di interruzione aggiunti interrompano l'esecuzione dello script fino a quando non si collega un debugger per eseguire il debug dello script dello spazio di esecuzione. È stato aggiunto il supporto del debug annidato per gli spazi di esecuzione arbitrari al debugger di script di Windows PowerShell per gli spazi di esecuzione.
- È stato aggiunto il nuovo cmdlet Format-Hex al modulo [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx). Format-Hex consente di visualizzare dati di testo o binari in formato esadecimale.
- Sono stati aggiunti i cmdlet Get-Clipboard e Set-Clipboard al modulo [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx). Questi cmdlet semplificano il trasferimento di contenuto verso e da una sessione di Windows PowerShell. I cmdlet Clipboard supportano immagini, file audio, elenchi di file e testo.
- È stato aggiunto il nuovo cmdlet Clear-RecycleBin nel modulo [Microsoft.PowerShell.Management](https://technet.microsoft.com/library/hh849827(v=wps.640).aspx). Questo cmdlet svuota il Cestino per un'unità fissa, che include le unità esterne. Per impostazione predefinita, viene richiesto di confermare il comando Clear-RecycleBin, perché la proprietà ConfirmImpact del cmdlet è impostata su ConfirmImpact.High.
- Il nuovo cmdlet New-TemporaryFile consente di creare un file temporaneo durante la creazione dello script. Per impostazione predefinita, il nuovo file temporaneo viene creato in ```C:\Users\<user name>\AppData\Local\Temp```.
- Nei cmdlet Out-File, Add-Content e Set-Content è ora disponibile il nuovo parametro -NoNewline che omette una nuova riga dopo l'output.
- Il cmdlet New-Guid sfrutta la classe Guid di .NET Framework per generare un GUID, un'opzione utile durante la scrittura di script o risorse DSC.
- Dato che le informazioni sulla versione di un file possono essere fuorvianti, in particolare dopo l'applicazione di una patch a un file, sono disponibili le nuove proprietà di script FileVersionRaw e ProductVersionRaw per gli oggetti FileInfo. Ad esempio, è possibile eseguire il comando seguente per visualizzare i valori di queste proprietà per powershell.exe, in cui $pid contiene l'ID di processo per una sessione di Windows PowerShell in esecuzione:  ```Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force```
- I nuovi cmdlet Enter-PSHostProcess ed Exit-PSHostProcess consentono di eseguire il debug di script di Windows PowerShell in processi separati dal processo corrente in esecuzione nella console di Windows PowerShell. Eseguire Enter-PSHostProcess per entrare in un processo con un ID specifico, o collegarsi al processo, quindi eseguire Get-Runspace per restituire gli spazi di esecuzione attivi all'interno del processo. Eseguire Exit-PSHostProcess per scollegarsi dal processo dopo aver terminato il debug dello script all'interno del processo.
- È stato aggiunto il nuovo cmdlet Wait-Debugger al modulo [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx). È possibile eseguire Wait-Debugger per interrompere uno script nel debugger prima di eseguire l'istruzione successiva nello script.
- Il debugger del flusso di lavoro di Windows PowerShell supporta ora il completamento dei comandi o tramite tasto TAB ed è possibile eseguire il debug di funzioni del flusso di lavoro annidate. È ora possibile premere **CTRL+INTERR** per accedere al debugger in uno script in esecuzione, sia in sessioni locali che remote, e in uno script del flusso di lavoro.
- È stato aggiunto il cmdlet Debug-Job al modulo [Microsoft.PowerShell.Core](https://technet.microsoft.com/library/hh849695.aspx) per eseguire il debug di script di processi in esecuzione per il flusso di lavoro di Windows PowerShell, processi in background e processi in esecuzione in sessioni remote.
- È stato aggiunto il nuovo stato AtBreakpoint per i processi di Windows PowerShell. Lo stato AtBreakpoint si applica quando un processo esegue uno script che include punti di interruzione e lo script raggiunge un punto di interruzione. Quando un processo viene interrotto in corrispondenza di un punto di interruzione di debug, è necessario eseguire il debug del processo tramite il cmdlet Debug-Job.
- Windows PowerShell 5.0 implementa il supporto per più versioni di un singolo modulo di Windows PowerShell nella stessa cartella in $PSModulePath. È stata aggiunta la proprietà RequiredVersion alla classe ModuleSpecification per facilitare il recupero della versione desiderata di un modulo. Questa proprietà e la proprietà ModuleVersion si escludono a vicenda. La proprietà RequiredVersion è ora supportata come parte del valore del parametro FullyQualifiedName dei cmdlet Get-Module, Import-Module e Remove-Module.
- È ora possibile eseguire la convalida della versione del modulo eseguendo il cmdlet Test-ModuleManifest.
- I risultati del cmdlet Get-Command includono ora una colonna Version. È stata aggiunta una nuova proprietà Version alla classe CommandInfo. Get-Command mostra i comandi da più versioni dello stesso modulo. La proprietà Version è inclusa anche nelle classi derivate di CmdletInfo: CmdletInfo e ApplicationInfo.
- Get-Command include il nuovo parametro -ShowCommandInfo, che restituisce informazioni ShowCommand in forma di PSObjects. Questa funzionalità è particolarmente utile quando si esegue Show-Command in Windows PowerShell ISE usando la comunicazione remota di Windows PowerShell. Il parametro -ShowCommandInfo sostituisce la funzione Get-SerializedCommand esistente nel modulo Microsoft.PowerShell.Utility, ma lo script Get-SerializedCommand è ancora disponibile per il supporto di script di livello inferiore.
- Il nuovo cmdlet Get-ItemPropertyValue consente di ottenere il valore di una proprietà senza usare la notazione del punto. Ad esempio, nelle versioni precedenti di Windows PowerShell è possibile eseguire il comando seguente per ottenere il valore della proprietà Application Base della chiave del Registro di sistema PowerShellEngine: **(Get-ItemProperty -Path HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine -Name ApplicationBase).ApplicationBase**. A partire da Windows PowerShell 5.0 è possibile eseguire **Get-ItemPropertyValue -Path HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine -Name ApplicationBase**.
- La console di Windows PowerShell usa ora la colorazione della sintassi, come in Windows PowerShell ISE.
- Il nuovo modulo NetworkSwitch contiene cmdlet che consentono di applicare la configurazione di commutatore, LAN virtuale (VLAN) e porte del commutatore di rete di livello 2 di base ai commutatori di rete con certificazione per il logo di Windows Server 2012 R2.
- È stato aggiunto il parametro FullyQualifiedName ai cmdlet Import-Module e Remove-Module per supportare l'archiviazione di più versioni di un singolo modulo.
- Per i cmdlet Save-Help, Update-Help, Import-PSSession, Export-PSSession e Get-Command è disponibile il nuovo parametro FullyQualifiedModule di tipo ModuleSpecification. Aggiungere questo parametro per specificare un modulo usando il nome completo.
- Il valore di **$PSVersionTable.PSVersion** è stato aggiornato alla versione 5.0.
- WMF 5.0 (PowerShell 5.0) include il modulo **Pester**.  Pester è un framework di testing unità per PowerShell. Offre alcune parole chiave di semplice utilizzo che consentono di creare test per gli script.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Nuove funzionalità di Windows PowerShell Desired State Configuration

- I miglioramenti del linguaggio di Windows PowerShell consentono di usare classi per definire risorse di Windows PowerShell Desired State Configuration (DSC). Import-DscResource è ora una parola chiave dinamica. Windows PowerShell analizza il modulo radice del modulo specificato alla ricerca delle classi che contengono l'attributo DscResource. È ora possibile usare classi per definire le risorse DSC, senza che sia richiesto un file MOF o una sottocartella DSCResource nella cartella del modulo. Un file di modulo di Windows PowerShell può contenere più classi di risorse DSC.
- È stato aggiunto il nuovo parametro ThrottleLimit per i cmdlet seguenti nel modulo PSDesiredStateConfiguration. Aggiungere il parametro ThrottleLimit per specificare il numero di computer o dispositivi di destinazione a cui si vuole applicare il comando contemporaneamente.
  - Get-DscConfiguration
  - Get-DscConfigurationStatus
  - Get-DscLocalConfigurationManager
  - Restore-DscConfiguration
  - Test-DscConfiguration
  - Compare-DscConfiguration
  - Publish-DscConfiguration
  - Set-DscLocalConfigurationManager
  - Start-DscConfiguration
  - Update-DscConfiguration
- Grazie ai report di errori DSC centralizzati, le informazioni complete sugli errori non vengono salvate solo nel registro eventi, ma possono essere inviate a una posizione centrale per analisi successive. È possibile usare questa posizione centrale per archiviare gli errori di configurazione DSC che si sono verificati per qualsiasi server nell'ambiente. Dopo aver definito il server di report nella metaconfigurazione, tutti gli errori vengono inviati al server di report e quindi archiviati in un database. È possibile configurare questa funzionalità indipendentemente dal fatto che un nodo di destinazione sia configurato o meno per il pull delle configurazioni da un server di pull.
- I miglioramenti di Windows PowerShell ISE facilitano la creazione di risorse DSC. È ora possibile eseguire le operazioni seguenti.
  - Elencare tutte le risorse DSC all'interno di un blocco **configuration** o **node** premendo **CTRL+BARRA SPAZIATRICE** in una riga vuota all'interno del blocco.
  - Usare il completamento automatico per le proprietà della risorsa di tipo **enumeration**.
  - Completamento automatico per la proprietà **DependsOn** della risorsa DSC, in base alle altre istanze della risorsa nella configurazione.
  - Usare il completamento tramite TAB migliorato per i valori delle proprietà della risorsa.
- Un utente può ora eseguire una risorsa con un set di credenziali specificate aggiungendo l'attributo **PSDscRunAsCredential** a un blocco Node. Ad esempio, PSDscRunAsCredential = Get-Credential Contoso\\DscUser. Questa funzionalità è utile per la creazione di configurazioni che eseguono Windows Installer e i programmi di installazione eseguibili, accedono all'hive del Registro di sistema per utente o eseguono altre attività all'esterno del contesto utente corrente.
- È stato aggiunto il supporto di 32 bit (x86) per la parola chiave **Configuration**.
- Windows PowerShell include ora il supporto della Guida personalizzata per le configurazioni DSC, definito aggiungendo \[CmdletBinding()] alla funzione di configurazione generata.
- Il nuovo attributo **DscLocalConfigurationManager** definisce un blocco di configurazione come metaconfigurazione, usata per configurare Gestione configurazione locale DSC. Questo attributo limita una configurazione ai soli elementi per configurare Gestione configurazione locale DSC. Durante l'elaborazione, questa configurazione genera un file \*.meta.mof che viene poi inviato ai nodi di destinazione appropriati tramite il cmdlet Set-DscLocalConfigurationManager.
- Le configurazioni parziali sono ora consentite in Windows PowerShell 5.0. È possibile recapitare i documenti di configurazione a un nodo in frammenti. Affinché un nodo possa ricevere più frammenti di un documento di configurazione, è necessario innanzitutto impostare Gestione configurazione locale del nodo in modo da specificare i frammenti previsti
- La sincronizzazione tra computer è una novità di DSC in Windows PowerShell 5.0. Grazie alle risorse predefinite WaitFor\* (**WaitForAll**, **WaitForAny** e **WaitForSome**), è ora possibile specificare le dipendenze tra i computer durante le esecuzioni della configurazione, senza orchestrazione esterna. Queste risorse consentono la sincronizzazione tra nodi tramite connessioni CIM sul protocollo WS-Man. Una configurazione può attendere la modifica dello stato di una risorsa specifica di un altro computer.
- La nuova funzionalità di sicurezza con delega JEA (Just Enough Administration) si basa su DSC e gli spazi di esecuzione limitati di Windows PowerShell per proteggere le aziende da perdite di dati o compromissioni causate dai dipendenti, sia intenzionalmente che non. Per altre informazioni su JEA, inclusa la posizione da cui è possibile scaricare la risorsa xJEA DSC, vedere il post di blog di [presentazione dei dettagli di JEA (Just Enough Administration)](https://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx).
- Sono stati aggiungi i nuovi cmdlet seguenti al modulo PSDesiredStateConfiguration.
  - Il nuovo cmdlet Get-DscConfigurationStatus ottiene informazioni generali sullo stato di configurazione da un nodo di destinazione. È possibile ottenere lo stato dell'ultima configurazione o di tutte.
  - Il nuovo cmdlet Compare-DscConfiguration confronta una configurazione specificata con lo stato effettivo di uno o più nodi di destinazione.
  - Il nuovo cmdlet Publish-DscConfiguration copia un file di configurazione con estensione mof in un nodo di destinazione, ma non applica la configurazione. La configurazione viene applicata durante il passaggio di controllo della coerenza successivo o quando si esegue il cmdlet Update-DscConfiguration.
  - Il nuovo cmdlet Test-DscConfiguration consente di verificare che una configurazione risultante corrisponda alla configurazione desiderata e restituisce True se la configurazione corrisponde alla configurazione desiderata o False se la configurazione effettiva non corrisponde alla configurazione desiderata.
  - Il nuovo cmdlet Update-DscConfiguration forza l'elaborazione di una configurazione. Se Gestione configurazione locale è in modalità pull, il cmdlet recupera la configurazione dal server di pull prima di applicarla.

### <a name="new-features-in-windows-powershell-ise"></a>Nuove funzionalità di Windows PowerShell ISE

- È ora possibile modificare script e file remoti di Windows PowerShell in una copia locale di Windows PowerShell ISE eseguendo Enter-PSSession per avviare una sessione remota nel computer in cui sono archiviati i file da modificare e quindi eseguendo **PSEdit \<percorso e nome file nel computer remoto\>** . Questa funzionalità semplifica la modifica dei file di Windows PowerShell archiviati nell'opzione di installazione Server Core di Windows Server, in cui non è possibile eseguire Windows PowerShell ISE.
- Il cmdlet Start-Transcript è ora supportato in Windows PowerShell ISE.
- È ora possibile eseguire il debug di script remoti in Windows PowerShell ISE.
- Il nuovo comando di menu **Interrompi tutto** (CTRL+B) consente di interrompere l'esecuzione nel debugger sia per script in esecuzione in locale che in remoto.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Nuove funzionalità dei servizi Web di Windows PowerShell (Estensione IIS OData di gestione)

- A partire da Windows PowerShell 5.0, è possibile generare un set di cmdlet di Windows PowerShell basato sulle funzionalità esposte da un determinato endpoint OData eseguendo il cmdlet Export-ODataEndpointProxy, disponibile nel nuovo modulo [Microsoft.PowerShell.OdataUtils](https://technet.microsoft.com/library/dn818507(v=wps.640).aspx).

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Correzioni di bug importanti in Windows PowerShell 5.0

- Windows PowerShell 5.0 include una nuova implementazione di COM, che offre miglioramenti significativi delle prestazioni quando si lavora con gli oggetti COM. Per una dimostrazione video dell'effetto, vedere [Com_Perf_Improvements](https://1drv.ms/1qu3UPZ).
- Miglioramenti significativi delle prestazioni sono stati introdotti per il primo completamento tramite tasto TAB in una sessione di Windows PowerShell, con una riduzione del tempo di completamento di quasi 500 ms.

## <a name="new-features-in-windows-powershell-40"></a>Nuove funzionalità di Windows PowerShell 4.0

Windows PowerShell 4.0 è compatibile con le versioni precedenti. Cmdlet, provider, moduli, snap-in, script, funzioni e profili progettati per Windows PowerShell 3.0 e Windows PowerShell 2.0 funzionano in Windows PowerShell 4.0 senza modifiche.

Windows PowerShell 4.0 viene installato per impostazione predefinita in Windows 8.1 e Windows Server 2012 R2. Per installare Windows PowerShell 4.0 in Windows 7 con SP1 o Windows Server 2008 R2, scaricare e installare [Windows Management Framework 4.0](https://www.microsoft.com/download/details.aspx?id=40855). Prima di installare Windows Management Framework 4.0, assicurarsi di leggere i dettagli sul download e di soddisfare tutti i requisiti di sistema.

- [Nuove funzionalità di Windows PowerShell](#new-features-in-windows-powershell-1)
- [Nuove funzionalità di Windows PowerShell ISE (Integrated Scripting Environment)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Nuove funzionalità del flusso di lavoro di Windows PowerShell](#new-features-in-windows-powershell-workflow)
- [Nuove funzionalità dei servizi Web di Windows PowerShell](#new-features-in-windows-powershell-web-services)
- [Nuove funzionalità di Accesso Web Windows PowerShell](#new-features-in-windows-powershell-web-access)
- [Correzioni di bug importanti in Windows PowerShell 4.0](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0 include le nuove funzionalità seguenti.

### <a name="a-namenew-features-in-windows-powershell-1-new-features-in-windows-powershell"></a><a name="new-features-in-windows-powershell-1" />Nuove funzionalità di Windows PowerShell

- **Windows PowerShell Desired State Configuration** (DSC) è un nuovo sistema di gestione di Windows PowerShell 4.0 che consente di distribuire e gestire dati di configurazione per i servizi software e per l'ambiente in cui vengono eseguiti. Per altre informazioni, vedere [Introduzione a Windows PowerShell DSC (Desired State Configuration)](https://technet.microsoft.com/library/c134aa32-b085-4656-9a89-955d8ff768d0).
- **Save-Help** consente ora di salvare la Guida per i moduli installati in computer remoti. È possibile usare Save-Help per scaricare la Guida sui moduli da un client connesso a Internet (in cui non sono necessariamente installati tutti i moduli per cui si vogliono informazioni) e quindi copiare la Guida salvata in una cartella condivisa remota o in un computer remoto privo di accesso a Internet.
- Il debugger di Windows PowerShell è stato migliorato per consentire il debug dei flussi di lavoro di Windows PowerShell oltre che degli script in esecuzione in computer remoti. Il debug dei flussi di lavoro di Windows PowerShell può ora essere eseguito a livello di script dalla riga di comando di Windows PowerShell o da Windows PowerShell ISE. È ora possibile eseguire il debug degli script di Windows PowerShell e dei relativi flussi di lavoro con le sessioni remote. Le sessioni di debug remoto vengono conservate quando le sessioni remote di Windows PowerShell vengono disconnesse e in seguito riconnesse.
- Il parametro **RunNow** di **Register-ScheduledJob** e **Set-ScheduledJob** elimina la necessità di impostare una data e un'ora di inizio immediate per i processi tramite il parametro **Trigger**.
- **Invoke-RestMethod** e **Invoke-WebRequest** consentono ora di impostare tutte le intestazioni con il parametro Headers. Anche se esiste da sempre, questo è uno dei numerosi parametri per i cmdlet Web che generavano eccezioni o errori.
- **Get-Module** include il nuovo parametro **FullyQualifiedName** di tipo **ModuleSpecification\[]** . Il parametro **FullyQualifiedName** di Get-Module consente ora di specificare un modulo tramite il relativo nome, la versione e, facoltativamente, il GUID.
- L'impostazione predefinita dei criteri di esecuzione in Windows Server 2012 R2 è **RemoteSigned**. In Windows 8.1 l'impostazione predefinita non viene modificata.
- A partire da Windows PowerShell 4.0, è supportata la chiamata al metodo con i nomi di metodo dinamici. È possibile usare una variabile per archiviare il nome di un metodo e quindi richiamarlo dinamicamente con una chiamata alla variabile.
- I processi asincroni del flusso di lavoro non vengono più eliminati una volta trascorso il periodo di timeout specificato dal parametro comune del flusso di lavoro **PSElapsedTimeoutSec**.
- È stato aggiunto il nuovo parametro **RepeatIndefinitely** ai cmdlet **New-JobTrigger** e **Set-JobTrigger**. In questo modo non è più necessario specificare un valore **TimeSpan.MaxValue** per il parametro **RepetitionDuration** per eseguire un processo pianificato ripetutamente per un periodo di tempo indefinito.
- È stato aggiunto il parametro **Passthru** ai cmdlet **Enable-JobTrigger** e **Disable-JobTrigger**. Questo parametro visualizza tutti gli oggetti creati o modificati dal comando.
- I nomi dei parametri per specificare un gruppo di lavoro nei cmdlet **Add-Computer** e **Remove-Computer** sono ora coerenti. Entrambi i cmdlet usano ora il parametro **WorkgroupName**.
- È stato aggiunto il nuovo parametro comune **PipelineVariable**, che consente di salvare i risultati di un comando (o di parte di esso) inviato tramite pipe come variabile che può quindi essere passata attraverso il resto della pipeline.
- È ora supportato il filtro delle raccolte tramite la sintassi di un metodo. Questo significa che è possibile filtrare una raccolta di oggetti usando una sintassi semplificata, simile a quella di Where() o Where-Object, formattata come una chiamata a metodo. Di seguito viene riportato un esempio. (Get-Process).where({$_.Name -match 'powershell'})
- Il cmdlet **Get-Process** include ora il nuovo parametro opzionale **IncludeUserName**.
- È stato aggiunto il nuovo cmdlet **Get-FileHash**, che restituisce l'hash di un file specificato in uno dei diversi formati disponibili.
- In Windows PowerShell 4.0, se un modulo usa la chiave **DefaultCommandPrefix** nel manifesto o se l'utente importa un modulo con il parametro **Prefix**, la proprietà **ExportedCommands** del modulo mostra i comandi nel modulo con il prefisso. I nomi dei comandi eseguiti usando la sintassi qualificata di modulo ModuleName\\CommandName devono includere il prefisso.
- Il valore di **$PSVersionTable.PSVersion** è stato aggiornato alla versione 4.0.
- Il comportamento dell'operatore **Where()** è cambiato. L'accettazione di un'espressione stringa nel formato `"Property -CompareOperator Value"` in `Collection.Where('property -match name')` non è più supportata. Tuttavia, l'operatore **Where()** accetta espressioni stringa nel formato di un blocco di script. Questa funzionalità è ancora supportata.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Nuove funzionalità di Windows PowerShell ISE (Integrated Scripting Environment)

- Windows PowerShell ISE supporta il debug del flusso di lavoro di Windows PowerShell e il debug degli script remoti.
- Per i provider e le configurazioni del servizio Windows PowerShell Desired State Configuration è stato aggiunto il supporto di IntelliSense.

### <a name="new-features-in-windows-powershell-workflow"></a>Nuove funzionalità del flusso di lavoro di Windows PowerShell

- È stato aggiunto il supporto del nuovo parametro comune **PipelineVariable** nel contesto delle pipeline iterative, ad esempio quelle usate da System Center Orchestrator, ossia le pipeline che eseguono i comandi semplicemente da sinistra a destra, a differenza dell'esecuzione frammista tramite flusso.
- L'associazione di parametri è stata sensibilmente migliorata e ora funziona all'esterno di scenari con completamento tramite TAB, ad esempio con comandi che non esistono nello spazio di esecuzione corrente.
- Al flusso di lavoro di Windows PowerShell è stato aggiunto il supporto per le attività del contenitore personalizzato. Se un parametro di attività è di tipo **Activity**, **Activity\[]** o è una raccolta generica di attività e se l'utente ha specificato un blocco di script come argomento, il flusso di lavoro di Windows PowerShell converte il blocco di script in XAML, come in una normale compilazione da script a flusso di lavoro di Windows PowerShell.
- Dopo un arresto anomalo del sistema, il flusso di lavoro di Windows PowerShell si riconnette automaticamente ai nodi gestiti.
- È ora possibile limitare le istruzioni di attività **Foreach -Parallel** tramite la proprietà **ThrottleLimit**.
- Il parametro comune **ErrorAction** ha un nuovo valore valido, **Suspend**, riservato esclusivamente ai flussi di lavoro.
- Un endpoint del flusso di lavoro viene ora automaticamente chiuso se non ci sono sessioni attive, processi in corso e in sospeso. Questa funzionalità conserva le risorse nel computer che funge da server del flusso di lavoro, quando vengono soddisfatte le condizioni per la chiusura automatica.

### <a name="new-features-in-windows-powershell-web-services"></a>Nuove funzionalità dei servizi Web di Windows PowerShell

- Quando si verifica un errore nei servizi Web di Windows PowerShell (PSWS, noto anche come Estensione IIS OData di gestione), mentre un cmdlet è in esecuzione, vengono restituiti messaggi di errore più dettagliati al chiamante. Inoltre, i codici di errore seguono le [linee guida dei codici di errore dell'API REST di Microsoft Azure](https://msdn.microsoft.com/library/windowsazure/dd179357.aspx).
- Un endpoint può ora definire la versione dell'API, nonché imporre l'uso di una versione specifica. Ogni volta che si verifica una mancata corrispondenza di versione tra client e server, vengono visualizzati messaggi di errore sia nel client che nel server.
- La gestione dello schema di invio è stata semplificata con la generazione automatica dei valori per eventuali campi mancanti. La generazione si verifica, come utile punto di partenza, anche se lo schema di invio non esiste.
- La gestione dei tipi in PSWS è stata migliorata per supportare tipi che usano un costruttore diverso rispetto a quello predefinito grazie a un comportamento simile a quello di **PSTypeConverter** in Windows PowerShell. In questo modo è possibile usare tipi complessi con i servizi Web.
- I servizi Web di PowerShell consentono ora di espandere un'istanza associata durante l'esecuzione di una query. Per contenuti binari più grandi, ad esempio immagini, audio o video, il costo del trasferimento è significativo ed è preferibile trasferire dati binari senza codifica. I servizi Web di PowerShell usano flussi di risorse denominati per il trasferimento senza codifica. Il flusso di risorse denominato è una proprietà di un'entità del tipo **Edm.Stream**. Ogni flusso di risorse denominato ha un URI separato per le operazioni GET o UPDATE.
- Le azioni OData forniscono ora un meccanismo per richiamare metodi non CRUD (Create, Read, Update e Delete) su una risorsa. È possibile richiamare un'azione inviando una richiesta POST HTTP all'URI definito per la stessa. I parametri dell'azione sono definiti nel corpo della richiesta POST.
- Per coerenza con le linee guida di Microsoft Azure, tutti gli URL devono essere semplificati. Una modifica inclusa in **Key As Segment** consente di rappresentare singole chiavi come segmenti. Si noti che i riferimenti che usano più valori di chiave richiedono valori delimitati da virgole nella notazione parentetica, come prima.
- Prima di questa versione dei servizi Web di PowerShell, l'unico modo per eseguire operazioni Create, Update o Delete consiste nel richiamare Post, Put o Delete su una risorsa di primo livello. Le operazioni su risorse contenute, una novità di questa versione dei servizi Web di PowerShell, consentono di ottenere gli stessi risultati raggiungendo la stessa risorsa in modo meno diretto, avvicinandosi come se queste risorse fossero contenute.

### <a name="new-features-in-windows-powershell-web-access"></a>Nuove funzionalità di Accesso Web Windows PowerShell

- È possibile eseguire la disconnessione e la riconnessione a sessioni esistenti nella console di Accesso Web Windows PowerShell. Il pulsante **Salva** della console basata sul Web consente di disconnettersi da una sessione senza eliminarla e quindi di riconnettersi in un secondo momento.
- I parametri predefiniti possono essere visualizzati nella pagina di accesso. Per visualizzare i parametri predefiniti, configurare i valori per tutte le impostazioni visualizzate nell'area **Impostazioni di connessione facoltative** della pagina di accesso in un file denominato **web.config**. È possibile usare il file **web.config** per configurare tutte le impostazioni di connessione facoltative, ad eccezione di un secondo set di credenziali o di un set alternativo.
- In Windows Server 2012 R2 è possibile gestire in remoto le regole di autorizzazione per Accesso Web Windows PowerShell. I cmdlet **Add-PswaAuthorizationRule** e **Test-PswaAuthorizationRule** ora includono un parametro Credential che consente agli amministratori di gestire le regole di autorizzazione da un computer remoto o in una sessione di Accesso Web Windows PowerShell.
- Ora è possibile avere più sessioni di Accesso Web Windows PowerShell in un'unica sessione del browser usando una nuova scheda del browser per ogni sessione. Non è più necessario aprire una nuova sessione del browser per connettersi a una nuova sessione nella console di Windows PowerShell basata sul Web.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Correzioni di bug importanti in Windows PowerShell 4.0

- **Get-Counter** può ora restituire contatori che contengono un carattere apostrofo nelle edizioni in francese di Windows.
- È ora possibile visualizzare il metodo **GetType** negli oggetti deserializzati.
- Le istruzioni **#Requires** consentono ora agli utenti di chiedere diritti di accesso di amministratore, se necessario.
- Il cmdlet **Import-Csv** ignora ora le righe vuote.
- È stato risolto un problema che causava un uso eccessivo di memoria di Windows PowerShell ISE durante l'esecuzione di un comando **Invoke-WebRequest**.
- **Get-Module** visualizza ora le versioni dei moduli in una colonna **Version**.
- Remove-Item -Recurse ora rimuove gli elementi dalle sottocartelle come previsto.
- È stata aggiunta la proprietà **UserName** agli oggetti output di **Get-Process**.
- Il cmdlet **Invoke-RestMethod** restituisce ora tutti i risultati disponibili.
- **Add-Member** ha ora effetto sulle tabelle hash, anche su quelle a cui non è stato ancora effettuato l'accesso.
- **Select-Object -Expand** non genera più errori o eccezioni se il valore della proprietà è Null o vuoto.
- **Get-Process** può ora essere usato in una pipeline con altri comandi che ottengono la proprietà **ComputerName** dagli oggetti.
- **ConvertTo-Json** e **ConvertFrom-Json** possono ora accettare termini con virgolette doppie e i messaggi di errore sono ora localizzabili.
- **Get-Job** restituisce ora qualsiasi processo pianificato completato, anche nelle nuove sessioni.
- I problemi di montaggio e smontaggio dei dischi rigidi virtuali con il provider **FileSystem** in Windows PowerShell 4.0 sono stati corretti. Ora Windows PowerShell può rilevare le nuove unità montate nella stessa sessione.
- Non è più necessario caricare esplicitamente i moduli **ScheduledJob** o **Workflow** per usare i relativi tipi di processo.
- Sono stati apportati miglioramenti alle prestazioni del processo di importazione dei flussi di lavoro che definiscono flussi di lavoro annidati. Questo processo è ora più veloce.

## <a name="new-features-in-windows-powershell-30"></a>Nuove funzionalità di Windows PowerShell 3.0

Windows PowerShell 3.0 include le nuove funzionalità seguenti.

- [Flusso di lavoro di Windows PowerShell](#windows-powershell-workflow)
- [Accesso Web di Windows PowerShell](#windows-powershell-web-access)
- [Nuove funzionalità di Windows PowerShell ISE](#new-windows-powershell-ise-features)
- [Supporto per Microsoft .NET Framework 4.0](#support-for-microsoft-net-framework-4)
- [Supporto per l'Ambiente preinstallazione di Windows](#support-for-windows-preinstallation-environment)
- [Sessioni disconnesse](#disconnected-sessions)
- [Connettività stabile delle sessioni](#robust-session-connectivity)
- [Sistema della Guida aggiornabile](#updatable-help-system)
- [Guida online ottimizzata](#enhanced-online-help)
- [Integrazione con CIM](#cim-integration)
- [File di configurazione di sessione](#session-configuration-files)
- [Processi pianificati e integrazione con l'Utilità di pianificazione](#scheduled-jobs-and-task-scheduler-integration)
- [Miglioramenti del linguaggio di Windows PowerShell](#windows-powershell-language-enhancements)
- [Nuovi cmdlet di sistema](#new-core-cmdlets)
- [Miglioramenti dei cmdlet e provider principali esistenti](#improvements-to-existing-core-cmdlets-and-providers)
- [Importazione e individuazione di moduli remoti](#remote-module-import-and-discovery)
- [Completamento tramite TAB migliorato](#enhanced-tab-completion)
- [Caricamento automatico dei moduli](#module-auto-loading)
- [Miglioramento dell'esperienza con i moduli](#module-experience-improvements)
- [Individuazione semplificata dei comandi](#simplified-command-discovery)
- [Funzionalità migliorate di registrazione e diagnostica e supporto di Criteri di gruppo](#improved-logging-diagnostics-and-group-policy-support)
- [Miglioramenti di formattazione e output](#formatting-and-output-improvements)
- [Esperienza ottimizzata con l'host della console](#enhanced-console-host-experience)
- [Nuove API di cmdlet e hosting](#new-cmdlet-and-hosting-apis)
- [Miglioramenti delle prestazioni](#performance-improvements)
- [Supporto per RunAs e SharedHost](#runas-and-shared-host-support)
- [Miglioramenti nella gestione di caratteri speciali](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Flusso di lavoro di Windows PowerShell

Il flusso di lavoro di Windows PowerShell estende le potenzialità di Windows Workflow Foundation a Windows PowerShell. È possibile scrivere flussi di lavoro in XAML o nel linguaggio di Windows PowerShell ed eseguirli allo stesso modo dei cmdlet. Il cmdlet [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) ottiene i comandi del flusso di lavoro e il cmdlet [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) visualizza la Guida.

I flussi di lavoro sono sequenze di attività di gestione di più computer ad esecuzione prolungata, ripetibili, frequenti, parallelizzabili, interrompibili, sospendibili e riavviabili. Possono essere ripresi dopo un'interruzione intenzionale o accidentale, come un'interruzione di rete, un riavvio di Windows o un'interruzione dell'alimentazione.

Sono anche trasportabili, ossia possono essere esportati o importati da file XAML. È possibile scrivere configurazioni di sessione personalizzate che consentono l'esecuzione di un flusso di lavoro o delle attività al suo interno da parte di utenti delegati o subordinati.

I vantaggi del flusso di lavoro di Windows PowerShell sono descritti di seguito.

- Automazione di attività in sequenza e a esecuzione prolungata.
- **Monitoraggio remoto delle attività con esecuzione prolungata**. Lo stato e l'avanzamento delle attività sono visibili in qualsiasi momento.
- **Gestione di più computer.** È possibile eseguire attività come flussi di lavoro contemporaneamente in centinaia di nodi gestiti. Il flusso di lavoro di Windows PowerShell include una raccolta predefinita di parametri di gestione comuni, ad esempio **PSComputerName**, che consente scenari di gestione di più computer.
- **Esecuzione di singole attività di processi complessi.** È possibile combinare script correlati che implementano un intero scenario end-to-end in un singolo flusso di lavoro.
- **Salvataggio permanente.** Un flusso di lavoro viene salvato, ovvero vengono impostati dei checkpoint, in specifici punti definiti dall'autore. È quindi possibile riprendere il flusso di lavoro dall'ultima attività salvata, o dall'ultimo checkpoint, invece di riavviarlo dall'inizio.
- **Stabilità.** Ripristino automatizzato dagli errori. I flussi di lavoro continuano a esistere in seguito a riavvii pianificati e non pianificati. È possibile sospendere l'esecuzione di un flusso di lavoro e poi riprenderla dall'ultimo punto di salvataggio permanente. Gli autori dei flussi di lavoro possono designare specifiche attività da rieseguire in caso di errore in uno o più nodi gestiti.
- **Possibilità di disconnettersi e riconnettersi alle sessioni e di continuare l'esecuzione nelle sessioni disconnesse.** Gli utenti possono connettersi e disconnettersi dal server del flusso di lavoro, ma l'esecuzione del flusso di lavoro continua ininterrottamente. È possibile disconnettersi dal computer client o riavviarlo e monitorare l'esecuzione del flusso di lavoro da un altro computer senza interromperlo.
- **Pianificazione.** Le attività del flusso di lavoro possono essere pianificate come qualsiasi cmdlet o script di Windows PowerShell.
- **Limitazione di connessioni e flussi di lavoro.** L'esecuzione dei flussi di lavoro e le connessioni ai nodi possono essere limitate, rendendo possibili scenari di scalabilità e disponibilità elevata.

### <a name="windows-powershell-web-access"></a>Accesso Web di Windows PowerShell

Accesso Web Windows PowerShell è una funzionalità di Windows Server 2012 che consente agli utenti di eseguire comandi e script di Windows PowerShell in una console basata sul Web. I dispositivi che usano la console basata sul Web non richiedono Windows PowerShell, un software di gestione remota o l'installazione di plug-in del browser. È richiesto solo un gateway di Accesso Web Windows PowerShell configurato correttamente e un browser del dispositivo client che supporti JavaScript e accetti cookie.

Per altre informazioni, vedere [Distribuire Accesso Web Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkID=221050).

### <a name="new-windows-powershell-ise-features"></a>Nuove funzionalità di Windows PowerShell ISE

Per Windows PowerShell 3.0, Windows PowerShell Integrated Scripting Environment (ISE) include molte nuove funzionalità, tra cui IntelliSense, finestra Show-Command, riquadro della console unificato, frammenti di codice, controllo della corrispondenza delle parentesi graffe, sezioni espandibili e comprimibili, salvataggio automatico, elenco di elementi recenti, copia di testo formattato, copia in blocco e supporto completo per la scrittura di flussi di lavoro di script di Windows PowerShell. Per altre informazioni, vedere [about_Windows_PowerShell_ISE [v3]](https://technet.microsoft.com/library/dfa54d47-60c6-4fff-8197-c747e8d411bb).

### <a name="support-for-microsoft-net-framework-4"></a>Supporto per Microsoft .NET Framework 4

Windows PowerShell è basato su Common Language Runtime 4.0. Gli autori di cmdlet, script e flussi di lavoro possono usare le nuove classi di Microsoft .NET Framework 4 in Windows PowerShell, con funzionalità come la compatibilità e la distribuzione di applicazioni, Managed Extensibility Framework, calcolo parallelo, rete, Windows Communication Foundation e Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Supporto per l'Ambiente preinstallazione di Windows

Windows PowerShell 3.0 è un componente facoltativo di Ambiente preinstallazione di Windows (Windows PE) 4.0 per Windows 8. Windows PE è un sistema operativo minimale che consente di avviare un computer privo di sistema operativo e lo prepara per l'installazione di Windows. Può essere usato per partizionare e formattare unità disco rigido, copiare immagini del disco in un computer e avviare l'installazione di Windows da una condivisione di rete. Windows PowerShell 3.0 può essere usato in Windows PE per gestire scenari di distribuzione, diagnostica e ripristino.

### <a name="disconnected-sessions"></a>Sessioni disconnesse

A partire da Windows PowerShell 3.0, le sessioni permanenti gestite dall'utente ("PSSession") create con il cmdlet New-PSSession vengono salvate nel computer remoto. Non dipendono più dalla sessione in cui sono state create.

È ora possibile disconnettersi da una sessione senza interrompere i comandi in esecuzione al suo interno. È possibile chiudere la sessione e arrestare il computer. In seguito, è possibile riconnettersi alla sessione da una sessione diversa nello stesso computer o in uno diverso.

Il parametro **ComputerName** del cmdlet [Get-PSSession](https://technet.microsoft.com/library/b2b10531-d0df-4746-b877-e75c09955cb6) ottiene ora tutte le sessioni dell'utente che si connettono al computer, anche se sono state avviate in una sessione diversa e in un computer diverso. È ora possibile connettersi alle sessioni, ottenere i risultati dei comandi, avviare nuovi comandi e quindi disconnettersi.

Sono stati aggiunti nuovi cmdlet per supportare la funzionalità delle sessioni disconnesse, tra cui [Disconnect-PSSession](https://technet.microsoft.com/library/f8f95111-612f-4cba-9098-77904b0473d8), [Connect-PSSession](https://technet.microsoft.com/library/b803dd29-f208-4079-80d4-db04d778f060) e Receive-PSSession. Sono inoltre stati aggiunti nuovi parametri ai cmdlet che gestiscono PSSession, ad esempio il parametro **InDisconnectedSession** del cmdlet [Invoke-Command](https://technet.microsoft.com/library/906b4b41-7da8-4330-9363-e7164e5e6970).

La funzionalità delle sessioni disconnesse è supportata solo se sia il computer all'estremità di origine ("client") che quello all'estremità di destinazione ("server") della connessione eseguono Windows PowerShell 3.0.

### <a name="robust-session-connectivity"></a>Connettività stabile delle sessioni

Windows PowerShell 3.0 rileva interruzioni impreviste della connessione tra client e server e prova a ristabilirla e a riprendere automaticamente l'esecuzione. Se la connessione tra client e server non può essere ristabilita entro l'intervallo assegnato, l'utente riceve una notifica e la sessione viene disconnessa. Durante il tentativo di riconnessione, Windows PowerShell fornisce un feedback continuo all'utente.

Se la sessione disconnessa è stata avviata con InvokeCommand, Windows PowerShell crea un apposito processo per semplificare la riconnessione e la ripresa dell'esecuzione.

Queste funzionalità assicurano un'esperienza di comunicazione remota affidabile e ripristinabile e consentono agli utenti di eseguire attività a esecuzione prolungata che richiedono sessioni stabili, come i flussi di lavoro.

### <a name="updatable-help-system"></a>Sistema della Guida aggiornabile

È ora possibile scaricare file della Guida aggiornati per i cmdlet dei moduli. Il cmdlet [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) identifica i file della Guida più recenti, li scarica da Internet, li decomprime, li convalida e li installa nella directory specifica della lingua corretta per il modulo.

Per usare i file della Guida aggiornati, basta digitare `Get-Help`. Non è necessario riavviare Windows o Windows PowerShell. Per aggiornare la Guida per i moduli nella directory $pshome, avviare Windows PowerShell con l'opzione "Esegui come amministratore".

Per supportare gli utenti che non hanno accesso a Internet e quelli che operano in ambienti protetti da firewall, il nuovo cmdlet [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) scarica i file della Guida in una directory del file system, ad esempio una condivisione file. Gli utenti possono quindi usare il cmdlet [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) per recuperare i file della Guida aggiornata dalla condivisione file.

È possibile usare il cmdlet [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) per aggiornare i file della Guida per tutti i moduli o solo per alcuni specifici in tutte le impostazioni cultura supportate dell'interfaccia utente. È anche possibile inserire un comando [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) nel profilo di Windows PowerShell. Per impostazione predefinita, Windows PowerShell scarica i file della Guida in un modulo non più di una volta al giorno.

I moduli di Windows 8 e Windows Server 2012 non includono file della Guida. Per scaricare i file della Guida più recenti, digitare `Update-Help`. Per altre informazioni, digitare `Get-Help` senza parametri oppure vedere [about_Updatable_Help](https://technet.microsoft.com/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

Se i file della Guida per un cmdlet non sono installati nel computer, il cmdlet [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) visualizza ora la Guida generata automaticamente, che include la sintassi dei comandi e le istruzioni per scaricare i file della Guida tramite il cmdlet [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545).

Qualsiasi autore di moduli può ora supportare la Guida aggiornabile. È possibile includere i file della Guida nel modulo e usare la Guida aggiornabile per aggiornarli oppure omettere tali file e usare la Guida aggiornabile per installarli. Per altre informazioni, vedere [Supporto per la Guida aggiornabile](https://go.microsoft.com/FWLink/?LinkID=242129) in MSDN.

### <a name="enhanced-online-help"></a>Guida online ottimizzata

La Guida online di Windows PowerShell è una risorsa preziosa per tutti gli utenti, ma è particolarmente importante per quelli che non hanno installato i file della Guida aggiornati o non possono farlo.

Per ottenere la Guida online per qualsiasi cmdlet di Windows PowerShell, digitare:

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell apre la versione online dell'argomento della Guida nel browser Internet predefinito.

La funzionalità **Get-Help -Online** in Windows PowerShell 3.0 è ora ancora più potente, perché può essere eseguita anche se i file della Guida per il cmdlet non sono installati nel computer. La funzionalità **Get-Help -Online** ottiene l'URI dell'argomento della Guida online dalla proprietà HelpUri dei cmdlet e delle funzioni avanzate.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
https://go.microsoft.com/fwlink/?LinkID=223923
```

A partire da Windows PowerShell 3.0, gli autori dei cmdlet scritti in C# possono popolare la proprietà **HelpUri** creando un attributo **HelpUri** nella classe del cmdlet. Gli autori di funzioni avanzate possono definire una proprietà **HelpUri** nell'attributo **CmdletBinding**. Il valore della proprietà **HelpUri** deve iniziare con "http" o "https".

È anche possibile includere un valore **HelpUri** nel primo collegamento correlato di un file della Guida sui cmdlet basato su XML o la direttiva .Link della Guida basata su commenti in una funzione.

Per altre informazioni, vedere [Supporto per la Guida online](/powershell/scripting/developer/module/supporting-online-help) in Microsoft Docs.

### <a name="cim-integration"></a>Integrazione con CIM

Windows PowerShell 3.0 include il supporto per CIM (Common Information Model), che fornisce definizioni comuni delle informazioni di gestione per sistemi, reti, applicazioni e servizi, consentendo lo scambio di tali informazioni tra sistemi eterogenei. Supporto per CIM in Windows PowerShell 3.0, con la possibilità di creare cmdlet di Windows PowerShell basati su classi CIM nuove o esistenti e di comandi basati su file XML di definizione dei cmdlet, oltre al supporto per .NET Framework CIM. API, cmdlet di gestione CIM e provider WMI 2.0.

### <a name="session-configuration-files"></a>File di configurazione di sessione

A partire da Windows PowerShell 3.0, è possibile progettare una configurazione di sessione personalizzata usando un file. Il nuovo file di configurazione consente di determinare l'ambiente delle sessioni che usano la configurazione di sessione, indicando quali moduli, script e file di formato sono caricati nelle sessioni, quali cmdlet ed elementi del linguaggio possono essere usati dagli utenti, quali moduli e script possono essere eseguiti e quali variabili possono essere visualizzate.

È possibile progettare una sessione in cui gli utenti possono eseguire solo i cmdlet di un determinato modulo oppure una sessione in cui gli utenti hanno accesso a tutti i moduli, in tutti i linguaggi, e agli script che eseguono attività avanzate.

Nelle versioni precedenti di Windows PowerShell il controllo a questo livello era disponibile solo per gli utenti in grado di scrivere programmi in C# o complessi script di avvio. Ora qualsiasi membro del gruppo Administrators del computer può personalizzare una configurazione di sessione tramite un file di configurazione.

Per creare un file di configurazione di sessione, usare il cmdlet [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866). Per applicare il file a una configurazione di sessione, usare il cmdlet [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) o [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea).

Per altre informazioni, vedere [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-5.0) e [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866).

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Processi pianificati e integrazione con l'Utilità di pianificazione

È ora possibile pianificare i processi in background di Windows PowerShell e gestirli in Windows PowerShell e nell'Utilità di pianificazione.

I processi pianificati di Windows PowerShell sono un utile ibrido di processi in background di Windows PowerShell e attività dell'Utilità di pianificazione.

Analogamente ai processi in background di Windows PowerShell, i processi pianificati vengono eseguiti in modo asincrono in background. Le istanze dei processi pianificati che sono state completate possono essere gestite tramite cmdlet di processo come [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) e [Get-Job](https://technet.microsoft.com/library/1352c534-7193-46ca-9ab1-0c5219a661ad).

Analogamente alle attività dell'Utilità di pianificazione, è possibile eseguire i processi pianificati in base a una pianificazione una tantum o ricorrente oppure in risposta a un'azione o a un evento. È possibile visualizzare e gestire i processi pianificati nell'Utilità di pianificazione, abilitarli e disabilitarli secondo necessità, eseguirli o usarli come modelli e definire le condizioni in base a cui devono essere avviati.

Inoltre, i processi pianificati includono un set personalizzato di cmdlet per gestirli. I cmdlet consentono di creare, modificare, gestire, disabilitare e riabilitare i processi pianificati, creare appositi trigger e impostare le opzioni.

Per altre informazioni sui processi pianificati, vedere [about_Scheduled_Jobs](https://technet.microsoft.com/library/3b546629-703c-4939-b44f-52dd567bce92).

### <a name="windows-powershell-language-enhancements"></a>Miglioramenti del linguaggio di Windows PowerShell

Windows PowerShell 3.0 include molte funzionalità progettate per rendere il linguaggio più semplice, più facile da usare e meno soggetto a errori comuni. I miglioramenti includono l'enumerazione di proprietà, le proprietà di conteggio e lunghezza su oggetti scalari, nuovi operatori di reindirizzamento, il modificatore di ambito $Using, la variabile automatica PSItem, una formattazione di script flessibile, attributi di variabili, argomenti degli attributi semplificati, nomi di comandi numerici, operatore Stop-Parsing, splatting delle matrici migliorato, nuovi operatori bit a bit, dizionari ordinati, casting di PSCustomObject e una Guida migliorata basata su commenti.

### <a name="new-core-cmdlets"></a>Nuovi cmdlet di sistema

Nell'installazione di sistema di Windows PowerShell sono stati aggiunti nuovi cmdlet, tra cui cmdlet per gestire processi pianificati, sessioni disconnesse, integrazione con CIM e Guida aggiornabile.

|||
|-|-|
|Add-JobTrigger|New-JobTrigger|
|Connect-PSSession|New-PSSessionConfigurationFile|
|ConvertFrom-Json|New-PSTransportOption|
|ConvertTo-Json|New-PSWorkflowExecutionOption|
|Disable-JobTrigger|New-PSWorkflowSession|
|Disable-ScheduledJob|New-ScheduledJobOption|
|Disconnect-PSSession|New-WinEvent|
|Enable-JobTrigger|Receive-PSSession|
|Enable-ScheduledJob|Register-CimIndicationEvent|
|Get-CimAssociatedInstance|Register-ScheduledJob|
|Get-CimClass|Remove-CimInstance|
|Get-CimInstance|Remove-CimSession|
|Get-CimSession|Remove-TypeData|
|Get-ControlPanelItem|Rename-Computer|
|Get-IseSnippet|Resume-Job|
|Get-JobTrigger|Save-Help|
|Get-ScheduledJob|Set-CimInstance|
|Get-ScheduledJobOption|Set-JobTrigger|
|Get-TypeData|Set-ScheduledJob|
|Import-IseSnippet|Set-ScheduledJobOption|
|Invoke-AsWorkflow|Show-Command|
|Invoke-CimMethod|Show-ControlPanelItem|
|Invoke-RestMethod|Suspend-Job|
|Invoke-WebRequest|Test-PSSessionConfigurationFile|
|New-CimInstance|Unblock-File|
|New-CimSession|Unregister-ScheduledJob|
|New-CimSessionOption|Update-Help|
|New-IseSnippet||

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Miglioramenti dei cmdlet e provider principali esistenti

Windows PowerShell 3.0 include nuove funzionalità per gli attuali cmdlet, tra cui una sintassi migliorata e nuovi parametri per i cmdlet seguenti: cmdlet Computer, cmdlet CSV, Get-ChildItem, Get-Command, Get-Content, Get-History, Measure-Object, cmdlet Security, Select-Object, Select-String, Split-Path, Start-Process, Tee-Object, Test-Connection, Add-Member e cmdlet WMI.

Anche i provider di Windows PowerShell sono stati migliorati in modo significativo, con l'aggiunta del supporto del provider Certificate per la gestione di certificati SSL (Secure Socket Layer) per l'hosting Web, il supporto di unità di rete permanenti basate su credenziali e flussi di dati alternativi nelle unità di file system.

### <a name="remote-module-import-and-discovery"></a>Importazione e individuazione di moduli remoti

Windows PowerShell 3.0 estende le funzionalità di individuazione dei moduli, importazione e comunicazione remota implicita nei computer remoti. I cmdlet Module ottengono i moduli nei computer remoti e li importano in computer remoti o locali tramite la comunicazione remota di Windows PowerShell. Il nuovo supporto per sessioni CIM consente di usare CIM e WMI per gestire computer non Windows importando nel computer locale comandi che vengono eseguiti in modo implicito nel computer remoto.

Per altre informazioni, vedere gli argomenti della Guida per i cmdlet [Get-Module](https://technet.microsoft.com/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) e [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade).

### <a name="enhanced-tab-completion"></a>Completamento tramite TAB migliorato

Il completamento tramite tasto TAB nella console di Windows PowerShell ora completa i nomi di cmdlet, parametri, valori dei parametri, enumerazioni, tipi .NET Framework, oggetti COM, directory nascoste e altro. Questa funzionalità è stata completamente riscritta in base a un nuovo albero sintattico astratto e di analisi per supportare più scenari, tra cui alberi di analisi in memoria e completamento tramite TAB sulla riga centrale.

### <a name="module-auto-loading"></a>Caricamento automatico dei moduli

Il cmdlet [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) ottiene ora tutti i cmdlet e le funzioni da tutti i moduli installati nel computer, anche quelli non importati nella sessione corrente.

Una volta ottenuto il cmdlet necessario, è possibile usarlo immediatamente senza importare nessun modulo. I moduli di Windows PowerShell vengono ora importati automaticamente quando si usa uno dei cmdlet al loro interno. Non è più necessario cercare il modulo e importarlo per usare i relativi cmdlet.

L'importazione automatica dei moduli viene avviata usando il cmdlet in un comando, eseguendo **Get-Command** per un cmdlet senza caratteri jolly oppure eseguendo [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) per un cmdlet senza caratteri jolly.

È possibile abilitare, disabilitare e configurare l'importazione automatica dei moduli usando la variabile di preferenza **$PSModuleAutoLoadingPreference**.

Per altre informazioni, vedere [about_Modules](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-5.0), [about_Preference_Variables [v4]](https://technet.microsoft.com/library/31344314-be29-4286-b039-afa5460cbe8b) e gli argomenti della Guida sui cmdlet [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) e [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade).

### <a name="module-experience-improvements"></a>Miglioramento dell'esperienza con i moduli

Windows PowerShell 3.0 offre il supporto di funzionalità avanzate per il modulo, tra cui le nuove funzionalità seguenti.

1. Registrazione per singoli moduli (LogPipelineExecutionDetails) e nuova impostazione di Criteri di gruppo "Turn on Module Logging"
2. Oggetti modulo estesi che espongono i valori del manifesto del modulo
3. Nuova proprietà **ExportedCommands** dei moduli, inclusi i moduli annidati, che combina i comandi di tutti i tipi
4. Individuazione migliorata dei moduli disponibili (non importati), consentendo anche l'uso dei parametri **Path** e **ListAvailable** nello stesso comando
5. Nuova chiave **DefaultCommandPrefix** nei manifesti dei moduli che evita conflitti dei nomi senza cambiare il codice del modulo
6. Requisiti migliorati dei moduli, tra cui il requisito di moduli completi con versione e GUID e l'importazione automatica dei moduli necessari
7. Funzionamento semplificato del cmdlet [New-ModuleManifest](https://technet.microsoft.com/library/512adced-f42f-4e88-ba7c-834fc9e5d047)
8. Nuovo parametro **Module** per #Requires
9. Cmdlet [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) migliorato con entrambi i parametri **MinimumVersion** e **RequiredVersion**.

### <a name="simplified-command-discovery"></a>Individuazione semplificata dei comandi

Non è più necessario importare tutti i moduli per individuare i comandi disponibili nella sessione. In Windows PowerShell 3.0 il cmdlet [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) ottiene tutti i comandi da tutti i moduli installati. Se inoltre si usa un comando, il modulo che lo esporta viene automaticamente importato nella sessione.

Il nuovo cmdlet [Show-Command](https://technet.microsoft.com/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) è progettato specificamente per utenti meno esperti. È possibile cercare i comandi in una finestra. È possibile visualizzare tutti i comandi o applicare un filtro per modulo, importare un modulo facendo clic su un pulsante, usare caselle di testo ed elenchi a discesa per creare un comando valido e quindi copiarlo o eseguirlo senza mai uscire dalla finestra.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Funzionalità migliorate di registrazione e diagnostica e supporto di Criteri di gruppo

In Windows PowerShell 3.0 è stato migliorato il supporto per la registrazione e la traccia per comandi e moduli grazie al supporto per i log di Event Tracing for Windows (ETW) e una proprietà **LogPipelineExecutionDetails** modificabile dei moduli, oltre all'impostazione di Criteri di gruppo "Attiva registrazione moduli". È ora possibile ottenere i valori dei parametri dai dettagli dei log visualizzando le proprietà dei log.

### <a name="formatting-and-output-improvements"></a>Miglioramenti di formattazione e output

I nuovi miglioramenti alla formattazione e all'output aumentano l'efficienza per tutti gli utenti di Windows PowerShell. I miglioramenti includono il reindirizzamento dell'output per tutti i flussi, un cmdlet Update-Type ottimizzato che aggiunge dinamicamente i tipi senza i file Format.ps1xml, il ritorno a capo automatico nell'output, le proprietà predefinite di formattazione di oggetti personalizzati, il tipo **PSCustomObject**, la formattazione migliorata di oggetti WMI e oggetti eterogenei e il supporto per l'individuazione degli overload dei metodi.

### <a name="enhanced-console-host-experience"></a>Esperienza ottimizzata con l'host della console

Il programma host della console di Windows PowerShell include nuove funzionalità in Windows PowerShell 3.0, tra cui l'apartment a thread singolo per impostazione predefinita. La nuova opzione "Esegui con PowerShell" di Esplora file consente di eseguire gli script in una sessione senza restrizioni facendo semplicemente clic con il pulsante destro del mouse. La nuova logica di avvio dell'host della console avvia più velocemente Windows PowerShell e i nuovi tipi di carattere consentono di personalizzare l'esperienza con la consueta finestra della console.

Per altre informazioni, vedere [about_Run_With_PowerShell](https://technet.microsoft.com/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).

### <a name="new-cmdlet-and-hosting-apis"></a>Nuove API di cmdlet e hosting

Le nuove API di cmdlet e hosting includono API AST (Advanced Syntax Tree) e API per il paging delle pipeline, le pipeline annidate, il completamento tramite TAB di pool di spazi di esecuzione, Windows RT, l'attributo Obsolete dei cmdlet e le proprietà Verb e Noun dell'oggetto FunctionInfo.

### <a name="performance-improvements"></a>Miglioramenti delle prestazioni

I miglioramenti significativi delle prestazioni di Windows PowerShell sono attribuibili al nuovo parser del linguaggio, basato sul linguaggio DLR (Dynamic Runtime Language) di .NET Framework 4, oltre alla compilazione di script di runtime, alla maggiore affidabilità del motore e alle modifiche apportate all'algoritmo di [Get-ChildItem](https://technet.microsoft.com/library/75cf79bb-4db6-4a67-8c36-3d20754e2190), che ne migliorano le prestazioni in particolare per le ricerche nelle condivisioni di rete.

### <a name="runas-and-shared-host-support"></a>Supporto per RunAs e SharedHost

Windows PowerShell 3.0 include il supporto per le funzionalità RunAs e Shared Host.

La funzionalità *RunAs*, progettata per il flusso di lavoro di Windows PowerShell, consente agli utenti di una configurazione di sessione di creare sessioni che vengono eseguite con l'autorizzazione di un account utente condiviso. In questo modo gli utenti con privilegi meno elevati possono eseguire specifici comandi e script con autorizzazioni di amministratore, riducendo la necessità di aggiungere utenti meno avanzati al gruppo Administrators.

La funzionalità **SharedHost** consente a più utenti di più computer di connettersi a una sessione del flusso di lavoro contemporaneamente e di monitorare lo stato di un flusso di lavoro. Gli utenti possono avviare un flusso di lavoro in un computer e quindi connettersi alla sessione del flusso di lavoro di un altro computer senza disconnettersi da quella del computer originale. È necessario che gli utenti abbiano le stesse autorizzazioni e usino la stessa configurazione di sessione. Per altre informazioni, vedere la sezione sull'esecuzione di un flusso di lavoro di Windows PowerShell nella guida introduttiva di questa funzionalità.

### <a name="special-character-handling-improvements"></a>Miglioramenti nella gestione di caratteri speciali

Per migliorare le capacità di Windows PowerShell 3.0 di interpretare e gestire correttamente i caratteri speciali, il parametro **LiteralPath**, che gestisce i caratteri speciali nei percorsi, è valido in quasi tutti i cmdlet con un parametro **Path**, inclusi i nuovi cmdlet [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) e [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa). Il parser include anche una logica speciale per migliorare la gestione del carattere apice inverso (\`) e delle parentesi quadre nei nomi file e nei percorsi.

## <a name="see-also"></a>Vedere anche

- [about_Windows_PowerShell_5.0](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
