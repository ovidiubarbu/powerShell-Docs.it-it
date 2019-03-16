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
ms.openlocfilehash: c9963819f1842d1245735dabc487babaa566c160
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057162"
---
# <a name="events01-sample"></a>Esempio di Events01

In questo esempio viene illustrato come creare un cmdlet che consente all'utente di registrare gli eventi che vengono generati [FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher). Con questo cmdlet, gli utenti possono registrare un'azione da eseguire quando viene creato un file in una directory specifica. In questo esempio deriva dal [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) classe di base.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Come compilare l'esempio mediante Visual Studio.

1. Con Windows PowerShell 2.0 SDK installato, passare alla cartella Events01. Il percorso predefinito è C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.

2. Fare doppio clic sull'icona per il file di soluzione (sln). Verrà aperto il progetto di esempio in Microsoft Visual Studio.

3. Nel **compilare** dal menu **Compila soluzione**.

    La libreria per il codice di esempio verrà compilata nelle cartelle \bin o \bin\Debug. predefinito.

### <a name="how-to-run-the-sample"></a>Come eseguire il codice di esempio

1. Creare la cartella del modulo seguente:

    `[user]/documents/windowspowershell/modules/events01`

2. Copiare il file di libreria per il codice di esempio per la cartella del modulo.

3. Avviare Windows PowerShell.

4. Eseguire il comando seguente per caricare i cmdlet in Windows PowerShell:

    ```powershell
    import-module events01
    ```

5. Usare il cmdlet Register-FileSystemEvent per registrare un'azione che verrà scritto un messaggio quando viene creato un file nella directory TEMP.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. Creare un file nella directory TEMP e si noti che l'azione viene eseguita (viene visualizzato il messaggio).

Questo è un esempio di output risultante seguendo questa procedura.

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

## <a name="requirements"></a>Requisiti

Questo esempio richiede Windows PowerShell 2.0.

## <a name="demonstrates"></a>Illustra

In questo esempio viene illustrato quanto segue.

- Come scrivere un cmdlet per la registrazione eventi. Il cmdlet deriva dal [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) (classe), che fornisce il supporto per i parametri comuni di Register-* i cmdlet di eventi. I cmdlet che derivano da [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) necessario solo definire i relativi parametri specifici ed eseguire l'override di `GetSourceObject` e `GetSourceObjectEventName` metodi astratti.

## <a name="example"></a>Esempio

In questo esempio viene illustrato come effettuare la registrazione per gli eventi generati da [FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).

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

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)