---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Guida alla riga di comando PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: b2236decb3295ee5b543f72f083e516c91fa4b5f
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="47fe3-103">Guida della riga di comando PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="47fe3-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="47fe3-104">Avvia una sessione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47fe3-104">Starts a Windows PowerShell session.</span></span> <span data-ttu-id="47fe3-105">È possibile usare PowerShell.exe per avviare una sessione di Windows PowerShell dalla riga di comando di un altro strumento, come Cmd.exe, o usarlo nella riga di comando di Windows PowerShell per avviare una nuova sessione.</span><span class="sxs-lookup"><span data-stu-id="47fe3-105">You can use PowerShell.exe to start a Windows PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the Windows PowerShell command line to start a new session.</span></span> <span data-ttu-id="47fe3-106">Usare i parametri per personalizzare la sessione.</span><span class="sxs-lookup"><span data-stu-id="47fe3-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="47fe3-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="47fe3-107">Syntax</span></span>

```syntax
PowerShell[.exe]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-InputFormat {Text | XML}] 
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive] 
       [-NoProfile] 
       [-OutputFormat {Text | XML}] 
       [-PSConsoleFile <FilePath> | -Version <Windows PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
       [-File <FilePath> [<Args>]]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="47fe3-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="47fe3-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="47fe3-109">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="47fe3-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="47fe3-110">Accetta una versione di un comando di tipo stringa codificata in base 64.</span><span class="sxs-lookup"><span data-stu-id="47fe3-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="47fe3-111">Usare questo parametro per inviare a Windows PowerShell comandi che richiedono virgolette complesse o parentesi graffe.</span><span class="sxs-lookup"><span data-stu-id="47fe3-111">Use this parameter to submit commands to Windows PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="47fe3-112">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="47fe3-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="47fe3-113">Imposta i criteri di esecuzione predefiniti per la sessione corrente e li salva nella variabile di ambiente $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="47fe3-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="47fe3-114">Questo parametro non modifica i criteri di esecuzione di Windows PowerShell impostati nel Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="47fe3-114">This parameter does not change the Windows PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="47fe3-115">Per informazioni sui criteri di esecuzione di Windows PowerShell, incluso un elenco di valori validi, vedere about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span><span class="sxs-lookup"><span data-stu-id="47fe3-115">For information about Windows PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="47fe3-116">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="47fe3-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="47fe3-117">Esegue lo script specificato nell'ambito locale ("dot sourcing" ), in modo che le funzioni e le variabili create dallo script siano disponibili nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="47fe3-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="47fe3-118">Immettere il percorso del file di script ed eventuali parametri.</span><span class="sxs-lookup"><span data-stu-id="47fe3-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="47fe3-119">**File** deve essere l'ultimo parametro del comando, perché tutti i caratteri digitati dopo il nome del parametro **File** vengono interpretati come il percorso del file di script seguito dai parametri di script e dai relativi valori.</span><span class="sxs-lookup"><span data-stu-id="47fe3-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="47fe3-120">È possibile includere i parametri di uno script e i relativi valori nel valore del parametro **File**.</span><span class="sxs-lookup"><span data-stu-id="47fe3-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="47fe3-121">Ad esempio: `-File .\Get-Script.ps1 -Domain Central` Si noti che i parametri passati allo script vengono passati come stringhe letterali (dopo l'interpretazione dalla shell corrente).</span><span class="sxs-lookup"><span data-stu-id="47fe3-121">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="47fe3-122">Ad esempio, se si usa cmd.exe e si vuole passare un valore di variabile di ambiente, è necessario usare la sintassi di cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` Se si usasse la sintassi di PowerShell, in questo esempio lo script riceverebbe il valore letterale "$env: windir" e non il valore della variabile di ambiente: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="47fe3-122">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="47fe3-123">In genere, i parametri opzionali di uno script sono inclusi o omessi.</span><span class="sxs-lookup"><span data-stu-id="47fe3-123">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="47fe3-124">Il comando seguente usa ad esempio il parametro **All** del file di script Get-Script.ps1: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="47fe3-124">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="47fe3-125">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="47fe3-125">\-InputFormat {Text | XML}</span></span>
