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

Esegue lo script specificato nell'ambito locale ("dot sourcing" ), in modo che le funzioni e le variabili create dallo script siano disponibili nella sessione corrente. Immettere il percorso del file di script ed eventuali parametri. **File** deve essere l'ultimo parametro nel comando. Tutti i valori digitati dopo il parametro **-File** vengono interpretati come percorso del file script e i parametri passati a tale script.

I parametri passati allo script vengono passati come stringhe letterali, dopo l'interpretazione da parte della shell corrente. Ad esempio, se si trovano in cmd.exe e si desidera passare un valore di variabile di ambiente, utilizzare la sintassi cmd.exe: `powershell.exe -File .\test.ps1 -TestParam %windir%`

Al contrario, in esecuzione `powershell.exe -File .\test.ps1 -TestParam $env:windir` nei risultati cmd.exe nello script di ricevere la stringa letterale `$env:windir` perché non ha significato speciale shell cmd.exe corrente.
Il `$env:windir` stile del riferimento alla variabile di ambiente _possibile_ utilizzabile all'interno di un `-Command` parametro, poiché non esiste verrà interpretato come codice di PowerShell.

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

Esegue i comandi specificati (e gli eventuali parametri) come se fossero stati digitati al prompt dei comandi di PowerShell.
Dopo l'esecuzione, PowerShell viene chiuso, a meno che il **NoExit** parametro è specificato.
Qualsiasi testo dopo `-Command` viene inviato come singola riga di comando a PowerShell.
Questo approccio è diverso dal modo in cui `-File` gestisce i parametri inviati a uno script.

Il valore di `-Command` può essere "-", una stringa o un blocco di script.
I risultati del comando vengono restituiti alla shell padre come oggetti XML deserializzati, gli oggetti non attivi.

Se il valore di `-Command` è "-", il testo del comando viene letto dall'input standard.

Quando il valore di `-Command` è una stringa **comandi** _necessario_ essere l'ultimo parametro specificato perché i caratteri digitati dopo il comando vengono interpretati come argomenti del comando.

Il **comandi** parametro accetta solo un blocco di script per l'esecuzione quando in grado di riconoscere il valore passato a `-Command` come tipo di blocco di script.
Si tratta _solo_ possibili durante l'esecuzione PowerShell.exe da un altro host di PowerShell.
Il parametro ScriptBlock tipo può essere contenuto nella variabile, restituito da un'espressione o analizzati da PowerShell esistente ospitare come un blocco di script letterale racchiuso tra parentesi graffe `{}`prima che venga passato a PowerShell.exe.

Cmd.exe, non include alcun equivalente di un blocco di script (o tipo di blocco di script), pertanto il valore passato a **comandi** verranno _sempre_ sia una stringa.
È possibile scrivere un blocco di script all'interno della stringa, ma anziché in esecuzione questo si comporta esattamente come se venisse digitato, al prompt di PowerShell tipico, stampa il contenuto dello script Prenditi nuovamente all'utente.

Una stringa passata a `-Command` verrà comunque eseguito come PowerShell, in modo che le parentesi graffe blocco di script spesso non sono necessarie in primo luogo durante l'esecuzione da cmd.exe.
Per eseguire un blocco di script inline definito all'interno di una stringa, il [operatore di chiamata](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` consente di:

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help, -?, /?

Mostra la sintassi di powershell.exe. Se si digita un comando PowerShell.exe in PowerShell, anteporre ai parametri del comando un trattino (-) e non una barra (/). In Cmd.exe è possibile usare sia il trattino che la barra.

> [!NOTE]
> Nota sulla risoluzione dei problemi: In PowerShell 2.0 l'avvio di alcuni programmi nella console di Windows PowerShell un errore con LastExitCode uguale a 0xc0000142.

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
