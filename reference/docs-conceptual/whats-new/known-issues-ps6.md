---
ms.date: 05/17/2018
keywords: powershell,core
title: Problemi noti di PowerShell 6.0
ms.openlocfilehash: 502143b660204edada6a9e62bdf6b260a384a078
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733835"
---
# <a name="known-issues-for-powershell-60"></a>Problemi noti di PowerShell 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Problemi noti di PowerShell in piattaforme non Windows

Le versioni alfa di PowerShell su Linux e macOS sono in gran parte funzionali, ma presentano alcuni problemi di usabilità e limitazioni significativi. Le versioni beta di PowerShell in Linux e macOS sono più funzionali e stabili delle versioni alfa, ma potrebbero ancora mancare alcuni set di funzionalità e possono essere presenti bug. In alcuni casi, questi problemi sono semplicemente bug non ancora risolti. In altri casi (come nel caso degli alias predefiniti per ls, cp e così via), sono richiesti i commenti e i suggerimenti della community in merito alle scelte effettuate.

Nota: a causa delle similitudini di molti sottosistemi sottostanti, le installazioni di PowerShell su Linux e macOS tendono a condividere lo stesso livello di maturità sia a livello di funzionalità che di bug. Ad eccezione di quanto segnalato di seguito, i problemi in questa sezione sono applicabili a entrambi i sistemi operativi.

### <a name="case-sensitivity-in-powershell"></a>Distinzione tra maiuscole e minuscole in PowerShell

PowerShell non ha fatto storicamente distinzione tra maiuscole e minuscole in modo coerente e con poche eccezioni. Nei sistemi operativi simili a UNIX, il file system effettua in modo predominante la distinzione tra maiuscole e minuscole e PowerShell rispetta lo standard del file system. L'esposizione di questo comportamento avviene in vari modi, sia ovvi che meno ovvi.

#### <a name="directly"></a>Direttamente

- Quando si specifica un file in PowerShell, è necessario usare la corretta combinazione di maiuscole/minuscole.

#### <a name="indirectly"></a>Indirettamente

- Se uno script tenta di caricare un modulo e il nome del modulo non è specificato con la corretta combinazione di maiuscole/minuscole, il caricamento del modulo avrà esito negativo. Ciò può causare un problema con gli script esistenti se il nome con cui si fa riferimento al modulo non corrisponde al nome di file effettivo.
- Il completamento tramite TAB non eseguirà il completamento automatico se la combinazione di maiuscole/minuscole del nome non è corretta. Il frammento da completare deve avere la combinazione di maiuscole/minuscole corretta. (La funzionalità di completamento non effettua distinzione tra maiuscole e minuscole per i completamenti del nome di tipo e del membro del tipo.)

### <a name="ps1-file-extensions"></a>Estensioni di file PS1

Gli script di PowerShell devono terminare in `.ps1` affinché l'interprete possa capire come caricarli ed eseguirli nel processo corrente. L'esecuzione di script nel processo corrente è il comportamento normale previsto per PowerShell. Si potrebbe aggiungere il numero chiave `#!` a uno script senza estensione `.ps1`, ma ciò causerà l'esecuzione dello script in una nuova istanza di PowerShell impedendo il corretto funzionamento dello script con oggetti interscambiabili. (Nota: questo potrebbe essere il comportamento auspicabile per l'esecuzione di uno script di PowerShell da `bash` o un'altra shell.)

### <a name="missing-command-aliases"></a>Alias di comandi mancanti

In Linux/macOS sono stati rimossi gli alias di comodità per i comandi di base `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps`. In Windows, PowerShell offre un set di alias corrispondenti a nomi di comandi di Linux per comodità degli utenti. Tali alias sono stati rimossi dalla versione predefinita di PowerShell nelle distribuzioni di Linux/macOS, consentendo l'esecuzione dell'eseguibile nativo senza specificare un percorso.

Ciò comporta vantaggi e svantaggi. La rimozione degli alias espone l'esperienza nativa per i comandi per l'utente di PowerShell, ma riduce la funzionalità nella shell perché i comandi nativi restituiscono stringhe invece di oggetti.

