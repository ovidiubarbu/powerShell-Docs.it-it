---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Guida alla riga di comando PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401357"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="ddff1-103">Guida della riga di comando PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="ddff1-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="ddff1-104">È possibile usare PowerShell.exe per avviare una sessione PowerShell dalla riga di comando di un altro strumento, come Cmd.exe, o usarlo nella riga di comando PowerShell per avviare una nuova sessione.</span><span class="sxs-lookup"><span data-stu-id="ddff1-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="ddff1-105">Usare i parametri per personalizzare la sessione.</span><span class="sxs-lookup"><span data-stu-id="ddff1-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="ddff1-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ddff1-106">Syntax</span></span>

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="ddff1-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="ddff1-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="ddff1-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="ddff1-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="ddff1-109">Accetta una versione di un comando di tipo stringa codificata in base 64.</span><span class="sxs-lookup"><span data-stu-id="ddff1-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="ddff1-110">Usare questo parametro per inviare a PowerShell comandi che richiedono virgolette complesse o parentesi graffe.</span><span class="sxs-lookup"><span data-stu-id="ddff1-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="ddff1-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="ddff1-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="ddff1-112">Imposta i criteri di esecuzione predefiniti per la sessione corrente e li salva nella variabile di ambiente $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="ddff1-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="ddff1-113">Questo parametro non modifica i criteri di esecuzione di PowerShell impostati nel Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="ddff1-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="ddff1-114">Per informazioni sui criteri di esecuzione di PowerShell, incluso un elenco di valori validi, vedere [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="ddff1-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="ddff1-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="ddff1-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="ddff1-116">Esegue lo script specificato nell'ambito locale ("dot sourcing" ), in modo che le funzioni e le variabili create dallo script siano disponibili nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="ddff1-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="ddff1-117">Immettere il percorso del file di script ed eventuali parametri.</span><span class="sxs-lookup"><span data-stu-id="ddff1-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="ddff1-118">**File** deve essere l'ultimo parametro nel comando.</span><span class="sxs-lookup"><span data-stu-id="ddff1-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="ddff1-119">Tutti i valori digitati dopo il parametro **-File** vengono interpretati come percorso del file script e i parametri passati a tale script.</span><span class="sxs-lookup"><span data-stu-id="ddff1-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="ddff1-120">I parametri passati allo script vengono passati come stringhe letterali, dopo l'interpretazione da parte della shell corrente.</span><span class="sxs-lookup"><span data-stu-id="ddff1-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="ddff1-121">Ad esempio, se si trovano in cmd.exe e si desidera passare un valore di variabile di ambiente, utilizzare la sintassi cmd.exe: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="ddff1-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="ddff1-122">Al contrario, in esecuzione `powershell.exe -File .\test.ps1 -TestParam $env:windir` nei risultati cmd.exe nello script di ricevere la stringa letterale `$env:windir` perché non ha significato speciale shell cmd.exe corrente.</span><span class="sxs-lookup"><span data-stu-id="ddff1-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="ddff1-123">Il `$env:windir` stile del riferimento alla variabile di ambiente _possibile_ utilizzabile all'interno di un `-Command` parametro, poiché non esiste verrà interpretato come codice di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddff1-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="ddff1-124">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="ddff1-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="ddff1-125">Descrive il formato dei dati inviati a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddff1-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="ddff1-126">I valori validi sono "Text" (stringhe di testo) o "XML" (formato CLIXML serializzato).</span><span class="sxs-lookup"><span data-stu-id="ddff1-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="ddff1-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="ddff1-127">-Mta</span></span>

<span data-ttu-id="ddff1-128">Avvia PowerShell usando un apartment a thread multipli.</span><span class="sxs-lookup"><span data-stu-id="ddff1-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="ddff1-129">Questo parametro è stato introdotto in PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="ddff1-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="ddff1-130">In PowerShell 3.0 l'impostazione predefinita è apartment a thread singolo (STA).</span><span class="sxs-lookup"><span data-stu-id="ddff1-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="ddff1-131">In PowerShell 2.0 l'impostazione predefinita è apartment a thread multipli (MTA).</span><span class="sxs-lookup"><span data-stu-id="ddff1-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="ddff1-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="ddff1-132">-NoExit</span></span>

<span data-ttu-id="ddff1-133">Non viene chiuso dopo l'esecuzione dei comandi di avvio.</span><span class="sxs-lookup"><span data-stu-id="ddff1-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="ddff1-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="ddff1-134">-NoLogo</span></span>

<span data-ttu-id="ddff1-135">Nasconde le informazioni sul copyright all'avvio.</span><span class="sxs-lookup"><span data-stu-id="ddff1-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="ddff1-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="ddff1-136">-NonInteractive</span></span>

<span data-ttu-id="ddff1-137">Non presenta un prompt interattivo all'utente.</span><span class="sxs-lookup"><span data-stu-id="ddff1-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="ddff1-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="ddff1-138">-NoProfile</span></span>

<span data-ttu-id="ddff1-139">Non carica il profilo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddff1-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="ddff1-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="ddff1-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="ddff1-141">Determina la formattazione dell'output di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddff1-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="ddff1-142">I valori validi sono "Text" (stringhe di testo) o "XML" (formato CLIXML serializzato).</span><span class="sxs-lookup"><span data-stu-id="ddff1-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="ddff1-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="ddff1-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="ddff1-144">Carica il file della console di PowerShell specificato.</span><span class="sxs-lookup"><span data-stu-id="ddff1-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="ddff1-145">Immettere il percorso e il nome del file della console.</span><span class="sxs-lookup"><span data-stu-id="ddff1-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="ddff1-146">Per creare un file di console, usare il cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddff1-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="ddff1-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="ddff1-147">-Sta</span></span>

<span data-ttu-id="ddff1-148">Avvia PowerShell usando un apartment a thread singolo.</span><span class="sxs-lookup"><span data-stu-id="ddff1-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="ddff1-149">In PowerShell 3.0 l'impostazione predefinita è apartment a thread singolo (STA).</span><span class="sxs-lookup"><span data-stu-id="ddff1-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="ddff1-150">In PowerShell 2.0 l'impostazione predefinita è apartment a thread multipli (MTA).</span><span class="sxs-lookup"><span data-stu-id="ddff1-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="ddff1-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="ddff1-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="ddff1-152">Avvia la versione specificata di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddff1-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="ddff1-153">La versione specificata deve essere installata nel sistema.</span><span class="sxs-lookup"><span data-stu-id="ddff1-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="ddff1-154">Se PowerShell 3.0 è installato nel computer, i valori validi sono "2.0" e "3.0".</span><span class="sxs-lookup"><span data-stu-id="ddff1-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="ddff1-155">Il valore predefinito è "3.0".</span><span class="sxs-lookup"><span data-stu-id="ddff1-155">The default value is "3.0".</span></span>

<span data-ttu-id="ddff1-156">Se PowerShell 3.0 non è installato, l'unico valore valido è "2.0".</span><span class="sxs-lookup"><span data-stu-id="ddff1-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="ddff1-157">Gli altri valori sono ignorati.</span><span class="sxs-lookup"><span data-stu-id="ddff1-157">Other values are ignored.</span></span>

<span data-ttu-id="ddff1-158">Per altre informazioni, vedere [Installazione di Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ddff1-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="ddff1-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="ddff1-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="ddff1-160">Imposta lo stile della finestra per la sessione.</span><span class="sxs-lookup"><span data-stu-id="ddff1-160">Sets the window style for the session.</span></span> <span data-ttu-id="ddff1-161">I valori validi sono Normal, Minimized, Maximized e Hidden.</span><span class="sxs-lookup"><span data-stu-id="ddff1-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="ddff1-162">-Command</span><span class="sxs-lookup"><span data-stu-id="ddff1-162">-Command</span></span>

<span data-ttu-id="ddff1-163">Esegue i comandi specificati (e gli eventuali parametri) come se fossero stati digitati al prompt dei comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddff1-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="ddff1-164">Dopo l'esecuzione, PowerShell viene chiuso, a meno che il **NoExit** parametro è specificato.</span><span class="sxs-lookup"><span data-stu-id="ddff1-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="ddff1-165">Qualsiasi testo dopo `-Command` viene inviato come singola riga di comando a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddff1-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="ddff1-166">Questo approccio è diverso dal modo in cui `-File` gestisce i parametri inviati a uno script.</span><span class="sxs-lookup"><span data-stu-id="ddff1-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="ddff1-167">Il valore di `-Command` può essere "-", una stringa o un blocco di script.</span><span class="sxs-lookup"><span data-stu-id="ddff1-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="ddff1-168">I risultati del comando vengono restituiti alla shell padre come oggetti XML deserializzati, gli oggetti non attivi.</span><span class="sxs-lookup"><span data-stu-id="ddff1-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="ddff1-169">Se il valore di `-Command` è "-", il testo del comando viene letto dall'input standard.</span><span class="sxs-lookup"><span data-stu-id="ddff1-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="ddff1-170">Quando il valore di `-Command` è una stringa **comandi** _necessario_ essere l'ultimo parametro specificato perché i caratteri digitati dopo il comando vengono interpretati come argomenti del comando.</span><span class="sxs-lookup"><span data-stu-id="ddff1-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="ddff1-171">Il **comandi** parametro accetta solo un blocco di script per l'esecuzione quando in grado di riconoscere il valore passato a `-Command` come tipo di blocco di script.</span><span class="sxs-lookup"><span data-stu-id="ddff1-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="ddff1-172">Si tratta _solo_ possibili durante l'esecuzione PowerShell.exe da un altro host di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddff1-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="ddff1-173">Il parametro ScriptBlock tipo può essere contenuto nella variabile, restituito da un'espressione o analizzati da PowerShell esistente ospitare come un blocco di script letterale racchiuso tra parentesi graffe `{}`prima che venga passato a PowerShell.exe.</span><span class="sxs-lookup"><span data-stu-id="ddff1-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="ddff1-174">Cmd.exe, non include alcun equivalente di un blocco di script (o tipo di blocco di script), pertanto il valore passato a **comandi** verranno _sempre_ sia una stringa.</span><span class="sxs-lookup"><span data-stu-id="ddff1-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="ddff1-175">È possibile scrivere un blocco di script all'interno della stringa, ma anziché in esecuzione questo si comporta esattamente come se venisse digitato, al prompt di PowerShell tipico, stampa il contenuto dello script Prenditi nuovamente all'utente.</span><span class="sxs-lookup"><span data-stu-id="ddff1-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="ddff1-176">Una stringa passata a `-Command` verrà comunque eseguito come PowerShell, in modo che le parentesi graffe blocco di script spesso non sono necessarie in primo luogo durante l'esecuzione da cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="ddff1-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="ddff1-177">Per eseguire un blocco di script inline definito all'interno di una stringa, il [operatore di chiamata](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` consente di:</span><span class="sxs-lookup"><span data-stu-id="ddff1-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="ddff1-178">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="ddff1-178">-Help, -?, /?</span></span>

<span data-ttu-id="ddff1-179">Mostra la sintassi di powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="ddff1-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="ddff1-180">Se si digita un comando PowerShell.exe in PowerShell, anteporre ai parametri del comando un trattino (-) e non una barra (/).</span><span class="sxs-lookup"><span data-stu-id="ddff1-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="ddff1-181">In Cmd.exe è possibile usare sia il trattino che la barra.</span><span class="sxs-lookup"><span data-stu-id="ddff1-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="ddff1-182">Nota sulla risoluzione dei problemi: In PowerShell 2.0 l'avvio di alcuni programmi nella console di Windows PowerShell un errore con LastExitCode uguale a 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="ddff1-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="ddff1-183">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="ddff1-183">EXAMPLES</span></span>

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
