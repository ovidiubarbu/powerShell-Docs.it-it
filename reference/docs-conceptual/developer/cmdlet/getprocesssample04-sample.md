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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365710"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="8d9fe-102">Esempio di GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="8d9fe-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="8d9fe-103">In questo esempio viene illustrato come implementare un cmdlet che recupera i processi nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="8d9fe-104">Genera un errore non fatale se si verifica un errore durante il recupero di un processo.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="8d9fe-105">Questo cmdlet è una versione semplificata del cmdlet `Get-Process` fornito da Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="8d9fe-106">Come compilare l'esempio con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="8d9fe-107">Con Windows PowerShell 2,0 SDK installato, passare alla cartella GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="8d9fe-108">Il percorso predefinito è C:\Programmi (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="8d9fe-109">Fare doppio clic sull'icona del file di soluzione (con estensione sln).</span><span class="sxs-lookup"><span data-stu-id="8d9fe-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="8d9fe-110">Verrà aperto il progetto di esempio in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="8d9fe-111">Scegliere **Compila soluzione** dal menu **Compila**.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="8d9fe-112">La libreria per l'esempio verrà compilata nelle cartelle \bin o \bin\Debug predefinite.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="8d9fe-113">Per eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="8d9fe-113">How to run the sample</span></span>

1. <span data-ttu-id="8d9fe-114">Creare la cartella dei moduli seguente:</span><span class="sxs-lookup"><span data-stu-id="8d9fe-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="8d9fe-115">Copiare l'assembly di esempio nella cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="8d9fe-116">Avviare Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="8d9fe-117">Eseguire il comando seguente per caricare l'assembly in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8d9fe-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="8d9fe-118">Eseguire il comando seguente per eseguire il cmdlet:</span><span class="sxs-lookup"><span data-stu-id="8d9fe-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="8d9fe-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8d9fe-119">Requirements</span></span>

<span data-ttu-id="8d9fe-120">Questo esempio richiede Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8d9fe-121">Illustra</span><span class="sxs-lookup"><span data-stu-id="8d9fe-121">Demonstrates</span></span>

<span data-ttu-id="8d9fe-122">In questo esempio vengono illustrate le operazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="8d9fe-123">Dichiarazione di una classe di cmdlet mediante l'attributo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="8d9fe-124">Dichiarazione di un parametro del cmdlet mediante l'attributo Parameter.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="8d9fe-125">Specifica la posizione del parametro.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="8d9fe-126">Specifica che il parametro accetta input dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="8d9fe-127">L'input può essere tratto da un oggetto o da un valore di una proprietà di un oggetto il cui nome di proprietà corrisponde al nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="8d9fe-128">Dichiarazione di un attributo di convalida per l'input del parametro.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="8d9fe-129">Intercettare un errore non fatale e scrivere un messaggio di errore nel flusso di errori.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="8d9fe-130">Esempio</span><span class="sxs-lookup"><span data-stu-id="8d9fe-130">Example</span></span>

<span data-ttu-id="8d9fe-131">In questo esempio viene illustrato come creare un cmdlet che gestisce errori non fatali e scrive messaggi di errore nel flusso di errori.</span><span class="sxs-lookup"><span data-stu-id="8d9fe-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8d9fe-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8d9fe-132">See Also</span></span>

[<span data-ttu-id="8d9fe-133">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d9fe-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
