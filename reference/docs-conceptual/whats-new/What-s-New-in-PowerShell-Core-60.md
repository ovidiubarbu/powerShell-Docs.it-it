# <a name="whats-new-in-powershell-core-60"></a>Novità di PowerShell Core 6.0

[PowerShell Core 6.0][github] è una nuova edizione di PowerShell multipiattaforma (Windows, macOS e Linux), open source e creata per gli ambienti eterogenei e il cloud ibrido.

## <a name="moved-from-net-framework-to-net-core"></a>Passaggio da .NET Framework a .NET Core

PowerShell Core usa [.NET Core 2.0][] come proprio runtime.
.NET Core 2.0 consente a PowerShell Core di funzionare su più piattaforme (Windows, macOS e Linux).
PowerShell Core espone anche il set di API offerto da .NET Core 2.0 per l'uso nei comdlet e negli script di PowerShell.

Windows PowerShell usava il runtime di .NET Framework per ospitare il motore PowerShell.
Ciò significa che Windows PowerShell espone il set di API offerto da .NET Framework.

Le API condivise tra .NET Core e .NET Framework sono definite come parte di [.NET Standard][].

Per altre informazioni su eventuali modifiche della compatibilità di moduli e script tra PowerShell Core e Windows PowerShell, vedere [Compatibilità con le versioni precedenti di Windows PowerShell][#backwards-compatibility-with-windows-powershell]

## <a name="support-for-macos-and-linux"></a>Supporto per macOS e Linux

PowerShell supporta ora ufficialmente macOS e Linux, inclusi:

- Windows 7, 8.1 e 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Canale semestrale di Windows Server][semi-annual]
- Ubuntu 14.04, 16.04 e 17.04
- Debian 8.7+ e 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12+

La nostra community ha anche reso disponibili pacchetti per le piattaforme seguenti, ma non sono ufficialmente supportati:

- Arch Linux
- Kali Linux
- AppImage (funziona su più piattaforme Linux)

Sono anche disponibili versioni sperimentali (non supportate) per le piattaforme seguenti:

- Windows su ARM32/ARM64
- Raspbian (Stretch)

Sono state apportate diverse modifiche a PowerShell Core 6.0 per migliorarne il funzionamento nei sistemi non Windows.
Alcune di queste modifiche sono di primaria importanza e influiscono anche su Windows.
Altre sono solo presenti o applicabili in installazioni non Windows di PowerShell Core.

