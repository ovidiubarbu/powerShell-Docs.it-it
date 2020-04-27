---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Creazione di una pipeline di integrazione continua e distribuzione continua con DSC
ms.openlocfilehash: 2d049cd640f0df9b018a88ad106e59dbeed7bcee
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954238"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="4859b-103">Creazione di una pipeline di integrazione continua e distribuzione continua con DSC</span><span class="sxs-lookup"><span data-stu-id="4859b-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="4859b-104">In questo esempio viene illustrato come creare una pipeline di integrazione continua e distribuzione continua (CI/CD) tramite PowerShell, DSC, Pester e Visual Studio Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="4859b-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="4859b-105">Dopo averla creata e configurata, è possibile usare la pipeline per eseguire una distribuzione, una configurazione e un test completi di un server DNS e dei record host associati.</span><span class="sxs-lookup"><span data-stu-id="4859b-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="4859b-106">Questo processo simula la prima parte di una pipeline da usare in un ambiente di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="4859b-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="4859b-107">Una pipeline CI/CD automatizzata consente di aggiornare il software in modo più rapido e affidabile, assicurandosi che tutto il codice venga testato e che una compilazione corrente del codice sia sempre disponibile.</span><span class="sxs-lookup"><span data-stu-id="4859b-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4859b-108">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="4859b-108">Prerequisites</span></span>

