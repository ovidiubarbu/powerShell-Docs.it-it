---
title: Creazione di un cmdlet che modifica il sistema | Microsoft Docs
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
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365760"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Creazione di un cmdlet che modifica il sistema

A volte un cmdlet deve modificare lo stato di esecuzione del sistema, non solo lo stato del runtime di Windows PowerShell. In questi casi, il cmdlet deve consentire all'utente di confermare se apportare o meno la modifica.

Per supportare la conferma, un cmdlet deve eseguire due operazioni.

- Dichiarare che il cmdlet supporta la conferma quando si specifica l'attributo [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) impostando la parola chiave SupportsShouldProcess su `true`.

- Chiamare [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) durante l'esecuzione del cmdlet (come illustrato nell'esempio seguente).

Grazie al supporto della conferma, un cmdlet espone i parametri `Confirm` e `WhatIf` forniti da Windows PowerShell e soddisfa anche le linee guida di sviluppo per i cmdlet. per ulteriori informazioni sulle linee guida per lo sviluppo di cmdlet, vedere [linee guida per lo](./cmdlet-development-guidelines.md)sviluppo di cmdlet.

## <a name="changing-the-system"></a>Modifica del sistema

L'azione di "modifica del sistema" si riferisce a qualsiasi cmdlet che potenzialmente modifica lo stato del sistema al di fuori di Windows PowerShell. Ad esempio, l'arresto di un processo, l'abilitazione o la disabilitazione di un account utente o l'aggiunta di una riga a una tabella di database sono tutte modifiche al sistema che devono essere confermate. Al contrario, le operazioni di lettura dei dati o di stabilire connessioni temporanee non cambiano il sistema e in genere non richiedono la conferma. Non è inoltre necessaria una conferma per le azioni il cui effetto è limitato all'interno del runtime di Windows PowerShell, ad esempio `set-variable`. I cmdlet che potrebbero o meno apportare una modifica permanente devono dichiarare `SupportsShouldProcess` e chiamare [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solo se stanno per apportare una modifica permanente.

> [!NOTE]
> La conferma ShouldProcess si applica solo ai cmdlet. Se un comando o uno script modifica lo stato di esecuzione di un sistema chiamando direttamente i metodi o le proprietà .NET oppure chiamando le applicazioni all'esterno di Windows PowerShell, questo tipo di conferma non sarà disponibile.

## <a name="the-stopproc-cmdlet"></a>Cmdlet StopProc

Questo argomento descrive un cmdlet Stop-proc che tenta di arrestare i processi recuperati usando il cmdlet Get-proc, descritto in [creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md).

## <a name="defining-the-cmdlet"></a>Definizione del cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il nome del cmdlet e la dichiarazione della classe .NET che implementa il cmdlet. Poiché si sta scrivendo un cmdlet per modificare il sistema, è necessario denominarlo di conseguenza. Questo cmdlet interrompe i processi di sistema, quindi il nome del verbo scelto qui è "Stop", definito dalla classe [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , con il sostantivo "proc" per indicare che il cmdlet interrompe i processi. Per altre informazioni sui verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Di seguito è riportata la definizione della classe per il cmdlet Stop-proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Tenere presente che nella Dichiarazione [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) la parola chiave `SupportsShouldProcess` attribute è impostata su `true` per consentire al cmdlet di effettuare chiamate a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Senza questa parola chiave impostata, i parametri `Confirm` e `WhatIf` non saranno disponibili per l'utente.

### <a name="extremely-destructive-actions"></a>Azioni estremamente distruttive

