---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Guida alla riga di comando PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133103"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="ac621-103">Guida della riga di comando PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="ac621-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="ac621-104">È possibile usare PowerShell.exe per avviare una sessione PowerShell dalla riga di comando di un altro strumento, come Cmd.exe, o usarlo nella riga di comando PowerShell per avviare una nuova sessione.</span><span class="sxs-lookup"><span data-stu-id="ac621-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="ac621-105">Usare i parametri per personalizzare la sessione.</span><span class="sxs-lookup"><span data-stu-id="ac621-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="ac621-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ac621-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="ac621-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="ac621-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="ac621-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="ac621-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="ac621-109">Accetta una versione di un comando di tipo stringa codificata in base 64.</span><span class="sxs-lookup"><span data-stu-id="ac621-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="ac621-110">Usare questo parametro per inviare a PowerShell comandi che richiedono virgolette complesse o parentesi graffe.</span><span class="sxs-lookup"><span data-stu-id="ac621-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="ac621-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="ac621-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="ac621-112">Imposta i criteri di esecuzione predefiniti per la sessione corrente e li salva nella variabile di ambiente $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="ac621-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="ac621-113">Questo parametro non modifica i criteri di esecuzione di PowerShell impostati nel Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="ac621-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="ac621-114">Per informazioni sui criteri di esecuzione di PowerShell, incluso un elenco di valori validi, vedere [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="ac621-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="ac621-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="ac621-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="ac621-116">Esegue lo script specificato nell'ambito locale ("dot sourcing" ), in modo che le funzioni e le variabili create dallo script siano disponibili nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="ac621-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="ac621-117">Immettere il percorso del file di script ed eventuali parametri.</span><span class="sxs-lookup"><span data-stu-id="ac621-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="ac621-118">**File** deve essere l'ultimo parametro nel comando.</span><span class="sxs-lookup"><span data-stu-id="ac621-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="ac621-119">Tutti i valori digitati dopo il parametro **-File** vengono interpretati come percorso del file script e i parametri passati a tale script.</span><span class="sxs-lookup"><span data-stu-id="ac621-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="ac621-120">I parametri passati allo script vengono passati come stringhe letterali, dopo l'interpretazione da parte della shell corrente.</span><span class="sxs-lookup"><span data-stu-id="ac621-120">Parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span> <span data-ttu-id="ac621-121">Ad esempio, se si usa cmd.exe e si vuole passare un valore di variabile di ambiente, è necessario usare la sintassi di cmd.exe: `powershell -File .\test.ps1 -Sample %windir%`. In questo esempio lo script riceve la stringa letterale `$env:windir` e non il valore della variabile di ambiente: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="ac621-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` In this example, the script receives the literal string `$env:windir` and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="ac621-122">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="ac621-122">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="ac621-123">Descrive il formato dei dati inviati a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac621-123">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="ac621-124">I valori validi sono "Text" (stringhe di testo) o "XML" (formato CLIXML serializzato).</span><span class="sxs-lookup"><span data-stu-id="ac621-124">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="ac621-125">-Mta</span><span class="sxs-lookup"><span data-stu-id="ac621-125">-Mta</span></span>

<span data-ttu-id="ac621-126">Avvia PowerShell usando un apartment a thread multipli.</span><span class="sxs-lookup"><span data-stu-id="ac621-126">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="ac621-127">Questo parametro è stato introdotto in PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="ac621-127">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="ac621-128">In PowerShell 3.0 l'impostazione predefinita è apartment a thread singolo (STA).</span><span class="sxs-lookup"><span data-stu-id="ac621-128">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="ac621-129">In PowerShell 2.0 l'impostazione predefinita è apartment a thread multipli (MTA).</span><span class="sxs-lookup"><span data-stu-id="ac621-129">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="ac621-130">-NoExit</span><span class="sxs-lookup"><span data-stu-id="ac621-130">-NoExit</span></span>

<span data-ttu-id="ac621-131">Non viene chiuso dopo l'esecuzione dei comandi di avvio.</span><span class="sxs-lookup"><span data-stu-id="ac621-131">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="ac621-132">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="ac621-132">-NoLogo</span></span>

<span data-ttu-id="ac621-133">Nasconde le informazioni sul copyright all'avvio.</span><span class="sxs-lookup"><span data-stu-id="ac621-133">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="ac621-134">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="ac621-134">-NonInteractive</span></span>

<span data-ttu-id="ac621-135">Non presenta un prompt interattivo all'utente.</span><span class="sxs-lookup"><span data-stu-id="ac621-135">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="ac621-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="ac621-136">-NoProfile</span></span>

<span data-ttu-id="ac621-137">Non carica il profilo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac621-137">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="ac621-138">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="ac621-138">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="ac621-139">Determina la formattazione dell'output di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac621-139">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="ac621-140">I valori validi sono "Text" (stringhe di testo) o "XML" (formato CLIXML serializzato).</span><span class="sxs-lookup"><span data-stu-id="ac621-140">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="ac621-141">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="ac621-141">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="ac621-142">Carica il file della console di PowerShell specificato.</span><span class="sxs-lookup"><span data-stu-id="ac621-142">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="ac621-143">Immettere il percorso e il nome del file della console.</span><span class="sxs-lookup"><span data-stu-id="ac621-143">Enter the path and name of the console file.</span></span> <span data-ttu-id="ac621-144">Per creare un file di console, usare il cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac621-144">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="ac621-145">-Sta</span><span class="sxs-lookup"><span data-stu-id="ac621-145">-Sta</span></span>

