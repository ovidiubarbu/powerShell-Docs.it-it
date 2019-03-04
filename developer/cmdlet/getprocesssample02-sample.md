---
title: GetProcessSample02 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859857"
---
# <a name="getprocesssample02-sample"></a>Esempio di GetProcessSample02

In questo esempio viene illustrato come scrivere un cmdlet che recupera i processi nel computer locale. Fornisce un `Name` parametro che può essere usato per specificare i processi da recuperare. Questo cmdlet è una versione semplificata del `Get-Process` cmdlet forniti da Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Come compilare l'esempio utilizzando Visual Studio.

1. Con Windows PowerShell 2.0 SDK installato, passare alla cartella GetProcessSample02. Il percorso predefinito è C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.

2. Fare doppio clic sull'icona per il file di soluzione (sln). Verrà aperto il progetto di esempio in Visual Studio.

3. Nel **compilare** dal menu **Compila soluzione**.

    La libreria per il codice di esempio verrà compilata nelle cartelle \bin o \bin\Debug. predefinito.

### <a name="how-to-run-the-sample"></a>Come eseguire il codice di esempio

1. Creare la cartella del modulo seguente:

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. Copiare l'assembly di esempio per la cartella del modulo.

3. Avviare Windows PowerShell.

4. Eseguire il comando seguente per caricare l'assembly in Windows PowerShell:

    `import-module getprossessample02`

5. Eseguire il comando seguente per eseguire il cmdlet:

    `get-proc`

## <a name="requirements"></a>Requisiti

Questo esempio richiede Windows PowerShell 2.0.

## <a name="demonstrates"></a>Illustra

In questo esempio viene illustrato quanto segue.

- Dichiarazione di una classe cmdlet utilizzando l'attributo Cmdlet.

- Dichiarare un parametro di cmdlet tramite l'attributo di parametro.

- Che specifica la posizione del parametro.

- Dichiarazione di un attributo di convalida per il parametro di input.

## <a name="example"></a>Esempio

In questo esempio viene illustrata un'implementazione del cmdlet Get-Process che include un `Name` parametro.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
