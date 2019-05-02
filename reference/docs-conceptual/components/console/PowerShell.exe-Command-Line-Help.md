---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Guida alla riga di comando PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058514"
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

I parametri passati allo script vengono passati come stringhe letterali, dopo l'interpretazione da parte della shell corrente. Ad esempio, all'interno di cmd.exe se si vuole passare un valore di variabile di ambiente, si usa la sintassi di cmd.exe: `powershell.exe -File .\test.ps1 -TestParam %windir%`

Al contrario, se si esegue `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe, lo script riceve la stringa letterale `$env:windir` perché non ha un significato speciale per la shell cmd.exe corrente.
Lo stile `$env:windir` per i riferimenti alla variabile di ambiente _può_ essere usato all'interno di un parametro `-Command`, perché in tale posizione verrebbe interpretato come codice di PowerShell.

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
Dopo l'esecuzione, PowerShell viene chiuso a meno che non venga specificato il parametro **NoExit**.
Qualsiasi testo dopo `-Command` viene inviato come singola riga di comando a PowerShell.
Questo approccio è diverso dal modo in cui `-File` gestisce i parametri inviati a uno script.

Il valore di `-Command` può essere "-", una stringa o un blocco di script.
I risultati del comando vengono restituiti alla shell padre come oggetti XML deserializzati e non come oggetti attivi.

Se il valore di `-Command` è "-", il testo del comando viene letto dall'input standard.

Se il valore di `-Command` è una stringa, **Command** _deve_ essere l'ultimo parametro specificato, perché i caratteri digitati dopo il comando vengono interpretati come argomenti del comando.

Il parametro **Command** accetta solo un blocco di script per l'esecuzione quando è in grado di riconoscere il valore passato a `-Command` come tipo ScriptBlock.
Ciò è possibile _solo_ durante l'esecuzione PowerShell.exe da un altro host di PowerShell.
Il tipo ScriptBlock può essere contenuto in una variabile esistente, restituito da un'espressione o analizzato dall'host di PowerShell come un blocco di script letterale racchiuso tra parentesi graffe `{}`, prima che venga passato a PowerShell.exe.

In cmd.exe non è disponibile un elemento simile a un blocco di script (o il tipo ScriptBlock), quindi il valore passato a **Command** sarà _sempre_ una stringa.
È possibile scrivere un blocco di script all'interno della stringa, ma anziché essere eseguito, si comporterà esattamente come se fosse stato digitato a un prompt tipico di PowerShell, ovvero verrà stampato il contenuto del blocco di script.

Anche una stringa passata a `-Command` verrà comunque eseguita come PowerShell, quindi le parentesi graffe per il blocco di script spesso non sono necessarie per l'esecuzione da cmd.exe.
Per eseguire un blocco di script inline definito all'interno di una stringa, è possibile usare l'[operatore di chiamata](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&`:

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help, -?, /?

Mostra la sintassi di powershell.exe. Se si digita un comando PowerShell.exe in PowerShell, anteporre ai parametri del comando un trattino (-) e non una barra (/). In Cmd.exe è possibile usare sia il trattino che la barra.

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
