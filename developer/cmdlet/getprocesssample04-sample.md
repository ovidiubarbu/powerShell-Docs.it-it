---
title: Esempio GetProcessSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068029"
---
# <a name="getprocesssample04-sample"></a>Esempio di GetProcessSample04

Questo esempio viene illustrato come implementare un cmdlet che recupera i processi nel computer locale. Se si verifica un errore durante il recupero di un processo, viene generato un errore non fatali. Questo cmdlet è una versione semplificata del `Get-Process` cmdlet forniti da Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Come compilare l'esempio utilizzando Visual Studio.

1. Con Windows PowerShell 2.0 SDK installato, passare alla cartella GetProcessSample04. Il percorso predefinito è C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.

2. Fare doppio clic sull'icona per il file di soluzione (sln). Verrà aperto il progetto di esempio in Visual Studio.

3. Nel **compilare** dal menu **Compila soluzione**.

    La libreria per il codice di esempio verrà compilata nelle cartelle \bin o \bin\Debug. predefinito.

### <a name="how-to-run-the-sample"></a>Come eseguire il codice di esempio

1. Creare la cartella del modulo seguente:

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. Copiare l'assembly di esempio per la cartella del modulo.

3. Avviare Windows PowerShell.

4. Eseguire il comando seguente per caricare l'assembly in Windows PowerShell:

    `Import-module getprossessample04`

5. Eseguire il comando seguente per eseguire il cmdlet:

    `get-proc`

## <a name="requirements"></a>Requisiti

Questo esempio richiede Windows PowerShell 2.0.

## <a name="demonstrates"></a>Di seguito viene illustrato

In questo esempio viene illustrato quanto segue.

- Dichiarazione di una classe cmdlet utilizzando l'attributo Cmdlet.

- Dichiarare un parametro di cmdlet tramite l'attributo di parametro.

- Che specifica la posizione del parametro.

- Specifica che il parametro accetta input dalla pipeline. L'input può essere eseguita da un oggetto o un valore da una proprietà di un oggetto il cui nome di proprietà è identico al nome del parametro.

- Dichiarazione di un attributo di convalida per il parametro di input.

- Intercettare un errore non fatali e la scrittura di un messaggio di errore nel flusso di errori.

## <a name="example"></a>Esempio

In questo esempio viene illustrato come creare un cmdlet che gestisce gli errori non fatali e scrive i messaggi di errore nel flusso di errori.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes specified by the Name
      /// parameter. Then, the WriteObject method writes the
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
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
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
