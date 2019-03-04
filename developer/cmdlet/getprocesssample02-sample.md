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
# <a name="getprocesssample02-sample"></a><span data-ttu-id="186c9-102">Esempio di GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="186c9-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="186c9-103">In questo esempio viene illustrato come scrivere un cmdlet che recupera i processi nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="186c9-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="186c9-104">Fornisce un `Name` parametro che può essere usato per specificare i processi da recuperare.</span><span class="sxs-lookup"><span data-stu-id="186c9-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="186c9-105">Questo cmdlet è una versione semplificata del `Get-Process` cmdlet forniti da Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="186c9-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="186c9-106">Come compilare l'esempio utilizzando Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="186c9-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="186c9-107">Con Windows PowerShell 2.0 SDK installato, passare alla cartella GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="186c9-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="186c9-108">Il percorso predefinito è C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="186c9-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="186c9-109">Fare doppio clic sull'icona per il file di soluzione (sln).</span><span class="sxs-lookup"><span data-stu-id="186c9-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="186c9-110">Verrà aperto il progetto di esempio in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="186c9-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="186c9-111">Nel **compilare** dal menu **Compila soluzione**.</span><span class="sxs-lookup"><span data-stu-id="186c9-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="186c9-112">La libreria per il codice di esempio verrà compilata nelle cartelle \bin o \bin\Debug. predefinito.</span><span class="sxs-lookup"><span data-stu-id="186c9-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="186c9-113">Come eseguire il codice di esempio</span><span class="sxs-lookup"><span data-stu-id="186c9-113">How to run the sample</span></span>

1. <span data-ttu-id="186c9-114">Creare la cartella del modulo seguente:</span><span class="sxs-lookup"><span data-stu-id="186c9-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="186c9-115">Copiare l'assembly di esempio per la cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="186c9-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="186c9-116">Avviare Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="186c9-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="186c9-117">Eseguire il comando seguente per caricare l'assembly in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="186c9-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="186c9-118">Eseguire il comando seguente per eseguire il cmdlet:</span><span class="sxs-lookup"><span data-stu-id="186c9-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="186c9-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="186c9-119">Requirements</span></span>

<span data-ttu-id="186c9-120">Questo esempio richiede Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="186c9-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="186c9-121">Illustra</span><span class="sxs-lookup"><span data-stu-id="186c9-121">Demonstrates</span></span>

<span data-ttu-id="186c9-122">In questo esempio viene illustrato quanto segue.</span><span class="sxs-lookup"><span data-stu-id="186c9-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="186c9-123">Dichiarazione di una classe cmdlet utilizzando l'attributo Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="186c9-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="186c9-124">Dichiarare un parametro di cmdlet tramite l'attributo di parametro.</span><span class="sxs-lookup"><span data-stu-id="186c9-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="186c9-125">Che specifica la posizione del parametro.</span><span class="sxs-lookup"><span data-stu-id="186c9-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="186c9-126">Dichiarazione di un attributo di convalida per il parametro di input.</span><span class="sxs-lookup"><span data-stu-id="186c9-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="186c9-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="186c9-127">Example</span></span>

<span data-ttu-id="186c9-128">In questo esempio viene illustrata un'implementazione del cmdlet Get-Process che include un `Name` parametro.</span><span class="sxs-lookup"><span data-stu-id="186c9-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="186c9-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="186c9-129">See Also</span></span>

[<span data-ttu-id="186c9-130">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="186c9-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
