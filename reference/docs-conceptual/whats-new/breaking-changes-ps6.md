---
ms.date: 05/17/2018
keywords: powershell,core
title: Modifiche di rilievo in PowerShell Core 6.0
ms.openlocfilehash: d25cf07baa11040af57f330feede44635c00c551
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623926"
---
# <a name="breaking-changes-for-powershell-60"></a>Modifiche di rilievo in PowerShell Core 6.0

## <a name="features-no-longer-available-in-powershell-core"></a>Funzionalità non più disponibili in PowerShell Core

### <a name="powershell-workflow"></a>Flusso di lavoro PowerShell

[Flusso di lavoro PowerShell][workflow] è una funzionalità di Windows PowerShell basata su [Windows Workflow Foundation (WF)][workflow-foundation] che consente di creare runbook affidabili per le attività di lunga durata o parallelizzate.

A causa della mancanza di supporto per Windows Workflow Foundation in .NET Core, Flusso di lavoro PowerShell non continuerà a essere supportato in PowerShell Core.

In futuro, è prevista l'abilitazione di parallelismo/concorrenza nativi nel linguaggio di PowerShell senza la necessità di Flusso di lavoro PowerShell.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Snap-in personalizzati

Gli [snap-in di PowerShell][snapin] sono predecessori dei moduli di PowerShell, che non sono stati adottati diffusamente nella community di PowerShell.

A causa della complessità di supportare gli snap-in e dello scarso utilizzo nella community, gli snap-in personalizzati non sono più supportati in PowerShell Core.

Attualmente, ciò causa problemi per i moduli `ActiveDirectory` e `DnsClient` in Windows e Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>Cmdlet WMI v1

A causa della complessità del supporto di due set di moduli basati su WMI, i cmdlet WMI v1 sono stati rimossi da PowerShell Core:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

In alternativa, viene consigliato l'uso dei cmdlet CIM (noti anche come WMI versione 2) che offrono le stesse funzionalità con alcune novità e una sintassi riprogettata:

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

A causa dell'uso di API non supportate, `Microsoft.PowerShell.LocalAccounts` è stato rimosso da PowerShell Core finché non viene trovata una soluzione migliore.

### <a name="-computer-cmdlets"></a>Cmdlet di `*-Computer`

A causa dell'uso di API non supportate, i cmdlet seguenti sono stati rimossi da PowerShell Core finché non viene trovata una soluzione migliore.

- Add-Computer
- Checkpoint-Computer
- Remove-Computer
- Restore-Computer

### <a name="-counter-cmdlets"></a>Cmdlet di `*-Counter`

A causa dell'uso di API non supportate, `*-Counter` è stato rimosso da PowerShell Core finché non viene trovata una soluzione migliore.

### <a name="-eventlog-cmdlets"></a>Cmdlet di `*-EventLog`

A causa dell'uso di API non supportate, `*-EventLog` è stato rimosso da PowerShell Core fino a quando non viene trovata una soluzione migliore. `Get-WinEvent` e `Create-WinEvent` sono disponibili per ottenere e creare gli eventi in Windows.

## <a name="enginelanguage-changes"></a>Modifiche del motore/linguaggio

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Rinominare `powershell.exe` in `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Per offrire agli utenti un modo deterministico per chiamare PowerShell Core in Windows (in contrapposizione a Windows PowerShell), il file binario di PowerShell Core è stato modificato in `pwsh.exe` in Windows e in `pwsh` nelle piattaforme non Windows.

Il nome abbreviato è anche coerente con la denominazione delle shell in piattaforme non Windows.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Non inserire interruzioni di riga nell'output (ad eccezione delle tabelle) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

In precedenza, l'output veniva allineato alla larghezza della console e venivano aggiunte interruzioni di riga alla fine in base alla larghezza della console. L'output non veniva però riformattato come previsto in caso di ridimensionamento del terminale. Questa modifica non è stata applicata alle tabelle, perché le interruzioni di riga sono necessarie per mantenere allineate le colonne.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Ignorare il controllo degli elementi Null per le raccolte con elementi di tipo valore [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Per il parametro `Mandatory` e gli attributi `ValidateNotNull` e `ValidateNotNullOrEmpty`, ignorare il controllo degli elementi Null se il tipo di elemento della raccolta è un tipo valore.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Modificare `$OutputEncoding` per usare la codifica `UTF-8 NoBOM` invece di ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

La codifica precedente, ASCII (7 bit), comporterebbe la modifica non corretta dell'output in alcuni casi. Questa modifica è finalizzata a rendere `UTF-8 NoBOM` la codifica predefinita, in modo da mantenere l'output in formato Unicode con una codifica supportata dalla maggior parte degli strumenti e dei sistemi operativi.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Rimuovere `AllScope` dalla maggior parte degli alias predefiniti [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Per velocizzare la creazione dell'ambito, `AllScope` è stato rimosso dalla maggior parte degli alias predefiniti. `AllScope` è stato lasciato per alcuni alias usati di frequente in cui la ricerca era più veloce.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` e `-Debug` non eseguono più l'override di `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

