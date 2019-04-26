---
title: Creazione di un Cmdlet che modifichi il sistema | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: bbe9f0213754d1cc47e0fd9a7a898bde916c0636
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068440"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Creazione di un cmdlet che modifica il sistema

In alcuni casi un cmdlet è necessario modificare lo stato del sistema, non solo lo stato del runtime di Windows PowerShell in esecuzione. In questi casi, il cmdlet deve consentire all'utente la possibilità di confermare se apportare la modifica o meno.

Per supportare la conferma un cmdlet deve fare due cose.

- Dichiarare che il cmdlet supporta conferma quando si specifica la [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attributo impostando la parola chiave SupportsShouldProcess su `true`.

- Chiamare [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) durante l'esecuzione del cmdlet (come illustrato nell'esempio seguente).

Grazie al supporto di conferma, espone un cmdlet di `Confirm` e `WhatIf` parametri che vengono forniti da Windows PowerShell e anche soddisfano le linee guida sullo sviluppo per i cmdlet (per altre informazioni sulle linee guida sullo sviluppo di cmdlet, vedere [ Linee guida sullo sviluppo di cmdlet](./cmdlet-development-guidelines.md).).

## <a name="changing-the-system"></a>La modifica del sistema

L'atto di "modifica il sistema" si riferisce a tutti i cmdlet che potenzialmente modifica lo stato del sistema di fuori di Windows PowerShell. Ad esempio, l'arresto di un processo, Abilita o disabilita un account utente o aggiunta di una riga a una tabella di database sono tutte le modifiche apportate al sistema che deve essere confermata. Operazioni di lettura dei dati o stabiliscono le connessioni temporanee, invece, non modificare il sistema e in genere non necessitano di una conferma. Conferma non serve anche per le azioni il cui effetto è limitata all'interno del runtime di Windows PowerShell, ad esempio `set-variable`. I cmdlet che possono o non potrebbero apportare una modifica permanente devono dichiarare `SupportsShouldProcess` e chiamare [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solo se si sta tentando di apportare una modifica permanente.

> [!NOTE]
> Conferma ShouldProcess si applica solo ai cmdlet. Se un comando o lo script modifica lo stato in esecuzione di un sistema chiamando direttamente i metodi .NET o proprietà o da applicazioni chiamanti all'esterno di Windows PowerShell, questa forma di conferma non saranno disponibile.

## <a name="the-stopproc-cmdlet"></a>Il StopProc Cmdlet

