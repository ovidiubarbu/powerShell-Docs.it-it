---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Guida alla riga di comando PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 9c56f09ac186b0c3a64cce6700740ca1ba6abd06
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="ef6f1-103">Guida della riga di comando PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="ef6f1-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="ef6f1-104">Avvia una sessione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-104">Starts a Windows PowerShell session.</span></span> <span data-ttu-id="ef6f1-105">È possibile usare PowerShell.exe per avviare una sessione di Windows PowerShell dalla riga di comando di un altro strumento, come Cmd.exe, o usarlo nella riga di comando di Windows PowerShell per avviare una nuova sessione.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-105">You can use PowerShell.exe to start a Windows PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the Windows PowerShell command line to start a new session.</span></span> <span data-ttu-id="ef6f1-106">Usare i parametri per personalizzare la sessione.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef6f1-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ef6f1-107">Syntax</span></span>

```
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

## <a name="parameters"></a><span data-ttu-id="ef6f1-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="ef6f1-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="ef6f1-109">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="ef6f1-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="ef6f1-110">Accetta una versione di un comando di tipo stringa codificata in base 64.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="ef6f1-111">Usare questo parametro per inviare a Windows PowerShell comandi che richiedono virgolette complesse o parentesi graffe.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-111">Use this parameter to submit commands to Windows PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="ef6f1-112">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="ef6f1-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="ef6f1-113">Imposta i criteri di esecuzione predefiniti per la sessione corrente e li salva nella variabile di ambiente $env:PSExecutionPolicyPreference.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="ef6f1-114">Questo parametro non modifica i criteri di esecuzione di Windows PowerShell impostati nel Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-114">This parameter does not change the Windows PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="ef6f1-115">Per informazioni sui criteri di esecuzione di Windows PowerShell, incluso un elenco di valori validi, vedere about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span><span class="sxs-lookup"><span data-stu-id="ef6f1-115">For information about Windows PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="ef6f1-116">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="ef6f1-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="ef6f1-117">Esegue lo script specificato nell'ambito locale ("dot sourcing" ), in modo che le funzioni e le variabili create dallo script siano disponibili nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="ef6f1-118">Immettere il percorso del file di script ed eventuali parametri.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="ef6f1-119">**File** deve essere l'ultimo parametro del comando, perché tutti i caratteri digitati dopo il nome del parametro **File** vengono interpretati come il percorso del file di script seguito dai parametri di script e dai relativi valori.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="ef6f1-120">È possibile includere i parametri di uno script e i relativi valori nel valore del parametro **File**.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="ef6f1-121">Ad esempio: `-File .\Get-Script.ps1 -Domain Central`</span><span class="sxs-lookup"><span data-stu-id="ef6f1-121">For example: `-File .\Get-Script.ps1 -Domain Central`</span></span>

<span data-ttu-id="ef6f1-122">In genere, i parametri opzionali di uno script sono inclusi o omessi.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="ef6f1-123">Il comando seguente usa ad esempio il parametro **All** del file di script Get-Script.ps1: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="ef6f1-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="ef6f1-124">In rari casi potrebbe essere necessario fornire un valore booleano per un parametro opzionale.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-124">In rare cases, you might need to provide a Boolean value for a switch parameter.</span></span> <span data-ttu-id="ef6f1-125">Per fornire un valore booleano per un parametro opzionale nel valore del parametro **File**, racchiudere il nome e il valore del parametro tra parentesi graffe, come nell'esempio seguente: `-File .\Get-Script.ps1 {-All:$False}`</span><span class="sxs-lookup"><span data-stu-id="ef6f1-125">To provide a Boolean value for a switch parameter in the value of the **File** parameter, enclose the parameter name and value in curly braces, such as the following: `-File .\Get-Script.ps1 {-All:$False}`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="ef6f1-126">-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="ef6f1-126">-InputFormat {Text | XML}</span></span>
<span data-ttu-id="ef6f1-127">Descrive il formato dei dati inviati a Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-127">Describes the format of data sent to Windows PowerShell.</span></span> <span data-ttu-id="ef6f1-128">I valori validi sono "Text" (stringhe di testo) o "XML" (formato CLIXML serializzato).</span><span class="sxs-lookup"><span data-stu-id="ef6f1-128">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="ef6f1-129">-Mta</span><span class="sxs-lookup"><span data-stu-id="ef6f1-129">-Mta</span></span>
<span data-ttu-id="ef6f1-130">Avvia Windows PowerShell usando un apartment a thread multipli.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-130">Starts Windows PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="ef6f1-131">Questo parametro è stato introdotto in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-131">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="ef6f1-132">In Windows PowerShell 3.0 l'impostazione predefinita è apartment a thread singolo (STA).</span><span class="sxs-lookup"><span data-stu-id="ef6f1-132">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="ef6f1-133">In Windows PowerShell 2.0 l'impostazione predefinita è apartment a thread multipli (MTA).</span><span class="sxs-lookup"><span data-stu-id="ef6f1-133">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="ef6f1-134">-NoExit</span><span class="sxs-lookup"><span data-stu-id="ef6f1-134">-NoExit</span></span>
<span data-ttu-id="ef6f1-135">Non viene chiuso dopo l'esecuzione dei comandi di avvio.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-135">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="ef6f1-136">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="ef6f1-136">-NoLogo</span></span>
<span data-ttu-id="ef6f1-137">Nasconde le informazioni sul copyright all'avvio.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-137">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="ef6f1-138">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="ef6f1-138">-NonInteractive</span></span>
<span data-ttu-id="ef6f1-139">Non presenta un prompt interattivo all'utente.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-139">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="ef6f1-140">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="ef6f1-140">-NoProfile</span></span>
<span data-ttu-id="ef6f1-141">Non carica il profilo di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-141">Does not load the Windows PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="ef6f1-142">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="ef6f1-142">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="ef6f1-143">Determina la formattazione dell'output di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-143">Determines how output from Windows PowerShell is formatted.</span></span> <span data-ttu-id="ef6f1-144">I valori validi sono "Text" (stringhe di testo) o "XML" (formato CLIXML serializzato).</span><span class="sxs-lookup"><span data-stu-id="ef6f1-144">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="ef6f1-145">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="ef6f1-145">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="ef6f1-146">Carica il file della console di Windows PowerShell specificato.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-146">Loads the specified Windows PowerShell console file.</span></span> <span data-ttu-id="ef6f1-147">Immettere il percorso e il nome del file della console.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-147">Enter the path and name of the console file.</span></span> <span data-ttu-id="ef6f1-148">Per creare un file di console, usare il cmdlet [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-148">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in Windows PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="ef6f1-149">-Sta</span><span class="sxs-lookup"><span data-stu-id="ef6f1-149">-Sta</span></span>
<span data-ttu-id="ef6f1-150">Avvia Windows PowerShell usando un apartment a thread singolo.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-150">Starts Windows PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="ef6f1-151">In Windows PowerShell 3.0 l'impostazione predefinita è apartment a thread singolo (STA).</span><span class="sxs-lookup"><span data-stu-id="ef6f1-151">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="ef6f1-152">In Windows PowerShell 2.0 l'impostazione predefinita è apartment a thread multipli (MTA).</span><span class="sxs-lookup"><span data-stu-id="ef6f1-152">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-windows-powershell-version"></a><span data-ttu-id="ef6f1-153">-Version <Windows PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="ef6f1-153">-Version <Windows PowerShell Version></span></span>
<span data-ttu-id="ef6f1-154">Avvia la versione specificata di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-154">Starts the specified version of Windows PowerShell.</span></span> <span data-ttu-id="ef6f1-155">La versione specificata deve essere installata nel sistema.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-155">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="ef6f1-156">Se Windows PowerShell 3.0 è installato nel computer, i valori validi sono "2.0" e "3.0".</span><span class="sxs-lookup"><span data-stu-id="ef6f1-156">If Windows PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="ef6f1-157">Il valore predefinito è "3.0".</span><span class="sxs-lookup"><span data-stu-id="ef6f1-157">The default value is "3.0".</span></span>

<span data-ttu-id="ef6f1-158">Se Windows PowerShell 3.0 non è installato, l'unico valore valido è "2.0".</span><span class="sxs-lookup"><span data-stu-id="ef6f1-158">If Windows PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="ef6f1-159">Gli altri valori sono ignorati.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-159">Other values are ignored.</span></span>

<span data-ttu-id="ef6f1-160">Per altre informazioni, vedere "Installazione di Windows PowerShell" nella [Guida introduttiva a Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span><span class="sxs-lookup"><span data-stu-id="ef6f1-160">For more information, see "Installing Windows PowerShell" in the [Getting Started with Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="ef6f1-161">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="ef6f1-161">-WindowStyle <Window style></span></span>
<span data-ttu-id="ef6f1-162">Imposta lo stile della finestra per la sessione.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-162">Sets the window style for the session.</span></span> <span data-ttu-id="ef6f1-163">I valori validi sono Normal, Minimized, Maximized e Hidden.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-163">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="ef6f1-164">-Command</span><span class="sxs-lookup"><span data-stu-id="ef6f1-164">-Command</span></span>
<span data-ttu-id="ef6f1-165">Esegue i comandi specificati (e gli eventuali parametri) come se fossero stati digitati al prompt dei comandi di Windows PowerShell, quindi viene chiuso, a meno che non sia stato specificato il parametro NoExit.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-165">Executes the specified commands (and any parameters) as though they were typed at the Windows PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>

<span data-ttu-id="ef6f1-166">Il valore di Command può essere "-", una stringa</span><span class="sxs-lookup"><span data-stu-id="ef6f1-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="ef6f1-167">o un blocco di script.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-167">or a script block.</span></span> <span data-ttu-id="ef6f1-168">Se il valore di Command è "-", il testo del comando viene letto dall'input standard.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="ef6f1-169">I blocchi di script devono essere racchiusi tra parentesi graffe ({}).</span><span class="sxs-lookup"><span data-stu-id="ef6f1-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="ef6f1-170">È possibile specificare un blocco di script solo se si esegue PowerShell.exe in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-170">You can specify a script block only when running PowerShell.exe in Windows PowerShell.</span></span> <span data-ttu-id="ef6f1-171">I risultati dello script vengono restituiti alla shell padre come oggetti XML deserializzati, non come oggetti attivi.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="ef6f1-172">Se il valore di Command è una stringa, **Command** deve essere l'ultimo parametro del comando, perché i caratteri digitati dopo il comando vengono interpretati come argomenti del comando.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-172">If the value of Command is a string, **Command** must be the last parameter in the command , because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="ef6f1-173">Per scrivere una stringa che esegua un comando di Windows PowerShell, usare il formato:</span><span class="sxs-lookup"><span data-stu-id="ef6f1-173">To write a string that runs a Windows PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="ef6f1-174">in cui le virgolette indicano una stringa e l'operatore invoke (&) causa l'esecuzione del comando.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="ef6f1-175">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="ef6f1-175">-Help, -?, /?</span></span>
<span data-ttu-id="ef6f1-176">Mostra questo messaggio.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-176">Shows this message.</span></span> <span data-ttu-id="ef6f1-177">Se si digita un comando PowerShell.exe in Windows PowerShell, anteporre ai parametri del comando un trattino (-) e non una barra (/).</span><span class="sxs-lookup"><span data-stu-id="ef6f1-177">If you are typing a PowerShell.exe command in Windows PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="ef6f1-178">In Cmd.exe è possibile usare sia il trattino che la barra.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="ef6f1-179">Nota relativa alla risoluzione dei problemi: in Windows PowerShell 2.0 l'avvio di alcuni programmi nella console di Windows PowerShell genera un errore con LastExitCode uguale a 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="ef6f1-179">Troubleshooting Note: In Windows PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="ef6f1-180">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="ef6f1-180">EXAMPLES</span></span>

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

