---
title: L'importazione e richiamare un flusso di lavoro di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854587"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Importazione e richiamo di un flusso di lavoro di Windows PowerShell

3 di Windows PowerShell, consente di importare e richiamare un flusso di lavoro che viene fornito come un modulo di Windows PowerShell. Per informazioni sui moduli di Windows PowerShell, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).

Il [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)classe viene utilizzata come un proxy lato client per gli oggetti del flusso di lavoro nel server. La procedura seguente illustra come usare un [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)oggetto sul quale richiamare un flusso di lavoro.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>Creazione di un oggetto PSJobProxy per eseguire i comandi del flusso di lavoro in un server remoto.

1. Creare un [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)oggetto per creare una connessione a uno spazio di esecuzione remoto.

2. Impostare il [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) proprietà del [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)oggetto `Microsoft.PowerShell.Workflow` a specificare un endpoint di Windows PowerShell.

3. Creare uno spazio di esecuzione che usa la connessione creata completando i passaggi precedenti.

4. Creare un [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)dell'oggetto e impostare relativo [System.Management.Automation.Powershell.Runspace*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) proprietà allo spazio di esecuzione creato nel passaggio precedente.

5. Importare il modulo del flusso di lavoro e i relativi comandi nel [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).

6. Creare un [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) dell'oggetto e usarla per eseguire i comandi del flusso di lavoro nel server remoto.

## <a name="example"></a>Esempio

Esempio di codice seguente viene illustrato come richiamare un flusso di lavoro utilizzando Windows PowerShell.

Questo esempio richiede Windows PowerShell 3.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;
using System.Management.Automation.Runspaces;

namespace WorkflowHostTest
{

class Program
    {
        static void Main(string[] args)
        {
            if (args.Length == 0)
            {
                Console.WriteLine("Specify path to Workflow module");
                return;
            }

            string moduleFile = args[0];

            Console.Write("Creating Remote runspace connection...");
            WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

            //Set the shellURI to workflow endpoint Microsoft.PowerShell.Workflow
            connectionInfo.ShellUri = "Microsoft.PowerShell.Workflow";

            //Create and open a runspace.
            Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo);
            runspace.Open();
            Console.WriteLine("done");

            PowerShell powershell = PowerShell.Create();
            powershell.Runspace = runspace;
            Console.Write("Setting $VerbosePreference=\"Continue\"...");
            powershell.AddScript("$VerbosePreference=\"Continue\"");
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Importing Workflow module...");
            powershell.Commands.Clear();

            //Import the module in to the PowerShell runspace. A XAML file could also be imported directly by using Import-Module.
            powershell.AddCommand("Import-Module").AddArgument(moduleFile);
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Creating job proxy...");
            powershell.Commands.Clear();
            powershell.AddCommand("Get-Proc").AddArgument("*");
            PSJobProxy job = powershell.AsJobProxy();
            Console.WriteLine("done");

                Console.WriteLine();
                Console.WriteLine("Using job proxy and performing operations...");
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine("Starting job...");
                job.StartJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());

                // use blocking enumerator to wait for objects until job finishes
                job.Output.BlockingEnumerator = true;
                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                // wait for a random time before attempting to stop job
                Random random = new Random();
                int time = random.Next(1, 10);
                Console.Write("Sleeping for {0} seconds when job is running on another thread...", time);
                System.Threading.Thread.Sleep(time * 1000);
                Console.WriteLine("done");
                Console.WriteLine("Stopping job...");
                job.StopJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine();
                job.Finished.WaitOne();
                Console.WriteLine("Output from job");
                Console.WriteLine("---------------");

                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                Console.WriteLine();
                Console.WriteLine("Verbose messages from job");
                Console.WriteLine("-------------------------");
                foreach (VerboseRecord v in job.Verbose)
                {
                    Console.WriteLine(v.Message);
                }

            runspace.Close();
        }
    }
}

```