Questo argomento viene descritto un cmdlet Stop-Process che tenta di arrestare i processi che vengono recuperati usando il cmdlet Get-Proc (descritto nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Gli argomenti in questa sezione includono quanto segue:

- [Che definisce il Cmdlet](#Defining-the-Cmdlet)

- [Definizione dei parametri per la modifica di sistema](#Defining-Parameters-for-System-Modification)

- [Si esegue l'override di un metodo di elaborazione dell'Input](#Overriding-an-Input-Processing-Method)

- [La chiamata al metodo ShouldProcess](#Calling-the-ShouldProcess-Method)

- [La chiamata al metodo ShouldContinue](#Calling-the-ShouldContinue-Method)

- [Arresto l'elaborazione dell'Input](#Stopping-Input-Processing)

- [Esempio di codice](#Code-Sample)

- [Definizione di tipi di oggetto e formattazione](#Defining-Object-Types-and-Formatting)

- [Creazione di Cmdlet](#Building-the-Cmdlet)

- [Il Cmdlet di test](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Che definisce il Cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet. Poiché si sta scrivendo un cmdlet per modificare il sistema, devono essere denominato di conseguenza. Questo cmdlet arresta i processi di sistema, in modo che il nome del verbo selezionato qui è "Stop", definiti per il [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) (classe), con il sostantivo "Proc" per indicare che il cmdlet arresta i processi. Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Di seguito è la definizione della classe per questo cmdlet Stop-Process.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Tenere presente che nel [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) dichiarazione, il `SupportsShouldProcess` parola chiave di attributo è impostato su `true` per abilitare il cmdlet di effettuare chiamate a [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Senza questo set di parole chiave, il `Confirm` e `WhatIf` parametri non sarà disponibili per l'utente.

### <a name="extremely-destructive-actions"></a>Azioni distruttive

Alcune operazioni sono estremamente distruttive, ad esempio la riformattazione di una partizione disco rigido attivo. In questi casi, è necessario impostare il cmdlet `ConfirmImpact`  =  `ConfirmImpact.High` quando si dichiara il [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attributo. Questa impostazione forza il cmdlet per richiesta conferma all'utente, anche quando l'utente non ha specificato il `Confirm` parametro. Tuttavia, gli sviluppatori di cmdlet devono evitare un uso eccessivo `ConfirmImpact` per le operazioni che sono semplicemente potenzialmente distruttive, ad esempio l'eliminazione di un account utente. Tenere presente che, se `ConfirmImpact` è impostata su [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).

In modo analogo, alcune operazioni sono probabilmente non distruttiva, sebbene in teoria modificano tuttavia lo stato di un sistema all'esterno di Windows PowerShell in esecuzione. Questi cmdlet è possono impostare `ConfirmImpact` al [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Si possono ignorare le richieste di conferma in cui l'utente ha richiesto di confermare le operazioni di solo supporto a impatto e a impatto elevato.

## <a name="defining-parameters-for-system-modification"></a>Definizione dei parametri per la modifica di sistema

Questa sezione descrive come definire i parametri del cmdlet, inclusi quelli che sono necessari per la modifica di sistema di supporto. Visualizzare [aggiunta di parametri di Input della riga di comando processo](./adding-parameters-that-process-command-line-input.md) se sono necessarie informazioni generali sulla definizione dei parametri.

Il cmdlet Stop-Process definisce tre parametri: `Name`, `Force`, e `PassThru`.

Il `Name` parametro corrisponde al `Name` proprietà dell'oggetto di input di processo. Tenere presente che il `Name` in questo esempio il parametro è obbligatorio, come il cmdlet avrà esito negativo se non dispone di un processo denominato arrestare.

Il `Force` parametro consente all'utente di eseguire l'override di chiamate a [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). In effetti, tutti i cmdlet che chiama [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) deve avere una `Force` parametri in modo che quando `Force` viene specificato, il cmdlet ignora la chiamata a [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) e procede con l'operazione. Tenere presente che questa operazione non influenza le chiamate a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

Il `PassThru` parametro consente all'utente di indicare se il cmdlet passa un oggetto di output tramite la pipeline, in questo caso, dopo un processo viene arrestato. Tenere presente che questo parametro è correlato al cmdlet stesso anziché a una proprietà dell'oggetto di input.

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

Il cmdlet deve eseguire l'override di un metodo di elaborazione dell'input. Il codice seguente illustra il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) sostituzione usata nel cmdlet Stop-Process esempio. Per ogni richiesta di nome di processo, questo metodo garantisce che il processo non è un processo speciale, tenta di arrestare il processo e quindi invia un oggetto di output se il `PassThru` parametro è specificato.

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a>La chiamata al metodo ShouldProcess

Deve chiamare il metodo del cmdlet di elaborazione dell'input di [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodo per confermare l'esecuzione di un'operazione prima di allo stato di esecuzione viene apportata una modifica (ad esempio, l'eliminazione di file) del sistema. In questo modo il runtime di Windows PowerShell fornire il comportamento corretto "WhatIf" e "Conferma" all'interno della shell.

> [!NOTE]
> Se un cmdlet indica il supporto deve essere elaborato e non riesce a eseguire la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chiamare, l'utente può modificare il sistema in modo imprevisto.

La chiamata a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) invia il nome della risorsa da modificare per l'utente, con il runtime di Windows PowerShell prendendo in considerazione tutte le impostazioni della riga di comando o variabili di preferenza determinare ciò che deve essere visualizzato all'utente.

L'esempio seguente illustra la chiamata a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) dall'override del [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) nell'esempio di metodo Cmdlet Stop-Process.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>La chiamata al metodo ShouldContinue

La chiamata per il [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodo invia un messaggio secondario all'utente. Questa chiamata viene eseguita dopo la chiamata a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) restituisce `true` e, se il `Force` parametro non è stato impostato su `true`. L'utente può quindi fornire commenti e suggerimenti, ad esempio, se l'operazione deve proseguire. Chiama il cmdlet [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) come un controllo aggiuntivo per le modifiche del sistema potenzialmente pericolose o quando si desidera fornire all'utente, le opzioni yes to all e no-to-all.

L'esempio seguente illustra la chiamata a [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) dall'override del [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) nell'esempio di metodo Cmdlet Stop-Process.

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a>Arresto l'elaborazione dell'Input

Il metodo di un cmdlet che rende le modifiche di sistema di elaborazione dell'input è necessario fornire un modo per arrestare l'elaborazione dell'input. Nel caso di questo cmdlet Stop-Process, viene eseguita una chiamata dal [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo per il [System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill) (metodo). Poiché il `PassThru` parametro è impostato su `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) chiama inoltre [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) inviare l'oggetto processo per la pipeline.

## <a name="code-sample"></a>Esempio di codice

Per l'intero C# esempi di codice, vedere [esempio StopProcessSample01](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetto e formattazione

Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .net. Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet. Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Creazione di Cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell. Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Il Cmdlet di test

Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando. Ecco alcuni test che verificano il cmdlet Stop-Process. Per altre informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Avviare Windows PowerShell e usare il cmdlet Stop-Process per arrestare l'elaborazione come illustrato di seguito. Poiché il cmdlet specifica la `Name` parametro come obbligatorio, la query dei cmdlet per il parametro.

    ```powershell
    PS> stop-proc
    ```

Viene visualizzato l'output seguente.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- A questo punto è possibile usare il cmdlet per arrestare il processo denominato "NOTEPAD". Il cmdlet chiede di confermare l'azione.

    ```powershell
    PS> stop-proc -Name notepad
    ```

Viene visualizzato l'output seguente.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Come illustrato, usare Stop-Process per arrestare il processo critico denominato "WINLOGON". Si è richiesto e visualizzato un avviso su come eseguire questa azione perché si verificheranno di riavvio del sistema operativo.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

Viene visualizzato l'output seguente.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- A questo punto Proviamo ad arrestare il processo WINLOGON senza ricevere un avviso. Tenere presente che questa voce comando Usa il `Force` parametro per ignorare l'avviso.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

Viene visualizzato l'output seguente.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Vedere anche

[Aggiunta di parametri che elaborano gli Input della riga di comando](./adding-parameters-that-process-command-line-input.md)

[Estensione di tipi di oggetto e la formattazione](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Come registrare i cmdlet, provider e applicazioni Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Esempi di cmdlet](./cmdlet-samples.md)