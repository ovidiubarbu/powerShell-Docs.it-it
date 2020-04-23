---
title: Novità di PowerShell 7.0
description: Nuove funzionalità e modifiche rilasciate in PowerShell 7.0
ms.date: 03/04/2020
ms.openlocfilehash: 84631d9fa169c8d1b4cd4dd23eb3d7c1bca120bb
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "80263136"
---
# <a name="whats-new-in-powershell-70"></a>Novità di PowerShell 7.0

PowerShell 7.0 è una edizione open source multipiattaforma di PowerShell (Windows, macOS e Linux) creata per la gestione di ambienti eterogenei e del cloud ibrido.

In questa versione sono state introdotte alcune nuove funzionalità, tra cui:

- Parallelizzazione della pipeline con `ForEach-Object -Parallel`
- Nuovi operatori:
  - Operatore ternario: `a ? b : c`
  - Operatori di concatenamento delle pipeline: `||` e `&&`
  - Operatori condizionali Null: `??` e `??=`
- Visualizzazione degli errori semplificata e dinamica e cmdlet `Get-Error` per semplificare l'analisi degli errori
- Livello di compatibilità che consente agli utenti di importare i moduli in una sessione implicita di Windows PowerShell
- Notifiche automatiche di nuove versioni
- La possibilità di richiamare le risorse DSC direttamente da PowerShell 7 (sperimentale)

Per visualizzare un elenco completo delle funzionalità e delle correzioni, vedere i [log delle modifiche](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).

## <a name="where-can-i-install-powershell"></a>Dove è possibile installare PowerShell?

PowerShell 7 supporta attualmente i sistemi operativi x64 seguenti:

- Windows 8.1 e 10
- Windows Server 2012, 2012 R2, 2016 e 2019
- macOS 10.13+
- Red Hat Enterprise Linux (RHEL)/CentOS 7
- Fedora 30+
- Debian 9
- Ubuntu LTS 16.04+
- Alpine Linux 3.8+

PowerShell 7.0 supporta anche le versioni ARM32 e ARM64 Debian e Ubuntu e la versione ARM64 Alpine Linux.

Vedere le istruzioni di installazione per il sistema operativo preferito [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) o [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).