In precedenza, specificando `-Verbose` o `-Debug` veniva eseguito l'override del comportamento di `$ErrorActionPreference`. Con questa modifica, `-Verbose` e `-Debug` non influiscono più sul comportamento di `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Modifiche dei cmdlet

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Invoke-RestMethod non restituisce informazioni utili quando non vengono restituiti dati. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Quando un'API restituisce solo `null`, Invoke-RestMethod serializza questo valore come stringa `"null"` anziché come `$null`. Questa modifica consente di correggere la logica in `Invoke-RestMethod` per serializzare correttamente un singolo valore letterale valido JSON `null` come `$null`.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Rimozione di `-ComputerName` dai cmdlet `*-Computer` [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

A causa di problemi con la comunicazione remota RPC in CoreFX (in particolare nelle piattaforme non Windows) e per garantire un'esperienza coerente di comunicazione remota in PowerShell, il parametro `-ComputerName` è stato rimosso dai cmdlet `\*-Computer`. Usare invece `Invoke-Command` come modo per eseguire i cmdlet in remoto.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Rimuovere `-ComputerName` dai cmdlet `*-Service` [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

Per favorire l'uso coerente di PSRP, il parametro `-ComputerName` è stato rimosso dai cmdlet `*-Service`.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Correggere `Get-Item -LiteralPath a*b` se `a*b` non esiste per restituire un errore [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

In precedenza, `-LiteralPath` con un carattere jolly specificato veniva considerato uguale a `-Path` e se il carattere jolly non trovava alcun file, il cmdlet veniva chiuso senza messaggi. Il comportamento corretto prevede che `-LiteralPath` sia un valore letterale in modo che generi un errore se il file non esiste. La modifica consiste nel considerare i caratteri jolly usati con `-Literal` come valore letterale.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` deve applicare `PSTypeNames` al momento dell'importazione quando nel CSV sono presenti informazioni sui tipi [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

In precedenza, gli oggetti esportati usando `Export-CSV` con `TypeInformation` e importati con `ConvertFrom-Csv` non mantenevano le informazioni sui tipi. Questa modifica aggiunge le informazioni sui tipi al membro `PSTypeNames` se disponibili dal file CSV.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` deve essere l'impostazione predefinita per `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Questa modifica è stata apportata in risposta ai commenti e suggerimenti dei clienti in merito al comportamento predefinito di `Export-CSV` per includere le informazioni sui tipi.

