---
title: Aggiunta di messaggi dell'utente al Cmdlet | Microsoft Docs
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
ms.openlocfilehash: 1e048f6ae94ac226218c18c8f8f7590a4db26226
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733765"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Aggiunta di messaggi utente al cmdlet

I cmdlet possono scrivere diversi tipi di messaggi che possono essere visualizzati all'utente dal runtime di Windows PowerShell. Questi messaggi includono i tipi seguenti:

- Messaggi dettagliati contenenti informazioni utente generali.

- I messaggi che contengono informazioni sulla risoluzione dei problemi di debug.

- I messaggi di avviso che contengono una notifica che il cmdlet deve eseguire un'operazione che può avere risultati imprevisti.

- Report stato di avanzamento dei messaggi che contengono informazioni sulla quantità di lavoro il cmdlet è stata completata durante l'esecuzione di un'operazione che richiede molto tempo.

Non sono previsti limiti al numero di messaggi che può scrivere cmdlet o il tipo di messaggi che il cmdlet scrive. Ogni messaggio viene scritto eseguendo una chiamata specifica da entro il metodo del cmdlet di elaborazione dell'input.

## <a name="defining-the-cmdlet"></a>Che definisce il Cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet. Una sorta di cmdlet è possibile scrivere le notifiche utente dal proprio input; i metodi di elaborazione Pertanto, in generale, è possibile denominare questo cmdlet tramite qualsiasi verbo che indica quali modifiche di sistema esegue il cmdlet. Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Il cmdlet Stop-Process è progettato per modificare il sistema. Pertanto, il [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) dichiarazione della classe .NET deve includere il `SupportsShouldProcess` parola chiave dell'attributo e impostato su `true`.

Il codice seguente è la definizione per questa classe cmdlet Stop-Process. Per altre informazioni su questa definizione, vedere [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definizione dei parametri per la modifica di sistema

Il cmdlet Stop-Process definisce tre parametri: `Name`, `Force`, e `PassThru`. Per altre informazioni sulla definizione di questi parametri, vedere [creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).

Ecco la dichiarazione di parametro per il cmdlet Stop-Process.

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

## <a name="overriding-an-input-processing-method"></a>Si esegue l'override di un metodo di elaborazione dell'Input

Il cmdlet deve eseguire l'override di un metodo di elaborazione dell'input, in genere si tratterà [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Esegue l'override di questo cmdlet Stop-Process il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo di elaborazione di input. In questa implementazione del cmdlet Stop-Process, eseguono chiamate a scrivere i messaggi dettagliati, messaggi di debug e i messaggi di avviso.

> [!NOTE]
> Per altre informazioni sul modo in cui questo metodo chiama il [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodi, vedere [Creazione di un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>La scrittura di un messaggio dettagliato

Il [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metodo viene utilizzato per scrivere le informazioni utente a livello generale non sono correlate alle condizioni di errore specifico. L'amministratore di sistema può quindi usare tali informazioni per continuare a elaborare altri comandi. Inoltre, eventuali informazioni scritte utilizzando questo metodo devono essere localizzate in base alle esigenze.

Il codice seguente da questo cmdlet Stop-Process Mostra due chiamate al [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) l'override del metodo di [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo).

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>La scrittura di un messaggio di Debug

Il [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metodo viene utilizzato per scrivere i messaggi di debug che possono essere utilizzati per risolvere i problemi di funzionamento del cmdlet. La chiamata viene effettuata da un metodo di elaborazione dell'input.

> [!NOTE]
> Windows PowerShell definisce anche un `Debug` parametro presenta sia dettagliato e informazioni di debug. Se il cmdlet supporta questo parametro, non dovrà chiamare [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) nello stesso codice che chiama [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

Le due sezioni di codice tramite il cmdlet Stop-Process di esempio seguente mostrano le chiamate per il [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) l'override del metodo il [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo).

Questo messaggio di debug viene scritto immediatamente prima [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) viene chiamato.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Questo messaggio di debug viene scritto immediatamente prima [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) viene chiamato.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell instrada automaticamente uno [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) chiamate per l'infrastruttura di traccia e i cmdlet. In questo modo le chiamate al metodo da tracciare senza che sia necessario eseguire alcuna operazione aggiuntiva sviluppo entro il cmdlet per l'applicazione host, un file o un debugger. La voce della riga di comando seguente implementa un'operazione di traccia.

**PS > espressione di traccia stop-Process-file proc.log-notepad stop-Process di comando**

## <a name="writing-a-warning-message"></a>La scrittura di un messaggio di avviso

Il [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metodo viene utilizzato per scrivere un messaggio di avviso quando il cmdlet sta per eseguire un'operazione che potrebbe avere un risultato di imprevisto, ad esempio, sovrascrivere un file di sola lettura.

Il codice seguente tramite il cmdlet Stop-Process di esempio illustra la chiamata ai [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) l'override del metodo di [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo).

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Scrittura di un messaggio di stato di avanzamento

Il [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) viene usato per scrivere i messaggi di stato di avanzamento durante operazioni del cmdlet richiedono una certa quantità di tempo. Una chiamata a [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passa una [progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) oggetto che viene inviato all'applicazione host per il rendering all'utente.

> [!NOTE]
> Questo cmdlet Stop-Process non include una chiamata per il [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) (metodo).

Il codice riportato di seguito è riportato un esempio di un messaggio di stato scritto da un cmdlet che sta tentando di copiare un elemento.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Esempio di codice

Per l'intero C# esempi di codice, vedere [StopProcessSample02 campione](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Definire i tipi di oggetto e la formattazione

Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .NET. Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet. Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Creazione di Cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell. Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Il Cmdlet di test

Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando. È possibile testare il cmdlet Stop-Process di esempio. Per altre informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- La voce della riga di comando seguente usa Stop-Process per arrestare il processo denominato "NOTEPAD", fornire notifiche dettagliate e stampare le informazioni di debug.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

Viene visualizzato l'output seguente.

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

[Creare un Cmdlet che modifichi il sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Come creare un Cmdlet di Windows PowerShell](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Estensione di tipi di oggetto e la formattazione](/previous-versions//ms714665(v=vs.85))

[Come registrare i cmdlet, provider e applicazioni Host](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
