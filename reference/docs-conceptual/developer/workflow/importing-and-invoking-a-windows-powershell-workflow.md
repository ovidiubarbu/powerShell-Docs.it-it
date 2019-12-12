---
title: Importazione e richiamo di un flusso di lavoro di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366040"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Importazione e richiamo di un flusso di lavoro di Windows PowerShell

Windows PowerShell 3 consente di importare e richiamare un flusso di lavoro incluso in un pacchetto come modulo di Windows PowerShell. Per informazioni sui moduli di Windows PowerShell, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).

La classe [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)viene utilizzata come proxy sul lato client per gli oggetti del flusso di lavoro nel server. Nella procedura seguente viene illustrato come utilizzare un oggetto [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)per richiamare un flusso di lavoro.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>Creazione di un oggetto PSJobProxy per l'esecuzione di comandi del flusso di lavoro in un server remoto.

1. Creare un oggetto [System. Management. Automation. Runspaces. WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)per creare una connessione a un spazio remoto.

2. Impostare la proprietà [System. Management. Automation. Runspaces. WSManConnectionInfo. Shelluri *](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) dell'oggetto [System. Management. Automation. Runspaces. WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)su `Microsoft.PowerShell.Workflow` per specificare un endpoint di Windows PowerShell.

3. Creare un spazio che usa la connessione creata completando i passaggi precedenti.

4. Creare un oggetto [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell)e impostare la proprietà [System. Management. Automation. PowerShell. spazio *](/dotnet/api/System.Management.Automation.PowerShell.Runspace) su spazio creato nel passaggio precedente.

5. Importare il modulo del flusso di lavoro e i relativi comandi in [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell).

6. Creare un oggetto [System. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) e usarlo per eseguire i comandi del flusso di lavoro nel server remoto.

## <a name="example"></a>Esempio

Nell'esempio di codice riportato di seguito viene illustrato come richiamare un flusso di lavoro utilizzando Windows PowerShell.

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