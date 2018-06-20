---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Imparare i nomi usati in Windows PowerShell
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 381aa619a41ccacb2ff3a4cdbc2b75b7f04282d1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953474"
---
# <a name="learning-windows-powershell-names"></a>Imparare i nomi usati in Windows PowerShell
Nella maggior parte delle interfacce della riga di comando, imparare nomi e parametri dei comandi richiede molto tempo. Il problema è che esistono pochissimi schemi, quindi l'unica possibilità è memorizzare ogni comando e parametro che è necessario usare regolarmente.

Quando si lavora con un nuovo comando o parametro, in genere non è possibile sfruttare le competenze già acquisite, ma è necessario trovare e imparare un nuovo nome. Se si pensa al modo in cui crescono le interfacce, partendo da un piccolo set di strumenti a cui vengono man mano aggiunte funzionalità, è facile capire perché la struttura non sia standard. Con i nomi dei comandi, in particolare, questo può sembrare logico visto che ogni comando è uno strumento a sé stante, ma esiste un modo migliore per gestire i nomi dei comandi.

La maggior parte dei comandi serve per gestire elementi del sistema operativo o applicazioni, ad esempio servizi o processi. I comandi hanno un'ampia varietà di nomi, che non sempre appartengono a una famiglia. Nei sistemi Windows, ad esempio, è possibile usare i comandi **net start** e **net stop** per avviare e arrestare un servizio. Esiste anche un altro strumento di controllo dei servizi per Windows con un nome completamente diverso, **sc**, che non rientra nello schema di denominazione dei comandi per i servizi **net**. Per la gestione dei processi, Windows ha il comando **tasklist** per elencare i processi e il comando **taskkill** per terminarli.

I comandi che accettano parametri hanno specifiche irregolari rispetto ai parametri. Non è possibile usare il comando **net start** per avviare un servizio in un computer remoto. Il comando **sc** avvierà un servizio in un computer remoto, ma per specificare il computer remoto è necessario anteporre al nome una doppia barra rovesciata. Ad esempio, per avviare il servizio spooler in un computer remoto denominato DC01, occorre digitare **sc \\\\DC01 start spooler**. Per ottenere l'elenco delle attività in esecuzione in DC01 è necessario usare il parametro **/S** (per "sistema") e specificare il nome DC01 senza barre rovesciate, in questo modo: **tasklist /S DC01**.

Anche se esistono notevoli differenze tecniche tra un servizio e un processo, entrambi sono esempi di elementi gestibili in un computer caratterizzati da un ciclo di vita ben definito. Si può voler avviare o arrestare un servizio o un processo oppure ottenere un elenco di tutti i servizi o processi in esecuzione. In altre parole, anche se un servizio è diverso da un processo, le azioni che eseguiamo su un servizio o un processo sono spesso le stesse dal punto di vista concettuale, così come sono simili le scelte che possiamo fare per personalizzare un'azione specificando parametri.

Windows PowerShell sfrutta queste analogie per ridurre il numero di nomi diversi che è necessario conoscere per comprendere e usare i cmdlet.

### <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>I cmdlet usano nomi nel formato verbo-sostantivo per semplificare la memorizzazione
Windows PowerShell usa un sistema di denominazione di tipo "verbo-sostantivo", in cui ogni cmdlet è composto da un verbo standard e un sostantivo specifico separati da un trattino. I verbi di Windows PowerShell non sono necessariamente verbi della lingua inglese, ma esprimono azioni specifiche in Windows PowerShell. I sostantivi descrivono tipi specifici di oggetti importanti nell'amministrazione del sistema. È facile dimostrare che questi nomi composti sono più semplici da memorizzare, esaminando alcuni esempi.

Per i sostantivi esistono meno restrizioni, ma dovrebbero sempre descrivere ciò su cui agisce un comando. Windows PowerShell ha comandi come **Get-Process**, **Stop-Process**, **Get-Service** e **Stop-Service**.

Nel caso di due sostantivi e due verbi, la coerenza non semplifica altrettanto l'apprendimento. Tuttavia, se si esamina un set standard composto da 10 verbi e 10 sostantivi, è necessario imparare solo 20 parole, che però possono essere usate per formare 100 diversi nomi di comando.