<span data-ttu-id="4859b-109">Per usare questo esempio, è necessario avere familiarità con quanto segue:</span><span class="sxs-lookup"><span data-stu-id="4859b-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="4859b-110">Concetti di CI/CD.</span><span class="sxs-lookup"><span data-stu-id="4859b-110">CI-CD concepts.</span></span> <span data-ttu-id="4859b-111">Informazioni di riferimento utili sono disponibili in [The Release Pipeline Model](https://aka.ms/thereleasepipelinemodelpdf) (Modello di pipeline di versione).</span><span class="sxs-lookup"><span data-stu-id="4859b-111">A good reference can be found at [The Release Pipeline Model](https://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="4859b-112">Controllo del codice sorgente tramite [Git](https://git-scm.com/)</span><span class="sxs-lookup"><span data-stu-id="4859b-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="4859b-113">Framework di test [Pester](https://github.com/pester/Pester)</span><span class="sxs-lookup"><span data-stu-id="4859b-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="4859b-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="4859b-114">Team Foundation Server</span></span>](https://visualstudio.microsoft.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="4859b-115">Materiale necessario</span><span class="sxs-lookup"><span data-stu-id="4859b-115">What you will need</span></span>

<span data-ttu-id="4859b-116">Per compilare ed eseguire questo esempio, è necessario un ambiente con più computer e/o macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="4859b-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="4859b-117">Client</span><span class="sxs-lookup"><span data-stu-id="4859b-117">Client</span></span>

<span data-ttu-id="4859b-118">Si tratta del computer in cui verranno eseguite tutte le operazioni di impostazione ed esecuzione dell'esempio.</span><span class="sxs-lookup"><span data-stu-id="4859b-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="4859b-119">Il computer client deve essere un computer Windows dotato dei componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="4859b-119">The client computer must be a Windows computer with the following installed:</span></span>

- [<span data-ttu-id="4859b-120">Git</span><span class="sxs-lookup"><span data-stu-id="4859b-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="4859b-121">repository Git locale clonato da https://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="4859b-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="4859b-122">un editor di testo, ad esempio [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="4859b-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="4859b-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="4859b-123">TFSSrv1</span></span>

<span data-ttu-id="4859b-124">Computer che ospita il server TFS in cui verranno definite la compilazione e la versione.</span><span class="sxs-lookup"><span data-stu-id="4859b-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="4859b-125">In questo computer deve essere installato [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/).</span><span class="sxs-lookup"><span data-stu-id="4859b-125">This computer must have [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="4859b-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="4859b-126">BuildAgent</span></span>

<span data-ttu-id="4859b-127">Computer che esegue l'agente di compilazione Windows che compila il progetto.</span><span class="sxs-lookup"><span data-stu-id="4859b-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="4859b-128">In questo computer deve essere installato e in esecuzione un agente di compilazione Windows.</span><span class="sxs-lookup"><span data-stu-id="4859b-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="4859b-129">Per istruzioni su come installare ed eseguire un agente di compilazione Windows, vedere [Deploy an agent on Windows](/azure/devops/pipelines/agents/v2-windows) (Distribuire un agente in Windows).</span><span class="sxs-lookup"><span data-stu-id="4859b-129">See [Deploy an agent on Windows](/azure/devops/pipelines/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="4859b-130">In questo computer è anche necessario installare i moduli DSC `xDnsServer` e `xNetworking`.</span><span class="sxs-lookup"><span data-stu-id="4859b-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="4859b-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="4859b-131">TestAgent1</span></span>

<span data-ttu-id="4859b-132">In questo esempio si tratta del computer configurato come server DNS dalla configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="4859b-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="4859b-133">Nel computer deve essere in esecuzione [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="4859b-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="4859b-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="4859b-134">TestAgent2</span></span>

<span data-ttu-id="4859b-135">Si tratta del computer che ospita il sito Web configurato in questo esempio.</span><span class="sxs-lookup"><span data-stu-id="4859b-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="4859b-136">Nel computer deve essere in esecuzione [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="4859b-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="4859b-137">Aggiungere il codice a TFS</span><span class="sxs-lookup"><span data-stu-id="4859b-137">Add the code to TFS</span></span>

<span data-ttu-id="4859b-138">Come prima cosa si creerà un repository Git in TFS e si importerà il codice dal repository locale nel computer client.</span><span class="sxs-lookup"><span data-stu-id="4859b-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="4859b-139">Se il repository Demo_CI non è stato ancora clonato nel computer client, eseguire questa operazione ora tramite il comando Git seguente:</span><span class="sxs-lookup"><span data-stu-id="4859b-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="4859b-140">Dal computer client passare al server TFS in un Web browser.</span><span class="sxs-lookup"><span data-stu-id="4859b-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="4859b-141">In TFS [creare un nuovo progetto team](/azure/devops/organizations/projects/create-project) denominato Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="4859b-141">In TFS, [Create a new team project](/azure/devops/organizations/projects/create-project) named Demo_CI.</span></span>

   <span data-ttu-id="4859b-142">Assicurarsi che **Controllo versione** sia impostato su **Git**.</span><span class="sxs-lookup"><span data-stu-id="4859b-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="4859b-143">Dal computer client aggiungere un remote al repository appena creato in TFS con il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="4859b-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

   `git remote add tfs <YourTFSRepoURL>`

   <span data-ttu-id="4859b-144">Dove `<YourTFSRepoURL>` è l'URL clone del repository TFS creato nel passaggio precedente.</span><span class="sxs-lookup"><span data-stu-id="4859b-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

   <span data-ttu-id="4859b-145">Se non si conosce la posizione di questo URL, vedere [Clone an existing Git repo](/azure/devops/repos/git/clone) (Clonare un repository Git esistente).</span><span class="sxs-lookup"><span data-stu-id="4859b-145">If you don't know where to find this URL, see [Clone an existing Git repo](/azure/devops/repos/git/clone).</span></span>
1. <span data-ttu-id="4859b-146">Eseguire il push del codice dal repository locale al repository TFS con il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="4859b-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

   `git push tfs --all`
1. <span data-ttu-id="4859b-147">Il repository TFS verrà popolato con il codice Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="4859b-147">The TFS repository will be populated with the Demo_CI code.</span></span>

> [!NOTE]
> <span data-ttu-id="4859b-148">Questo esempio usa il codice nel ramo `ci-cd-example` del repository Git.</span><span class="sxs-lookup"><span data-stu-id="4859b-148">This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
> <span data-ttu-id="4859b-149">Assicurarsi di specificare questo ramo come ramo predefinito nel progetto TFS e per i trigger CI/CD creati.</span><span class="sxs-lookup"><span data-stu-id="4859b-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="4859b-150">Informazioni sul codice</span><span class="sxs-lookup"><span data-stu-id="4859b-150">Understanding the code</span></span>

<span data-ttu-id="4859b-151">Prima di creare le pipeline di compilazione e distribuzione, verrà ora esaminata una parte del codice per comprendere le operazioni eseguite da quest'ultimo.</span><span class="sxs-lookup"><span data-stu-id="4859b-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="4859b-152">Nel computer client aprire l'editor di testo preferito e passare alla radice del repository Git Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="4859b-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="4859b-153">Configurazione DSC</span><span class="sxs-lookup"><span data-stu-id="4859b-153">The DSC configuration</span></span>

<span data-ttu-id="4859b-154">Aprire il file `DNSServer.ps1` dalla radice del repository locale Demo_CI, `./InfraDNS/Configs/DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="4859b-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="4859b-155">Questo file contiene la configurazione DSC per l'impostazione del server DNS.</span><span class="sxs-lookup"><span data-stu-id="4859b-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="4859b-156">Ecco il file completo:</span><span class="sxs-lookup"><span data-stu-id="4859b-156">Here it is in its entirety:</span></span>

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

<span data-ttu-id="4859b-157">Si noti l'istruzione `Node`:</span><span class="sxs-lookup"><span data-stu-id="4859b-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="4859b-158">Questa trova tutti i nodi definiti con il ruolo `DNSServer` nei [dati di configurazione](../configurations/configData.md), creati tramite lo script `DevEnv.ps1`.</span><span class="sxs-lookup"><span data-stu-id="4859b-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](../configurations/configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="4859b-159">Sono disponibili altre informazioni sul metodo `Where` in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span><span class="sxs-lookup"><span data-stu-id="4859b-159">You can read more about the `Where` method in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span></span>

<span data-ttu-id="4859b-160">L'uso di dati di configurazione per definire i nodi è importante quando si esegue l'integrazione continua. È probabile infatti che le informazioni sui nodi siano diverse da un ambiente all'altro e l'uso di dati di configurazione consente di apportare facilmente modifiche a tali informazioni senza modificare il codice di configurazione.</span><span class="sxs-lookup"><span data-stu-id="4859b-160">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="4859b-161">Nel primo blocco di risorse la configurazione chiama **WindowsFeature** per assicurare che sia abilitata la funzionalità DNS.</span><span class="sxs-lookup"><span data-stu-id="4859b-161">In the first resource block, the configuration calls the **WindowsFeature** to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="4859b-162">I blocchi di risorse che seguono chiamano risorse dal modulo [xDnsServer](https://github.com/PowerShell/xDnsServer) per configurare la zona primaria e i record DNS.</span><span class="sxs-lookup"><span data-stu-id="4859b-162">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="4859b-163">Si noti che i due blocchi `xDnsRecord` sono racchiusi all'interno di cicli `foreach` che eseguono un'iterazione attraverso matrici nei dati di configurazione.</span><span class="sxs-lookup"><span data-stu-id="4859b-163">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="4859b-164">Anche in questo caso i dati di configurazione vengono creati dallo script `DevEnv.ps1`, che verrà esaminato subito dopo.</span><span class="sxs-lookup"><span data-stu-id="4859b-164">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="4859b-165">Dati di configurazione</span><span class="sxs-lookup"><span data-stu-id="4859b-165">Configuration data</span></span>

<span data-ttu-id="4859b-166">Il file `DevEnv.ps1`, nella radice del repository Demo_CI locale, `./InfraDNS/DevEnv.ps1`, specifica i dati di configurazione specifici dell'ambiente in una tabella hash e quindi passa la tabella hash alla funzione `New-DscConfigurationDataDocument`, definita in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="4859b-166">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="4859b-167">Ecco il file `DevEnv.ps1`:</span><span class="sxs-lookup"><span data-stu-id="4859b-167">The `DevEnv.ps1` file:</span></span>

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

<span data-ttu-id="4859b-168">La funzione `New-DscConfigurationDataDocument`, definita in `\Assets\DscPipelineTools\DscPipelineTools.psm1`, crea a livello di codice un documento di dati di configurazione dalla tabella hash (dati di nodo) e dalla matrice (dati non di nodo) passati come parametri `RawEnvData` e `OtherEnvData`.</span><span class="sxs-lookup"><span data-stu-id="4859b-168">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="4859b-169">In questo caso viene usato solo il parametro `RawEnvData`.</span><span class="sxs-lookup"><span data-stu-id="4859b-169">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="4859b-170">Script di compilazione psake</span><span class="sxs-lookup"><span data-stu-id="4859b-170">The psake build script</span></span>

<span data-ttu-id="4859b-171">Lo script di compilazione [psake](https://github.com/psake/psake) definito in `Build.ps1` (nella radice del repository Demo_CI, `./InfraDNS/Build.ps1`) definisce le attività che fanno parte della compilazione</span><span class="sxs-lookup"><span data-stu-id="4859b-171">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="4859b-172">e indica da quali altre attività ogni attività dipende.</span><span class="sxs-lookup"><span data-stu-id="4859b-172">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="4859b-173">Quando viene richiamato, lo script psake assicura che l'attività specificata (o l'attività denominata `Default`, se non è specificata alcuna attività) venga eseguita,così come tutte le dipendenze. Questa esecuzione è ricorsiva, perché vengano eseguite anche le dipendenze delle dipendenze e così via.</span><span class="sxs-lookup"><span data-stu-id="4859b-173">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="4859b-174">In questo esempio l'attività `Default` è definita come:</span><span class="sxs-lookup"><span data-stu-id="4859b-174">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="4859b-175">L'attività `Default` di per sé non ha un'implementazione, ma presenta una dipendenza dall'attività `CompileConfigs`.</span><span class="sxs-lookup"><span data-stu-id="4859b-175">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="4859b-176">La catena di relazioni tra attività risultante garantisce che tutte le attività nello script di compilazione vengano eseguite.</span><span class="sxs-lookup"><span data-stu-id="4859b-176">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="4859b-177">In questo esempio lo script psake viene richiamato da una chiamata a `Invoke-PSake` nel file `Initiate.ps1`, nella radice del repository Demo_CI:</span><span class="sxs-lookup"><span data-stu-id="4859b-177">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

<span data-ttu-id="4859b-178">Quando si crea la definizione di compilazione per questo esempio in TFS, il file di script psake viene specificato come parametro `fileName` di questo script.</span><span class="sxs-lookup"><span data-stu-id="4859b-178">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="4859b-179">Lo script di compilazione definisce le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="4859b-179">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="4859b-180">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="4859b-180">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="4859b-181">Esegue `DevEnv.ps1`, che genera il file di dati di configurazione.</span><span class="sxs-lookup"><span data-stu-id="4859b-181">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="4859b-182">InstallModules</span><span class="sxs-lookup"><span data-stu-id="4859b-182">InstallModules</span></span>

<span data-ttu-id="4859b-183">Installa i moduli necessari per il file `DNSServer.ps1` di configurazione.</span><span class="sxs-lookup"><span data-stu-id="4859b-183">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="4859b-184">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="4859b-184">ScriptAnalysis</span></span>

<span data-ttu-id="4859b-185">Chiama [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="4859b-185">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="4859b-186">UnitTests</span><span class="sxs-lookup"><span data-stu-id="4859b-186">UnitTests</span></span>

<span data-ttu-id="4859b-187">Esegue gli unit test [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="4859b-187">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="4859b-188">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="4859b-188">CompileConfigs</span></span>

<span data-ttu-id="4859b-189">Compila la configurazione (`DNSServer.ps1`) in un file MOF, usando i dati di configurazione generati dall'attività `GenerateEnvironmentFiles`.</span><span class="sxs-lookup"><span data-stu-id="4859b-189">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="4859b-190">Clean</span><span class="sxs-lookup"><span data-stu-id="4859b-190">Clean</span></span>

<span data-ttu-id="4859b-191">Crea le cartelle usate per l'esempio e rimuove tutti i risultati dei test, i file di dati di configurazione e i moduli delle esecuzioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="4859b-191">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="4859b-192">Script di distribuzione psake</span><span class="sxs-lookup"><span data-stu-id="4859b-192">The psake deploy script</span></span>

<span data-ttu-id="4859b-193">Lo script di distribuzione [psake](https://github.com/psake/psake) definito in `Deploy.ps1` (nella radice del repository Demo_CI, `./InfraDNS/Deploy.ps1`) definisce le attività che distribuiscono ed eseguono la configurazione.</span><span class="sxs-lookup"><span data-stu-id="4859b-193">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="4859b-194">`Deploy.ps1` definisce le attività seguenti:</span><span class="sxs-lookup"><span data-stu-id="4859b-194">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="4859b-195">DeployModules</span><span class="sxs-lookup"><span data-stu-id="4859b-195">DeployModules</span></span>

<span data-ttu-id="4859b-196">Avvia una sessione di PowerShell in `TestAgent1` e installa i moduli contenenti le risorse DSC necessarie per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="4859b-196">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="4859b-197">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="4859b-197">DeployConfigs</span></span>

<span data-ttu-id="4859b-198">Chiama il cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) per eseguire la configurazione in `TestAgent1`.</span><span class="sxs-lookup"><span data-stu-id="4859b-198">Calls the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="4859b-199">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="4859b-199">IntegrationTests</span></span>

<span data-ttu-id="4859b-200">Esegue i test di integrazione di [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="4859b-200">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="4859b-201">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="4859b-201">AcceptanceTests</span></span>

<span data-ttu-id="4859b-202">Esegue i test di accettazione di [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="4859b-202">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="4859b-203">Clean</span><span class="sxs-lookup"><span data-stu-id="4859b-203">Clean</span></span>

<span data-ttu-id="4859b-204">Rimuove tutti i moduli installati durante le esecuzioni precedenti e verifica l'esistenza della cartella dei risultati dei test.</span><span class="sxs-lookup"><span data-stu-id="4859b-204">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="4859b-205">Script di test</span><span class="sxs-lookup"><span data-stu-id="4859b-205">Test scripts</span></span>

<span data-ttu-id="4859b-206">I test di accettazione e di integrazione e gli unit test sono definiti all'interno di script nella cartella `Tests` (nella radice del repository Demo_CI, `./InfraDNS/Tests`), ognuno all'interno di un file `DNSServer.tests.ps1` nella rispettiva cartella.</span><span class="sxs-lookup"><span data-stu-id="4859b-206">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="4859b-207">I test di script usano la sintassi di [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).</span><span class="sxs-lookup"><span data-stu-id="4859b-207">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="4859b-208">Unit test</span><span class="sxs-lookup"><span data-stu-id="4859b-208">Unit tests</span></span>

<span data-ttu-id="4859b-209">Gli unit test eseguono il test delle configurazioni DSC per garantire che durante l'esecuzione le configurazioni funzionino come previsto.</span><span class="sxs-lookup"><span data-stu-id="4859b-209">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="4859b-210">Gli script di unit test script usano [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="4859b-210">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="4859b-211">Test di integrazione</span><span class="sxs-lookup"><span data-stu-id="4859b-211">Integration tests</span></span>

<span data-ttu-id="4859b-212">I test di integrazione eseguono il test della configurazione del sistema per garantire che, quando integrato con altri componenti, il sistema sia configurato come previsto.</span><span class="sxs-lookup"><span data-stu-id="4859b-212">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="4859b-213">Questi test vengono eseguiti nel nodo di destinazione dopo la configurazione di quest'ultimo con DSC.</span><span class="sxs-lookup"><span data-stu-id="4859b-213">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="4859b-214">Gli script dei test di integrazione usano una combinazione della sintassi di [Pester](https://github.com/pester/Pester/wiki) e di [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).</span><span class="sxs-lookup"><span data-stu-id="4859b-214">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="4859b-215">Test di accettazione</span><span class="sxs-lookup"><span data-stu-id="4859b-215">Acceptance tests</span></span>

<span data-ttu-id="4859b-216">I test di accettazione eseguono il test del sistema per assicurarsi che funzioni come previsto.</span><span class="sxs-lookup"><span data-stu-id="4859b-216">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="4859b-217">I test verificano, ad esempio, che una query a una pagina Web restituisca le informazioni corrette.</span><span class="sxs-lookup"><span data-stu-id="4859b-217">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="4859b-218">Questi test vengono eseguiti in remoto dal nodo di destinazione per testare scenari reali.</span><span class="sxs-lookup"><span data-stu-id="4859b-218">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="4859b-219">Gli script dei test di integrazione usano una combinazione della sintassi di [Pester](https://github.com/pester/Pester/wiki) e di [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).</span><span class="sxs-lookup"><span data-stu-id="4859b-219">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="4859b-220">Definire la compilazione</span><span class="sxs-lookup"><span data-stu-id="4859b-220">Define the build</span></span>

<span data-ttu-id="4859b-221">Dopo aver caricato il codice in TFS e averne osservato il funzionamento, è possibile definire la compilazione.</span><span class="sxs-lookup"><span data-stu-id="4859b-221">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="4859b-222">In questo esempio verranno trattati solo i passaggi di compilazione da aggiungere alla compilazione stessa.</span><span class="sxs-lookup"><span data-stu-id="4859b-222">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="4859b-223">Per istruzioni su come creare una definizione di compilazione in TFS, vedere [Create your first build and release](/azure/devops/pipelines/create-first-pipeline) (Creare la prima compilazione e la prima versione).</span><span class="sxs-lookup"><span data-stu-id="4859b-223">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](/azure/devops/pipelines/create-first-pipeline).</span></span>

<span data-ttu-id="4859b-224">Creare una nuova definizione di compilazione (selezionare il modello **vuoto**) denominato "InfraDNS".</span><span class="sxs-lookup"><span data-stu-id="4859b-224">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="4859b-225">Aggiungere alla definizione di compilazione i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4859b-225">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="4859b-226">Script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4859b-226">PowerShell Script</span></span>
- <span data-ttu-id="4859b-227">Pubblicazione dei risultati dei test</span><span class="sxs-lookup"><span data-stu-id="4859b-227">Publish Test Results</span></span>
- <span data-ttu-id="4859b-228">Copia dei file</span><span class="sxs-lookup"><span data-stu-id="4859b-228">Copy Files</span></span>
- <span data-ttu-id="4859b-229">Pubblicazione dell'elemento</span><span class="sxs-lookup"><span data-stu-id="4859b-229">Publish Artifact</span></span>

<span data-ttu-id="4859b-230">Dopo l'aggiunta di queste istruzioni di compilazione, modificare le proprietà di ogni istruzione nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="4859b-230">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="4859b-231">Script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4859b-231">PowerShell Script</span></span>

1. <span data-ttu-id="4859b-232">Impostare la proprietà **Tipo** su `File Path`.</span><span class="sxs-lookup"><span data-stu-id="4859b-232">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="4859b-233">Impostare la proprietà **Percorso script** su `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="4859b-233">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="4859b-234">Aggiungere `-fileName build` alla proprietà **Argomenti**.</span><span class="sxs-lookup"><span data-stu-id="4859b-234">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="4859b-235">Questa istruzione di compilazione esegue il file `initiate.ps1`, che chiama lo script di compilazione psake.</span><span class="sxs-lookup"><span data-stu-id="4859b-235">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="4859b-236">Pubblicazione dei risultati dei test</span><span class="sxs-lookup"><span data-stu-id="4859b-236">Publish Test Results</span></span>

1. <span data-ttu-id="4859b-237">Impostare **Formato dei risultati test** su `NUnit`</span><span class="sxs-lookup"><span data-stu-id="4859b-237">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="4859b-238">Impostare **File dei risultati del test** su `InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="4859b-238">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="4859b-239">Impostare **Titolo esecuzione dei test** su `Unit`.</span><span class="sxs-lookup"><span data-stu-id="4859b-239">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="4859b-240">Verificare che in **Opzioni di controllo** le opzioni **Abilitato** ed **Esegui sempre** siano entrambe selezionate.</span><span class="sxs-lookup"><span data-stu-id="4859b-240">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="4859b-241">Questa istruzione di compilazione esegue gli unit test dello script Pester esaminato in precedenza e archivia i risultati nella cartella `InfraDNS/Tests/Results/*.xml`.</span><span class="sxs-lookup"><span data-stu-id="4859b-241">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="4859b-242">Copia dei file</span><span class="sxs-lookup"><span data-stu-id="4859b-242">Copy Files</span></span>

1. <span data-ttu-id="4859b-243">Aggiungere ognuna delle righe seguenti a **Contenuto**:</span><span class="sxs-lookup"><span data-stu-id="4859b-243">Add each of the following lines to **Contents**:</span></span>

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. <span data-ttu-id="4859b-244">Impostare **TargetFolder** su `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="4859b-244">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="4859b-245">Questa istruzione copia gli script di compilazione e di test nella directory di gestione temporanea, in modo che i risultati possano essere pubblicati come elementi di compilazione nel passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="4859b-245">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="4859b-246">Pubblicazione dell'elemento</span><span class="sxs-lookup"><span data-stu-id="4859b-246">Publish Artifact</span></span>

1. <span data-ttu-id="4859b-247">Impostare **Percorso per la pubblicazione** su `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="4859b-247">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="4859b-248">Impostare **Nome elemento** su `Deploy`</span><span class="sxs-lookup"><span data-stu-id="4859b-248">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="4859b-249">Impostare **Tipo elemento** su `Server`</span><span class="sxs-lookup"><span data-stu-id="4859b-249">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="4859b-250">Selezionare `Enabled` in **Opzioni di controllo**</span><span class="sxs-lookup"><span data-stu-id="4859b-250">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="4859b-251">Abilitare l'integrazione continua</span><span class="sxs-lookup"><span data-stu-id="4859b-251">Enable continuous integration</span></span>

<span data-ttu-id="4859b-252">Ora verrà configurato un trigger che attiva la compilazione del progetto ogni volta che una modifica viene archiviata nel ramo `ci-cd-example` del repository Git.</span><span class="sxs-lookup"><span data-stu-id="4859b-252">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="4859b-253">In TFS fare clic sulla scheda **Compilazione e versione**</span><span class="sxs-lookup"><span data-stu-id="4859b-253">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="4859b-254">Selezionare la definizione di compilazione `DNS Infra` e fare clic su **Modifica**</span><span class="sxs-lookup"><span data-stu-id="4859b-254">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="4859b-255">Fare clic sulla scheda **Trigger**</span><span class="sxs-lookup"><span data-stu-id="4859b-255">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="4859b-256">Selezionare **Integrazione continua (CI)** e selezionare `refs/heads/ci-cd-example` nell'elenco a discesa dei rami</span><span class="sxs-lookup"><span data-stu-id="4859b-256">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="4859b-257">Fare clic su **Salva** e quindi su **OK**</span><span class="sxs-lookup"><span data-stu-id="4859b-257">Click **Save** and then **OK**</span></span>

<span data-ttu-id="4859b-258">Ora qualsiasi modifica al repository Git in TFS attiva una compilazione automatizzata.</span><span class="sxs-lookup"><span data-stu-id="4859b-258">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="4859b-259">Creare la definizione di versione</span><span class="sxs-lookup"><span data-stu-id="4859b-259">Create the release definition</span></span>

<span data-ttu-id="4859b-260">Verrà ora creata una definizione di versione, in modo che il progetto venga distribuito nell'ambiente di sviluppo a ogni archiviazione di codice.</span><span class="sxs-lookup"><span data-stu-id="4859b-260">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="4859b-261">A tale scopo, aggiungere una nuova definizione di versione associata alla definizione di compilazione `InfraDNS` creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="4859b-261">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="4859b-262">Assicurarsi di selezionare **Distribuzione continua**, in modo che venga attivata una nuova versione ogni volta che viene completata una nuova compilazione</span><span class="sxs-lookup"><span data-stu-id="4859b-262">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="4859b-263">([Che cosa sono le pipeline di versione?](/azure/devops/pipelines/release/)). Configurare indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="4859b-263">([What are release pipelines?](/azure/devops/pipelines/release/)) and configure it as follows:</span></span>

<span data-ttu-id="4859b-264">Aggiungere alla definizione di versione i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4859b-264">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="4859b-265">Script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4859b-265">PowerShell Script</span></span>
- <span data-ttu-id="4859b-266">Pubblicazione dei risultati dei test</span><span class="sxs-lookup"><span data-stu-id="4859b-266">Publish Test Results</span></span>
- <span data-ttu-id="4859b-267">Pubblicazione dei risultati dei test</span><span class="sxs-lookup"><span data-stu-id="4859b-267">Publish Test Results</span></span>

<span data-ttu-id="4859b-268">Modificare i passaggi come segue:</span><span class="sxs-lookup"><span data-stu-id="4859b-268">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="4859b-269">Script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4859b-269">PowerShell Script</span></span>

1. <span data-ttu-id="4859b-270">Impostare il campo **Percorso script** su `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="4859b-270">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="4859b-271">Impostare il campo **Argomenti** su `-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="4859b-271">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="4859b-272">Prima pubblicazione dei risultati dei test</span><span class="sxs-lookup"><span data-stu-id="4859b-272">First Publish Test Results</span></span>

1. <span data-ttu-id="4859b-273">Selezionare `NUnit` per il campo **Formato dei risultati test**</span><span class="sxs-lookup"><span data-stu-id="4859b-273">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="4859b-274">Impostare il campo **File dei risultati del test** su `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="4859b-274">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="4859b-275">Impostare il campo **Titolo esecuzione dei test** su `Integration`</span><span class="sxs-lookup"><span data-stu-id="4859b-275">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="4859b-276">In **Opzioni di controllo** selezionare **Esegui sempre**</span><span class="sxs-lookup"><span data-stu-id="4859b-276">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="4859b-277">Seconda pubblicazione dei risultati dei test</span><span class="sxs-lookup"><span data-stu-id="4859b-277">Second Publish Test Results</span></span>

1. <span data-ttu-id="4859b-278">Selezionare `NUnit` per il campo **Formato dei risultati test**</span><span class="sxs-lookup"><span data-stu-id="4859b-278">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="4859b-279">Impostare il campo **File dei risultati del test** su `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="4859b-279">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="4859b-280">Impostare il campo **Titolo esecuzione dei test** su `Acceptance`</span><span class="sxs-lookup"><span data-stu-id="4859b-280">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="4859b-281">In **Opzioni di controllo** selezionare **Esegui sempre**</span><span class="sxs-lookup"><span data-stu-id="4859b-281">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="4859b-282">Verificare i risultati</span><span class="sxs-lookup"><span data-stu-id="4859b-282">Verify your results</span></span>

<span data-ttu-id="4859b-283">A questo punto, ogni volta che si esegue il push delle modifiche apportate al ramo `ci-cd-example` in TFS viene avviata una nuova compilazione.</span><span class="sxs-lookup"><span data-stu-id="4859b-283">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="4859b-284">Se la compilazione viene completata correttamente, viene attivata una nuova distribuzione.</span><span class="sxs-lookup"><span data-stu-id="4859b-284">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="4859b-285">Per controllare il risultato della distribuzione, aprire un browser nel computer client e passare a `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="4859b-285">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4859b-286">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="4859b-286">Next steps</span></span>

<span data-ttu-id="4859b-287">Questo esempio configura il server DNS `TestAgent1` in modo che l'URL `www.contoso.com` venga risolto in `TestAgent2` ma non distribuisca un sito Web.</span><span class="sxs-lookup"><span data-stu-id="4859b-287">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="4859b-288">Lo scheletro per questa operazione è disponibile nel repository nella cartella `WebApp`.</span><span class="sxs-lookup"><span data-stu-id="4859b-288">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="4859b-289">Per creare script psake, test Pester e configurazioni DSC per la distribuzione di un sito Web personale, è possibile usare gli stub forniti.</span><span class="sxs-lookup"><span data-stu-id="4859b-289">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>