> [!NOTE]
> Questa è un'area per la quale il team di PowerShell vorrebbe ricevere commenti e suggerimenti.
> Quale è la soluzione preferibile? Va bene così o è meglio aggiungere di nuovo gli alias di comodità? Vedere il [problema #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Supporto mancante dei caratteri jolly (globbing)

Attualmente, PowerShell esegue l'espansione dei caratteri jolly (globbing) solo per i cmdlet predefiniti in Windows e per i comandi o i file binari esterni, nonché per i cmdlet in Linux. Questo significa che un comando come `ls
*.txt` avrà esito negativo perché l'asterisco non verrà espanso per trovare i nomi di file corrispondenti. È possibile risolvere il problema eseguendo `ls (gci *.txt | % name)` o, più semplicemente `gci *.txt` usando l'equivalente predefinito di PowerShell di `ls`.

Vedere il [problema #954](https://github.com/PowerShell/PowerShell/issues/954) per inviare commenti e suggerimenti su come migliorare l'esperienza di globbing in Linux/macOS.

### <a name="net-framework-vs-net-core-framework"></a>.NET Framework a confronto con .NET Core Framework

PowerShell in Linux/macOS usa .NET Core che è un subset della versione completa di .NET Framework in Microsoft Windows. Ciò è importante perché PowerShell consente l'accesso diretto a tipi, metodi e altri elementi del framework sottostante. Di conseguenza, gli script eseguiti in Windows potrebbero non essere eseguiti in piattaforme non Windows a causa delle differenze nei framework. Per altre informazioni su .NET Core Framework, vedere <https://dotnetfoundation.org/net-core>

Con l'avvento di [.NET Standard 2.0](https://devblogs.microsoft.com/dotnet/introducing-net-standard/), .NET Core 2.0 renderà di nuovo disponibili molti dei tipi e dei metodi tradizionali presenti nella versione completa di .NET Framework. Questo significa che PowerShell Core sarà in grado di caricare molti moduli tradizionali di Windows PowerShell senza apportare modifiche. È possibile seguire il lavoro correlato a .NET Standard 2.0 [qui](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Problemi di reindirizzamento

Il reindirizzamento dell'input non è supportato in PowerShell su qualsiasi piattaforma.
[Problema #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Usare `Get-Content` per scrivere il contenuto di un file nella pipeline.

L'output reindirizzato conterrà il byte order mark (BOM) Unicode quando viene usata la codifica predefinita UTF-8. Il BOM causerà problemi quando si utilizzano utilità che non lo prevedono o per le aggiunte a un file. Usare `-Encoding Ascii` per scrivere testo ASCII che non includerà un BOM non essendo Unicode.

> [!Note]
> Vedere [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) per inviare commenti e suggerimenti su come migliorare l'esperienza di codifica per PowerShell Core per tutte le piattaforme. Stiamo lavorando per supportare UTF-8 senza un BOM e per modificare potenzialmente le impostazioni predefinite di codifica per vari cmdlet in tutte le piattaforme.

### <a name="job-control"></a>Controllo dei processi

PowerShell in Linux/macOS non supporta il controllo dei processi.
I comandi `fg` e `bg` non sono disponibili.

Per il momento, è possibile usare i [processi di PowerShell](/powershell/module/microsoft.powershell.core/about/about_jobs) che funzionano in tutte le piattaforme.

### <a name="remoting-support"></a>Supporto della comunicazione remota

Attualmente, PowerShell Core supporta il protocollo PSRP (PowerShell Remoting Protocol) su WS-Management con l'autenticazione di base in macOS e Linux e con l'autenticazione basata su NTLM in Linux. (L'autenticazione basata su Kerberos non è supportata.)

Il lavoro per la comunicazione remota basata su WS-Management viene eseguito nel repository [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider).

PowerShell Core supporta anche il protocollo PSRP (PowerShell Remoting Protocol) su SSH in tutte le piattaforme (Windows, macOS e Linux). Anche se non è attualmente supportato in ambiente di produzione, [qui](../learn/remoting/SSH-Remoting-in-PowerShell-Core.md) sono disponibili altre informazioni sulla configurazione.

### <a name="just-enough-administration-jea-support"></a>Supporto di JEA (Just Enough Administration)

La possibilità di creare endpoint di comunicazione remota con amministrazione vincolata (JEA) non è attualmente disponibile in PowerShell su Linux/macOS. Questa funzionalità non è attualmente nell'ambito per la versione 6.0 e verrà presa in considerazione per una versione successiva perché richiede un notevole impegno di progettazione.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec` e PowerShell

Dato che PowerShell esegue la maggior parte dei comandi in memoria (come Python o Ruby), non è possibile usare sudo direttamente con i comandi predefiniti di PowerShell. È ovviamente possibile eseguire `pwsh` da sudo. Se è necessario eseguire un cmdlet di PowerShell dall'interno di PowerShell con sudo, ad esempio `sudo Set-Date 8/18/2016`, eseguire `sudo pwsh Set-Date 8/18/2016`. Analogamente, non è possibile eseguire direttamente un comando predefinito di PowerShell, ma è invece necessario eseguire `exec pwsh item_to_exec`.

Questo problema è attualmente monitorato come parte del problema [#3232](https://github.com/PowerShell/PowerShell/issues/3232).

### <a name="missing-cmdlets"></a>Cmdlet mancanti

Un numero elevato di comandi (cmdlet) normalmente disponibili in PowerShell non è disponibile in Linux/macOS. In molti casi, questi comandi non sono significativi per queste piattaforme (ad esempio, funzionalità specifiche di Windows come il Registro di sistema). Gli altri comandi, ad esempio i comandi di controllo del servizio (Get/Start/Stop-Service) sono presenti, ma non funzionali. Nelle versioni future questi problemi verranno risolti con la correzione dei cmdlet non funzionanti e con l'aggiunta di nuovi nel corso del tempo.

### <a name="command-availability"></a>Disponibilità dei comandi

Nella tabella seguente sono elencati i comandi che sicuramente non funzionano in PowerShell in Linux/macOS.

|Comandi|Stato operativo|Note|
|--------|-----------------|-----|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|Non disponibile.|Questi comandi non verranno riconosciuti. Questo problema dovrebbe essere risolto in una versione futura.|
|`Get-Acl`, `Set-Acl`|Non disponibile.|Questi comandi non verranno riconosciuti. Questo problema dovrebbe essere risolto in una versione futura.|
|`Get-AuthenticodeSignature`, `Set-AuthenticodeSignature`|Non disponibile.|Questi comandi non verranno riconosciuti. Questo problema dovrebbe essere risolto in una versione futura.|
|`Wait-Process`|Disponibile, non funziona correttamente. |Ad esempio, `Start-Process gvim -PassThru | Wait-Process` non funziona; l'attesa del processo ha esito negativo.|
|`Register-PSSessionConfiguration`, `Unregister-PSSessionConfiguration`, `Get-PSSessionConfiguration`|Disponibile, ma non funziona.|Scrive un messaggio di errore che indica che i comandi non funzionano. Questi dovrebbero essere corretti in una versione futura.|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Register-WmiEvent`, `Remove-Event`, `Unregister-Event`|Disponibili, ma non sono disponibili origini evento.|I comandi di gestione degli eventi di PowerShell sono presenti, ma la maggior parte delle origini evento usate con i comandi (ad esempio System.Timers.Timer) non è disponibile in Linux rendendo quindi inutili i comandi nella versione alfa.|
|`Set-ExecutionPolicy`|Disponibile, ma non funziona.|Restituisce un messaggio che indica che non è supportato in questa piattaforma. I criteri di esecuzione sono una "cintura di sicurezza" pensata per gli utenti, che consente di impedire all'utente di commettere errori onerosi. Non è un limite di sicurezza.|
|`New-PSSessionOption`, `New-PSTransportOption`|Disponibile, ma `New-PSSession` non funziona.|Il funzionamento di `New-PSSessionOption` e `New-PSTransportOption` non è attualmente verificato ora che funziona `New-PSSession`.|
