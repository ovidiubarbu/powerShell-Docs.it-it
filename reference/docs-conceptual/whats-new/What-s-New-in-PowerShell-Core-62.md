---
title: Novità di PowerShell Core 6.2
description: Nuove funzionalità e modifiche rilasciate in PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 6a0da8a410e602ae3963e0bc7bace745317d7d4b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058098"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="12f60-103">Novità di PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="12f60-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="12f60-104">La versione di PowerShell Core 6.2 è incentrata sul miglioramento delle prestazioni, su correzioni di bug e su miglioramenti di cmdlet e linguaggi di entità ridotta che contribuiscono ad aumentare la qualità.</span><span class="sxs-lookup"><span data-stu-id="12f60-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="12f60-105">Per visualizzare un elenco completo dei miglioramenti, consultare i [log delle modifiche](https://github.com/PowerShell/PowerShell/releases) su GitHub.</span><span class="sxs-lookup"><span data-stu-id="12f60-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="12f60-106">Funzionalità sperimentali</span><span class="sxs-lookup"><span data-stu-id="12f60-106">Experimental Features</span></span>

<span data-ttu-id="12f60-107">In precedenza è stato abilitato il supporto per le [funzionalità sperimentali][].</span><span class="sxs-lookup"><span data-stu-id="12f60-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="12f60-108">Nella versione 6.2 è possibile provare quattro funzionalità sperimentali. Inviare commenti e suggerimenti per permetterci di apportare miglioramenti e decidere se promuovere la funzionalità allo stato mainstream.</span><span class="sxs-lookup"><span data-stu-id="12f60-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="12f60-109">Usare `Get-ExperimentalFeature` per ottenere un elenco delle funzionalità sperimentali disponibili.</span><span class="sxs-lookup"><span data-stu-id="12f60-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="12f60-110">È possibile abilitare o disabilitare queste funzionalità con `Enable-ExperimentalFeature` e `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="12f60-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="12f60-111">Suggerimenti per comandi non trovati</span><span class="sxs-lookup"><span data-stu-id="12f60-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="12f60-112">Questa funzionalità usa la corrispondenza fuzzy per trovare suggerimenti per comandi o cmdlet che potrebbero essere stati digitati in modo errato.</span><span class="sxs-lookup"><span data-stu-id="12f60-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="12f60-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="12f60-113">Example</span></span>

<span data-ttu-id="12f60-114">In questo esempio viene eseguita una corrispondenza fuzzy del nome del cmdlet con alcuni suggerimenti, dal più probabile al meno probabile.</span><span class="sxs-lookup"><span data-stu-id="12f60-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

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

### <a name="implicit-remoting-batching"></a><span data-ttu-id="12f60-115">Comunicazione remota implicita in batch</span><span class="sxs-lookup"><span data-stu-id="12f60-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="12f60-116">Quando si usa la [comunicazione remota implicita](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in una pipeline, PowerShell considera ogni comando nella pipeline in modo indipendente.</span><span class="sxs-lookup"><span data-stu-id="12f60-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="12f60-117">Gli oggetti vengono ripetutamente serializzati e `de-serialized` tra il client e il sistema remoto nell'esecuzione della pipeline.</span><span class="sxs-lookup"><span data-stu-id="12f60-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="12f60-118">Con questa funzionalità, PowerShell analizza la pipeline per determinare se il comando è eseguibile in modo sicuro ed è presente nel sistema di destinazione.</span><span class="sxs-lookup"><span data-stu-id="12f60-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="12f60-119">Se True, PowerShell esegue l'intera pipeline in modalità remota e si limita a serializzare e `de-serializes` i risultati nuovamente nel client.</span><span class="sxs-lookup"><span data-stu-id="12f60-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="12f60-120">Un test reale di `Get-Process | Sort-Object` tramite localhost si riduce da 10-15 secondi a circa 20-30 **millisecondi**.</span><span class="sxs-lookup"><span data-stu-id="12f60-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="12f60-121">È sufficiente che la funzionalità sia abilitata nel client.</span><span class="sxs-lookup"><span data-stu-id="12f60-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="12f60-122">Non sono necessarie modifiche nel server.</span><span class="sxs-lookup"><span data-stu-id="12f60-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="12f60-123">Unità Temp</span><span class="sxs-lookup"><span data-stu-id="12f60-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="12f60-124">Se si usa PowerShell Core in sistemi operativi diversi, sarà possibile osservare che la variabile di ambiente per individuare la directory temporanea è diversa in Windows, macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="12f60-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="12f60-125">Con questa funzionalità, un'[PSDrive][] denominata `Temp:` viene automaticamente sottoposta a mapping alla cartella temporanea per il sistema operativo in uso.</span><span class="sxs-lookup"><span data-stu-id="12f60-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="12f60-126">Esempio</span><span class="sxs-lookup"><span data-stu-id="12f60-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

