---
title: Esempio GetProcessSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364570"
---
# <a name="getprocesssample02-sample"></a>Esempio di GetProcessSample02

In questo esempio viene illustrato come scrivere un cmdlet che recupera i processi nel computer locale. Fornisce un `Name` parametro che può essere usato per specificare i processi da recuperare. Questo cmdlet è una versione semplificata del cmdlet `Get-Process` fornito da Windows PowerShell 2,0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Come compilare l'esempio con Visual Studio.

1. Con Windows PowerShell 2,0 SDK installato, passare alla cartella GetProcessSample02. Il percorso predefinito è C:\Programmi (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.

2. Fare doppio clic sull'icona del file di soluzione (con estensione sln). Verrà aperto il progetto di esempio in Visual Studio.

3. Scegliere **Compila soluzione** dal menu **Compila**.

    La libreria per l'esempio verrà compilata nelle cartelle \bin o \bin\Debug predefinite.

### <a name="how-to-run-the-sample"></a>Per eseguire l'esempio

1. Creare la cartella dei moduli seguente:

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. Copiare l'assembly di esempio nella cartella del modulo.

3. Avviare Windows PowerShell.

4. Eseguire il comando seguente per caricare l'assembly in Windows PowerShell:

    `import-module getprossessample02`

5. Eseguire il comando seguente per eseguire il cmdlet:

    `get-proc`

## <a name="requirements"></a>Requisiti

Questo esempio richiede Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustra

In questo esempio vengono illustrate le operazioni seguenti.

- Dichiarazione di una classe di cmdlet mediante l'attributo cmdlet.

- Dichiarazione di un parametro del cmdlet mediante l'attributo Parameter.

- Specifica la posizione del parametro.

- Dichiarazione di un attributo di convalida per l'input del parametro.

## <a name="example"></a>Esempio

Questo esempio illustra un'implementazione del cmdlet Get-proc che include un parametro `Name`.

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
