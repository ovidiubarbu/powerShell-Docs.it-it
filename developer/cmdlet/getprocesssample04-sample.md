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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861877"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="34480-102">Esempio di GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="34480-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="34480-103">Questo esempio viene illustrato come implementare un cmdlet che recupera i processi nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="34480-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="34480-104">Se si verifica un errore durante il recupero di un processo, viene generato un errore non fatali.</span><span class="sxs-lookup"><span data-stu-id="34480-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="34480-105">Questo cmdlet è una versione semplificata del `Get-Process` cmdlet forniti da Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="34480-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="34480-106">Come compilare l'esempio utilizzando Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34480-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="34480-107">Con Windows PowerShell 2.0 SDK installato, passare alla cartella GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="34480-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="34480-108">Il percorso predefinito è C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="34480-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="34480-109">Fare doppio clic sull'icona per il file di soluzione (sln).</span><span class="sxs-lookup"><span data-stu-id="34480-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="34480-110">Verrà aperto il progetto di esempio in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34480-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="34480-111">Nel **compilare** dal menu **Compila soluzione**.</span><span class="sxs-lookup"><span data-stu-id="34480-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="34480-112">La libreria per il codice di esempio verrà compilata nelle cartelle \bin o \bin\Debug. predefinito.</span><span class="sxs-lookup"><span data-stu-id="34480-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="34480-113">Come eseguire il codice di esempio</span><span class="sxs-lookup"><span data-stu-id="34480-113">How to run the sample</span></span>

1. <span data-ttu-id="34480-114">Creare la cartella del modulo seguente:</span><span class="sxs-lookup"><span data-stu-id="34480-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="34480-115">Copiare l'assembly di esempio per la cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="34480-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="34480-116">Avviare Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34480-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="34480-117">Eseguire il comando seguente per caricare l'assembly in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="34480-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="34480-118">Eseguire il comando seguente per eseguire il cmdlet:</span><span class="sxs-lookup"><span data-stu-id="34480-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="34480-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="34480-119">Requirements</span></span>

<span data-ttu-id="34480-120">Questo esempio richiede Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="34480-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="34480-121">Illustra</span><span class="sxs-lookup"><span data-stu-id="34480-121">Demonstrates</span></span>

<span data-ttu-id="34480-122">In questo esempio viene illustrato quanto segue.</span><span class="sxs-lookup"><span data-stu-id="34480-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="34480-123">Dichiarazione di una classe cmdlet utilizzando l'attributo Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="34480-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="34480-124">Dichiarare un parametro di cmdlet tramite l'attributo di parametro.</span><span class="sxs-lookup"><span data-stu-id="34480-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="34480-125">Che specifica la posizione del parametro.</span><span class="sxs-lookup"><span data-stu-id="34480-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="34480-126">Specifica che il parametro accetta input dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="34480-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="34480-127">L'input può essere eseguita da un oggetto o un valore da una proprietà di un oggetto il cui nome di proprietà è identico al nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="34480-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="34480-128">Dichiarazione di un attributo di convalida per il parametro di input.</span><span class="sxs-lookup"><span data-stu-id="34480-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="34480-129">Intercettare un errore non fatali e la scrittura di un messaggio di errore nel flusso di errori.</span><span class="sxs-lookup"><span data-stu-id="34480-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="34480-130">Esempio</span><span class="sxs-lookup"><span data-stu-id="34480-130">Example</span></span>

<span data-ttu-id="34480-131">In questo esempio viene illustrato come creare un cmdlet che gestisce gli errori non fatali e scrive i messaggi di errore nel flusso di errori.</span><span class="sxs-lookup"><span data-stu-id="34480-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="34480-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="34480-132">See Also</span></span>

[<span data-ttu-id="34480-133">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="34480-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
