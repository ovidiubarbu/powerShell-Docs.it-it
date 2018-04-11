---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Guida alla riga di comando PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 60b6a7e310821a4092b0972b7abbdae0e2d5f738
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="powershellexe-command-line-help"></a>Guida della riga di comando PowerShell.exe

È possibile usare PowerShell.exe per avviare una sessione PowerShell dalla riga di comando di un altro strumento, come Cmd.exe, o usarlo nella riga di comando PowerShell per avviare una nuova sessione. Usare i parametri per personalizzare la sessione.

## <a name="syntax"></a>Sintassi

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

## <a name="parameters"></a>Parametri

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

Accetta una versione di un comando di tipo stringa codificata in base 64. Usare questo parametro per inviare a PowerShell comandi che richiedono virgolette complesse o parentesi graffe.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Imposta i criteri di esecuzione predefiniti per la sessione corrente e li salva nella variabile di ambiente $env:PSExecutionPolicyPreference. Questo parametro non modifica i criteri di esecuzione di PowerShell impostati nel Registro di sistema. Per informazioni sui criteri di esecuzione di PowerShell, incluso un elenco di valori validi, vedere [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]

Esegue lo script specificato nell'ambito locale ("dot sourcing" ), in modo che le funzioni e le variabili create dallo script siano disponibili nella sessione corrente. Immettere il percorso del file di script ed eventuali parametri. **File** deve essere l'ultimo parametro del comando, perché tutti i caratteri digitati dopo il nome del parametro **File** vengono interpretati come il percorso del file di script seguito dai parametri di script e dai relativi valori.

È possibile includere i parametri di uno script e i relativi valori nel valore del parametro **File**. Ad esempio: `-File .\Get-Script.ps1 -Domain Central` Si noti che i parametri passati allo script vengono passati come stringhe letterali (dopo l'interpretazione dalla shell corrente).
Ad esempio, se si usa cmd.exe e si vuole passare un valore di variabile di ambiente, è necessario usare la sintassi di cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` Se si usasse la sintassi di PowerShell, in questo esempio lo script riceverebbe il valore letterale "$env: windir" e non il valore della variabile di ambiente: `powershell -File .\test.ps1 -Sample $env:windir`

In genere, i parametri opzionali di uno script sono inclusi o omessi. Il comando seguente usa ad esempio il parametro **All** del file di script Get-Script.ps1: `-File .\Get-Script.ps1 -All`

### <a name="-inputformat-text--xml"></a>\-InputFormat {Text | XML}

Descrive il formato dei dati inviati a PowerShell. I valori validi sono "Text" (stringhe di testo) o "XML" (formato CLIXML serializzato).

### <a name="-mta"></a>-Mta

Avvia PowerShell usando un apartment a thread multipli. Questo parametro è stato introdotto in PowerShell 3.0. In PowerShell 3.0 l'impostazione predefinita è apartment a thread singolo (STA). In PowerShell 2.0 l'impostazione predefinita è apartment a thread multipli (MTA).

### <a name="-noexit"></a>-NoExit

Non viene chiuso dopo l'esecuzione dei comandi di avvio.

### <a name="-nologo"></a>-NoLogo

Nasconde le informazioni sul copyright all'avvio.

### <a name="-noninteractive"></a>-NonInteractive

Non presenta un prompt interattivo all'utente.

### <a name="-noprofile"></a>-NoProfile

Non carica il profilo di PowerShell.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

Determina la formattazione dell'output di PowerShell. I valori validi sono "Text" (stringhe di testo) o "XML" (formato CLIXML serializzato).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Carica il file della console di PowerShell specificato. Immettere il percorso e il nome del file della console. Per creare un file di console, usare il cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) in PowerShell.

### <a name="-sta"></a>-Sta

Avvia PowerShell usando un apartment a thread singolo. In PowerShell 3.0 l'impostazione predefinita è apartment a thread singolo (STA). In PowerShell 2.0 l'impostazione predefinita è apartment a thread multipli (MTA).

### <a name="-version-powershell-version"></a>-Version <PowerShell Version>

Avvia la versione specificata di PowerShell. La versione specificata deve essere installata nel sistema. Se PowerShell 3.0 è installato nel computer, i valori validi sono "2.0" e "3.0". Il valore predefinito è "3.0".

Se PowerShell 3.0 non è installato, l'unico valore valido è "2.0". Gli altri valori sono ignorati.

Per altre informazioni, vedere [Installazione di Windows PowerShell](../../setup/installing-windows-powershell.md).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Imposta lo stile della finestra per la sessione. I valori validi sono Normal, Minimized, Maximized e Hidden.

### <a name="-command"></a>-Command

Esegue i comandi specificati (e gli eventuali parametri) come se fossero stati digitati al prompt dei comandi di PowerShell, quindi viene chiuso, a meno che non sia stato specificato il parametro NoExit.
In pratica, qualsiasi testo che segue `-Command` viene inviato come una singola riga di comando di PowerShell (diverso da come `-File` gestisce i parametri inviati a uno script).

Il valore di Command può essere "-", una stringa o un blocco di script. Se il valore di Command è "-", il testo del comando viene letto dall'input standard.

I blocchi di script devono essere racchiusi tra parentesi graffe ({}). È possibile specificare un blocco di script solo se si esegue PowerShell.exe in PowerShell. I risultati dello script vengono restituiti alla shell padre come oggetti XML deserializzati, non come oggetti attivi.

Se il valore di Command è una stringa, **Command** deve essere l'ultimo parametro del comando, perché i caratteri digitati dopo il comando vengono interpretati come argomenti del comando.

Per scrivere una stringa che esegua un comando di PowerShell, usare il formato:

```powershell
"& {<command>}"
```

in cui le virgolette indicano una stringa e l'operatore invoke (&) causa l'esecuzione del comando.

### <a name="-help---"></a>-Help, -?, /?

Mostra questo messaggio. Se si digita un comando PowerShell.exe in PowerShell, anteporre ai parametri del comando un trattino (-) e non una barra (/). In Cmd.exe è possibile usare sia il trattino che la barra.

> [!NOTE]
> Nota relativa alla risoluzione dei problemi: in PowerShell 2.0 l'avvio di alcuni programmi nella console di Windows PowerShell genera un errore con LastExitCode di 0xc0000142.

## <a name="examples"></a>ESEMPI

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