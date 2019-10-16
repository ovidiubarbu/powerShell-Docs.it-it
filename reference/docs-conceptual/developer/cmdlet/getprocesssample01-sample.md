---
title: Esempio GetProcessSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369730"
---
# <a name="getprocesssample01-sample"></a><span data-ttu-id="9bc42-102">Esempio di GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="9bc42-102">GetProcessSample01 Sample</span></span>

<span data-ttu-id="9bc42-103">In questo esempio viene illustrato come implementare un cmdlet che recupera i processi nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="9bc42-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="9bc42-104">Questo cmdlet è una versione semplificata del cmdlet `Get-Process` fornito da Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="9bc42-104">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="9bc42-105">Come compilare l'esempio usando Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9bc42-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="9bc42-106">Con Windows PowerShell 2,0 SDK installato, passare alla cartella GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="9bc42-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="9bc42-107">Il percorso predefinito è C:\Programmi (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="9bc42-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="9bc42-108">Fare doppio clic sull'icona del file di soluzione (con estensione sln).</span><span class="sxs-lookup"><span data-stu-id="9bc42-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="9bc42-109">Verrà aperto il progetto di esempio in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9bc42-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="9bc42-110">Scegliere **Compila soluzione**dal menu **Compila** .</span><span class="sxs-lookup"><span data-stu-id="9bc42-110">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="9bc42-111">La libreria per l'esempio verrà compilata nelle cartelle \bin o \bin\Debug predefinite.</span><span class="sxs-lookup"><span data-stu-id="9bc42-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="9bc42-112">Come eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="9bc42-112">How to run the sample</span></span>

1. <span data-ttu-id="9bc42-113">Aprire una finestra del prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="9bc42-113">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="9bc42-114">Passare alla directory contenente il file con estensione dll di esempio.</span><span class="sxs-lookup"><span data-stu-id="9bc42-114">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="9bc42-115">Eseguire installutil "GetProcessSample01. dll".</span><span class="sxs-lookup"><span data-stu-id="9bc42-115">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="9bc42-116">Avviare Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9bc42-116">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="9bc42-117">Eseguire il comando seguente per aggiungere lo snap-in alla Shell.</span><span class="sxs-lookup"><span data-stu-id="9bc42-117">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="9bc42-118">Immettere il comando seguente per eseguire il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9bc42-118">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="9bc42-119">Si tratta di un output di esempio risultante dalla procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="9bc42-119">This is a sample output that results from following these steps.</span></span>

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a><span data-ttu-id="9bc42-120">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9bc42-120">Requirements</span></span>

<span data-ttu-id="9bc42-121">Questo esempio richiede Windows PowerShell 1,0 o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="9bc42-121">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9bc42-122">Dimostra</span><span class="sxs-lookup"><span data-stu-id="9bc42-122">Demonstrates</span></span>

<span data-ttu-id="9bc42-123">In questo esempio vengono illustrate le operazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="9bc42-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="9bc42-124">Creazione di un cmdlet di esempio di base.</span><span class="sxs-lookup"><span data-stu-id="9bc42-124">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="9bc42-125">Definizione di una classe di cmdlet tramite l'attributo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9bc42-125">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="9bc42-126">Creazione di uno snap-in che funziona sia con Windows PowerShell 1,0 che con Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="9bc42-126">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="9bc42-127">Gli esempi successivi usano i moduli anziché gli snap-in in modo che richiedano Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="9bc42-127">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="9bc42-128">Esempio</span><span class="sxs-lookup"><span data-stu-id="9bc42-128">Example</span></span>

<span data-ttu-id="9bc42-129">In questo esempio viene illustrato come creare un cmdlet semplice e il relativo snap-in.</span><span class="sxs-lookup"><span data-stu-id="9bc42-129">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a><span data-ttu-id="9bc42-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9bc42-130">See Also</span></span>

[<span data-ttu-id="9bc42-131">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bc42-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)