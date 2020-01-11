---
title: Aggiunta di segnalazione errori non fatale al cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: ec29d1cffa083e4cce667d3e1efbd4eeecbffb51
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870116"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Aggiunta di segnalazioni di errori non irreversibili al cmdlet

I cmdlet possono segnalare errori non fatali chiamando il metodo [System. Management. Automation. cmdlet. WriteError][] e continuano comunque a funzionare sull'oggetto di input corrente o su altri oggetti pipeline in ingresso. In questa sezione viene illustrato come creare un cmdlet per la segnalazione di errori non fatali dei relativi metodi di elaborazione dell'input.

Per gli errori non fatali (nonché per la terminazione degli errori), il cmdlet deve passare un oggetto [System. Management. Automation. ErrorRecord][] che identifica l'errore. Ogni record di errore è identificato da una stringa univoca denominata "identificatore errore". Oltre all'identificatore, la categoria di ogni errore viene specificata dalle costanti definite da un'enumerazione [System. Management. Automation. ErrorCategory][] . L'utente può visualizzare gli errori in base alla relativa categoria impostando la variabile `$ErrorView` su "CategoryView".

Per ulteriori informazioni sui record degli errori, vedere la pagina relativa ai [record degli errori di Windows PowerShell](./windows-powershell-error-records.md).

## <a name="defining-the-cmdlet"></a>Definizione del cmdlet

