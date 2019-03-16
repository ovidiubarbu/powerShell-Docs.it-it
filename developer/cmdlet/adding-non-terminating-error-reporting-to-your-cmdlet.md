---
title: Aggiunta di segnalazione errori al Cmdlet di Non definitive | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: e0550dacc33f45f45ba105ca5cb4d2e5b5d675fb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056057"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Aggiunta di segnalazioni di errori non irreversibili al cmdlet

I cmdlet possono segnalare gli errori non fatali chiamando il [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (metodo) e comunque continuare a operare sull'oggetto di input corrente o in entrata ulteriormente gli oggetti di pipeline. Questa sezione viene illustrato come creare un cmdlet che segnala gli errori non fatali dai relativi metodi di elaborazione dell'input.

Per gli errori non fatali (così come gli errori irreversibili), il cmdlet è necessario passare un [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetto che identifica l'errore. Ogni record di errore è identificato da una stringa univoca, chiamata "identificatore dell'errore". Oltre all'identificatore, la categoria di ogni errore è specificata dalle costanti definite da un [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumerazione. L'utente può visualizzare gli errori in base alla categoria basati impostando il `$ErrorView` variabile "CategoryView".

Per altre informazioni sui record di errore, vedere [record di errore di Windows PowerShell](./windows-powershell-error-records.md).

Gli argomenti in questa sezione includono quanto segue:

- [Che definisce il Cmdlet](#Defining-the-Cmdlet)

- [Definizione dei parametri](#Defining-Parameters)

- [Si esegue l'override di metodi di elaborazione dell'Input](#Overriding-Input-Processing-Methods)

- [Segnalazione di errori non fatali](#Reporting-Nonterminating-Errors)

- [Esempio di codice](#Code-Sample)

- [Definizione di tipi di oggetto e formattazione](#Define-Object-Types-and-Formatting)

- [Creazione di Cmdlet](#Building-the-Cmdlet)

- [Il Cmdlet di test](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Che definisce il Cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il cmdlet di denominazione e la dichiarazione di classe .NET che implementa il cmdlet. Questo cmdlet recupera le informazioni sul processo, in modo che il nome del verbo selezionato qui è "Get". (Quasi una sorta di cmdlet che è in grado di recuperare le informazioni può elaborare input della riga di comando). Per altre informazioni sui verbi approvati di cmdlet, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Di seguito è la definizione per il cmdlet Get-Process. Dettagli di questa definizione sono disponibili nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>Definizione dei parametri

Se necessario, il cmdlet necessario definire i parametri per l'elaborazione dell'input. Questo cmdlet Get-Proc definisce una `Name` parametro, come descritto in [aggiunta di parametri di Input della riga di comando processo](./adding-parameters-that-process-command-line-input.md).

Di seguito è riportata la dichiarazione di parametro per il `Name` parametro del cmdlet Get-Process.

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a>Si esegue l'override di metodi di elaborazione dell'Input

Tutti i cmdlet devono eseguire l'override di almeno uno dei metodi forniti dall'elaborazione dell'input di [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Questi metodi sono descritti in [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> Il cmdlet consente di gestire ogni record più indipendente possibile.

Esegue l'override di questo cmdlet Get-Proc il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo per gestire il `Name` parametro per l'input fornito dall'utente o uno script. Questo metodo otterranno i processi per ogni nome di processo richiesto o tutti i processi se viene fornito alcun nome. Dettagli di questa sostituzione sono disponibili nella [la creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md).

#### <a name="things-to-remember-when-reporting-errors"></a>Aspetti da ricordare quando si segnalano gli errori

Il [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) che il cmdlet ha esito positivo quando la scrittura di un errore richiede un'eccezione alla base dell'oggetto. Seguire le linee guida di .NET durante la determinazione di eccezione da usare. In sostanza, se l'errore è semanticamente identico un'eccezione esistente, il cmdlet deve usare o derivare da tale eccezione. In caso contrario, consigliabile derivare una nuova eccezione o una gerarchia di eccezione direttamente dai [System. Exception](/dotnet/api/System.Exception) classe.

Durante la creazione di identificatori di errore, accessibili tramite la proprietà FullyQualifiedErrorId della classe ErrorRecord, tenere presente quanto segue.

- Stringhe di utilizzo assegnati per scopi diagnostici in modo che quando si esamina l'identificatore completo è possibile determinare la causa del problema è e in cui l'errore proviene dal.

- Un identificatore di errore completo valido potrebbe essere come segue.

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

Si noti che nell'esempio precedente, l'identificatore dell'errore (il primo token) definisce l'errore e la parte rimanente indica dove l'errore proviene.

- Per scenari più complessi, l'identificatore dell'errore può essere un token separati da punto che può essere analizzato in ispezione. In questo modo che si crea un ramo troppo sulle parti dell'identificatore dell'errore, nonché la categoria dell'errore identificatore ed errore.

Il cmdlet deve assegnare identificatori di errore specifico ai percorsi del codice diversi. Tenere presente per l'assegnazione di identificatori di errore le informazioni seguenti:

- Un identificatore di errore dovrebbe rimanere costante durante il ciclo di vita di cmdlet. Non modificare la semantica di un identificatore di errore tra le versioni di cmdlet.

- Usare testo per un identificatore di errore che fornisce risposte superficiali corrispondente all'errore segnalato. Non usare spazi vuoti o punteggiatura.

- Generare solo gli identificatori degli errori che sono riproducibile con il cmdlet. Ad esempio, non deve generare un identificatore che include un identificatore di processo. Gli identificatori di errore sono utili per un utente solo se corrispondono agli identificatori visualizzate da altri utenti che rilevano lo stesso problema.

Le eccezioni non gestite non vengono rilevate da Windows PowerShell nelle condizioni seguenti:

- Se un cmdlet crea un nuovo thread e il codice in esecuzione in quanto thread genera un'eccezione non gestita, Windows PowerShell non rileva l'errore e terminerà il processo.

- Se un oggetto dispone di codice che genera un'eccezione non gestita nel relativo distruttore o i metodi Dispose, Windows PowerShell non rileva l'errore e terminerà il processo.

## <a name="reporting-nonterminating-errors"></a>Segnalazione di errori non fatali

Uno dei metodi di elaborazione dell'input può segnalare un errore non fatali per il flusso di output usando il [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (metodo). Di seguito è riportato un esempio di codice da questo cmdlet Get-Process che illustra la chiamata a [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) all'interno dell'override del [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo). In questo caso, la chiamata viene eseguita se il cmdlet non è possibile trovare un processo per un identificatore di processo specificato.

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Aspetti da ricordare sulla scrittura di errori non fatali

Per un errore non fatali, il cmdlet necessario generare un identificatore di errore specifico per ogni oggetto di input specifico.

Un cmdlet deve spesso modificare l'azione di Windows PowerShell generato da un errore non fatali. È possibile eseguire questa operazione definendo i `ErrorAction` e `ErrorVariable` parametri. Se la definizione del `ErrorAction` parametro, il cmdlet Visualizza le opzioni utente [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), è possibile influenzare anche direttamente l'azione impostando il `$ErrorActionPreference` variabile.

Il cmdlet è possibile salvare gli errori non fatali in una variabile utilizzando la `ErrorVariable` parametro, che non è interessato dall'impostazione della `ErrorAction`. Errori possono essere aggiunta in una variabile di errore esistente aggiungendo un segno più (+) all'inizio del nome della variabile.

## <a name="code-sample"></a>Esempio di codice

Per l'intero C# esempi di codice, vedere [GetProcessSample04 campione](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Definire i tipi di oggetto e la formattazione

Windows PowerShell passa informazioni tra i cmdlet con gli oggetti .NET. Di conseguenza, potrebbe essere necessario definire un proprio tipo di un cmdlet o il cmdlet potrebbe essere necessario estendere un tipo esistente fornito da un altro cmdlet. Per altre informazioni sulla definizione di nuovi tipi o estendere i tipi esistenti, vedere [estendendo i tipi di oggetto e formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Creazione di Cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in Windows PowerShell. Per altre informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Il Cmdlet di test

Quando il cmdlet è stato registrato con Windows PowerShell, è possibile testarlo eseguendolo dalla riga di comando. È possibile testare il cmdlet Get-Process di esempio per vedere se viene segnalato un errore:

- Avviare Windows PowerShell e usare il cmdlet Get-Process per recuperare i processi denominati "TEST".

    ```powershell
    PS> get-proc -name test
    ```

Viene visualizzato l'output seguente.

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>Vedere anche

[Aggiunta di parametri di Input della Pipeline di processo](./adding-parameters-that-process-pipeline-input.md)

[Aggiunta di parametri che elaborano gli Input della riga di comando](./adding-parameters-that-process-command-line-input.md)

[Creazione del primo Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Estensione di tipi di oggetto e la formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Reference](../windows-powershell-reference.md) (Guida di riferimento di PowerShell)

[Esempi di cmdlet](./cmdlet-samples.md)
