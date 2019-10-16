---
title: Esempio Events01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 8f745cc0e5ef6db7a6bbdf39d826103f3b8a98ce
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369740"
---
# <a name="events01-sample"></a><span data-ttu-id="bd9e0-102">Esempio di Events01</span><span class="sxs-lookup"><span data-stu-id="bd9e0-102">Events01 Sample</span></span>

<span data-ttu-id="bd9e0-103">In questo esempio viene illustrato come creare un cmdlet che consente all'utente di eseguire la registrazione per gli eventi generati da [System. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="bd9e0-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>
<span data-ttu-id="bd9e0-104">Con questo cmdlet, gli utenti possono registrare un'azione da eseguire quando viene creato un file in una directory specifica.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span>
<span data-ttu-id="bd9e0-105">Questo esempio deriva dalla classe di base [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .</span><span class="sxs-lookup"><span data-stu-id="bd9e0-105">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="bd9e0-106">Come compilare l'esempio usando Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="bd9e0-107">Con Windows PowerShell 2,0 SDK installato, passare alla cartella Events01.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span>
   <span data-ttu-id="bd9e0-108">Il percorso predefinito è `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-108">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="bd9e0-109">Fare doppio clic sull'icona del file di soluzione (con estensione sln).</span><span class="sxs-lookup"><span data-stu-id="bd9e0-109">Double-click the icon for the solution (.sln) file.</span></span>
   <span data-ttu-id="bd9e0-110">Verrà aperto il progetto di esempio in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="bd9e0-111">Scegliere **Compila soluzione**dal menu **Compila** .</span><span class="sxs-lookup"><span data-stu-id="bd9e0-111">In the **Build** menu, select **Build Solution**.</span></span>
   <span data-ttu-id="bd9e0-112">La libreria per l'esempio verrà compilata nelle cartelle predefinite `\bin` o `\bin\debug`.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-112">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="bd9e0-113">Come eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="bd9e0-113">How to run the sample</span></span>

1. <span data-ttu-id="bd9e0-114">Creare la cartella dei moduli seguente:</span><span class="sxs-lookup"><span data-stu-id="bd9e0-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="bd9e0-115">Copiare il file di libreria per l'esempio nella cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="bd9e0-116">Avviare Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="bd9e0-117">Eseguire il comando seguente per caricare il cmdlet in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bd9e0-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="bd9e0-118">Usare il cmdlet Register-FileSystemEvent per registrare un'azione che scriverà un messaggio quando viene creato un file nella directory TEMP.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="bd9e0-119">Creare un file nella directory TEMP e notare che l'azione viene eseguita (il messaggio viene visualizzato).</span><span class="sxs-lookup"><span data-stu-id="bd9e0-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="bd9e0-120">Si tratta di un output di esempio risultante dalla procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="bd9e0-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bd9e0-121">Requirements</span></span>

<span data-ttu-id="bd9e0-122">Questo esempio richiede Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="bd9e0-123">Dimostra</span><span class="sxs-lookup"><span data-stu-id="bd9e0-123">Demonstrates</span></span>

<span data-ttu-id="bd9e0-124">In questo esempio vengono illustrate le operazioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-124">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="bd9e0-125">Come scrivere un cmdlet per la registrazione degli eventi</span><span class="sxs-lookup"><span data-stu-id="bd9e0-125">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="bd9e0-126">Il cmdlet deriva dalla classe [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) , che fornisce il supporto per i parametri comuni ai cmdlet `Register-*Event`.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span>
<span data-ttu-id="bd9e0-127">I cmdlet che derivano da [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) devono solo definire i propri parametri specifici ed eseguire l'override dei metodi astratti `GetSourceObject` e `GetSourceObjectEventName`.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="bd9e0-128">Esempio</span><span class="sxs-lookup"><span data-stu-id="bd9e0-128">Example</span></span>

<span data-ttu-id="bd9e0-129">In questo esempio viene illustrato come eseguire la registrazione per gli eventi generati da [System. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="bd9e0-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="bd9e0-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bd9e0-130">See Also</span></span>

[<span data-ttu-id="bd9e0-131">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd9e0-131">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)