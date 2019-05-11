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
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229295"
---
# <a name="events01-sample"></a><span data-ttu-id="140dc-102">Esempio di Events01</span><span class="sxs-lookup"><span data-stu-id="140dc-102">Events01 Sample</span></span>

<span data-ttu-id="140dc-103">In questo esempio viene illustrato come creare un cmdlet che consente all'utente di registrare gli eventi che vengono generati [FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="140dc-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>
<span data-ttu-id="140dc-104">Con questo cmdlet, gli utenti possono registrare un'azione da eseguire quando viene creato un file in una directory specifica.</span><span class="sxs-lookup"><span data-stu-id="140dc-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span>
<span data-ttu-id="140dc-105">In questo esempio deriva dal [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe di base.</span><span class="sxs-lookup"><span data-stu-id="140dc-105">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="140dc-106">Come compilare l'esempio mediante Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="140dc-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="140dc-107">Con Windows PowerShell 2.0 SDK installato, passare alla cartella Events01.</span><span class="sxs-lookup"><span data-stu-id="140dc-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span>
   <span data-ttu-id="140dc-108">Il percorso predefinito è `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span><span class="sxs-lookup"><span data-stu-id="140dc-108">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="140dc-109">Fare doppio clic sull'icona per il file di soluzione (sln).</span><span class="sxs-lookup"><span data-stu-id="140dc-109">Double-click the icon for the solution (.sln) file.</span></span>
   <span data-ttu-id="140dc-110">Verrà aperto il progetto di esempio in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="140dc-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="140dc-111">Nel **compilare** dal menu **Compila soluzione**.</span><span class="sxs-lookup"><span data-stu-id="140dc-111">In the **Build** menu, select **Build Solution**.</span></span>
   <span data-ttu-id="140dc-112">La libreria per il codice di esempio verrà compilata nel valore predefinito `\bin` o `\bin\debug` cartelle.</span><span class="sxs-lookup"><span data-stu-id="140dc-112">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="140dc-113">Come eseguire il codice di esempio</span><span class="sxs-lookup"><span data-stu-id="140dc-113">How to run the sample</span></span>

1. <span data-ttu-id="140dc-114">Creare la cartella del modulo seguente:</span><span class="sxs-lookup"><span data-stu-id="140dc-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="140dc-115">Copiare il file di libreria per il codice di esempio per la cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="140dc-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="140dc-116">Avviare Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="140dc-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="140dc-117">Eseguire il comando seguente per caricare i cmdlet in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="140dc-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="140dc-118">Usare il cmdlet Register-FileSystemEvent per registrare un'azione che verrà scritto un messaggio quando viene creato un file nella directory TEMP.</span><span class="sxs-lookup"><span data-stu-id="140dc-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="140dc-119">Creare un file nella directory TEMP e si noti che l'azione viene eseguita (viene visualizzato il messaggio).</span><span class="sxs-lookup"><span data-stu-id="140dc-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="140dc-120">Questo è un esempio di output risultante seguendo questa procedura.</span><span class="sxs-lookup"><span data-stu-id="140dc-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="140dc-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="140dc-121">Requirements</span></span>

<span data-ttu-id="140dc-122">Questo esempio richiede Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="140dc-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="140dc-123">Di seguito viene illustrato</span><span class="sxs-lookup"><span data-stu-id="140dc-123">Demonstrates</span></span>

<span data-ttu-id="140dc-124">In questo esempio viene illustrato quanto segue.</span><span class="sxs-lookup"><span data-stu-id="140dc-124">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="140dc-125">Come scrivere un cmdlet per la registrazione eventi</span><span class="sxs-lookup"><span data-stu-id="140dc-125">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="140dc-126">Il cmdlet deriva dal [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) (classe), che fornisce il supporto per i parametri comuni per la `Register-*Event` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="140dc-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span>
<span data-ttu-id="140dc-127">I cmdlet che derivano da [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) necessario solo definire i relativi parametri specifici ed eseguire l'override di `GetSourceObject` e `GetSourceObjectEventName` metodi astratti.</span><span class="sxs-lookup"><span data-stu-id="140dc-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="140dc-128">Esempio</span><span class="sxs-lookup"><span data-stu-id="140dc-128">Example</span></span>

<span data-ttu-id="140dc-129">In questo esempio viene illustrato come effettuare la registrazione per gli eventi generati da [FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="140dc-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="140dc-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="140dc-130">See Also</span></span>

[<span data-ttu-id="140dc-131">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="140dc-131">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)