Spesso è possibile comprendere le finalità di un comando leggendone il nome e in genere il nome che occorre usare per un nuovo comando è evidente. Ad esempio, un comando di arresto del computer potrebbe essere **Stop-Computer**. Un comando che elenca tutti i computer in una rete potrebbe essere **Get-Computer**. Il comando che ottiene la data di sistema è **Get-Date**.

È possibile ottenere un elenco di tutti i comandi che includono uno specifico verbo usando il parametro **-Verb** per **Get-Command** (**Get-Command** è illustrato in dettaglio nella sezione successiva). Ad esempio, per vedere tutti i cmdlet che usano il verbo **Get**, digitare:

```
PS> Get-Command -Verb Get
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

Il parametro **-Noun** è ancora più utile, perché consente di visualizzare una famiglia di comandi che agiscono sullo stesso tipo di oggetto. Ad esempio, per ottenere un elenco dei comandi disponibili per la gestione dei servizi, digitare il comando seguente:

```
PS> Get-Command -Noun Service
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

Un comando non è necessariamente un cmdlet solo perché usa lo schema di denominazione verbo-sostantivo. Un esempio di comando nativo di Windows PowerShell che non è un cmdlet pur avendo un nome composto da verbo e sostantivo è il comando per cancellare il contenuto di una finestra della console, Clear-Host. Clear-Host è in realtà una funziona interna, come si può vedere eseguendo Get-Command su di essa:

```
PS> Get-Command -Name Clear-Host

CommandType     Name                            Definition
-----------     ----                            ----------
Function        Clear-Host                      $spaceType = [System.Managem...
```

### <a name="cmdlets-use-standard-parameters"></a>I cmdlet usano parametri standard
Come illustrato in precedenza, i comandi usati nelle interfacce della riga di comando tradizionali in genere non hanno nomi di parametro coerenti. In alcuni casi i parametri non hanno affatto un nome. In questo caso, spesso si tratta di singoli caratteri o parole abbreviate, rapide da digitare ma non facilmente comprensibili per i nuovi utenti.

A differenza di molte altre interfacce della riga di comando tradizionali, Windows PowerShell elabora i parametri direttamente e usa questo accesso diretto ai parametri insieme a indicazioni per la standardizzazione dei nomi rivolte agli sviluppatori. Anche se questo non garantisce che ogni cmdlet sarà sempre conforme agli standard, favorisce comunque la standardizzazione.

> [!NOTE]
> Ai nomi di parametro va sempre anteposto il simbolo '-', per consentire a Windows PowerShell di identificarli chiaramente come parametri. Nell'esempio **Get-Command -Name Clear-Host** il nome del parametro è **Name**, ma viene inserito come -**Name**.

Ecco alcune delle caratteristiche generali relativi all'uso e ai nomi di parametro standard.

#### <a name="the-help-parameter-"></a>Il parametro della Guida (?)
Se si specifica il parametro **-?** per qualsiasi cmdlet, il cmdlet non viene eseguito. Windows PowerShell visualizza invece la Guida del cmdlet.

#### <a name="common-parameters"></a>Parametri comuni
Windows PowerShell ha svariati parametri noti come *parametri comuni*. Poiché questi parametri sono controllati dal motore di Windows PowerShell, ogni volta che vengono implementati da un cmdlet si comportano allo stesso modo. I parametri comuni sono **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable** e **OutBuffer**.

#### <a name="suggested-parameters"></a>Parametri consigliati
I cmdlet fondamentali di Windows PowerShell usano nomi standard per i parametri simili. Anche se l'uso di particolari nomi di parametro non è obbligatorio, esistono linee guida esplicite mirate a favorire la standardizzazione.

Ad esempio, le linee guida consigliano di chiamare un parametro che fa riferimento a un computer in base al nome **ComputerName**, invece di usare Server, Host, System, Node o altre parole alternative comuni. Tra i principali nomi di parametro suggeriti vi sono **Force**, **Exclude**, **Include**, **PassThru**, **Path** e **CaseSensitive**.