<span data-ttu-id="12f60-127">Tenere presente che i comandi file nativi (ad esempio `ls` in Linux) non riconoscono le unità PowerShell e non visualizzano questa unità `Temp:`.</span><span class="sxs-lookup"><span data-stu-id="12f60-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="12f60-128">Espansione di abbreviazioni</span><span class="sxs-lookup"><span data-stu-id="12f60-128">Abbreviation Expansion</span></span>

<span data-ttu-id="12f60-129">I cmdlet PowerShell devono avere nomi descrittivi.</span><span class="sxs-lookup"><span data-stu-id="12f60-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="12f60-130">Vengono quindi generati nomi lunghi, più difficili da digitare.</span><span class="sxs-lookup"><span data-stu-id="12f60-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="12f60-131">Questa funzionalità consente di digitare i caratteri maiuscoli del cmdlet e usare il completamento tramite TAB per trovare una corrispondenza.</span><span class="sxs-lookup"><span data-stu-id="12f60-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="12f60-132">Esempio</span><span class="sxs-lookup"><span data-stu-id="12f60-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="12f60-133">Se si preme il tasto TAB ed è stato installato il modulo [Az](https://www.powershellgallery.com/packages/Az) di Azure PowerShell, verrà eseguito il completamento automatico in:</span><span class="sxs-lookup"><span data-stu-id="12f60-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="12f60-134">Questa funzionalità deve essere usata in modo interattivo.</span><span class="sxs-lookup"><span data-stu-id="12f60-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="12f60-135">Non è possibile eseguire forme abbreviate dei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="12f60-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="12f60-136">Questa funzionalità non rappresenta una sostituzione per gli alias.</span><span class="sxs-lookup"><span data-stu-id="12f60-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="12f60-137">Modifiche che causano un'interruzione</span><span class="sxs-lookup"><span data-stu-id="12f60-137">Breaking Changes</span></span>

- <span data-ttu-id="12f60-138">Correzione del comportamento di `-NoEnumerate` in `Write-Output` in modo che sia coerente con Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12f60-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="12f60-139">(9069)</span><span class="sxs-lookup"><span data-stu-id="12f60-139">(#9069)</span></span>
- <span data-ttu-id="12f60-140">Risultato di `Join-String -InputObject 1,2,3` reso uguale al risultato di `1,2,3 | Join-String` (8611) (grazie @sethvs)</span><span class="sxs-lookup"><span data-stu-id="12f60-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="12f60-141">Aggiunta di `-Stable` a `Sort-Object` e ai test correlati (7862) (grazie @KirkMunro)</span><span class="sxs-lookup"><span data-stu-id="12f60-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="12f60-142">Miglioramento del cmdlet `Start-Sleep` in modo che accetti secondi frazionari (8537) (grazie @Prototyyppi)</span><span class="sxs-lookup"><span data-stu-id="12f60-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="12f60-143">Modifica della tabella hash in modo che OrdinalIgnoreCase sia `case-insensitive` in tutte le impostazioni cultura (8566)</span><span class="sxs-lookup"><span data-stu-id="12f60-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="12f60-144">Correzione di **LiteralPath** in `Import-Csv` per l'associazione all'output di `Get-ChildItem` (8277) (grazie @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="12f60-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="12f60-145">Una colonna senza nome non viene più ignorata se viene usato il delimitatore delle virgolette doppie in `Import-Csv` (7899) (grazie @Topping)</span><span class="sxs-lookup"><span data-stu-id="12f60-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="12f60-146">`Get-ExperimentalFeature` non include più switch `-ListAvailable` (8318)</span><span class="sxs-lookup"><span data-stu-id="12f60-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="12f60-147">Il parametro di debug imposta ora `$DebugPreference` su **Continue** anziché **Inquire** (8195) (grazie @KirkMunro)</span><span class="sxs-lookup"><span data-stu-id="12f60-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="12f60-148">Supporto di `-OutputFormat` se specificato in un comando non interattivo, reindirizzato e codificato, usato con pwsh (8115)</span><span class="sxs-lookup"><span data-stu-id="12f60-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="12f60-149">Caricamento dell'assembly dal percorso di base del modulo prima di provare a eseguire il caricamento dalla Global Assembly Cache (8073)</span><span class="sxs-lookup"><span data-stu-id="12f60-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="12f60-150">Rimozione della tilde dai pacchetti di anteprima Linux (8244)</span><span class="sxs-lookup"><span data-stu-id="12f60-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="12f60-151">Spostamento dell'elaborazione di `-WorkingDirectory` prima dell'elaborazione dei profili (8079)</span><span class="sxs-lookup"><span data-stu-id="12f60-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="12f60-152">La variabile di ambiente `PATHEXT` non viene aggiunta in Unix (7697) (grazie @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="12f60-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="12f60-153">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="12f60-153">Known Issues</span></span>

- <span data-ttu-id="12f60-154">La comunicazione remota nelle piattaforme ARM di Windows IoT non riesce a caricare i moduli.</span><span class="sxs-lookup"><span data-stu-id="12f60-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="12f60-155">Vedere (8053)</span><span class="sxs-lookup"><span data-stu-id="12f60-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="12f60-156">Correzioni e aggiornamenti generali</span><span class="sxs-lookup"><span data-stu-id="12f60-156">General Updates and Fixes</span></span>

- <span data-ttu-id="12f60-157">Abilitazione del completamento tramite TAB senza distinzione tra maiuscole e minuscole per file e cartelle nel file system senza distinzione tra maiuscole e minuscole (8128)</span><span class="sxs-lookup"><span data-stu-id="12f60-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="12f60-158">PSVersionInfo.PSVersion e PSVersionInfo.PSEdition resi pubblici (8054) (grazie @KirkMunro)</span><span class="sxs-lookup"><span data-stu-id="12f60-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="12f60-159">Aggiunta dell'inferenza del tipo per `$_` / `$PSItem` nei blocchi `catch{ }` (8020) (grazie @vexx32)</span><span class="sxs-lookup"><span data-stu-id="12f60-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="12f60-160">Correzione dell'inferenza del tipo di chiamata al metodo statica (8018) (grazie @SeeminglyScience)</span><span class="sxs-lookup"><span data-stu-id="12f60-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="12f60-161">Creazione di tipi derivati per `Select-Object`, `Group-Object`, **PSObject** e **Hashtable** (7231) (grazie @powercode)</span><span class="sxs-lookup"><span data-stu-id="12f60-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="12f60-162">Supporto del metodo di chiamata con parametri di tipo `ByRef-like` (7721)</span><span class="sxs-lookup"><span data-stu-id="12f60-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="12f60-163">Gestione del caso in cui il percorso del modulo Windows PowerShell è già in PSModulePath nell'ambiente (7727)</span><span class="sxs-lookup"><span data-stu-id="12f60-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="12f60-164">Abilitazione dei cmdlet `SecureString` per sistemi non Windows archiviando il testo normale (9199)</span><span class="sxs-lookup"><span data-stu-id="12f60-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="12f60-165">Miglioramento del messaggio di errore in ambienti non Windows in caso di importazione di clixml con securestring (7997)</span><span class="sxs-lookup"><span data-stu-id="12f60-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="12f60-166">Aggiunta del parametro ReplyTo a `Send-MailMessage` (8727) (grazie @replicaJunction)</span><span class="sxs-lookup"><span data-stu-id="12f60-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="12f60-167">Aggiunta del messaggio di obsolescenza a `Send-MailMessage` (9178)</span><span class="sxs-lookup"><span data-stu-id="12f60-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="12f60-168">Correzione di `Restart-Computer` per utilizzare `localhost` quando WinRM non è presente (9160)</span><span class="sxs-lookup"><span data-stu-id="12f60-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="12f60-169">Impostazione di `Start-Job` per la generazione di un errore fatale quando PowerShell è ospitato (9128)</span><span class="sxs-lookup"><span data-stu-id="12f60-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="12f60-170">Aggiunta di suffissi e acceleratori del tipo in stile C# per ushort, uint, ulong e valori letterali brevi (7813) (grazie @vexx32)</span><span class="sxs-lookup"><span data-stu-id="12f60-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="12f60-171">Nuovi suffissi aggiunti per valori letterali numerici. Vedere [about_Numeric_Literals][] (7901) (grazie @vexx32)</span><span class="sxs-lookup"><span data-stu-id="12f60-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="12f60-172">Segnalazione corretta del livello di impatto quando SupportsShouldProcess non è impostato su 'true' (8209) (grazie @vexx32)</span><span class="sxs-lookup"><span data-stu-id="12f60-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="12f60-173">Risoluzione dei problemi dei set di caratteri delle richieste nei cmdlet Web (8742) (grazie @markekraus)</span><span class="sxs-lookup"><span data-stu-id="12f60-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="12f60-174">Risoluzione del problema `100-continue` previsto con i cmdlet Web (8679) (grazie @markekraus)</span><span class="sxs-lookup"><span data-stu-id="12f60-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="12f60-175">Risoluzione del problema che causa un blocco file con i cmdlet Web (7676) (grazie @Claustn)</span><span class="sxs-lookup"><span data-stu-id="12f60-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="12f60-176">Risoluzione del problema di analisi della tabella codici in `Invoke-RestMethod` (8694) (grazie @markekraus)</span><span class="sxs-lookup"><span data-stu-id="12f60-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="12f60-177">Refactoring di `ConvertTo-Json` per esporre JsonObject.ConvertToJson come API pubblica (8682)</span><span class="sxs-lookup"><span data-stu-id="12f60-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="12f60-178">Aggiunta della profondità massima configurabile in `ConvertFrom-Json` con -Depth (8199) (grazie @louistio)</span><span class="sxs-lookup"><span data-stu-id="12f60-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="12f60-179">Aggiunta del parametro EscapeHandling nel cmdlet `ConvertTo-Json` (7775) (grazie @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="12f60-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="12f60-180">Aggiunta di `-CustomPipeName` a pwsh e `Enter-PSHostProcess` (8889)</span><span class="sxs-lookup"><span data-stu-id="12f60-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="12f60-181">Possibilità di creare collegamenti simbolici relativi in Windows con `New-Item` (8783)</span><span class="sxs-lookup"><span data-stu-id="12f60-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="12f60-182">Possibilità per gli utenti di Windows in modalità sviluppatore di creare collegamenti simbolici senza elevazione dei privilegi (8534)</span><span class="sxs-lookup"><span data-stu-id="12f60-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="12f60-183">Possibilità per `Write-Information` di accettare `$null` (8774)</span><span class="sxs-lookup"><span data-stu-id="12f60-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="12f60-184">Correzione di `Get-Help` per funzioni avanzate con il contenuto della guida MAML (8353)</span><span class="sxs-lookup"><span data-stu-id="12f60-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="12f60-185">Risoluzione del problema PSTypeName `Get-Help` con -Parameter quando viene dichiarato solo un parametro (8754)-(grazie @pougetat)</span><span class="sxs-lookup"><span data-stu-id="12f60-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="12f60-186">Correzione del calcolo token per `Get-Help` in esecuzione in ScriptBlock per la guida dei commenti.</span><span class="sxs-lookup"><span data-stu-id="12f60-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="12f60-187">(8238) (grazie @hubuk)</span><span class="sxs-lookup"><span data-stu-id="12f60-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="12f60-188">Modifica del parametro -Parameter del cmdlet `Get-Help` in modo che accetti matrici di stringhe (8454) (grazie @sethvs)</span><span class="sxs-lookup"><span data-stu-id="12f60-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="12f60-189">Risoluzione di PAGER se il relativo percorso contiene spazi (8571) (grazie @pougetat)</span><span class="sxs-lookup"><span data-stu-id="12f60-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="12f60-190">Aggiunta di un prompt all'uso di `less` nella funzione 'help' per indicare all'utente come disconnettersi (7998)</span><span class="sxs-lookup"><span data-stu-id="12f60-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="12f60-191">Aggiunta del supporto dei tipi di enumerazione e carattere nel cmdlet `Format-Hex` (8191) (grazie @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="12f60-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="12f60-192">Rimozione di ShouldProcess da `Format-Hex` (8178)</span><span class="sxs-lookup"><span data-stu-id="12f60-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="12f60-193">Aggiunta di nuovi parametri Offset e Count a `Format-Hex` e refactoring del cmdlet (7877) (grazie @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="12f60-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="12f60-194">'name' consentito come chiave di alias per 'label' in `ConvertTo-Html`, voce 'width' consentita come intero (8426) (grazie @mklement0)</span><span class="sxs-lookup"><span data-stu-id="12f60-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="12f60-195">Funzionamento delle proprietà calcolate basate su blocchi di script ripristinato in `ConvertTo-Html` (8427) (grazie @mklement0)</span><span class="sxs-lookup"><span data-stu-id="12f60-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="12f60-196">Aggiunta del cmdlet `Join-String` per la creazione di testo dall'input della pipeline (7660) (grazie @powercode)</span><span class="sxs-lookup"><span data-stu-id="12f60-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="12f60-197">Correzione del cmdlet `Join-String` per la logica del parametro FormatString (8449) (grazie @sethvs)</span><span class="sxs-lookup"><span data-stu-id="12f60-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="12f60-198">Modifica di `Clear-Host` per l'uso di `$RAWUI` e clear per il funzionamento con comunicazione remota (8609)</span><span class="sxs-lookup"><span data-stu-id="12f60-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="12f60-199">Modifica di `Clear-Host` per rinominarlo semplicemente `[console]::clear` e rimozione dell'alias clear da Unix (8603)</span><span class="sxs-lookup"><span data-stu-id="12f60-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="12f60-200">Correzione di LiteralPath in `Import-Csv` per l'associazione all'output di `Get-ChildItem` (8277) (grazie @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="12f60-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="12f60-201">La funzione help non deve utilizzare pager per AliasHelpInfo (8552)</span><span class="sxs-lookup"><span data-stu-id="12f60-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="12f60-202">Aggiunta di `-UseMinimalHeader` a `Start-Transcript` per ridurre al minimo l'intestazione della trascrizione (8402) (grazie @lukexjeremy)</span><span class="sxs-lookup"><span data-stu-id="12f60-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="12f60-203">Aggiunta dei cmdlet `Enable-ExperimentalFeature` e `Disable-ExperimentalFeature` (8318)</span><span class="sxs-lookup"><span data-stu-id="12f60-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="12f60-204">Esposizione di tutti i cmdlet da **PSDiagnostics** se logman.exe è disponibile (8366)</span><span class="sxs-lookup"><span data-stu-id="12f60-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="12f60-205">Rimozione del parametro **Persist** da `New-PSDrive` nella piattaforma `non-Windows` (8291) (grazie @lukexjeremy)</span><span class="sxs-lookup"><span data-stu-id="12f60-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="12f60-206">Aggiunta del supporto per `cd +` (7206) (grazie @bergmeister)</span><span class="sxs-lookup"><span data-stu-id="12f60-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="12f60-207">Abilitazione di `Set-Location -LiteralPath` per l'uso con cartelle denominate + e - (8089)</span><span class="sxs-lookup"><span data-stu-id="12f60-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="12f60-208">`Test-Path` restituisce `$false` in presenza di un valore di percorso vuoto o `$null` (8080) (grazie @vexx32)</span><span class="sxs-lookup"><span data-stu-id="12f60-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="12f60-209">Parametro dinamico restituito anche se il percorso non corrisponde ad alcun provider (7957)</span><span class="sxs-lookup"><span data-stu-id="12f60-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="12f60-210">Supporto di `Get-PSHostProcessInfo` e `Enter-PSHostProcess` nelle piattaforme Unix (8232)</span><span class="sxs-lookup"><span data-stu-id="12f60-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="12f60-211">Riduzione delle allocazioni nel cmdlet `Get-Content` (8103) (grazie @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="12f60-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="12f60-212">Possibilità per `Add-Content` di condividere l'accesso in lettura con altri strumenti durante la scrittura di contenuto (8091)</span><span class="sxs-lookup"><span data-stu-id="12f60-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="12f60-213">`Get/Add-Content` genera un errore migliorato quando si fa riferimento a un contenitore (7823) (grazie @kvprasoon)</span><span class="sxs-lookup"><span data-stu-id="12f60-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="12f60-214">Aggiunta di parametri `-Name`, `-NoUserOverrides` e `-ListAvailable` a `Get-Culture` (7702) (grazie @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="12f60-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="12f60-215">Aggiunta di un attributo unificato per il completamento per il parametro **Encoding**.</span><span class="sxs-lookup"><span data-stu-id="12f60-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="12f60-216">(7732) (grazie @ThreeFive-O)</span><span class="sxs-lookup"><span data-stu-id="12f60-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="12f60-217">ID numerici e nome delle tabelle codici registrate nei parametri **Encoding** (7636) (grazie @iSazonov)</span><span class="sxs-lookup"><span data-stu-id="12f60-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="12f60-218">Correzione di `Rename-Item -Path` con carattere jolly (7398) (grazie @kwkam)</span><span class="sxs-lookup"><span data-stu-id="12f60-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="12f60-219">Svuotamento anziché eliminazione del file quando si usa `Start-Transcript` ed è presente un file (8131) (grazie @paalbra)</span><span class="sxs-lookup"><span data-stu-id="12f60-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="12f60-220">Apertura di file di origine da parte di `Add-Type` con **FileAccess.Read** e **FileShare.Read** in modo esplicito (7915) (grazie @IISResetMe)</span><span class="sxs-lookup"><span data-stu-id="12f60-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="12f60-221">Correzione di `Enter-PSSession -ContainerId` per le versioni di Windows più recenti (7883)</span><span class="sxs-lookup"><span data-stu-id="12f60-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="12f60-222">Garanzia di popolamento della proprietà **NestedModules** da parte di `Test-ModuleManifest` (7859)</span><span class="sxs-lookup"><span data-stu-id="12f60-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="12f60-223">Aggiunta del case `%F` a `Get-Date` -UFormat (7630) (grazie @britishben)</span><span class="sxs-lookup"><span data-stu-id="12f60-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="12f60-224">Correzione di `Set-Service -Status Stopped` per arrestare i servizi con dipendenze (5525) (grazie @zhenggu)</span><span class="sxs-lookup"><span data-stu-id="12f60-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Funzionalità sperimentali]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