Il primo passaggio nella creazione di cmdlet è sempre il nome del cmdlet e la dichiarazione della classe .NET che implementa il cmdlet. Questo cmdlet recupera le informazioni sul processo, quindi il nome del verbo scelto qui è "Get". (Quasi tutti i tipi di cmdlet in grado di recuperare informazioni possono elaborare l'input della riga di comando). Per altre informazioni sui verbi di cmdlet approvati, vedere [nomi dei verbi di cmdlet](approved-verbs-for-windows-powershell-commands.md).

Di seguito è riportata la definizione di questo cmdlet `Get-Proc`. I dettagli di questa definizione sono forniti durante [la creazione del primo cmdlet](creating-a-cmdlet-without-parameters.md).

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

Se necessario, il cmdlet deve definire i parametri per l'elaborazione dell'input. Questo cmdlet Get-proc definisce un parametro del **nome** come descritto in [aggiunta di parametri che elaborano l'input della riga di comando](adding-parameters-that-process-command-line-input.md).

Di seguito è illustrata la dichiarazione di parametro per il parametro **Name** del cmdlet Get-proc.

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

## <a name="overriding-input-processing-methods"></a>Override dei metodi di elaborazione degli input

Tutti i cmdlet devono eseguire l'override di almeno uno dei metodi di elaborazione dell'input forniti dalla classe [System. Management. Automation. cmdlet][] . Questi metodi vengono descritti in [creazione del primo cmdlet](creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> Il cmdlet deve gestire ogni record nel modo più indipendente possibile.

Questo cmdlet Get-proc esegue l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord][] per gestire il parametro **Name** per l'input fornito dall'utente o da uno script. Questo metodo otterrà i processi per ogni nome di processo richiesto o per tutti i processi se non viene specificato alcun nome. I dettagli di questa sostituzione sono forniti in [creazione del primo cmdlet](creating-a-cmdlet-without-parameters.md).

### <a name="things-to-remember-when-reporting-errors"></a>Aspetti da ricordare quando si segnalano errori

L'oggetto [System. Management. Automation. ErrorRecord][] passato dal cmdlet quando si scrive un errore richiede un'eccezione al suo interno. Per determinare l'eccezione da usare, seguire le linee guida di .NET.
In sostanza, se l'errore è semanticamente uguale a un'eccezione esistente, il cmdlet deve usare o derivare da tale eccezione. In caso contrario, deve derivare una nuova eccezione o una nuova gerarchia di eccezioni direttamente dalla classe [System. Exception][] .

Quando si creano identificatori di errore (a cui si accede tramite la proprietà FullyQualifiedErrorId della classe ErrorRecord), tenere presente quanto segue.

- Usare le stringhe destinate a scopi diagnostici in modo che, quando si esamina l'identificatore completo, sia possibile determinare l'errore e il punto in cui è stato generato l'errore.

- Un identificatore di errore completo ben formato potrebbe essere il seguente.

  `CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

Si noti che nell'esempio precedente, l'identificatore di errore (il primo token) designa l'errore e la parte rimanente indica da dove proviene l'errore.

- Per scenari più complessi, l'identificatore di errore può essere un token separato da punti che può essere analizzato durante l'ispezione. In questo modo è possibile creare rami anche per le parti dell'identificatore di errore, nonché l'identificatore e la categoria di errore.

Il cmdlet deve assegnare identificatori di errore specifici a percorsi di codice diversi. Per l'assegnazione degli identificatori di errore, tenere presenti le seguenti informazioni:

- Un identificatore di errore deve rimanere costante durante tutto il ciclo di vita del cmdlet. Non modificare la semantica di un identificatore errore tra le versioni dei cmdlet.
- Usare il testo per un identificatore di errore che laconicamente corrisponde all'errore segnalato. Non usare spazi vuoti o segni di punteggiatura.
- Se il cmdlet genera solo identificatori di errore riproducibili. Ad esempio, non deve generare un identificatore che include un identificatore di processo. Gli identificatori di errore sono utili per un utente solo quando corrispondono agli identificatori visualizzati da altri utenti che hanno riscontrato lo stesso problema.

Le eccezioni non gestite non vengono rilevate da PowerShell nelle condizioni seguenti:

- Se un cmdlet crea un nuovo thread e il codice in esecuzione nel thread genera un'eccezione non gestita, PowerShell non rileva l'errore e termina il processo.
- Se un oggetto dispone di codice nel relativo distruttore o di metodi Dispose che causa un'eccezione non gestita, PowerShell non rileva l'errore e termina il processo.

## <a name="reporting-nonterminating-errors"></a>Segnalazione di errori non fatali

Uno dei metodi di elaborazione dell'input può segnalare un errore non fatale al flusso di output usando il metodo [System. Management. Automation. cmdlet. WriteError][] .

Di seguito è riportato un esempio di codice di questo cmdlet Get-proc che illustra la chiamata a [System. Management. Automation. cmdlet. WriteError][] dall'interno dell'override del metodo [System. Management. Automation. cmdlet. ProcessRecord][] . In questo caso, la chiamata viene eseguita se il cmdlet non riesce a trovare un processo per un identificatore di processo specificato.

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Aspetti da ricordare per la scrittura di errori non fatali

Per un errore non fatale, il cmdlet deve generare un identificatore di errore specifico per ogni oggetto di input specifico.

Un cmdlet deve spesso modificare l'azione di PowerShell generata da un errore non fatale. Questa operazione può essere eseguita definendo i parametri `ErrorAction` e `ErrorVariable`. Se si definisce il parametro `ErrorAction`, il cmdlet presenta le opzioni utente [System. Management. Automation. preferenzaazione][], è anche possibile influenzare direttamente l'azione impostando la variabile `$ErrorActionPreference`.

Il cmdlet consente di salvare errori non fatali in una variabile utilizzando il parametro `ErrorVariable`, che non è influenzato dall'impostazione di `ErrorAction`. Gli errori possono essere aggiunti a una variabile di errore esistente aggiungendo un segno più (+) all'inizio del nome della variabile.

## <a name="code-sample"></a>Codice di esempio

Per il codice C# di esempio completo, vedere l' [esempio GetProcessSample04](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Definire i tipi di oggetto e la formattazione

PowerShell passa informazioni tra i cmdlet usando oggetti .NET. Di conseguenza, un cmdlet potrebbe dover definire il proprio tipo oppure il cmdlet deve estendere un tipo esistente fornito da un altro cmdlet. Per ulteriori informazioni sulla definizione di nuovi tipi o sull'estensione di tipi esistenti, vedere [estensione di tipi di oggetti e formattazione](/previous-versions/ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Compilazione del cmdlet

Dopo l'implementazione di un cmdlet, è necessario registrarlo con Windows PowerShell tramite uno snap-in di Windows PowerShell. Per ulteriori informazioni sulla registrazione dei cmdlet, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Test del cmdlet

Quando il cmdlet è stato registrato con PowerShell, è possibile testarlo eseguendolo nella riga di comando. Testiamo il cmdlet Get-proc di esempio per verificare se viene segnalato un errore:

- Avviare PowerShell e usare il cmdlet Get-proc per recuperare i processi denominati "TEST".

  ```powershell
  get-proc -name test
  ```

  Viene visualizzato l'output seguente.

  ```
  get-proc : Operation is not valid due to the current state of the object.
  At line:1 char:9
  + get-proc  <<<< -name test
  ```

## <a name="see-also"></a>Vedere anche

[Aggiunta di parametri che elaborano l'input della pipeline](./adding-parameters-that-process-pipeline-input.md)

[Aggiunta di parametri che elaborano l'input della riga di comando](./adding-parameters-that-process-command-line-input.md)

[Creazione del primo cmdlet](./creating-a-cmdlet-without-parameters.md)

[Estensione di tipi di oggetti e formattazione](/previous-versions/ms714665(v=vs.85))

[Come registrare cmdlet, provider e applicazioni host](/previous-versions/ms714644(v=vs.85))

[Riferimenti Windows PowerShell](../windows-powershell-reference.md)

[Esempi di cmdlet](./cmdlet-samples.md)

[System. Exception]: /dotnet/api/System.Exception
[System. Management. Automation. Preferenzaazione]: /dotnet/api/System.Management.Automation.ActionPreference
[System. Management. Automation. cmdlet. ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System. Management. Automation. cmdlet. WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System. Management. Automation. cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System. Management. Automation. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System. Management. Automation. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