In precedenza, il cmdlet restituiva un commento come prima riga, contenente il nome del tipo dell'oggetto. La modifica prevede l'esclusione di questo comportamento per impostazione predefinita, perché non è riconosciuto dalla maggior parte degli strumenti. Usare `-IncludeTypeInformation` per mantenere il comportamento precedente.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>I cmdlet Web devono generare un avviso in caso di invio di `-Credential` su connessioni non crittografate [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Quando si usa HTTP, il contenuto che include password viene inviato come testo non crittografato. La modifica consiste nel non consentire questo comportamento per impostazione predefinita, con restituzione di un errore se le credenziali vengono passate in modo non sicuro. Gli utenti possono ignorare questa nuova impostazione usando l'opzione `-AllowUnencryptedAuthentication`.

## <a name="api-changes"></a>Modifiche delle API

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Rimuovere la classe `AddTypeCommandBase` [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

La classe `AddTypeCommandBase` è stata rimossa da `Add-Type` per migliorare le prestazioni. Questa classe viene usata solo dal cmdlet Add-Type e non dovrebbe avere effetti sugli utenti.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Tipo unificato `System.Text.Encoding` per i cmdlet con il parametro `-Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

Il valore `-Encoding` `Byte` è stato rimosso dai cmdlet per il provider filesystem. Viene ora usato un nuovo parametro, `-AsByteStream`, per specificare che un flusso di byte è richiesto come input o che l'output è un flusso di byte.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Aggiunta di un messaggio di errore migliore per il parametro `-UFormat` vuoto o Null [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

In precedenza, al passaggio di una stringa di formato vuota a `-UFormat` veniva visualizzato un messaggio di errore poco utile. È stato aggiunto un errore più descrittivo.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Pulizia del codice della console [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Le funzionalità seguenti sono state rimosse e non sono supportate in PowerShell Core e non è prevista l'aggiunta del supporto perché esistono per motivi legacy per Windows PowerShell: opzione `-psconsolefile` e codice, opzione `-importsystemmodules` e codice e codice per la modifica del tipo di carattere.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Rimuovere il supporto di `RunspaceConfiguration` [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

In precedenza, per la creazione di uno spazio di esecuzione di PowerShell a livello di codice con l'API era possibile usare la classe legacy [`RunspaceConfiguration`][runspaceconfig] o la più recente [`InitialSessionState`][iss]. Con questa modifica viene rimosso il supporto per `RunspaceConfiguration` ed è ora supportata solo la classe `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` associa gli argomenti a `$input` invece che a `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

A causa della posizione non corretta di un parametro, gli argomenti vengono passati come input invece che come argomenti.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Rimozione dell'opzione `-showwindow` non supportata da `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` si basa su WPF, che non è supportato in CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Consentire l'uso di * nel percorso del Registro di sistema per `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

In precedenza, `-LiteralPath` con un carattere jolly specificato veniva considerato uguale a `-Path` e se il carattere jolly non trovava alcun file, il cmdlet veniva chiuso senza messaggi. Il comportamento corretto prevede che `-LiteralPath` sia un valore letterale in modo che generi un errore se il file non esiste. La modifica consiste nel considerare i caratteri jolly usati con `-Literal` come valore letterale.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Correzione per l'esito negativo del test per `Set-Service` [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

In precedenza, usando `New-Service -StartupType foo` `foo` veniva ignorato e il servizio veniva creato con un tipo di avvio predefinito. La modifica consiste nel generare in modo esplicito un errore per un tipo di avvio non valido.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Rinominare `$IsOSX` in `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

La denominazione in PowerShell dovrebbe essere coerente con la denominazione Microsoft e conforme all'uso da parte di Apple di macOS invece di OSX. Ai fini della leggibilità e della coerenza, tuttavia, viene mantenuta la combinazione di maiuscole/minuscole Pascal.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Rendere coerente il messaggio di errore quando viene passato uno script non valido a - File, miglioramento dell'errore per il passaggio di un argomento ambiguo [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Modificare i codici di uscita di `pwsh.exe` per allinearsi alle convenzioni di Unix

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Rimozione di `LocalAccount` e dei cmdlet dai moduli `Diagnostics`. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

A causa di API non supportate, il modulo `LocalAccounts` e i cmdlet `Counter` nel modulo `Diagnostics` sono stati rimossi fino a quando non viene trovata una soluzione migliore.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>L'esecuzione dello script di PowerShell con il parametro bool non funziona [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

In precedenza, l'uso di **powershell.exe** (ora **pwsh.exe**) per eseguire uno script di PowerShell tramite `-File` non consentiva in alcun modo di passare `$true`/`$false` come valori di parametro. È stato aggiunto il supporto di `$true`/`$false` come valori analizzati ai parametri. Sono supportati anche valori di parametro perché la sintassi attualmente documentata non funziona.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Rimuovere la proprietà `ClrVersion` da `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

La proprietà `ClrVersion` di `$PSVersionTable` non è utile con CoreCLR. Gli utenti finali non devono usare tale valore per determinare la compatibilità.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Modificare il parametro posizionale per `powershell.exe` da `-Command` a `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Abilitare l'uso di shebang di PowerShell su piattaforme non Windows. Nei sistemi basati su Unix questo significa che è possibile rendere uno script eseguibile per richiamare automaticamente PowerShell invece di richiamare in modo esplicito `pwsh`. Significa anche che è ora possibile eseguire operazioni come `powershell foo.ps1` o `powershell fooScript` senza specificare `-File`. Tuttavia, questa modifica richiede ora di specificare in modo esplicito `-c` o `-Command` quando si tenta di eseguire operazioni come `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementare l'analisi per escape Unicode [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u####`` o `` `u{####}`` viene convertito nel carattere Unicode corrispondente. Per restituire un valore letterale `` `u``, usare il carattere di escape per l'apice inverso: ``` ``u```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Modificare la codifica `New-ModuleManifest` in `UTF8NoBOM` nelle piattaforme non Windows [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

In precedenza, `New-ModuleManifest` creava manifesti psd1 in UTF-16 con BOM, con conseguenti problemi per gli strumenti Linux. Questa modifica importante cambia la codifica di `New-ModuleManifest` in UTF (senza BOM) nelle piattaforme non Windows.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Evitare la ricorsione di `Get-ChildItem` in collegamenti simbolici (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Questa modifica allinea `Get-ChildItem` maggiormente ai comandi nativi Unix `ls -r` e Windows `dir /s`. Come i comandi indicati, il cmdlet consente di visualizzare i collegamenti simbolici alle directory individuate durante la ricorsione, ma non esegue la ricorsione.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Correggere `Get-Content -Delimiter` per non includere il delimitatore nelle righe restituite [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

In precedenza, l'output durante l'uso di `Get-Content -Delimiter` era incoerente e poco pratico, perché richiedeva ulteriori elaborazioni dei dati per rimuovere il delimitatore. Questa modifica rimuove il delimitatore nelle righe restituite.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementare Format-Hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

Il parametro `-Raw` è ora "no-op" (in quanto non esegue alcuna operazione). In futuro, tutto l'output verrà visualizzato con una rappresentazione reale di numeri che includono tutti i byte per il tipo (quello che il parametro `-Raw` faceva formalmente prima di questa modifica).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>PowerShell come shell predefinita non funziona con il comando script [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

In Unix, l'accettazione di `-i` per una shell interattiva è una convenzione per le shell e molti strumenti si aspettano questo comportamento (`script` ad esempio e quando si imposta PowerShell come la shell predefinita) e chiamano la shell con l'opzione `-i`. Questa modifica è significativa, perché `-i` si poteva usare in precedenza come forma breve di `-inputformat`, mentre è ora necessario specificare `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Correggere un errore di digitazione nel nome della proprietà Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` era digitata in modo errato come `BiosSeralNumber` ed è stata corretta.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Aggiunta dei cmdlet `Get-StringHash` e `Get-FileHash` [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Questa modifica riguarda alcuni algoritmi di hash non supportati da CoreFX, che pertanto non sono più disponibili:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Aggiungere la convalida per i cmdlet `Get-*` in cui il passaggio di $null restituisce tutti gli oggetti invece di un errore [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Il passaggio di `$null` a uno qualsiasi dei cmdlet seguenti ora genera un errore:

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Aggiunta del supporto del formato di file di log esteso W3C `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

In precedenza, il cmdlet `Import-Csv` non poteva essere usato per importare direttamente i file di log in formato W3C esteso ed era necessaria un'azione aggiuntiva. Con questa modifica, il formato di log esteso W3C è ora supportato.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Problema di associazione di parametro con `ValueFromRemainingArguments` nelle funzioni PS [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` restituisce ora i valori come matrice anziché come valore singolo che è a sua volta una matrice.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>Rimozione di `BuildVersion` da `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Rimuovere la proprietà `BuildVersion` da `$PSVersionTable`. Questa proprietà era associata alla versione della build di Windows. Si consiglia invece di usare `GitCommitId` per recuperare la versione build esatta di PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Modifiche ai cmdlet Web

L'API .NET sottostante dei cmdlet Web è stato modificata in `System.Net.Http.HttpClient`. Questa modifica offre numerosi vantaggi. Tuttavia, questa modifica insieme a una mancanza di interoperabilità con Internet Explorer ha dato luogo a diverse modifiche di rilievo all'interno di `Invoke-WebRequest` e `Invoke-RestMethod`.

- `Invoke-WebRequest` ora supporta solo l'analisi HTML di base. `Invoke-WebRequest` restituisce sempre un oggetto `BasicHtmlWebResponseObject`. Le proprietà `ParsedHtml` e `Forms` sono state rimosse.
- I valori `BasicHtmlWebResponseObject.Headers` sono ora `String[]` invece di `String`.
- `BasicHtmlWebResponseObject.BaseResponse` è ora un oggetto `System.Net.Http.HttpResponseMessage`.
- La proprietà `Response` per le eccezioni di cmdlet Web è ora un oggetto `System.Net.Http.HttpResponseMessage`.
- L'analisi delle intestazioni conforme a RFC è ora l'impostazione predefinita per il parametro `-Headers` e `-UserAgent`. Questa impostazione può essere ignorata con `-SkipHeaderValidation`.
- Gli schemi URI `file://` e `ftp://` non sono più supportati.
- Le impostazioni di `System.Net.ServicePointManager` non vengono più rispettate.
- Non è attualmente disponibile l'autenticazione basata su certificati in macOS.
- L'uso di `-Credential` su un URI `http://` genererà un errore. Usare un URI `https://` oppure specificare il parametro `-AllowUnencryptedAuthentication` per eliminare l'errore.
- `-MaximumRedirection` genera ora un errore fatale quando i tentativi di reindirizzamento superano il limite specificato anziché restituire i risultati dell'ultimo reindirizzamento.
