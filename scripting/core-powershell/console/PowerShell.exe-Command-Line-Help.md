---
title: Guida alla riga di comando PowerShell.exe
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
translationtype: Human Translation
ms.sourcegitcommit: 763dc6bb0410ec09fc237d41b96842895b15d142
ms.openlocfilehash: c3b263110a908c28569cf3048a94d48da8316684

---

# Guida della riga di comando PowerShell.exe
Avvia una sessione di Windows PowerShell. È possibile usare PowerShell.exe per avviare una sessione di Windows PowerShell dalla riga di comando di un altro strumento, come Cmd.exe, o usarlo nella riga di comando di Windows PowerShell per avviare una nuova sessione. Usare i parametri per personalizzare la sessione.

## Sintassi

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

## Parametri

### -EncodedCommand <Base64EncodedCommand>
Accetta una versione di un comando di tipo stringa codificata in base 64. Usare questo parametro per inviare a Windows PowerShell comandi che richiedono virgolette complesse o parentesi graffe.

### -ExecutionPolicy <ExecutionPolicy>
Imposta i criteri di esecuzione predefiniti per la sessione corrente e li salva nella variabile di ambiente $env:PSExecutionPolicyPreference. Questo parametro non modifica i criteri di esecuzione di Windows PowerShell impostati nel Registro di sistema. Per informazioni sui criteri di esecuzione di Windows PowerShell, incluso un elenco di valori validi, vedere about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).

### -File <FilePath> \[<Parameters>]
Esegue lo script specificato nell'ambito locale ("dot sourcing" ), in modo che le funzioni e le variabili create dallo script siano disponibili nella sessione corrente. Immettere il percorso del file di script ed eventuali parametri. **File** deve essere l'ultimo parametro del comando, perché tutti i caratteri digitati dopo il nome del parametro **File** vengono interpretati come il percorso del file di script seguito dai parametri di script e dai relativi valori.

È possibile includere i parametri di uno script e i relativi valori nel valore del parametro **File**. Ad esempio: `-File .\Get-Script.ps1 -Domain Central`

In genere, i parametri opzionali di uno script sono inclusi o omessi. Il comando seguente usa ad esempio il parametro **All** del file di script Get-Script.ps1: `-File .\Get-Script.ps1 -All`

In rari casi potrebbe essere necessario fornire un valore booleano per un parametro opzionale. Per fornire un valore booleano per un parametro opzionale nel valore del parametro **File**, racchiudere il nome e il valore del parametro tra parentesi graffe, come nell'esempio seguente: `-File .\Get-Script.ps1 {-All:$False}`

### -InputFormat {Text | XML}
Descrive il formato dei dati inviati a Windows PowerShell. I valori validi sono "Text" (stringhe di testo) o "XML" (formato CLIXML serializzato).

### -Mta
Avvia Windows PowerShell usando un apartment a thread multipli. Questo parametro è stato introdotto in Windows PowerShell 3.0. In Windows PowerShell 3.0 l'impostazione predefinita è apartment a thread singolo (STA). In Windows PowerShell 2.0 l'impostazione predefinita è apartment a thread multipli (MTA).

### -NoExit
Non viene chiuso dopo l'esecuzione dei comandi di avvio.

### -NoLogo
Nasconde le informazioni sul copyright all'avvio.

### -NonInteractive
Non presenta un prompt interattivo all'utente.

### -NoProfile
Non carica il profilo di Windows PowerShell.

### -OutputFormat {Text | XML}
Determina la formattazione dell'output di Windows PowerShell. I valori validi sono "Text" (stringhe di testo) o "XML" (formato CLIXML serializzato).

### -PSConsoleFile <FilePath>
Carica il file della console di Windows PowerShell specificato. Immettere il percorso e il nome del file della console. Per creare un file di console, usare il cmdlet [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) in Windows PowerShell.

### -Sta
Avvia Windows PowerShell usando un apartment a thread singolo. In Windows PowerShell 3.0 l'impostazione predefinita è apartment a thread singolo (STA). In Windows PowerShell 2.0 l'impostazione predefinita è apartment a thread multipli (MTA).

### -Version <Windows PowerShell Version>
Avvia la versione specificata di Windows PowerShell. La versione specificata deve essere installata nel sistema. Se Windows PowerShell 3.0 è installato nel computer, i valori validi sono "2.0" e "3.0". Il valore predefinito è "3.0".

Se Windows PowerShell 3.0 non è installato, l'unico valore valido è "2.0". Gli altri valori sono ignorati.

Per altre informazioni, vedere "Installazione di Windows PowerShell" nella [Guida introduttiva a Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).

### -WindowStyle <Window style>
Imposta lo stile della finestra per la sessione. I valori validi sono Normal, Minimized, Maximized e Hidden.

### -Command
Esegue i comandi specificati (e gli eventuali parametri) come se fossero stati digitati al prompt dei comandi di Windows PowerShell, quindi viene chiuso, a meno che non sia stato specificato il parametro NoExit.

Il valore di Command può essere "-", una stringa o un blocco di script. Se il valore di Command è "-", il testo del comando viene letto dall'input standard.

I blocchi di script devono essere racchiusi tra parentesi graffe ({}). È possibile specificare un blocco di script solo se si esegue PowerShell.exe in Windows PowerShell. I risultati dello script vengono restituiti alla shell padre come oggetti XML deserializzati, non come oggetti attivi.

Se il valore di Command è una stringa, **Command** deve essere l'ultimo parametro del comando, perché i caratteri digitati dopo il comando vengono interpretati come argomenti del comando.

Per scrivere una stringa che esegua un comando di Windows PowerShell, usare il formato:

```
"& {<command>}"
```

in cui le virgolette indicano una stringa e l'operatore invoke (&) causa l'esecuzione del comando.

### -Help, -?, /?
Mostra questo messaggio. Se si digita un comando PowerShell.exe in Windows PowerShell, anteporre ai parametri del comando un trattino (-) e non una barra (/). In Cmd.exe è possibile usare sia il trattino che la barra.

> [!NOTE]
> Nota relativa alla risoluzione dei problemi: in Windows PowerShell 2.0 l'avvio di alcuni programmi nella console di Windows PowerShell genera un errore con LastExitCode uguale a 0xc0000142.

## ESEMPI

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




<!--HONumber=Sep16_HO4-->