<span data-ttu-id="47fe3-126">Descrive il formato dei dati inviati a Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47fe3-126">Describes the format of data sent to Windows PowerShell.</span></span> <span data-ttu-id="47fe3-127">I valori validi sono "Text" (stringhe di testo) o "XML" (formato CLIXML serializzato).</span><span class="sxs-lookup"><span data-stu-id="47fe3-127">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="47fe3-128">-Mta</span><span class="sxs-lookup"><span data-stu-id="47fe3-128">-Mta</span></span>
<span data-ttu-id="47fe3-129">Avvia Windows PowerShell usando un apartment a thread multipli.</span><span class="sxs-lookup"><span data-stu-id="47fe3-129">Starts Windows PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="47fe3-130">Questo parametro è stato introdotto in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="47fe3-130">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="47fe3-131">In Windows PowerShell 3.0 l'impostazione predefinita è apartment a thread singolo (STA).</span><span class="sxs-lookup"><span data-stu-id="47fe3-131">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="47fe3-132">In Windows PowerShell 2.0 l'impostazione predefinita è apartment a thread multipli (MTA).</span><span class="sxs-lookup"><span data-stu-id="47fe3-132">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="47fe3-133">-NoExit</span><span class="sxs-lookup"><span data-stu-id="47fe3-133">-NoExit</span></span>
<span data-ttu-id="47fe3-134">Non viene chiuso dopo l'esecuzione dei comandi di avvio.</span><span class="sxs-lookup"><span data-stu-id="47fe3-134">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="47fe3-135">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="47fe3-135">-NoLogo</span></span>
<span data-ttu-id="47fe3-136">Nasconde le informazioni sul copyright all'avvio.</span><span class="sxs-lookup"><span data-stu-id="47fe3-136">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="47fe3-137">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="47fe3-137">-NonInteractive</span></span>
<span data-ttu-id="47fe3-138">Non presenta un prompt interattivo all'utente.</span><span class="sxs-lookup"><span data-stu-id="47fe3-138">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="47fe3-139">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="47fe3-139">-NoProfile</span></span>
<span data-ttu-id="47fe3-140">Non carica il profilo di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47fe3-140">Does not load the Windows PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="47fe3-141">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="47fe3-141">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="47fe3-142">Determina la formattazione dell'output di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47fe3-142">Determines how output from Windows PowerShell is formatted.</span></span> <span data-ttu-id="47fe3-143">I valori validi sono "Text" (stringhe di testo) o "XML" (formato CLIXML serializzato).</span><span class="sxs-lookup"><span data-stu-id="47fe3-143">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="47fe3-144">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="47fe3-144">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="47fe3-145">Carica il file della console di Windows PowerShell specificato.</span><span class="sxs-lookup"><span data-stu-id="47fe3-145">Loads the specified Windows PowerShell console file.</span></span> <span data-ttu-id="47fe3-146">Immettere il percorso e il nome del file della console.</span><span class="sxs-lookup"><span data-stu-id="47fe3-146">Enter the path and name of the console file.</span></span> <span data-ttu-id="47fe3-147">Per creare un file di console, usare il cmdlet [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47fe3-147">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in Windows PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="47fe3-148">-Sta</span><span class="sxs-lookup"><span data-stu-id="47fe3-148">-Sta</span></span>
<span data-ttu-id="47fe3-149">Avvia Windows PowerShell usando un apartment a thread singolo.</span><span class="sxs-lookup"><span data-stu-id="47fe3-149">Starts Windows PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="47fe3-150">In Windows PowerShell 3.0 l'impostazione predefinita è apartment a thread singolo (STA).</span><span class="sxs-lookup"><span data-stu-id="47fe3-150">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="47fe3-151">In Windows PowerShell 2.0 l'impostazione predefinita è apartment a thread multipli (MTA).</span><span class="sxs-lookup"><span data-stu-id="47fe3-151">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-windows-powershell-version"></a><span data-ttu-id="47fe3-152">-Version <Windows PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="47fe3-152">-Version <Windows PowerShell Version></span></span>
<span data-ttu-id="47fe3-153">Avvia la versione specificata di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47fe3-153">Starts the specified version of Windows PowerShell.</span></span> <span data-ttu-id="47fe3-154">La versione specificata deve essere installata nel sistema.</span><span class="sxs-lookup"><span data-stu-id="47fe3-154">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="47fe3-155">Se Windows PowerShell 3.0 è installato nel computer, i valori validi sono "2.0" e "3.0".</span><span class="sxs-lookup"><span data-stu-id="47fe3-155">If Windows PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="47fe3-156">Il valore predefinito è "3.0".</span><span class="sxs-lookup"><span data-stu-id="47fe3-156">The default value is "3.0".</span></span>

<span data-ttu-id="47fe3-157">Se Windows PowerShell 3.0 non è installato, l'unico valore valido è "2.0".</span><span class="sxs-lookup"><span data-stu-id="47fe3-157">If Windows PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="47fe3-158">Gli altri valori sono ignorati.</span><span class="sxs-lookup"><span data-stu-id="47fe3-158">Other values are ignored.</span></span>

<span data-ttu-id="47fe3-159">Per altre informazioni, vedere "Installazione di Windows PowerShell" nella [Guida introduttiva a Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span><span class="sxs-lookup"><span data-stu-id="47fe3-159">For more information, see "Installing Windows PowerShell" in the [Getting Started with Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="47fe3-160">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="47fe3-160">-WindowStyle <Window style></span></span>
<span data-ttu-id="47fe3-161">Imposta lo stile della finestra per la sessione.</span><span class="sxs-lookup"><span data-stu-id="47fe3-161">Sets the window style for the session.</span></span> <span data-ttu-id="47fe3-162">I valori validi sono Normal, Minimized, Maximized e Hidden.</span><span class="sxs-lookup"><span data-stu-id="47fe3-162">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="47fe3-163">-Command</span><span class="sxs-lookup"><span data-stu-id="47fe3-163">-Command</span></span>
<span data-ttu-id="47fe3-164">Esegue i comandi specificati (e gli eventuali parametri) come se fossero stati digitati al prompt dei comandi di Windows PowerShell, quindi viene chiuso, a meno che non sia stato specificato il parametro NoExit.</span><span class="sxs-lookup"><span data-stu-id="47fe3-164">Executes the specified commands (and any parameters) as though they were typed at the Windows PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="47fe3-165">In pratica, qualsiasi testo che segue `-Command` viene inviato come una singola riga di comando di PowerShell (diverso da come `-File` gestisce i parametri inviati a uno script).</span><span class="sxs-lookup"><span data-stu-id="47fe3-165">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="47fe3-166">Il valore di Command può essere "-", una stringa</span><span class="sxs-lookup"><span data-stu-id="47fe3-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="47fe3-167">o un blocco di script.</span><span class="sxs-lookup"><span data-stu-id="47fe3-167">or a script block.</span></span> <span data-ttu-id="47fe3-168">Se il valore di Command è "-", il testo del comando viene letto dall'input standard.</span><span class="sxs-lookup"><span data-stu-id="47fe3-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="47fe3-169">I blocchi di script devono essere racchiusi tra parentesi graffe ({}).</span><span class="sxs-lookup"><span data-stu-id="47fe3-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="47fe3-170">È possibile specificare un blocco di script solo se si esegue PowerShell.exe in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47fe3-170">You can specify a script block only when running PowerShell.exe in Windows PowerShell.</span></span> <span data-ttu-id="47fe3-171">I risultati dello script vengono restituiti alla shell padre come oggetti XML deserializzati, non come oggetti attivi.</span><span class="sxs-lookup"><span data-stu-id="47fe3-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="47fe3-172">Se il valore di Command è una stringa, **Command** deve essere l'ultimo parametro del comando, perché i caratteri digitati dopo il comando vengono interpretati come argomenti del comando.</span><span class="sxs-lookup"><span data-stu-id="47fe3-172">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="47fe3-173">Per scrivere una stringa che esegua un comando di Windows PowerShell, usare il formato:</span><span class="sxs-lookup"><span data-stu-id="47fe3-173">To write a string that runs a Windows PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="47fe3-174">in cui le virgolette indicano una stringa e l'operatore invoke (&) causa l'esecuzione del comando.</span><span class="sxs-lookup"><span data-stu-id="47fe3-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="47fe3-175">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="47fe3-175">-Help, -?, /?</span></span>
<span data-ttu-id="47fe3-176">Mostra questo messaggio.</span><span class="sxs-lookup"><span data-stu-id="47fe3-176">Shows this message.</span></span> <span data-ttu-id="47fe3-177">Se si digita un comando PowerShell.exe in Windows PowerShell, anteporre ai parametri del comando un trattino (-) e non una barra (/).</span><span class="sxs-lookup"><span data-stu-id="47fe3-177">If you are typing a PowerShell.exe command in Windows PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="47fe3-178">In Cmd.exe è possibile usare sia il trattino che la barra.</span><span class="sxs-lookup"><span data-stu-id="47fe3-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="47fe3-179">Nota relativa alla risoluzione dei problemi: in Windows PowerShell 2.0 l'avvio di alcuni programmi nella console di Windows PowerShell genera un errore con LastExitCode uguale a 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="47fe3-179">Troubleshooting Note: In Windows PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="47fe3-180">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="47fe3-180">EXAMPLES</span></span>

```
PowerShell -PSConsoleFile sqlsnapin.psc1

PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

PowerShell -Command "Get-EventLog -LogName security"

# in an existing PowerShell session that understands the curly braces mean a script block
PowerShell -Command {Get-EventLog -LogName security}

PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

