---
title: Aggiunta di messaggi utente al cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 9079f40e75dae86c22fd8b4f8a45d501c6125498
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416034"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Aggiunta di messaggi utente al cmdlet

I cmdlet possono scrivere diversi tipi di messaggi che possono essere visualizzati dall'utente dal runtime di Windows PowerShell. Questi messaggi includono i tipi seguenti:

- Messaggi dettagliati contenenti informazioni generali sugli utenti.

- Messaggi di debug che contengono informazioni sulla risoluzione dei problemi.

- Messaggi di avviso che contengono una notifica che il cmdlet sta per eseguire un'operazione che può avere risultati imprevisti.

- Messaggi di report di stato che contengono informazioni sulla quantità di lavoro completata dal cmdlet durante l'esecuzione di un'operazione che richiede molto tempo.

Non sono previsti limiti per il numero di messaggi che possono essere scritti dal cmdlet o il tipo di messaggi scritti dal cmdlet. Ogni messaggio viene scritto effettuando una chiamata specifica dall'interno del metodo di elaborazione dell'input del cmdlet.

## <a name="defining-the-cmdlet"></a>Definizione del cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il nome del cmdlet e la dichiarazione della classe .NET che implementa il cmdlet. Qualsiasi tipo di cmdlet può scrivere notifiche utente dai metodi di elaborazione dell'input; Pertanto, in generale, è possibile assegnare un nome a questo cmdlet utilizzando un verbo che indica le modifiche del sistema eseguite dal cmdlet. Per altre informazioni sui verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Il cmdlet Stop-proc è stato progettato per modificare il sistema; la Dichiarazione [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) per la classe .NET deve pertanto includere la parola chiave `SupportsShouldProcess` Attribute e essere impostata su `true`.

Il codice seguente è la definizione per questa classe di cmdlet Stop-proc. Per ulteriori informazioni su questa definizione, vedere [creazione di un cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definizione dei parametri per la modifica del sistema

Il cmdlet Stop-proc definisce tre parametri: `Name`, `Force`e `PassThru`. Per ulteriori informazioni sulla definizione di questi parametri, vedere [creazione di un cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).

Di seguito è illustrata la dichiarazione di parametro per il cmdlet Stop-proc.

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a>Override di un metodo di elaborazione dell'input

Il cmdlet deve eseguire l'override di un metodo di elaborazione dell'input, più spesso sarà [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Questo cmdlet Stop-proc esegue l'override del metodo di elaborazione dell'input [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . In questa implementazione del cmdlet Stop-proc vengono effettuate chiamate per scrivere messaggi dettagliati, messaggi di debug e messaggi di avviso.

> [!NOTE]
> Per ulteriori informazioni sul modo in cui questo metodo chiama i metodi [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , vedere [creazione di un cmdlet che modifica il sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Scrittura di un messaggio dettagliato

Il metodo [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) viene usato per scrivere informazioni generali a livello di utente che non sono correlate a condizioni di errore specifiche. L'amministratore di sistema può quindi utilizzare tali informazioni per continuare l'elaborazione di altri comandi. Inoltre, tutte le informazioni scritte utilizzando questo metodo devono essere localizzate in base alle esigenze.

Il codice seguente di questo cmdlet Stop-proc Mostra due chiamate al metodo [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) dall'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Scrittura di un messaggio di debug

Il metodo [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) viene usato per scrivere messaggi di debug che possono essere usati per risolvere i problemi relativi all'operazione del cmdlet. La chiamata viene eseguita da un metodo di elaborazione dell'input.

> [!NOTE]
> Windows PowerShell definisce anche un parametro di `Debug` che presenta informazioni dettagliate e di debug. Se il cmdlet supporta questo parametro, non è necessario chiamare [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) nello stesso codice che chiama [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).

Nelle due sezioni seguenti del codice del cmdlet di esempio Stop-proc vengono visualizzate le chiamate al metodo [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) dall'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

Questo messaggio di debug viene scritto immediatamente prima della chiamata a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Questo messaggio di debug viene scritto immediatamente prima della chiamata a [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell instrada automaticamente le chiamate [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) all'infrastruttura di traccia e ai cmdlet. In questo modo è possibile tracciare le chiamate al metodo nell'applicazione host, in un file o in un debugger senza dover eseguire ulteriori operazioni di sviluppo all'interno del cmdlet. La seguente voce della riga di comando implementa un'operazione di traccia.

**PS > Trace-Expression stop-proc-file proc. log-command stop-proc blocco note**

## <a name="writing-a-warning-message"></a>Scrittura di un messaggio di avviso

Il metodo [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) viene usato per scrivere un avviso quando il cmdlet sta per eseguire un'operazione che potrebbe avere un risultato imprevisto, ad esempio, sovrascrivendo un file di sola lettura.

Il codice seguente dal cmdlet Stop-proc di esempio mostra la chiamata al metodo [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) dall'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Scrittura di un messaggio di stato

[System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) viene utilizzato per scrivere i messaggi di stato quando le operazioni del cmdlet impiegano un periodo di tempo prolungato per il completamento. Una chiamata a [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passa un oggetto [System. Management. Automation. ProgressRecord](/dotnet/api/System.Management.Automation.ProgressRecord) che viene inviato all'applicazione host per il rendering all'utente.

> [!NOTE]
> Questo cmdlet Stop-proc non include una chiamata al metodo [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .

Il codice seguente è un esempio di messaggio di stato scritto da un cmdlet che tenta di copiare un elemento.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Codice di esempio

Per il codice C# di esempio completo, vedere l' [esempio StopProcessSample02](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Definire i tipi di oggetto e la formattazione

Windows PowerShell passa le informazioni tra i cmdlet usando gli oggetti .NET. Di conseguenza, un cmdlet potrebbe dover definire il proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet. Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilazione del cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell. Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test del cmdlet

Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo nella riga di comando. Testare il cmdlet di esempio Stop-proc. Per ulteriori informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- La voce della riga di comando seguente USA stop-proc per arrestare il processo denominato "blocco note", fornire notifiche dettagliate e stampare le informazioni di debug.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

Viene visualizzato l'output seguente:

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a>Vedere anche

[Creare un cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Come creare un cmdlet di Windows PowerShell](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85))

[Come registrare cmdlet, provider e applicazioni host](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
