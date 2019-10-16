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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364570"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="a3934-102">Esempio di GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="a3934-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="a3934-103">In questo esempio viene illustrato come scrivere un cmdlet che recupera i processi nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="a3934-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="a3934-104">Fornisce un parametro `Name` che può essere usato per specificare i processi da recuperare.</span><span class="sxs-lookup"><span data-stu-id="a3934-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="a3934-105">Questo cmdlet è una versione semplificata del cmdlet `Get-Process` fornito da Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="a3934-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="a3934-106">Come compilare l'esempio con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a3934-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="a3934-107">Con Windows PowerShell 2,0 SDK installato, passare alla cartella GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="a3934-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="a3934-108">Il percorso predefinito è C:\Programmi (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="a3934-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="a3934-109">Fare doppio clic sull'icona del file di soluzione (con estensione sln).</span><span class="sxs-lookup"><span data-stu-id="a3934-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="a3934-110">Verrà aperto il progetto di esempio in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a3934-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="a3934-111">Scegliere **Compila soluzione**dal menu **Compila** .</span><span class="sxs-lookup"><span data-stu-id="a3934-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="a3934-112">La libreria per l'esempio verrà compilata nelle cartelle \bin o \bin\Debug predefinite.</span><span class="sxs-lookup"><span data-stu-id="a3934-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="a3934-113">Come eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="a3934-113">How to run the sample</span></span>

1. <span data-ttu-id="a3934-114">Creare la cartella dei moduli seguente:</span><span class="sxs-lookup"><span data-stu-id="a3934-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="a3934-115">Copiare l'assembly di esempio nella cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="a3934-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="a3934-116">Avviare Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3934-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="a3934-117">Eseguire il comando seguente per caricare l'assembly in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a3934-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="a3934-118">Eseguire il comando seguente per eseguire il cmdlet:</span><span class="sxs-lookup"><span data-stu-id="a3934-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="a3934-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a3934-119">Requirements</span></span>

<span data-ttu-id="a3934-120">Questo esempio richiede Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="a3934-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a3934-121">Dimostra</span><span class="sxs-lookup"><span data-stu-id="a3934-121">Demonstrates</span></span>

<span data-ttu-id="a3934-122">In questo esempio vengono illustrate le operazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="a3934-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="a3934-123">Dichiarazione di una classe di cmdlet mediante l'attributo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3934-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="a3934-124">Dichiarazione di un parametro del cmdlet mediante l'attributo Parameter.</span><span class="sxs-lookup"><span data-stu-id="a3934-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="a3934-125">Specifica la posizione del parametro.</span><span class="sxs-lookup"><span data-stu-id="a3934-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="a3934-126">Dichiarazione di un attributo di convalida per l'input del parametro.</span><span class="sxs-lookup"><span data-stu-id="a3934-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="a3934-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="a3934-127">Example</span></span>

<span data-ttu-id="a3934-128">Questo esempio illustra un'implementazione del cmdlet Get-proc che include un parametro `Name`.</span><span class="sxs-lookup"><span data-stu-id="a3934-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a3934-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a3934-129">See Also</span></span>

[<span data-ttu-id="a3934-130">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3934-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