Sebbene non siano supportati ufficialmente, la community ha offerto anche pacchetti per [Arch](https://aur.archlinux.org/packages/powershell/) e Kali Linux.

> [!NOTE]
> Debian 10 e CentOS 8 attualmente non supportano la comunicazione remota WinRM. Per informazioni dettagliate sulla configurazione della comunicazione remota basata su SSH, vedere [Comunicazione remota di PowerShell su SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).

Per informazioni aggiornate sui sistemi operativi supportati e il ciclo di vita del supporto, vedere [Ciclo di vita del supporto di PowerShell](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).

## <a name="running-powershell-7"></a>Esecuzione di PowerShell 7

PowerShell 7 viene installato in una nuova directory ed eseguito side-by-side con Windows PowerShell 5.1. Per PowerShell Core 6.x, PowerShell 7 è un aggiornamento sul posto che rimuove PowerShell Core 6.x.

- PowerShell 7 è installato in `%programfiles%\PowerShell\7`
- La cartella `%programfiles%\PowerShell\7` viene aggiunta a `$env:PATH`

I pacchetti di installazione di PowerShell 7 aggiornano le versioni precedenti di PowerShell Core 6.x:

- PowerShell Core 6.x in Windows: `%programfiles%\PowerShell\6` è sostituito da `%programfiles%\PowerShell\7`
- Linux: `/opt/microsoft/powershell/6` è sostituito da `/opt/microsoft/powershell/7`
- macOS: `/usr/local/microsoft/powershell/6` è sostituito da `/usr/local/microsoft/powershell/7`

> [!NOTE]
> In Windows PowerShell l'eseguibile per l'avvio di PowerShell è denominato `powershell.exe`. Nella versione 6 e nelle versioni successive l'eseguibile è modificato per supportare l'esecuzione side-by-side. Il nuovo eseguibile per l'avvio di PowerShell 7 è `pwsh.exe`. Le build di anteprima vengono mantenute come `pwsh-preview` anziché `pwsh` nella directory di anteprima della versione 7.

## <a name="improved-backwards-compatibility-with-windows-powershell"></a>Compatibilità migliorata con le versioni precedenti di Windows PowerShell

PowerShell 7.0 comporta il passaggio verso .NET Core 3.1 offrendo una maggiore compatibilità con le versioni precedenti dei moduli di Windows PowerShell esistenti. Sono inclusi molti moduli in Windows che richiedono funzionalità GUI come `Out-GridView` e `Show-Command`, nonché molti moduli di gestione dei ruoli forniti con Windows.

Per Windows, viene aggiunto un nuovo parametro opzionale **UseWindowsPowerShell** a `Import-Module`. Questa opzione crea un modulo proxy in PowerShell 7 che usa un processo di Windows PowerShell locale per eseguire in modo implicito tutti i cmdlet contenuti nel modulo. Per altre informazioni, vedere [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).

Per altre informazioni sui moduli Microsoft che funzionano con PowerShell 7.0, vedere [Tabella di compatibilità dei moduli](https://aka.ms/PSModuleCompat).

## <a name="parallel-execution-added-to-foreach-object"></a>Esecuzione parallela aggiunta a ForEach-Object

Il cmdlet `ForEach-Object`, che esegue l'iterazione degli elementi di una raccolta, include ora il parallelismo integrato con il nuovo parametro **Parallel**.

Per impostazione predefinita, i blocchi di script paralleli usano la directory di lavoro corrente del chiamante che ha avviato le attività parallele.

Questo esempio recupera 50.000 voci di log da 5 registri di sistema in un computer Windows locale:

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

Il parametro **Parallel** specifica il blocco di script eseguito in parallelo per ogni nome di registro di input.

Il nuovo parametro **ThrottleLimit** limita il numero di blocchi di script in esecuzione in parallelo in un determinato momento. Il valore predefinito è 5.

Usare la variabile `$_` per rappresentare l'oggetto di input corrente nel blocco di script. Usare l'ambito `$using:` per passare riferimenti a variabili al blocco di script in esecuzione.

Per altre informazioni, vedere [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).

## <a name="ternary-operator"></a>Operatore ternario

PowerShell 7.0 introduce un operatore ternario che si comporta come un'istruzione `if-else` semplificata.
L'operatore ternario di PowerShell è strettamente modellato dalla sintassi dell'operatore ternario C#:

```
<condition> ? <if-true> : <if-false>
```

L'espressione condition viene sempre valutata e il risultato viene convertito in un **valore booleano** per determinare il ramo valutato successivo:

- L'espressione `<if-true>` viene eseguita se l'espressione `<condition>` è true
- L'espressione `<if-false>` viene eseguita se l'espressione `<condition>` è false

Ad esempio:

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

In questo esempio, se il percorso esiste, viene visualizzato **Path exists** (Percorso esistente). Se il percorso non esiste, viene visualizzato **Path not found** (Percorso non trovato).

Per altre informazioni, vedere [Informazioni su If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).

## <a name="pipeline-chain-operators"></a>Operatori di concatenamento delle pipeline

PowerShell 7 implementa gli operatori `&&` e `||` per concatenare le pipeline in modo condizionale. In PowerShell questi operatori sono chiamati "operatori di concatenamento delle pipeline" e sono simili agli elenchi AND e OR in shell come **Bash** e **Zsh** e ai simboli di elaborazione condizionale nella shell dei comandi di Windows (**cmd. exe**).

L'operatore `&&` esegue la pipeline di destra se la pipeline di sinistra ha avuto esito positivo. Viceversa, l'operatore `||` esegue la pipeline di destra se la pipeline di sinistra ha avuto esito negativo.

> [!NOTE]
> Questi operatori usano le variabili `$?` e `$LASTEXITCODE` per determinare se una pipeline ha avuto esito negativo. Ciò consente di usarli con comandi nativi e non solo con cmdlet o funzioni.

Di seguito, il primo comando ha esito positivo e viene eseguito il secondo comando:

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

Di seguito, il primo comando ha esito negativo e non viene eseguito il secondo comando:

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

Di seguito, il primo comando ha esito positivo e non viene eseguito il secondo comando:

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

Di seguito, il primo comando ha esito negativo e viene eseguito il secondo comando:

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

Per altre informazioni, vedere [Informazioni sugli operatori di concatenamento delle pipeline](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).

## <a name="null-coalescing-assignment-and-conditional-operators"></a>Operatori di coalescenza, di assegnazione e condizionali di valori Null

PowerShell 7 include l'operatore di coalescenza di valori Null `??`, l'operatore di assegnazione condizionale di valori Null `??=` e gli operatori di accesso membri condizionali di valori Null `?.` e `?[]`.

### <a name="null-coalescing-operator-"></a>Operatore di coalescenza di valori Null ??

L'operatore di coalescenza di valori Null `??` restituisce il valore dell'operando di sinistra se non è Null.
In caso contrario, valuta l'operando di destra e ne restituisce il risultato. L'operatore `??` non valuta l'operando di destra se l'operando di sinistra restituisce un valore non Null.

```powershell
$x = $null
$x ?? 100
100
```

Nell'esempio seguente l'operando di destra non verrà valutato:

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a>Operatore di assegnazione condizionale di valori Null ??=

L'operatore di assegnazione condizionale di valori Null `??=` assegna il valore dell'operando di destra all'operando di sinistra solo se l'operando di sinistra restituisce un valore Null. L'operatore `??=` non valuta l'operando di destra se l'operando di sinistra restituisce un valore non Null.

```powershell
$x = $null
$x ??= 100
$x
100
```

Nell'esempio seguente l'operando di destra non verrà valutato:

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a>Operatori di accesso membri condizionali di valori Null ?. e ?[] (sperimentale)

> [!NOTE]
> Questa funzionalità sperimentale è denominata **PSNullConditionalOperators**. Per altre informazioni, vedere [Funzionalità sperimentali](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).

Un operatore condizionale di valori Null consente l'accesso ai membri, `?.`, o l'accesso agli elementi, `?[]`, al relativo operando solo se l'operando restituisce un valore non Null. In caso contrario, restituisce un valore Null.

> [!NOTE]
> Poiché in PowerShell `?` può essere incluso nel nome della variabile, è necessario specificare formalmente il nome della variabile per usare questi operatori. Pertanto, è necessario usare `{}` per i nomi delle variabili, ad esempio `${a}`, o quando `?` è incluso nel nome della variabile `${a?}`.

Nell'esempio seguente viene restituito il valore della proprietà membro **Status**:

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

L'esempio seguente restituirà un valore Null senza tentare di accedere al nome del membro **Status**:

```powershell
$service = $Null
${Service}?.status
```

Analogamente, se si usa `?[]`, verrà restituito il valore dell'elemento:

```powershell
$a = 1..10
${a}?[0]
1
```

Quando l'operando è Null, non viene eseguito l'accesso all'elemento e viene restituito un valore Null:

```powershell
$a = $null
${a}?[0]
```

Per altre informazioni, vedere [Informazioni sugli operatori](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).

## <a name="new-view-conciseview-and-cmdlet-get-error"></a>Nuova visualizzazione ConciseView e nuovo cmdlet Get-Error

La visualizzazione dei messaggi di errore è stata migliorata per aumentare la leggibilità degli errori interattivi e di script con una nuova visualizzazione predefinita **ConciseView**. Le visualizzazioni possono essere selezionate dall'utente tramite la variabile di preferenza `$ErrorView`.

In **ConciseView**, se un errore non è dovuto a un errore di script o parser, viene visualizzato un messaggio di errore a riga singola:

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

Se l'errore si verifica durante l'esecuzione dello script o si tratta di un errore di analisi, PowerShell restituisce un messaggio di errore su più righe che contiene l'errore, un puntatore e un messaggio di errore che indicano la posizione dell'errore. Se il terminale non supporta le sequenze di escape dei colori ANSI (VT100), i colori non vengono visualizzati.

![Visualizzazione degli errori da uno script](./media/What-s-New-in-PowerShell-70/myscript-error.png)

La visualizzazione predefinita in PowerShell 7 è **ConciseView**. La visualizzazione predefinita precedente era **NormalView** ed era selezionabile dall'utente impostando la variabile di preferenza `$ErrorView`.

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> Una nuova proprietà **ErrorAccentColor** è stata aggiunta a `$Host.PrivateData` per supportare la modifica del colore principale del messaggio di errore.

Un nuovo cmdlet `Get-Error` offre una visualizzazione dettagliata completa dell'errore quando si desidera.
Per impostazione predefinita, il cmdlet visualizza i dettagli completi, incluse le eccezioni interne, dell'ultimo errore che si è verificato.

![Visualizzazione da Get-Error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

Il cmdlet `Get-Error` supporta l'input dalla pipeline tramite la variabile incorporata `$Error`.
`Get-Error` visualizza tutti gli errori delle pipeline.

```powershell
$Error | Get-Error
```

Il cmdlet `Get-Error` supporta il parametro **Newest** e consente di specificare il numero di errori della sessione corrente che si vuole visualizzare.

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

Per altre informazioni, vedere [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).

## <a name="new-version-notification"></a>Notifica di nuove versioni

PowerShell 7 usa le notifiche di aggiornamento per avvisare gli utenti dell'esistenza di aggiornamenti per PowerShell.
Una volta al giorno, PowerShell esegue una query su un servizio online per determinare se è disponibile una versione più recente.

> [!NOTE]
> Il controllo degli aggiornamenti si verifica durante la prima sessione in un determinato periodo di 24 ore. Per motivi di prestazioni, il controllo degli aggiornamenti inizia 3 secondi dopo l'inizio della sessione. La notifica viene visualizzata solo all'avvio delle sessioni successive.

Per impostazione predefinita, PowerShell esegue una sottoscrizione a uno dei due diversi canali di notifica, a seconda della versione/ramo. Le versioni supportate disponibili a livello generale (GA) di PowerShell restituiscono solo le notifiche per le versioni GA aggiornate. La versione di anteprima e la versione finale candidata (RC) inviano notifiche sugli aggiornamenti alle versioni di anteprima, RC e GA.

Il comportamento delle notifiche di aggiornamento può essere modificato usando la variabile di ambiente `$Env:POWERSHELL_UPDATECHECK`. Sono supportati i valori seguenti:

- **Default** corrisponde a non definire `$Env:POWERSHELL_UPDATECHECK`
  - Le versioni disponibili a livello generale (GA) inviano notifiche degli aggiornamenti alle versioni GA
  - Le versioni di anteprima/RC inviano notifiche degli aggiornamenti alle versioni GA e di anteprima
- **Off** disattiva la funzione di notifica degli aggiornamenti
- **LTS** notifica solo gli aggiornamenti alle versioni GA LTS (Long Term Servicing)

> [!NOTE]
> La variabile di ambiente `$Env:POWERSHELL_UPDATECHECK` non esiste fino a quando non viene impostata per la prima volta.

Per impostare la notifica delle versioni solo per le versioni `LTS`:

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

Per impostare la notifica delle versioni per il comportamento `Default`:

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

Per altre informazioni, vedere [Informazioni sulle notifiche degli aggiornamenti](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a>Nuovo supporto delle risorse DSC con Invoke-DSCResource (sperimentale)

> [!NOTE]
> Questa funzionalità sperimentale è denominata **PSDesiredStateConfiguration.InvokeDscResource**. Per altre informazioni, vedere [Funzionalità sperimentali](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).

Il cmdlet `Invoke-DscResource` esegue un metodo di una risorsa DSC (Desired State Configuration) specificata di PowerShell.

Questo cmdlet richiama direttamente una risorsa DSC senza creare un documento di configurazione. Usando questo cmdlet, i prodotti di gestione della configurazione possono gestire Windows o Linux usando le risorse DSC. Questo cmdlet abilita anche il debug delle risorse quando il motore DSC è in esecuzione con il debug abilitato.

Questo comando richiama il metodo **Set** di una risorsa denominata Log e specifica una proprietà **Message**.

```powershell
Invoke-DscResource -Name Log -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Message = 'Hello World'
}
```

Per altre informazioni, vedere [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).

## <a name="breaking-changes-and-improvements"></a>Modifiche e miglioramenti di rilievo

### <a name="breaking-changes"></a>Modifiche di rilievo

- Supporto delle notifiche degli aggiornamenti per LTS e i canali predefiniti (#11132)
- Aggiornamento di Test-Connection per un funzionamento più simile a quello in Windows PowerShell (#10697) (grazie @vexx32!)
- Mantenimento di $? per ParenExpression, SubExpression e ArrayExpression (#11040)
- Impostazione della directory di lavoro sulla directory corrente in Start-Job (#10920) (grazie @iSazonov!)
- $PSCulture riflette in modo coerente le modifiche delle impostazioni cultura della sessione (#10138) (grazie @iSazonov!)

### <a name="engine-updates-and-fixes"></a>Aggiornamenti e correzioni del motore

- Miglioramenti nelle API dei punti di interruzione per gli scenari remoti (#11312)
- Correzione della perdita della definizione di classe PowerShell in un altro spazio di esecuzione (#11273)
- Correzione di una regressione nella formattazione causata dalla primitiva FirstOrDefault aggiunta in 7.0.0-Preview1 (#11258)
- Moduli Microsoft aggiuntivi per tenere traccia dei dati di telemetria di PS7 (#10751)
- Conversione delle funzionalità approvate in funzionalità non sperimentali (#11303)
- Aggiornamento di ConciseView per l'uso di TargetObject, se applicabile (#11075)
- Correzione di NullReferenceException nei metodi pubblici CompletionCompleters (#11274)
- Correzione del controllo dello stato del thread apartment nelle piattaforme non Windows (#11301)
- Aggiornamento dell'impostazione PSModulePath per concatenare le variabili di ambiente del processo e del computer (#11276)
- Aggiornamento di .NET Core alla versione 3.1.0 (#11260)
- Correzione del rilevamento di $PSHOME che precede $env:PATH (#11141)
- Possibilità di pwsh di ereditare $env:PSModulePath e abilitare powershell.exe per un avvio corretto (#11057)
- Passaggio a .NET Core 3.1 Preview 1 (#10798)
- Refactoring dei controlli dei tag di rianalisi nel provider del file system (#10431) (grazie @iSazonov!)
- Sostituzione di CR e nuova riga con un carattere 0x23CE nella registrazione degli script (#10616)
- Correzione della perdita di una risorsa tramite l'annullamento della registrazione del gestore dell'evento da AppDomain.CurrentDomain.ProcessExit (#10626)
- Aggiunta del supporto in ActionPreference.Break per interrompere l'esecuzione nel debugger quando vengono generati messaggi di debug, errore, informazioni, stato, Verbose o di avviso (#8205) (grazie @KirkMunro!)
- Abilitazione dell'avvio di componenti aggiuntivi del pannello di controllo all'interno di PowerShell Core senza specificare l'estensione CPL. (#9828)
- Supporto di numeri negativi nell'operatore -split (#8960) (ringraziamenti @ece-jacob-scott!)

### <a name="general-cmdlet-updates-and-fixes"></a>Aggiornamenti e correzioni generali dei cmdlet

- Correzione del problema in Raspbian per l'impostazione della data delle modifiche dei file nella funzionalità sperimentale UnixStat (#11313)
- Aggiunta di -AsPlainText a ConvertFrom-SecureString (#11142)
- Aggiunta del controllo della versione WindowsPS per WinCompat (#11148)
- Correzione della segnalazione degli errori in alcuni scenari WinCompat (#11259)
- Aggiunta del sistema di risoluzione binario nativo (#11032) (grazie @iSazonov!)
- Aggiornamento del calcolo della larghezza del carattere per rispettare correttamente i caratteri CJK (#11262)
- Aggiunta di Unblock-File per macOS (#11137)
- Correzione della regressione in Get-PSCallStack (#11210) (grazie @iSazonov!)
- Rimozione del caricamento automatico del modulo ScheduledJob quando si usano i cmdlet Job (#11194)
- Aggiunta di OutputType al cmdlet Get-Error e mantenimento dei TypeName originali (#10856)
- Correzione di un riferimento Null nella proprietà SupportsVirtualTerminal (#11105)
- Aggiunta di un controllo del limite in Get-WinEvent (#10648) (grazie @iSazonov!)
- Correzione del runtime del comando in modo che StopUpstreamCommandsException non venga popolato in -ErrorVariable (#10840)
- Impostazione della codifica di output su [Console]::OutputEncoding per i comandi nativi (#10824)
- Supporto di blocchi di codice a più righe negli esempi (#10776) (grazie @Greg-Smulko!)
- Aggiunta del parametro Culture al cmdlet Select-String (#10943) (grazie @iSazonov!)
- Correzione del percorso della directory di lavoro Start-Job con barra rovesciata finale (#11041)
- ConvertFrom-Json: Annullamento del wrapping delle raccolte per impostazione predefinita (#10861) (grazie @danstur!)
- Uso di una tabella hash con distinzione tra maiuscole e minuscole per il cmdlet Group-Object con le opzioni -CaseSensitive e -AsHashtable (#11030) (grazie @vexx32!)
- Gestione dell'eccezione se l'enumerazione dei file ha esito negativo quando si ricompila il percorso per avere la combinazione di maiuscole e minuscole corretta (#11014)
- Correzione di ConciseView per visualizzare Activity anziché myCommand (#11007)
- Possibilità per i cmdlet Web di ignorare gli stati degli errori HTTP (#10466) (grazie @vdamewood!)
- Correzione del piping di più CommandInfo in Get-Command (#10929)
- Aggiunta del cmdlet Get-Counter per Windows (#10933)
- Conversione del treat ConvertTo-Json [AutomationNull]::Value e [NullString]::Value in $null (#10957)
- Rimozione delle parentesi quadre dall'indirizzo IPv6 per la comunicazione remota SSH (#10968)
- Correzione dell'arresto anomalo se il comando inviato a pwsh è solo uno spazio vuoto (#10977)
- Aggiunta di Get-Clipboard e Set-Clipboard multipiattaforma (#10340)
- Correzione dell'impostazione del percorso originale dell'oggetto filesystem in modo che non abbia una barra finale aggiuntiva (#10959)
- Supporto di $Null per ConvertTo-Json (#10947)
- Aggiunta del comando Out-Printer in Windows (#10906)
- Correzione di Start-Job -WorkingDirectory con spazio vuoto (#10951)
- Restituzione del valore predefinito quando si recupera un valore Null per un'impostazione in PSConfiguration.cs (#10963) (grazie @iSazonov!)
- Gestione dell'eccezione I/O come non fatale (#10950)
- Aggiunta dell'assembly GraphicalHost per abilitare Out-GridView, Show-Command e Get-Help -ShowWindow (#10899)
- Recupero di ComputerName tramite pipeline in Get-HotFix (#10852) (grazie @kvprasoon!)
- Correzione del completamento tramite TAB per i parametri in modo che mostri i parametri comuni come disponibili (#10850)
- Correzione di GetCorrectCasedPath() per controllare innanzitutto se vengono restituite voci di file di sistema prima di chiamare First() (#10930)
- Impostazione della directory di lavoro sulla directory corrente in Start-Job (#10920) (grazie @iSazonov!)
- Modifica di TabExpansion2 in modo che non richieda -CursorColumn e venga trattata come $InputScript.Length (#10849)
- Gestione del caso in cui Host non può restituire righe o colonne della schermata (#10938)
- Correzione dell'uso dei colori principali per gli host che non li supportano (#10937)
- Aggiunta del comando Update-List (#10922)
- Aggiornamento dell'ID FWLink per Clear-RecycleBin (#10925)
- Durante il completamento tramite TAB, ignorare il file se non è in grado di leggere gli attributi del file (#10910)
- Aggiunta di Clear-RecycleBin per Windows (#10909)
- Aggiunta di `$env:__SuppressAnsiEscapeSequences` per controllare se è presente una sequenza di escape VT nell'output (#10814)
- Aggiunta del parametro -NoEmphasize per colorare l'output di Select-String (#8963) (grazie @derek-xia!)
- Aggiunta del cmdlet Get-HotFix (#10740)
- Add-Type utilizzabile nelle applicazioni che ospitano PowerShell (#10587)
- Uso di un ordine di valutazione più efficace in LanguagePrimitives.IsNullLike() (#10781) (grazie @vexx32!)
- Miglioramento della gestione di input e flussi di input della pipeline della raccolta in Format-Hex (#8674) (grazie @vexx32!)
- Uso della conversione del tipo nelle tabelle hash SSHConnection quando il valore non corrisponde al tipo previsto (#10720) (grazie @SeeminglyScience!)
- Correzione del comportamento di Get-Content -ReadCount 0 quando viene impostato -TotalCount (#10749) (grazie @eugenesmlv!)
- Ridefinizione del messaggio di errore di accesso negato in Get-WinEvent (#10639) (grazie @iSazonov!)
- Abilitazione del completamento tramite tasto TAB per l'assegnazione di variabili vincolata da enumerazione o tipo (#10646)
- Rimozione della proprietà remota SourceLength inutilizzata che causa problemi di formattazione (#10765)
- Aggiunta del parametro -Delimiter a ConvertFrom-StringData (#10665) (grazie @steviecoaster!)
- Aggiunta del parametro posizionale per ScriptBlock quando si usa Invoke-Command con SSH (#10721) (grazie @machgo!)
- Visualizzazione delle informazioni di contesto della riga se sono presenti più righe ma nessun nome di script per ConciseView (#10746)
- Aggiunta del supporto per i percorsi \\wsl$\ al provider del file system (#10674)
- Aggiunta del testo del token mancante per TokenKind.QuestionMark nel parser (#10706)
- Impostazione della directory di lavoro corrente di ogni script in esecuzione ForEach-Object -Parallel sullo stesso percorso dello script chiamante. (#10672)
- Sostituzione di api-ms-win-core-file-l1-2-2.dll con Kernell32.dll per le API FindFirstStreamW e FindNextStreamW (#10680) (grazie @iSazonov!)
- Perfezionamento dello script di formattazione della Guida per maggiore supporto di StrictMode (#10563)
- Aggiunta del parametro -SecurityDescriptorSDDL a New-Service (#10483) (grazie @kvprasoon!)
- Rimozione dell'output informativo, consolidamento dell'utilizzo dei ping in Test-Connection (#10478) (grazie @vexx32!)
- Lettura dei punti di analisi speciali senza eseguire l'accesso (#10662) (grazie @iSazonov!)
- Indirizzamento dell'output Clear-Host al terminale (#10681) (grazie @iSazonov!)
- Aggiunta di una nuova riga per il raggruppamento con Format-Table e -Property (#10653)
- Rimozione di [ValidateNotNullOrEmpty] da -InputObject in Get-Random per consentire una stringa vuota (#10644)
- Impostazione dell'algoritmo della distanza delle stringhe del sistema dei suggerimenti senza distinzione tra maiuscole e minuscole (#10549) (grazie @iSazonov!)
- Correzione dell'eccezione di riferimento Null nell'elaborazione dell'input ForEach-Object -Parallel (#10577)
- Aggiunta delle definizioni dei criteri di gruppo di PowerShell Core (#10468)
- Aggiornamento dell'host della console per il supporto delle sequenza di controllo VT XTPUSHSGR/XTPOPSGR usante negli scenari di composizione. (#10208)
- Aggiunta del parametro WorkingDirectory a Start-Job (#10324) (grazie @davinci26!)
- Rimozione del gestore dell'evento che ha causato la replica erronea delle modifiche del punto di interruzione nel debugger dello spazio di esecuzione dell'host (#10503) (grazie @KirkMunro!)
- Sostituzione di api-ms-win-core-job-12-1-0.dll con Kernell32.dll nell'API P/Invoke Microsoft.PowerShell.Commands.NativeMethods (#10417) (grazie @iSazonov!)
- Correzione dell'output errato per New-Service nell'assegnazione di variabili e -OutVariable (#10444) (grazie @kvprasoon!)
- Risoluzione dei problemi degli strumenti globali per il codice di uscita, i parametri della riga di comando e il percorso con spazi (#10461)
- Correzione della ricorsione in OneDrive - modifica di FindFirstFileEx() per l'uso del tipo SafeFindHandle (#10405)
- Possibilità di ignorare il caricamento automatico di PSReadLine in Windows se il lettore NVDA è attivo (#10385)
- Aggiornamento delle versioni del modulo built-with-PowerShell alla versione 7.0.0.0 (#10356)
- Aggiunta della generazione di un errore in Add-Type se esiste già un tipo con lo stesso nome (#9609) (grazie @iSazonov!)

### <a name="performance"></a>Prestazioni

- Mancato utilizzo della chiusura in Parser.SaveError (#11006)
- Miglioramento della memorizzazione nella cache durante la creazione di nuove istanze Regex (#10657) (grazie @iSazonov!)
- Miglioramento dell'elaborazione dei dati del tipo predefinito di PowerShell da types.ps1xml, typesV3.ps1xml e GetEvent.types.ps1xml (#10898)
- Aggiornamento di PSConfiguration.ReadValueFromFile per renderlo più veloce e più efficiente per la memoria (#10839)
- Aggiunta di miglioramenti delle prestazioni secondari per l'inizializzazione dello spazio di esecuzione (#10569) (grazie @iSazonov!)
- ForEach-Object più veloce per gli scenari di uso comune (#10454) e correzione del problema di prestazioni di ForEach-Object -Parallel con molti spazi di esecuzione (#10455)

### <a name="code-cleanup"></a>Pulizia del codice

- Modifica del testo di commenti ed elementi per soddisfare gli standard Microsoft (#11304)
- Pulizia dei problemi di stile in Compiler.cs (#10368) (grazie @iSazonov!)
- Rimozione del convertitore di tipi non usati per CommaDelimitedStringCollection (#11000) (grazie @iSazonov!)
- Pulizia dello stile in InitialSessionState.cs (#10865) (grazie @iSazonov!)
- Pulizia del codice per la classe PSSession (#11001)
- Rimozione della funzionalità 'run Update-Help from Get-Help when Get-Help runs for the first time' non funzionante (#10974)
- Risoluzione dei problemi di stile (#10998) (grazie @iSazonov!)
- Pulizia: uso dell'alias di tipo predefinito (#10882) (grazie @iSazonov!)
- Rimozione della chiave di impostazione non usata ConsolePrompting e rimozione della creazione di stringhe non necessarie quando si esegue una query sull'impostazione ExecutionPolicy (#10985)
- Disabilitazione del controllo delle notifiche degli aggiornamenti per le build giornaliere (#10903) (grazie @bergmeister!)
- Reintegro dell'API di debug persa in #10338 (#10808)
- Rimozione del riferimento a WorkflowJobSourceAdapter non più usato (#10326) (grazie @KirkMunro!)
- Pulizia delle interfacce COM nel codice delle jump list tramite la correzione degli attributi PreserveSig (#9899) (grazie @weltkante!)
- Aggiunta di un commento che descrive perché -ia non è l'alias per il parametro comune -InformationAction (#10703) (grazie @KirkMunro!)
- Ridenominazione di InvokeCommandCmdlet.cs in InvokeExpressionCommand.cs (#10659) (grazie @kilasuit!)
- Aggiunta di pulizie del codice secondarie correlate alle notifiche degli aggiornamenti (#10698)
- Rimozione della logica del flusso di lavoro deprecato dagli script di installazione remota (#10320) (grazie @KirkMunro!)
- Aggiornamento del formato della Guida per l'uso appropriato delle maiuscole e minuscole (#10678) (grazie @tnieto88!)
- Pulizia dei problemi di stile di CodeFactor che si verificano nei commit dell'ultimo mese (#10591) (grazie @iSazonov!)
- Correzione dell'errore di ortografia nella descrizione della funzionalità sperimentale PSTernaryOperator (#10586) (grazie @bergmeister!)
- Conversione del valore di enumerazione ActionPreference.Suspend in uno stato riservato non supportato e rimozione della restrizione sull'uso di ActionPreference.Ignore nelle variabili di preferenza (#10317) (grazie @KirkMunro!)
- Sostituzione di ArrayList con List<T> per ottenere un codice più leggibile e affidabile senza modificare la funzionalità (#10333) (grazie @iSazonov!)
- Correzioni allo stile del codice in TestConnectionCommand (#10439) (grazie @vexx32!)
- Pulizia di AutomationEngine e rimozione della chiamata al metodo SetSessionStateDrive aggiuntiva (#10416) (grazie @iSazonov!)
- Ridenominazione di ParameterSetName predefinito in Delimiter per ConvertTo-Csv e ConvertFrom-Csv (#10425)

### <a name="tools"></a>Strumenti

- Aggiunta dell'impostazione predefinita per la proprietà SDKToUse in modo che venga compilata in VS (#11085)
- Install-Powershell.ps1: Aggiunta del parametro per l'uso dell'installazione MSI (#10921) (grazie @MJECloud!)
- Aggiunta di esempi di base per install-powershell.ps1 (#10914) (grazie @kilasuit!)
- Install-PowerShellRemoting.ps1 gestisce la stringa vuota nel parametro PowerShellHome (#10526) (grazie @Orca88!)
- Passaggio da /etc/lsb-release a /etc/os-release in install-powershell.sh (#10773) (grazie @Himura2la!)
- Controllo di pwsh.exe e pwsh nella versione giornaliera in Windows (#10738) (grazie @centreboard!)
- Rimozione del tocco non necessario in installpsh-osx.sh (#10752)
- Aggiornamento di install-powershell.ps1 per verificare la presenza di una build giornaliera già installata (#10489)

### <a name="tests"></a>Test

- Test DSC non affidabili in sospeso (#11131)
- Correzione del test stringdata per convalidare correttamente le chiavi di tabelle hash (#10810)
- Scaricamento di moduli di test (#11061) (grazie @iSazonov!)
- Aumento dell'intervallo di tempo tra i tentativi degli URL di test (#11015)
- Aggiornamento dei test per una descrizione accurata delle azioni di test. (#10928) (grazie @romero126!)
- Possibilità di ignorare temporaneamente il test inattendibile TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)
- Stabilità del test di perdita del gestore dell'evento (#10790)
- Sincronizzazione delle iniziali maiuscole in CI YAML (#10767) (grazie @RDIL!)
- Aggiunta del test per la correzione della perdita del gestore dell'evento (#10768)
- Aggiunta del test Get-ChildItem (#10507) (grazie @iSazonov!)
- Sostituzione del linguaggio ambiguo per i test da opzione a parametro per maggior accuratezza (#10666) (grazie @romero126!)
- Aggiunta del controllo sperimentale ai test ForEach-Object -Parallel (#10354) (grazie @KirkMunro!)
- Aggiornamento dei test per la convalida Alpine (#10428)

### <a name="build-and-package-improvements"></a>Miglioramenti di build e pacchetti

- Correzione della firma dei pacchetti NuGet per la build Coordinated Package (#11316)
- Aggiornamento delle dipendenze da PowerShell Gallery e NuGet (#11323)
- Aggiornamento di Microsoft.ApplicationInsights dalla versione 2.11.0 alla versione 2.12.0 (#11305)
- Aggiornamento di Microsoft.CodeAnalysis.CSharp dalla versione 3.3.1 alla versione 3.4.0 (#11265)
- Aggiornamento dei pacchetti per Debian 10 e 11 (#11236)
- Abilitazione delle funzionalità sperimentali solo prima della versione RC (#11162)
- Aggiornamento della versione minima di macOS (#11163)
- Aggiornamento di NJsonSchema dalla versione 10.0.27 alla versione 10.0.28 (#11170)
- Aggiornamento dei collegamenti in README.md e metadata.json per la versione Preview.5 (#10854)
- Selezione dei file per i test di conformità di proprietà di PowerShell (#10837)
- Compilazione del pacchetto msix di win7x86. (Interno 10515)
- Passaggio di versioni semantiche alla funzione NormalizeVersion (#11087)
- Aggiornamento del framework .NET Core alla versione 3.1-Preview.3 (#11079)
- Aggiornamento di PSReadLine dalla versione 2.0.0-beta5 alla versione 2.0.0-beta6 in /src/Modules (#11078)
- Aggiornamento di Newtonsoft.Json dalla versione 12.0.2 alla versione 12.0.3 (#11037) (#11038)
- Aggiunta dei pacchetti Debian 10, 11 e CentOS 8 (#11028)
- Caricamento del file JSON Build-Info con il campo ReleaseDate (#10986)
- Aggiornamento del framework .NET Core alla versione 3.1-Preview.2 (#10993)
- Abilitazione della compilazione del pacchetto MSIX x86 (#10934)
- Aggiornamento dell'URL dello script di installazione DotNet SDK in build.psm1 (#10927)
- Aggiornamento di Markdig.Signed dalla versione 0.17.1 alla versione 0.18.0 (#10887)
- Aggiornamento di ThreadJob dalla versione 2.0.1 alla versione 2.0.2 (#10886)
- Aggiornamento del manifesto AppX e del modulo di creazione pacchetti per soddisfare i requisiti di MS Store (#10878)
- Aggiornamento del riferimento al pacchetto per PowerShell SDK nella versione Preview.5 (Interno 10295)
- Aggiornamento di ThirdPartyNotices.txt (#10834)
- Aggiornamento di Microsoft.PowerShell.Native alla versione 7.0.0-Preview.3 (#10826)
- Aggiornamento di Microsoft.ApplicationInsights dalla versione 2.10.0 alla versione 2.11.0 (#10608)
- Aggiornamento di NJsonSchema dalla versione 10.0.24 alla versione 10.0.27 (#10756)
- Aggiunta del supporto MacPorts al sistema di compilazione (#10736) (grazie @Lucius-Q-User!)
- Aggiornamento di PackageManagement dalla versione 1.4.4 alla versione 1.4.5 (#10728)
- Aggiornamento di NJsonSchema dalla versione 10.0.23 alla versione 10.0.24 (#10635)
- Aggiunta della variabile di ambiente per distinguere i dati di telemetria client/server in MSI (#10612)
- Aggiornamento di PSDesiredStateConfiguration dalla versione 2.0.3 alla versione 2.0.4 (#10603)
- Aggiornamento di Microsoft.CodeAnalysis.CSharp dalla versione 3.2.1 alla versione 3.3.1 (#10607)
- Aggiornamento a .Net Core 3.0 RTM (#10604) (grazie @bergmeister!)
- Aggiornamento della creazione pacchetti MSIX per la versione per soddisfare i requisiti di Windows Store (#10588)
- Aggiornamento di PowerShellGet dalla versione 2.2 alla versione 2.2.1 (#10382)
- Aggiornamento di PackageManagement dalla versione 1.4.3 alla versione 1.4.4 (#10383)
- Aggiornamento di README.md e metadata.json per la versione 7.0.0-Preview.4 (Interno 10011)
- Aggiornamento di .Net Core 3.0 dalla versione Preview 9 alla versione RC1 (#10552) (grazie @bergmeister!)
- Correzione della generazione dell'elenco ExperimentalFeature (Interno 9996)
- Aggiornamento di PSReadLine dalla versione 2.0.0-beta4 alla versione 2.0.0-beta5 (#10536)
- Correzione dello script di compilazione della versione per l'impostazione del tag di versione
- Aggiornamento della versione di Microsoft.PowerShell.Native alla versione 7.0.0-Preview.2 (#10519)
- Aggiornamento a Netcoreapp3.0 preview9 (#10484) (grazie @bergmeister!)
- Verifica che la build coordinata giornaliera venga considerata come build giornaliera (#10464)
- Aggiornamento della build del pacchetto combinato per il rilascio di build giornaliere (#10449)
- Rimozione del riferimento ad appveyor (#10445) (grazie @RDIL!)
- Aggiornamento di NJsonSchema dalla versione 10.0.22 alla versione 10.0.23 (#10421)
- Rimozione dell'eliminazione della cartella della build linux-x64 perché richiesta da alcune dipendenze per Alpine (#10407)

### <a name="documentation-and-help-content"></a>Documentazione e contenuto della Guida

- Refactoring dei log delle modifiche in un unico log per ogni versione (#11165)
- Correzione dei FWLink per i documenti della Guida in linea di PowerShell 7 (#11071)
- Aggiornamento di CONTRIBUTING.md (#11096) (grazie @mklement0!)
- Correzione dei collegamenti della documentazione di installazione in README.md (#11083)
- Aggiunta di esempi allo script install-powershell.ps1 (#11024) (grazie @kilasuit!)
- Correzione dell'enfasi Select-String e Import-DscResource in CHANGELOG.md (#10890)
- Rimozione del collegamento non aggiornato da powershell-beginners-guide.md (#10926)
- Unione dei log delle modifiche stabili e di manutenzione (#10527)
- Aggiornamento della versione di .NET usata nelle documentazioni delle build (#10775) (grazie @Greg-Smulko!)
- Sostituzione dei collegamenti di MSDN a docs.microsoft.com in powershell-beginners-guide.md (#10778) (grazie @iSazonov!)
- Correzione del collegamento di panoramica DSC interrotto (#10702)
- Aggiornamento di Support_Question.md per il collegamento a Stack Overflow come risorsa di community diversa (#10638) (grazie @mklement0!)
- Aggiunta dell'architettura del processore al modello di richiesta di distribuzione (#10661)
- Aggiunta di un nuovo libro MoL di PowerShell alla documentazione di PowerShell per l'apprendimento (#10602)
- Aggiornamento di README.md e dei metadati per le versioni v6.1.6 e v6.2.3 (#10523)
- Correzione di un errore di ortografia in README.md (#10465) (grazie @vedhasp!)
- Aggiunta di un riferimento al modulo PSKoans alla documentazione delle risorse didattiche (#10369) (grazie @vexx32!)
- Aggiornamento di README.md e metadata.json per 7.0.0-Preview. 3 (#10393)