- Aggiunto il supporto per il glob dei comandi nativi nelle piattaforme Unix.
- La funzionalità `more` rispetta il `$PAGER` di Linux con valore predefinito `less`.
  Ciò significa che è ora possibile usare i caratteri jolly con file binari e comandi nativi, ad esempio `ls *.txt`. (#3463)
- La barra rovesciata finale viene automaticamente preceduta da un carattere di escape quando si usano argomenti di comandi nativi. (#4965)
- Ignorare l'opzione `-ExecutionPolicy` quando si esegue PowerShell su piattaforme non Windows, perché la firma degli script non è attualmente supportata. (#3481)
- Correzione di ConsoleHost per rispettare `NoEcho` sulle piattaforme Unix. (#3801)
- Correzione di `Get-Help` per supportare criteri di ricerca senza distinzione tra maiuscole e minuscole nelle piattaforme Unix. (#3852)
- Pagina di manuale di `powershell` aggiunta al pacchetto

### <a name="logging"></a>Registrazione

In macOS PowerShell usa le API `os_log` native per accedere al [sistema di registrazione unificato][os_log] di Apple.
In Linux PowerShell usa [Syslog][], una soluzione di registrazione universale.

### <a name="filesystem"></a>File System

Sono state apportate diverse modifiche in macOS e Linux per supportare caratteri di nomi di file tradizionalmente non supportati in Windows:

- I percorsi usati dai cmdlet sono ora indipendenti dalla barra (sia / che \ funzionano come separatore di directory)
- La specifica della directory di base XDG è ora rispettata e usata per impostazione predefinita:
  - Il percorso del profilo Linux/macOS si trova in `~/.config/powershell/profile.ps1`
  - Il percorso di salvataggio della cronologia si trova in `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Il percorso modulo utente si trova in `~/.local/share/powershell/Modules`
- Supporto per i nomi di file e cartelle contenenti il carattere due punti in Unix. (#4959)
- Supporto per i nomi di script o i percorsi completi con virgole. (#4136) (grazie a @TimCurwick)
- Viene rilevato quando si usa `-LiteralPath` per eliminare l'espansione di caratteri jolly per i cmdlet di navigazione. (#5038)
- `Get-ChildItem` aggiornata per funzionare in modo più simile ai comandi nativi `ls -R` di *nix e `DIR /S` di Windows.
  `Get-ChildItem` ora restituisce i collegamenti simbolici rilevati durante una ricerca ricorsiva e non esegue la ricerca nelle directory di destinazione di tali collegamenti. (#3780)

### <a name="case-sensitivity"></a>Distinzione tra maiuscole e minuscole

Linux e macOS tendono a fare distinzione tra maiuscole e minuscole, mentre Windows non fa distinzione tra maiuscole e minuscole benché mantenga le lettere maiuscole e minuscole.
In generale PowerShell non fa distinzione tra maiuscole e minuscole.

Ad esempio, le variabili di ambiente fanno distinzione tra maiuscole e minuscole in macOS e Linux, quindi l'uso delle maiuscole e minuscole della variabile di ambiente `PSModulePath` è stata standardizzata. (#3255) `Import-Module` non fa distinzione tra maiuscole e minuscole quando usa un percorso di file per determinare il nome del modulo. (#5097)

## <a name="support-for-side-by-side-installations"></a>Supporto per le installazioni side-by-side

PowerShell Core viene installato, configurato ed eseguito separatamente da Windows PowerShell.
PowerShell Core ha un pacchetto ZIP "portatile".
Usando il pacchetto ZIP è possibile installare qualsiasi numero di versioni in qualsiasi posizione sul disco, anche localmente in un'applicazione che usa PowerShell come dipendenza.
L'installazione side-by-side semplifica l'esecuzione dei test sulle nuove versioni di PowerShell e la migrazione degli script esistenti nel tempo.
Consente inoltre la compatibilità con le versioni precedenti poiché gli script possono essere aggiunti alle versioni specifiche che richiedono.

> [!NOTE]
> Per impostazione predefinita, il programma di installazione basato su MSI in Windows esegue un'installazione dell'aggiornamento sul posto.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>Rinominato `powershell(.exe)` in `pwsh(.exe)`

Il nome binario per PowerShell Core è stato modificato da `powershell(.exe)` a `pwsh(.exe)`.
Questa modifica offre agli utenti un modo deterministico per eseguire PowerShell Core nei computer per supportare le installazioni side-by-side di Windows PowerShell e PowerShell Core.
`pwsh` è inoltre molto più breve e facile da digitare.

Altre modifiche di `pwsh(.exe)` rispetto a `powershell.exe`:

- Modificato il primo parametro posizionale da `-Command` a `-File`.
  Questa modifica corregge l'uso di `#!` (noto anche come shebang) negli script di PowerShell che vengono eseguiti da shell non di PowerShell su piattaforme non Windows.
  Significa anche che è possibile eseguire comandi come `pwsh foo.ps1` o `pwsh fooScript` senza specificare `-File`.
  Tuttavia, questa modifica richiede di specificare in modo esplicito `-c` o `-Command` quando si tenta di eseguire comandi come `pwsh.exe -Command Get-Command`. (#4019)
- PowerShell Core accetta l'opzione `-i` (o `-Interactive`) per indicare una shell interattiva. (#3558) Questo consente di usare PowerShell come shell predefinita su piattaforme Unix.
- Rimossi i parametri `-importsystemmodules` e `-psconsoleFile` da `pwsh.exe`. (#4995)
- Modificati `pwsh -version` e la Guida incorporata per `pwsh.exe` per allinearli con altri strumenti nativi. (#4958 & #4931) (grazie @iSazonov)
- Messaggi di errore per argomento non valido per `-File` e `-Command` e codici di uscita conformi agli standard Unix (#4573)
- Aggiunto il parametro `-WindowStyle` in Windows. (#4573) Analogamente, gli aggiornamenti delle installazioni basati su pacchetto sulle piattaforme non Windows sono aggiornamenti sul posto.

## <a name="backwards-compatibility-with-windows-powershell"></a>Compatibilità con le versioni precedenti di Windows PowerShell

L'obiettivo di PowerShell Core è rimanere il più possibile compatibile con Windows PowerShell.
PowerShell Core usa [.NET Standard][] 2.0 per garantire la compatibilità binaria con gli assembly .NET esistenti.
Molti moduli di PowerShell dipendono da tali assembly (spesso DLL), quindi .NET Standard consente di continuare a usare .NET Core.
PowerShell Core include anche un'euristica per la ricerca nelle cartelle note, ad esempio dove si trova in genere Global Assembly Cache sul disco, per trovare le dipendenze DLL di .NET Framework.

Maggiori informazioni su .NET Standard sono disponibili nel [blog di .NET][], in questo video di [YouTube][] e in queste [domande frequenti][] su GitHub.

È stato fatto il possibile per garantire che il linguaggio di PowerShell e i moduli "predefiniti" (ad esempio `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility` e così via) funzionino come in Windows PowerShell.
In molti casi, con il supporto della community, sono state aggiunte nuove funzionalità e correzioni di bug ai cmdlet.
In alcuni casi, a causa di una dipendenza mancante nei livelli .NET sottostanti, la funzionalità è stata rimossa o non è disponibile.

La maggior parte dei moduli inclusi in Windows, ad esempio, `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage` e così via, e altri prodotti Microsoft tra cui Azure e Office non sono ancora stati trasferiti *in modo esplicito* a. NET Core.
Il team di PowerShell collabora con questi gruppi e team di prodotto per convalidare e trasferire i moduli esistenti in PowerShell Core.
Con .NET Standard e [CDXML][], molti di questi moduli di Windows PowerShell tradizionali sembrano funzionare in PowerShell Core, ma non sono stati formalmente convalidati e non sono ufficialmente supportati.

Installando il modulo [`WindowsPSModulePath`][windowspsmodulepath], è possibile usare i moduli di Windows PowerShell aggiungendo `PSModulePath` di Windows PowerShell a `PSModulePath` di PowerShell Core.

Installare prima il modulo `WindowsPSModulePath` da PowerShell Gallery:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

Dopo l'installazione di questo modulo, eseguire il cmdlet `Add-WindowsPSModulePath` per aggiungere `PSModulePath` di Windows PowerShell a PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Supporto Docker

PowerShell Core aggiunge il supporto per i contenitori Docker per tutte le principali piattaforme supportate, incluse più distribuzioni di Linux, Windows Server Core e Nano Server.

Per un elenco completo, consultare i tag su [ `microsoft/powershell` nell'hub Docker][docker-hub].
Per altre informazioni su Docker e PowerShell Core, vedere [Docker][] su GitHub.

## <a name="ssh-based-powershell-remoting"></a>Comunicazione remota di PowerShell basata su SSH

Il protocollo di comunicazione remota di PowerShell (PSRP) ora funziona con il protocollo Secure Shell (SSH) oltre al PSRP tradizionale basato su WinRM.

Ciò significa che è possibile usare cmdlet come `Enter-PSSession` e `New-PSSession` ed eseguire l'autenticazione con SSH.
È sufficiente registrare PowerShell come un sottosistema con server SSH basato su OpenSSH ed è possibile usare i meccanismi di autenticazione basati su SSH esistenti, ad esempio le password o le chiavi private, con la tradizionale semantica `PSSession`.

Per altre informazioni sulla configurazione e sull'uso della comunicazione remota basata su SSH, vedere [Comunicazione remota di PowerShell su SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom"></a>La codifica predefinita è UTF-8 senza BOM

In passato i cmdlet di Windows PowerShell come `Get-Content` e `Set-Content` usavano codifiche diverse, ad esempio ASCII e UTF-16.
La varianza nei valori di codifica predefiniti causavano problemi quando si combinavano i cmdlet senza specificare una codifica.

Le piattaforme non Windows in genere usano UTF-8 senza un Byte Order Mark (BOM) come codifica predefinita per i file di testo.
Un numero crescente di applicazioni e strumenti Windows stanno passando dalla codifica UTF-16 alla codifica UTF-8 senza BOM.
In PowerShell Core la codifica predefinita viene modificata in modo da assicurare la conformità con gli ecosistemi più ampi.

Ciò significa che tutti i cmdlet incorporati che usano il parametro `-Encoding` usano il valore `UTF8NoBOM` per impostazione predefinita.
Questa modifica interessa i cmdlet seguenti:

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- New-ModuleManifest
- Out-File
- Select-String
- Send-MailMessage
- Set-Content

Questi cmdlet sono anche stati aggiornati in modo che il parametro `-Encoding` accetti universalmente `System.Text.Encoding`.

Anche il valore predefinito di `$OutputEncoding` è stato modificato in UTF-8.

Come procedura consigliata, è opportuno impostare in modo esplicito le codifiche negli script usando il parametro `-Encoding` per produrre un comportamento deterministico tra le piattaforme.

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Supporto del background delle pipeline con la e commerciale (`&`) (#3360)

Il posizionamento di `&` alla fine di una pipeline causa l'esecuzione della pipeline come processo di PowerShell.
Quando una pipeline è supportata da un background, viene restituito un oggetto processo.
Quando la pipeline è in esecuzione come processo, tutti i cmdlet `*-Job` standard possono essere usati per gestire il processo.
Le variabili usate nella pipeline, ignorando quelle specifiche del processo, vengono copiate automaticamente nel processo in modo tale che `Copy-Item $foo $bar &` funzioni.
Il processo viene inoltre eseguito nella directory corrente anziché nella home directory dell'utente.
Per altre informazioni sui processi di PowerShell, vedere [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Versionamento Semantico

- `SemanticVersion` è stato reso compatibile con `SemVer 2.0`. (#5037) (grazie a @iSazonov)
- Modificato il valore predefinito `ModuleVersion` di `New-ModuleManifest` in `0.0.1` per allinearlo con SemVer. (#4842) (grazie @LDSpits)
- Aggiunto `semver` come acceleratore di tipo per `System.Management.Automation.SemanticVersion`. (#4142) (grazie a @oising)
- Abilitato il confronto tra un'istanza `SemanticVersion` e un'istanza `Version` che viene costruito solo con i valori di versione `Major` e `Minor`.

## <a name="language-updates"></a>Aggiornamenti del linguaggio

- Implementata l'analisi delle sequenze di escape Unicode in modo che gli utenti possano usare i caratteri Unicode come argomenti, stringhe o nomi di variabili. (#3958) (grazie a @rkeithhill)
- Aggiunto nuovo carattere di escape per ESC:`` `e``
- Aggiunto il supporto per la conversione delle enumerazioni in stringhe (#4318) (grazie @KirkMunro)
- Corretto il cast della matrice a elemento singolo in una raccolta generica. (#3170)
- Aggiunto l'overload dell'intervallo di caratteri all'operatore `..` in modo che `'a'..'z'` restituisca i caratteri da "a" a "z". (#5026) (grazie a @IISResetMe)
- Corretta l'assegnazione di variabili in modo da non sovrascrivere le variabili di sola lettura
- Push dei valori locali delle variabili automatiche in "DottedScopes" quando si esegue il dot-sourcing dei cmdlet di script (#4709)
- Abilitato l'uso dell'opzione "Singleline, Multiline" nell'operatore di divisione (#4721) (grazie @iSazonov)

## <a name="engine-updates"></a>Aggiornamenti del motore

- `$PSVersionTable` ha quattro nuove proprietà:
  - `PSEdition`: questa opzione è impostata su `Core` in PowerShell Core e su `Desktop` in Windows PowerShell
  - `GitCommitId`: questo è l'ID commit Git del ramo o tag Git in cui è stato compilato PowerShell.
    Per le compilazioni rilasciate corrisponde probabilmente a `PSVersion`.
  - `OS`: stringa di versione del sistema operativo restituita da`[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: valore restituito da `[System.Environment]::OSVersion.Platform`, impostato su `Win32NT` in Windows, `MacOSX` in macOS e `Unix` in Linux.
- Rimossa la proprietà `BuildVersion` da `$PSVersionTable`.
  Questa proprietà è strettamente legata alla versione build di Windows.
  Si consiglia invece di usare `GitCommitId` per recuperare la versione build esatta di PowerShell Core. (#3877) (grazie a @iSazonov)
- Rimuovere la proprietà `ClrVersion` da `$PSVersionTable`.
  Questa proprietà non è rilevante per .NET Core ed è stata mantenuta solo in .NET Core per specifici scopi di legacy non applicabili a PowerShell.
- Aggiunte tre nuove variabili automatiche per determinare se PowerShell è in esecuzione in un dato sistema operativo: `$IsWindows`, `$IsMacOs` e `$IsLinux`.
- Aggiunta di `GitCommitId` al banner di PowerShell Core.
  Ora non è necessario eseguire `$PSVersionTable` non appena si avvia PowerShell per ottenere la versione. (#3916) (grazie a @iSazonov)
- Aggiunta di un file di configurazione JSON denominato `PowerShellProperties.json` in `$PSHome` per archiviare alcune impostazioni richieste prima dell'ora di avvio, ad esempio `ExecutionPolicy`.
- Non bloccare la pipeline durante l'esecuzione dell'eseguibile di Windows
- Abilitata l'enumerazione delle raccolte COM. (#4553)

## <a name="cmdlet-updates"></a>Aggiornamenti dei cmdlet

### <a name="new-cmdlets"></a>Nuovi cmdlet

- Aggiunta di `Get-Uptime` a `Microsoft.PowerShell.Utility`.
- Aggiunto il comando `Remove-Alias`. (#5143) (grazie a @PowershellNinja)
- Aggiunta di `Remove-Service` al modulo Management. (#4858) (grazie a @joandrsn)

### <a name="web-cmdlets"></a>Cmdlet Web

- Aggiunto il supporto dell'autenticazione del certificato per i cmdlet Web. (#4646) (grazie @markekraus)
- Aggiunto il supporto per le intestazioni del contenuto ai cmdlet Web. (#4494 & #4640) (grazie @markekraus)
- Aggiunto il supporto per più intestazioni di collegamento ai cmdlet Web. (#5265) (grazie a @markekraus)
- Supporto della paginazione delle intestazioni di collegamento nei cmdlet Web (#3828)
  - Per `Invoke-WebRequest`, quando la risposta include un'intestazione di collegamento, viene creata una proprietà RelationLink come dizionario che rappresenta gli URL e gli attributi `rel` e si verifica che gli URL siano assoluti per semplificarne l'uso da parte dello sviluppatore.
  - Per `Invoke-RestMethod`, quando la risposta include un'intestazione di collegamento, si espone un'opzione `-FollowRelLink` per seguire automaticamente i collegamenti `next` `rel`finché non esistono più o si raggiunge il valore del parametro facoltativo `-MaximumFollowRelLink`.
- Aggiunta del parametro `-CustomMethod` ai cmdlet Web per consentire i verbi di metodo non standard. (#3142) (grazie a @Lee303)
- Aggiunta del supporto `SslProtocol` ai cmdlet Web. (#5329) (grazie a @markekraus)
- Aggiunta del supporto multiparte ai cmdlet Web. (#4782) (grazie @markekraus)
- Aggiunta di `-NoProxy` ai cmdlet Web in modo che ignorino l'impostazione del proxy a livello di sistema. (#3447) (grazie a @TheFlyingCorpse)
- L'agente utente dei cmdlet Web ora indica la piattaforma del sistema operativo (#4937) (grazie @LDSpits)
- Aggiunta l'opzione `-SkipHeaderValidation` ai cmdlet Web per supportare l'aggiunta di intestazioni senza convalidare il valore dell'intestazione. (#4085)
- Possibilità di evitare la convalida del certificato HTTPS del server da parte dei cmdlet Web, se necessario.
- Aggiunti i parametri di autenticazione ai cmdlet Web. (#5052) (grazie @markekraus)
  - Aggiunta di `-Authentication` che rende disponibili tre opzioni: Basic, OAuth e Bearer.
  - Aggiunta di `-Token` per ottenere il token di connessione per le opzioni OAuth e Bearer.
  - Aggiunta di `-AllowUnencryptedAuthentication` per ignorare l'autenticazione specificata per qualsiasi schema di trasporto diverso da HTTPS.
- Aggiunta di `-ResponseHeadersVariable` a `Invoke-RestMethod` per abilitare l'acquisizione delle intestazioni di risposta. (#4888) (grazie @markekraus)
- Correzione dei cmdlet Web in modo da includere la risposta HTTP nell'eccezione quando il codice di stato della risposta indica l'esito negativo. (#3201)
- Modifica dei cmdlet Web `UserAgent` da `WindowsPowerShell` a `PowerShell`. (#4914) (grazie @markekraus)
- Aggiunto il rilevamento esplicito di `ContentType` a `Invoke-RestMethod` (&#4692;)
- Correzione dei cmdlet Web `-SkipHeaderValidation` in modo che funzionino con le intestazioni agente utente non standard. (#4479 & #4512) (grazie@markekraus)

### <a name="json-cmdlets"></a>Cmdlet JSON

- Aggiunta di `-AsHashtable` a `ConvertFrom-Json` per restituire `Hashtable`. (#5043) (grazie @bergmeister)
- Uso di un formattatore più accattivante con output `ConvertTo-Json`. (#2787) (grazie a @kittholland)
- Aggiunto il supporto della serializzazione `Jobject` a `ConvertTo-Json`. (#5141)
- Correzione di `ConvertFrom-Json` per deserializzare una matrice di stringhe della pipeline che insieme costituiscono una stringa JSON completa.
  Queste correzioni risolvono alcuni casi in cui le nuove righe interrompono l'analisi del JSON. (#3823)
- Rimozione dell'elemento `AliasProperty "Count"` definito per `System.Array`.
  Questa operazione in alcuni casi rimuove la proprietà `Count` estranea dall'output `ConvertFrom-Json`. (#3231) (grazie a @PetSerAl)

### <a name="csv-cmdlets"></a>Cmdlet CSV

- Aggiunto il supporto `PSTypeName` per `Import-Csv` e `ConvertFrom-Csv`. (#5389) (grazie @markekraus)
- Ora `Import-Csv` supporta `CR`, `LF` e `CRLF` come delimitatori di riga. (#5363) (grazie @iSazonov)
- `-NoTypeInformation` ora è il valore predefinito per `Export-Csv` e `ConvertTo-Csv`. (#5164) (grazie @markekraus)

### <a name="service-cmdlets"></a>Cmdlet di servizio

- Aggiunte le proprietà `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName` e `StartupType` agli oggetti `ServiceController` restituiti da `Get-Service`. (#4907) (grazie @joandrsn)
- Aggiunta una funzionalità per impostare le credenziali sul comando `Set-Service`. (#4844) (grazie @joandrsn)

### <a name="other-cmdlets"></a>Altri cmdlet

- Aggiunto a `Get-ChildItem` un parametro denominato `-FollowSymlink` che attraversa i collegamenti simbolici su richiesta, con controlli per i cicli di collegamento. (#4020)
- Aggiornamento di `Add-Type` per supportare `CSharpVersion7`. (#3933) (grazie a @iSazonov)
- Rimosso il modulo `Microsoft.PowerShell.LocalAccounts` a causa dell'uso di API non supportate finché non viene trovata una soluzione migliore. (#4302)
- Rimossi i cmdlet `*-Counter` in `Microsoft.PowerShell.Diagnostics` a causa dell'uso di API non supportate finché non viene trovata una soluzione migliore. (#4303)
- Aggiunto il supporto per `Invoke-Item -Path <folder>`. (#4262)
- Aggiunte le opzioni `-Extension` e `-LeafBase` a `Split-Path` in modo che sia possibile suddividere i percorsi tra l'estensione del file e il resto del nome del file. (#2721) (grazie a @powercode)
- Aggiunti i parametri `-Top` e `-Bottom` a `Sort-Object` per l'ordinamento primi/ultimi N
- Esposizione di un processo padre del processo aggiungendo `CodeProperty "Parent"` a `System.Diagnostics.Process`. (#2850) (grazie a @powercode)
- Uso di MB anziché KB per le colonne della memoria di `Get-Process`
- Aggiunta l'opzione `-NoNewLine` per `Out-String`. (#5056) (grazie @raghav710)
- Il cmdlet `Move-Item` rispetta i parametri `-Include`, `-Exclude` e `-Filter`. (#3878)
- Consentito l'uso di `*` nel percorso del Registro di sistema per `Remove-Item`. (#4866)
- Aggiunta di `-Title` a `Get-Credential` e unificazione dell'uso dei prompt sulle varie piattaforme.
- Aggiunta del parametro `-TimeOut` a `Test-Connection`. (#2492)
- I cmdlet `Get-AuthenticodeSignature` ora possono ricevere il timestamp di firma del file. (#4061)
- Rimozione dell'opzione `-ShowWindow` non supportata da `Get-Help`. (#4903)
- Correzione di `Get-Content -Delimiter` per non includere il delimitatore negli elementi di matrice restituiti (#3706) (grazie @mklement0)
- Aggiunti i parametri `Meta`, `Charset` e `Transitional` a `ConvertTo-HTML` (#4184) (grazie @ergo3114)
- Aggiunte le proprietà `WindowsUBR` e `WindowsVersion` al risultato `Get-ComputerInfo`
- Aggiunta del parametro `-Group` a `Get-Verb`
- Aggiunta del supporto `ShouldProcess` a `New-FileCatalog` e `Test-FileCatalog` (correzione `-WhatIf` e `-Confirm`). (#3074) (grazie a @iSazonov)
- Aggiunta l'opzione `-WhatIf` al cmdlet `Start-Process` (#4735) (grazie @sarithsutha)
- Aggiunta di `ValidateNotNullOrEmpty` a molti parametri esistenti.

## <a name="tab-completion"></a>Completamento tramite TAB

- Migliorata l'inferenza dei tipi nel completamento con TAB in base ai valori delle variabili di runtime. (#2744) (grazie a @powercode) Questo consente il completamento con TAB in situazioni come:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Aggiunto il completamento con TAB di HashTable per `-Property` di `Select-Object`. (#3625) (grazie a @powercode)
- Abilitato il completamento automatico degli argomenti per `-ExcludeProperty` e `-ExpandProperty` di `Select-Object`. (#3443) (grazie a @iSazonov)
- Corretto un bug nel completamento con TAB per effettuare la chiamata `native.exe --<tab>` nel sistema di completamento nativo. (#3633) (grazie a @powercode)

## <a name="breaking-changes"></a>Modifiche di primaria importanza

È stato introdotto un numero di modifiche di rilievo in PowerShell Core 6.0.
Per informazioni dettagliate, vedere l'articolo sulle [modifiche di primaria importanza in PowerShell Core 6.0][breaking-changes].

## <a name="debugging"></a>Debug

- Supporto per il debug remoto dell'esecuzione dell'istruzione per `Invoke-Command -ComputerName`. (#3015)
- Abilitata la registrazione del debug del binder in PowerShell Core

## <a name="filesystem-updates"></a>Aggiornamenti di FileSystem

- Possibilità di usare il provider FileSystem da un percorso UNC. ($4998)
- `Split-Path` ora funziona con le directory principali in formato UNC
- `cd` senza argomenti ora si comporta come `cd ~`
- Correzione di PowerShell Core per consentire l'uso dei percorsi lunghi più di 260 caratteri. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Correzioni di bug e miglioramenti delle prestazioni

Sono stati apportati *molti* miglioramenti alle prestazioni in PowerShell, inclusi il tempo di avvio, vari cmdlet predefiniti e l'interazione con i file binari nativi.

Sono inoltre stati corretti diversi bug all'interno di PowerShell Core.
Per un elenco completo delle correzioni e delle modifiche, consultare il [log delle modifiche][] su GitHub.

## <a name="telemetry"></a>Telemetria

- In PowerShell Core 6.0 è stata aggiunta la telemetria all'host della console per segnalare due valori (#3620):
  - la piattaforma del sistema operativo (`$PSVersionTable.OSDescription`)
  - la versione esatta di PowerShell (`$PSVersionTable.GitCommitId`)

Se si sceglie di non usare la telemetria, è sufficiente eliminare `$PSHome\DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY`.
L'eliminazione di questo file consente di ignorare tutta la telemetria anche prima della prima esecuzione di PowerShell.
Si prevede inoltre di esporre i dati di telemetria e le informazioni dettagliate ottenute dalla telemetria nel [dashboard della community][community-dashboard].
Altre informazioni sull'uso di questi dati sono disponibili in questo [post di blog][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/en-us/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/en-us/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: https://github.com/PowerShell/PowerShell/tree/master/docs/BREAKINGCHANGES.md
[log delle modifiche]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[blog di .NET]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[domande frequenti]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/en-us/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview