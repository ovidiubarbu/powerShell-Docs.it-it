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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080340"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a><span data-ttu-id="1bd4a-102">Importazione e richiamo di un flusso di lavoro di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1bd4a-102">Importing and Invoking a Windows PowerShell Workflow</span></span>

<span data-ttu-id="1bd4a-103">3 di Windows PowerShell, consente di importare e richiamare un flusso di lavoro che viene fornito come un modulo di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1bd4a-103">Windows PowerShell 3, allows you to import and invoke a workflow that is packaged as a Windows PowerShell module.</span></span> <span data-ttu-id="1bd4a-104">Per informazioni sui moduli di Windows PowerShell, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="1bd4a-104">For information about Windows PowerShell modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

<span data-ttu-id="1bd4a-105">Il [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)classe viene utilizzata come un proxy lato client per gli oggetti del flusso di lavoro nel server.</span><span class="sxs-lookup"><span data-stu-id="1bd4a-105">The [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)class is used as a client side proxy for workflow objects on the server.</span></span> <span data-ttu-id="1bd4a-106">La procedura seguente illustra come usare un [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)oggetto sul quale richiamare un flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="1bd4a-106">The following procedure explains how to use a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)object to invoke a workflow.</span></span>

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a><span data-ttu-id="1bd4a-107">Creazione di un oggetto PSJobProxy per eseguire i comandi del flusso di lavoro in un server remoto.</span><span class="sxs-lookup"><span data-stu-id="1bd4a-107">Creating a PSJobProxy object to execute workflow commands on a remote server.</span></span>

1. <span data-ttu-id="1bd4a-108">Creare un [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)oggetto per creare una connessione a uno spazio di esecuzione remoto.</span><span class="sxs-lookup"><span data-stu-id="1bd4a-108">Create an [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to create a connection to a remote runspace.</span></span>

2. <span data-ttu-id="1bd4a-109">Impostare il [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) proprietà del [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)oggetto `Microsoft.PowerShell.Workflow` a specificare un endpoint di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1bd4a-109">Set the [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) property of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to `Microsoft.PowerShell.Workflow` to specify a Windows PowerShell endpoint.</span></span>

3. <span data-ttu-id="1bd4a-110">Creare uno spazio di esecuzione che usa la connessione creata completando i passaggi precedenti.</span><span class="sxs-lookup"><span data-stu-id="1bd4a-110">Create a runspace that uses the connection created by completing the previous steps.</span></span>

4. <span data-ttu-id="1bd4a-111">Creare un [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)dell'oggetto e impostare relativo [System.Management.Automation.Powershell.Runspace\*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) proprietà allo spazio di esecuzione creato nel passaggio precedente.</span><span class="sxs-lookup"><span data-stu-id="1bd4a-111">Create a [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)object and set its [System.Management.Automation.Powershell.Runspace\*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) property to the runspace created in the previous step.</span></span>

5. <span data-ttu-id="1bd4a-112">Importare il modulo del flusso di lavoro e i relativi comandi nel [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).</span><span class="sxs-lookup"><span data-stu-id="1bd4a-112">Import the workflow module and its commands into the [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).</span></span>

6. <span data-ttu-id="1bd4a-113">Creare un [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) dell'oggetto e usarla per eseguire i comandi del flusso di lavoro nel server remoto.</span><span class="sxs-lookup"><span data-stu-id="1bd4a-113">Create a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) object and use it to execute workflow commands on the remote server.</span></span>

## <a name="example"></a><span data-ttu-id="1bd4a-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="1bd4a-114">Example</span></span>

<span data-ttu-id="1bd4a-115">Esempio di codice seguente viene illustrato come richiamare un flusso di lavoro utilizzando Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1bd4a-115">The following code example demonstrates how to invoke a workflow by using Windows PowerShell.</span></span>

<span data-ttu-id="1bd4a-116">Questo esempio richiede Windows PowerShell 3.</span><span class="sxs-lookup"><span data-stu-id="1bd4a-116">This example requires Windows PowerShell 3.</span></span>

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