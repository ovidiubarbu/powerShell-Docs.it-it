---
title: Novità di PowerShell Core 6.2
description: Nuove funzionalità e modifiche rilasciate in PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 98dd97b064e11509bf97e68e0a312e6b34b5d2bc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995469"
---
# <a name="whats-new-in-powershell-core-62"></a>Novità di PowerShell Core 6.2

La versione di PowerShell Core 6.2 è incentrata sul miglioramento delle prestazioni, su correzioni di bug e su miglioramenti di cmdlet e linguaggi di entità ridotta che contribuiscono ad aumentare la qualità. Per visualizzare un elenco completo dei miglioramenti, consultare i [log delle modifiche](https://github.com/PowerShell/PowerShell/releases) su GitHub.

## <a name="experimental-features"></a>Funzionalità sperimentali

In precedenza è stato abilitato il supporto per le [funzionalità sperimentali][]. Nella versione 6.2 è possibile provare quattro funzionalità sperimentali. Inviare commenti e suggerimenti per permetterci di apportare miglioramenti e decidere se promuovere la funzionalità allo stato mainstream.

Usare `Get-ExperimentalFeature` per ottenere un elenco delle funzionalità sperimentali disponibili. È possibile abilitare o disabilitare queste funzionalità con `Enable-ExperimentalFeature` e `Disable-ExperimentalFeature`.

### <a name="command-not-found-suggestions"></a>Suggerimenti per comandi non trovati

Questa funzionalità usa la corrispondenza fuzzy per trovare suggerimenti per comandi o cmdlet che potrebbero essere stati digitati in modo errato.

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>Esempio

In questo esempio viene eseguita una corrispondenza fuzzy del nome del cmdlet con alcuni suggerimenti, dal più probabile al meno probabile.

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a>Comunicazione remota implicita in batch

Quando si usa la [comunicazione remota implicita](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in una pipeline, PowerShell considera ogni comando nella pipeline in modo indipendente. Gli oggetti vengono ripetutamente serializzati e `de-serialized` tra il client e il sistema remoto nell'esecuzione della pipeline.

Con questa funzionalità, PowerShell analizza la pipeline per determinare se il comando è eseguibile in modo sicuro ed è presente nel sistema di destinazione. Se True, PowerShell esegue l'intera pipeline in modalità remota e si limita a serializzare e `de-serializes` i risultati nuovamente nel client.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

Un test reale di `Get-Process | Sort-Object` tramite localhost si riduce da 10-15 secondi a circa 20-30 **millisecondi**. È sufficiente che la funzionalità sia abilitata nel client. Non sono necessarie modifiche nel server.

### <a name="temp-drive"></a>Unità Temp

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Se si usa PowerShell Core in sistemi operativi diversi, sarà possibile osservare che la variabile di ambiente per individuare la directory temporanea è diversa in Windows, macOS e Linux. Con questa funzionalità, un'[PSDrive][] denominata `Temp:` viene automaticamente sottoposta a mapping alla cartella temporanea per il sistema operativo in uso.

#### <a name="example"></a>Esempio

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

Tenere presente che i comandi file nativi (ad esempio `ls` in Linux) non riconoscono le unità PowerShell e non visualizzano questa unità `Temp:`.

### <a name="abbreviation-expansion"></a>Espansione di abbreviazioni

I cmdlet PowerShell devono avere nomi descrittivi. Vengono quindi generati nomi lunghi, più difficili da digitare. Questa funzionalità consente di digitare i caratteri maiuscoli del cmdlet e usare il completamento tramite TAB per trovare una corrispondenza.

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>Esempio

```powershell
PS> i-arsavsf
```

Se si preme il tasto TAB ed è stato installato il modulo [Az](https://www.powershellgallery.com/packages/Az) di Azure PowerShell, verrà eseguito il completamento automatico in:

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> Questa funzionalità deve essere usata in modo interattivo. Non è possibile eseguire forme abbreviate dei cmdlet.
> Questa funzionalità non rappresenta una sostituzione per gli alias.

## <a name="breaking-changes"></a>Modifiche di rilievo

- Correzione del comportamento di `-NoEnumerate` in `Write-Output` in modo che sia coerente con Windows PowerShell. (9069)
- Risultato di `Join-String -InputObject 1,2,3` reso uguale al risultato di `1,2,3 | Join-String` (8611) (grazie @sethvs)
- Aggiunta di `-Stable` a `Sort-Object` e ai test correlati (7862) (grazie @KirkMunro)
- Miglioramento del cmdlet `Start-Sleep` in modo che accetti secondi frazionari (8537) (grazie @Prototyyppi)
- Modifica della tabella hash in modo che OrdinalIgnoreCase sia `case-insensitive` in tutte le impostazioni cultura (8566)
- Correzione di **LiteralPath** in `Import-Csv` per l'associazione all'output di `Get-ChildItem` (8277) (grazie @iSazonov)
- Una colonna senza nome non viene più ignorata se viene usato il delimitatore delle virgolette doppie in `Import-Csv` (7899) (grazie @Topping)
- `Get-ExperimentalFeature` non include più switch `-ListAvailable` (8318)
- Il parametro di debug imposta ora `$DebugPreference` su **Continue** anziché **Inquire** (8195) (grazie @KirkMunro)
- Supporto di `-OutputFormat` se specificato in un comando non interattivo, reindirizzato e codificato, usato con pwsh (8115)
- Caricamento dell'assembly dal percorso di base del modulo prima di provare a eseguire il caricamento dalla Global Assembly Cache (8073)
- Rimozione della tilde dai pacchetti di anteprima Linux (8244)
- Spostamento dell'elaborazione di `-WorkingDirectory` prima dell'elaborazione dei profili (8079)
- La variabile di ambiente `PATHEXT` non viene aggiunta in Unix (7697) (grazie @iSazonov)

## <a name="known-issues"></a>Problemi noti

- La comunicazione remota nelle piattaforme ARM di Windows IoT non riesce a caricare i moduli. Vedere (8053)

## <a name="general-updates-and-fixes"></a>Correzioni e aggiornamenti generali

- Abilitazione del completamento tramite TAB senza distinzione tra maiuscole e minuscole per file e cartelle nel file system senza distinzione tra maiuscole e minuscole (8128)
- PSVersionInfo.PSVersion e PSVersionInfo.PSEdition resi pubblici (8054) (grazie @KirkMunro)
- Aggiunta dell'inferenza del tipo per `$_` / `$PSItem` nei blocchi `catch{ }` (8020) (grazie @vexx32)
- Correzione dell'inferenza del tipo di chiamata al metodo statica (8018) (grazie @SeeminglyScience)
- Creazione di tipi derivati per `Select-Object`, `Group-Object`, **PSObject** e **Hashtable** (7231) (grazie @powercode)
- Supporto del metodo di chiamata con parametri di tipo `ByRef-like` (7721)
- Gestione del caso in cui il percorso del modulo Windows PowerShell è già in PSModulePath nell'ambiente (7727)
- Abilitazione dei cmdlet `SecureString` per sistemi non Windows archiviando il testo normale (9199)
- Miglioramento del messaggio di errore in ambienti non Windows in caso di importazione di clixml con securestring (7997)
- Aggiunta del parametro ReplyTo a `Send-MailMessage` (8727) (grazie @replicaJunction)
- Aggiunta del messaggio di obsolescenza a `Send-MailMessage` (9178)
- Correzione di `Restart-Computer` per utilizzare `localhost` quando WinRM non è presente (9160)
- Impostazione di `Start-Job` per la generazione di un errore fatale quando PowerShell è ospitato (9128)
- Aggiunta di suffissi e acceleratori del tipo in stile C# per ushort, uint, ulong e valori letterali brevi (7813) (grazie @vexx32)
- Nuovi suffissi aggiunti per valori letterali numerici. Vedere [about_Numeric_Literals][] (7901) (grazie @vexx32)
- Segnalazione corretta del livello di impatto quando SupportsShouldProcess non è impostato su 'true' (8209) (grazie @vexx32)
- Risoluzione dei problemi dei set di caratteri delle richieste nei cmdlet Web (8742) (grazie @markekraus)
- Risoluzione del problema `100-continue` previsto con i cmdlet Web (8679) (grazie @markekraus)
- Risoluzione del problema che causa un blocco file con i cmdlet Web (7676) (grazie @Claustn)
- Risoluzione del problema di analisi della tabella codici in `Invoke-RestMethod` (8694) (grazie @markekraus)
- Refactoring di `ConvertTo-Json` per esporre JsonObject.ConvertToJson come API pubblica (8682)
- Aggiunta della profondità massima configurabile in `ConvertFrom-Json` con -Depth (8199) (grazie @louistio)
- Aggiunta del parametro EscapeHandling nel cmdlet `ConvertTo-Json` (7775) (grazie @iSazonov)
- Aggiunta di `-CustomPipeName` a pwsh e `Enter-PSHostProcess` (8889)
- Possibilità di creare collegamenti simbolici relativi in Windows con `New-Item` (8783)
- Possibilità per gli utenti di Windows in modalità sviluppatore di creare collegamenti simbolici senza elevazione dei privilegi (8534)
- Possibilità per `Write-Information` di accettare `$null` (8774)
- Correzione di `Get-Help` per funzioni avanzate con il contenuto della guida MAML (8353)
- Risoluzione del problema PSTypeName `Get-Help` con -Parameter quando viene dichiarato solo un parametro (8754)-(grazie @pougetat)
- Correzione del calcolo token per `Get-Help` in esecuzione in ScriptBlock per la guida dei commenti. (8238) (grazie @hubuk)
- Modifica del parametro -Parameter del cmdlet `Get-Help` in modo che accetti matrici di stringhe (8454) (grazie @sethvs)
- Risoluzione di PAGER se il relativo percorso contiene spazi (8571) (grazie @pougetat)
- Aggiunta di un prompt all'uso di `less` nella funzione 'help' per indicare all'utente come disconnettersi (7998)
- Aggiunta del supporto dei tipi di enumerazione e carattere nel cmdlet `Format-Hex` (8191) (grazie @iSazonov)
- Rimozione di ShouldProcess da `Format-Hex` (8178)
- Aggiunta di nuovi parametri Offset e Count a `Format-Hex` e refactoring del cmdlet (7877) (grazie @iSazonov)
- 'name' consentito come chiave di alias per 'label' in `ConvertTo-Html`, voce 'width' consentita come intero (8426) (grazie @mklement0)
- Funzionamento delle proprietà calcolate basate su blocchi di script ripristinato in `ConvertTo-Html` (8427) (grazie @mklement0)
- Aggiunta del cmdlet `Join-String` per la creazione di testo dall'input della pipeline (7660) (grazie @powercode)
- Correzione del cmdlet `Join-String` per la logica del parametro FormatString (8449) (grazie @sethvs)
- Modifica di `Clear-Host` per l'uso di `$RAWUI` e clear per il funzionamento con comunicazione remota (8609)
- Modifica di `Clear-Host` per rinominarlo semplicemente `[console]::clear` e rimozione dell'alias clear da Unix (8603)
- Correzione di LiteralPath in `Import-Csv` per l'associazione all'output di `Get-ChildItem` (8277) (grazie @iSazonov)
- La funzione help non deve utilizzare pager per AliasHelpInfo (8552)
- Aggiunta di `-UseMinimalHeader` a `Start-Transcript` per ridurre al minimo l'intestazione della trascrizione (8402) (grazie @lukexjeremy)
- Aggiunta dei cmdlet `Enable-ExperimentalFeature` e `Disable-ExperimentalFeature` (8318)
- Esposizione di tutti i cmdlet da **PSDiagnostics** se logman.exe è disponibile (8366)
- Rimozione del parametro **Persist** da `New-PSDrive` nella piattaforma `non-Windows` (8291) (grazie @lukexjeremy)
- Aggiunta del supporto per `cd +` (7206) (grazie @bergmeister)
- Abilitazione di `Set-Location -LiteralPath` per l'uso con cartelle denominate + e - (8089)
- `Test-Path` restituisce `$false` in presenza di un valore di percorso vuoto o `$null` (8080) (grazie @vexx32)
- Parametro dinamico restituito anche se il percorso non corrisponde ad alcun provider (7957)
- Supporto di `Get-PSHostProcessInfo` e `Enter-PSHostProcess` nelle piattaforme Unix (8232)
- Riduzione delle allocazioni nel cmdlet `Get-Content` (8103) (grazie @iSazonov)
- Possibilità per `Add-Content` di condividere l'accesso in lettura con altri strumenti durante la scrittura di contenuto (8091)
- `Get/Add-Content` genera un errore migliorato quando si fa riferimento a un contenitore (7823) (grazie @kvprasoon)
- Aggiunta di parametri `-Name`, `-NoUserOverrides` e `-ListAvailable` a `Get-Culture` (7702) (grazie @iSazonov)
- Aggiunta di un attributo unificato per il completamento per il parametro **Encoding**. (7732) (grazie @ThreeFive-O)
- ID numerici e nome delle tabelle codici registrate nei parametri **Encoding** (7636) (grazie @iSazonov)
- Correzione di `Rename-Item -Path` con carattere jolly (7398) (grazie @kwkam)
- Svuotamento anziché eliminazione del file quando si usa `Start-Transcript` ed è presente un file (8131) (grazie @paalbra)
- Apertura di file di origine da parte di `Add-Type` con **FileAccess.Read** e **FileShare.Read** in modo esplicito (7915) (grazie @IISResetMe)
- Correzione di `Enter-PSSession -ContainerId` per le versioni di Windows più recenti (7883)
- Garanzia di popolamento della proprietà **NestedModules** da parte di `Test-ModuleManifest` (7859)
- Aggiunta del case `%F` a `Get-Date` -UFormat (7630) (grazie @britishben)
- Correzione di `Set-Service -Status Stopped` per arrestare i servizi con dipendenze (5525) (grazie @zhenggu)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Funzionalità sperimentali]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
