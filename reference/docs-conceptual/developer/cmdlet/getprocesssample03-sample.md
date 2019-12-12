---
title: Esempio GetProcessSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369710"
---
# <a name="getprocesssample03-sample"></a>Esempio di GetProcessSample03

In questo esempio viene illustrato come implementare un cmdlet che recupera i processi nel computer locale. Fornisce un `Name` parametro che può accettare un oggetto dalla pipeline o un valore di una proprietà di un oggetto il cui nome di proprietà corrisponde al nome del parametro. Questo cmdlet è una versione semplificata del cmdlet `Get-Process` fornito da Windows PowerShell 2,0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Come compilare l'esempio con Visual Studio.

1. Con Windows PowerShell 2,0 SDK installato, passare alla cartella GetProcessSample03. Il percorso predefinito è C:\Programmi (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.

2. Fare doppio clic sull'icona del file di soluzione (con estensione sln). Verrà aperto il progetto di esempio in Visual Studio.

3. Scegliere **Compila soluzione** dal menu **Compila**.

    La libreria per l'esempio verrà compilata nelle cartelle \bin o \bin\Debug predefinite.

### <a name="how-to-run-the-sample"></a>Per eseguire l'esempio

1. Creare la cartella dei moduli seguente:

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. Copiare l'assembly di esempio nella cartella del modulo.

3. Avviare Windows PowerShell.

4. Eseguire il comando seguente per caricare l'assembly in Windows PowerShell:

    `Import-module getprossessample03`

5. Eseguire il comando seguente per eseguire il cmdlet:

    `get-proc`

## <a name="requirements"></a>Requisiti

Questo esempio richiede Windows PowerShell 2,0.

## <a name="demonstrates"></a>Illustra

In questo esempio vengono illustrate le operazioni seguenti.

- Dichiarazione di una classe di cmdlet mediante l'attributo cmdlet.

- Dichiarazione di un parametro del cmdlet mediante l'attributo Parameter.

- Specifica la posizione del parametro.

- Specifica che il parametro accetta input dalla pipeline. L'input può essere tratto da un oggetto o da un valore di una proprietà di un oggetto il cui nome di proprietà corrisponde al nome del parametro.

- Dichiarazione di un attributo di convalida per l'input del parametro.

## <a name="example"></a>Esempio

Questo esempio illustra un'implementazione del cmdlet Get-proc che include un parametro `Name` che accetta l'input dalla pipeline.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
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
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
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
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