Alcune operazioni sono estremamente distruttive, ad esempio la riformattazione di una partizione del disco rigido attiva. In questi casi, il cmdlet deve impostare `ConfirmImpact` = `ConfirmImpact.High` quando dichiara l'attributo [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) . Questa impostazione impone al cmdlet di richiedere la conferma dell'utente anche quando l'utente non ha specificato il parametro `Confirm`. Tuttavia, gli sviluppatori di cmdlet devono evitare di usare `ConfirmImpact` per operazioni potenzialmente distruttive, ad esempio l'eliminazione di un account utente. Tenere presente che se `ConfirmImpact` è impostato su [System. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.

Analogamente, è improbabile che alcune operazioni siano distruttive, sebbene in teoria modifichino lo stato di esecuzione di un sistema al di fuori di Windows PowerShell. Questi cmdlet possono impostare `ConfirmImpact` su [System. Management. Automation. ConfirmImpact. Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Questa operazione consente di ignorare le richieste di conferma in cui l'utente ha richiesto di confermare solo le operazioni a medio e a elevato utilizzo.

## <a name="defining-parameters-for-system-modification"></a>Definizione dei parametri per la modifica del sistema

In questa sezione viene descritto come definire i parametri del cmdlet, inclusi quelli necessari per supportare la modifica del sistema. Per informazioni generali sulla definizione dei parametri, vedere [aggiunta di parametri che elaborano l'input della riga](./adding-parameters-that-process-command-line-input.md) di comando.

Il cmdlet Stop-proc definisce tre parametri: `Name`, `Force`e `PassThru`.

Il parametro `Name` corrisponde alla proprietà `Name` dell'oggetto di input del processo. Tenere presente che il parametro `Name` in questo esempio è obbligatorio, in quanto il cmdlet avrà esito negativo se non è presente un processo denominato da arrestare.

Il parametro `Force` consente all'utente di eseguire l'override delle chiamate a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). In realtà, qualsiasi cmdlet che chiama [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) deve avere un parametro `Force` in modo che, quando viene specificato `Force`, il cmdlet ignora la chiamata a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) e procede con l'operazione. Tenere presente che questa operazione non influisce sulle chiamate a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

Il `PassThru` parametro consente all'utente di indicare se il cmdlet passa un oggetto di output attraverso la pipeline, in questo caso, dopo l'arresto di un processo. Tenere presente che questo parametro è associato al cmdlet stesso anziché a una proprietà dell'oggetto di input.

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

Il cmdlet deve eseguire l'override di un metodo di elaborazione dell'input. Il codice seguente illustra l'override di [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) usato nel cmdlet Stop-proc di esempio. Per ogni nome di processo richiesto, questo metodo garantisce che il processo non sia un processo speciale, tenta di arrestare il processo e quindi Invia un oggetto di output se viene specificato il parametro `PassThru`.

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

## <a name="calling-the-shouldprocess-method"></a>Chiamata al metodo ShouldProcess

Il metodo di elaborazione dell'input del cmdlet deve chiamare il metodo [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) per confermare l'esecuzione di un'operazione prima che venga apportata una modifica, ad esempio l'eliminazione di file, allo stato di esecuzione del sistema. Ciò consente al runtime di Windows PowerShell di fornire il comportamento corretto "WhatIf" e "Confirm" all'interno della shell.

> [!NOTE]
> Se un cmdlet dichiara che supporta deve elaborare e non riesce a eseguire la chiamata [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , l'utente potrebbe modificare il sistema in modo imprevisto.

La chiamata a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) invia il nome della risorsa da modificare all'utente, con il runtime di Windows PowerShell che prende in considerazione le impostazioni della riga di comando o le variabili di preferenza per determinare gli elementi da visualizzare all'utente.

Nell'esempio seguente viene illustrata la chiamata a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) dall'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) nel cmdlet Stop-proc di esempio.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>Chiamata al metodo ShouldContinue

La chiamata al metodo [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Invia un messaggio secondario all'utente. Questa chiamata viene eseguita dopo che la chiamata a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) restituisce `true` e se il parametro `Force` non è stato impostato su `true`. L'utente può quindi inviare commenti e suggerimenti per indicare se l'operazione deve essere continuata. Il cmdlet chiama [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) come controllo aggiuntivo per le modifiche di sistema potenzialmente pericolose o quando si desidera fornire all'utente opzioni Sì-a-tutti e no-to-all.

Nell'esempio seguente viene illustrata la chiamata a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) dall'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) nel cmdlet Stop-proc di esempio.

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

## <a name="stopping-input-processing"></a>Arresto dell'elaborazione dell'input

Il metodo di elaborazione dell'input di un cmdlet che apporta modifiche al sistema deve fornire un modo per arrestare l'elaborazione dell'input. Nel caso di questo cmdlet Stop-proc, viene eseguita una chiamata dal metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) al metodo [System. Diagnostics. Process. Kill *](/dotnet/api/System.Diagnostics.Process.Kill) . Poiché il parametro `PassThru` è impostato su `true`, [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) chiama anche [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) per inviare l'oggetto processo alla pipeline.

## <a name="code-sample"></a>Codice di esempio

Per il codice C# di esempio completo, vedere l' [esempio StopProcessSample01](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetti e formattazione

Windows PowerShell passa le informazioni tra i cmdlet usando gli oggetti .NET. Di conseguenza, un cmdlet può avere la necessità di definire un proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet. Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilazione del cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell. Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test del cmdlet

Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo nella riga di comando. Di seguito sono riportati diversi test che testano il cmdlet Stop-proc. Per ulteriori informazioni sull'utilizzo dei cmdlet dalla riga di comando, vedere la [Introduzione con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Avviare Windows PowerShell e usare il cmdlet Stop-proc per arrestare l'elaborazione, come illustrato di seguito. Poiché il cmdlet specifica il parametro `Name` come obbligatorio, il cmdlet esegue una query per il parametro.

    ```powershell
    PS> stop-proc
    ```

Viene visualizzato l'output seguente:

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- A questo punto è possibile usare il cmdlet per arrestare il processo denominato "blocco note". Il cmdlet richiede di confermare l'azione.

    ```powershell
    PS> stop-proc -Name notepad
    ```

Viene visualizzato l'output seguente:

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Usare stop-proc come illustrato per arrestare il processo critico denominato "WINLOGON". Viene richiesto e visualizzato un avviso relativo all'esecuzione di questa azione perché il sistema operativo verrà riavviato.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

Viene visualizzato l'output seguente:

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- A questo punto, provare ad arrestare il processo WINLOGON senza ricevere un avviso. Tenere presente che questa voce di comando usa il parametro `Force` per eseguire l'override dell'avviso.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

Viene visualizzato l'output seguente:

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Vedere anche

[Aggiunta di parametri che elaborano l'input della riga di comando](./adding-parameters-that-process-command-line-input.md)

[Estensione di tipi di oggetti e formattazione](/previous-versions//ms714665(v=vs.85))

[Come registrare cmdlet, provider e applicazioni host](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Esempi di cmdlet](./cmdlet-samples.md)