<span data-ttu-id="ac621-146">Avvia PowerShell usando un apartment a thread singolo.</span><span class="sxs-lookup"><span data-stu-id="ac621-146">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="ac621-147">In PowerShell 3.0 l'impostazione predefinita è apartment a thread singolo (STA).</span><span class="sxs-lookup"><span data-stu-id="ac621-147">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="ac621-148">In PowerShell 2.0 l'impostazione predefinita è apartment a thread multipli (MTA).</span><span class="sxs-lookup"><span data-stu-id="ac621-148">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="ac621-149">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="ac621-149">-Version <PowerShell Version></span></span>

<span data-ttu-id="ac621-150">Avvia la versione specificata di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac621-150">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="ac621-151">La versione specificata deve essere installata nel sistema.</span><span class="sxs-lookup"><span data-stu-id="ac621-151">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="ac621-152">Se PowerShell 3.0 è installato nel computer, i valori validi sono "2.0" e "3.0".</span><span class="sxs-lookup"><span data-stu-id="ac621-152">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="ac621-153">Il valore predefinito è "3.0".</span><span class="sxs-lookup"><span data-stu-id="ac621-153">The default value is "3.0".</span></span>

<span data-ttu-id="ac621-154">Se PowerShell 3.0 non è installato, l'unico valore valido è "2.0".</span><span class="sxs-lookup"><span data-stu-id="ac621-154">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="ac621-155">Gli altri valori sono ignorati.</span><span class="sxs-lookup"><span data-stu-id="ac621-155">Other values are ignored.</span></span>

<span data-ttu-id="ac621-156">Per altre informazioni, vedere [Installazione di Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ac621-156">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="ac621-157">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="ac621-157">-WindowStyle <Window style></span></span>

<span data-ttu-id="ac621-158">Imposta lo stile della finestra per la sessione.</span><span class="sxs-lookup"><span data-stu-id="ac621-158">Sets the window style for the session.</span></span> <span data-ttu-id="ac621-159">I valori validi sono Normal, Minimized, Maximized e Hidden.</span><span class="sxs-lookup"><span data-stu-id="ac621-159">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="ac621-160">-Command</span><span class="sxs-lookup"><span data-stu-id="ac621-160">-Command</span></span>

<span data-ttu-id="ac621-161">Esegue i comandi specificati (e gli eventuali parametri) come se fossero stati digitati al prompt dei comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac621-161">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span> <span data-ttu-id="ac621-162">Dopo l'esecuzione, PowerShell viene chiuso, a meno che non sia specificato il parametro `-NoExit`.</span><span class="sxs-lookup"><span data-stu-id="ac621-162">After execution, PowerShell exits unless the `-NoExit` parameter is specified.</span></span>
<span data-ttu-id="ac621-163">Qualsiasi testo dopo `-Command` viene inviato come singola riga di comando a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac621-163">Any text after `-Command` is sent as a single command line to PowerShell.</span></span> <span data-ttu-id="ac621-164">Questo approccio è diverso dal modo in cui `-File` gestisce i parametri inviati a uno script.</span><span class="sxs-lookup"><span data-stu-id="ac621-164">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="ac621-165">Il valore di Command può essere "-", una stringa</span><span class="sxs-lookup"><span data-stu-id="ac621-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="ac621-166">o un blocco di script.</span><span class="sxs-lookup"><span data-stu-id="ac621-166">or a script block.</span></span> <span data-ttu-id="ac621-167">Se il valore di Command è "-", il testo del comando viene letto dall'input standard.</span><span class="sxs-lookup"><span data-stu-id="ac621-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="ac621-168">I blocchi di script devono essere racchiusi tra parentesi graffe ({}).</span><span class="sxs-lookup"><span data-stu-id="ac621-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="ac621-169">È possibile specificare un blocco di script solo se si esegue PowerShell.exe in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac621-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="ac621-170">I risultati dello script vengono restituiti alla shell padre come oggetti XML deserializzati, non come oggetti attivi.</span><span class="sxs-lookup"><span data-stu-id="ac621-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="ac621-171">Se il valore di Command è una stringa, **Command** deve essere l'ultimo parametro del comando, perché i caratteri digitati dopo il comando vengono interpretati come argomenti del comando.</span><span class="sxs-lookup"><span data-stu-id="ac621-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="ac621-172">Per scrivere una stringa che esegua un comando di PowerShell, usare il formato:</span><span class="sxs-lookup"><span data-stu-id="ac621-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="ac621-173">Le virgolette indicano una stringa e l'operatore invoke (&) provoca l'esecuzione del comando.</span><span class="sxs-lookup"><span data-stu-id="ac621-173">The quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="ac621-174">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="ac621-174">-Help, -?, /?</span></span>

<span data-ttu-id="ac621-175">Mostra la sintassi di powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="ac621-175">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="ac621-176">Se si digita un comando PowerShell.exe in PowerShell, anteporre ai parametri del comando un trattino (-) e non una barra (/).</span><span class="sxs-lookup"><span data-stu-id="ac621-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="ac621-177">In Cmd.exe è possibile usare sia il trattino che la barra.</span><span class="sxs-lookup"><span data-stu-id="ac621-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="ac621-178">Nota relativa alla risoluzione dei problemi: in PowerShell 2.0 l'avvio di alcuni programmi nella console di Windows PowerShell genera un errore con LastExitCode di 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="ac621-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="ac621-179">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="ac621-179">EXAMPLES</span></span>

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
