---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Introduzione a DSC (Desired State Configuration)
ms.openlocfilehash: e21017f24db8c90229063895c1a7e4c6f0546d0c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
> <span data-ttu-id="b42a1-103">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b42a1-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="desired-state-configuration-quick-start"></a><span data-ttu-id="b42a1-104">Introduzione a DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="b42a1-104">Desired State Configuration Quick Start</span></span>

<span data-ttu-id="b42a1-105">Questo esercizio illustra nei dettagli tutti i passaggi per creare e applicare una configurazione DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="b42a1-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="b42a1-106">L'esempio che verrà usato garantisce che in un server sia abilitata la funzionalità `Web-Server` (IIS) e che il contenuto di un semplice sito Web "Hello World" sia presente nella directory `intepub\wwwroot` di tale server.</span><span class="sxs-lookup"><span data-stu-id="b42a1-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `intepub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="b42a1-107">Per una panoramica di DSC e del relativo funzionamento, vedere [Panoramica di DSC (Desired State Configuration) per decision maker](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="b42a1-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b42a1-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b42a1-108">Requirements</span></span>

<span data-ttu-id="b42a1-109">Per eseguire questo esempio, è necessario un computer che esegue Windows Server 2012 o versione successiva e PowerShell 4.0 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="b42a1-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="b42a1-110">Scrivere e posizionare il file index.htm</span><span class="sxs-lookup"><span data-stu-id="b42a1-110">Write and place the index.htm file</span></span>

<span data-ttu-id="b42a1-111">Verrà innanzitutto creato il file HTML usato come contenuto del sito Web.</span><span class="sxs-lookup"><span data-stu-id="b42a1-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="b42a1-112">Nella cartella radice creare una cartella denominata `test`.</span><span class="sxs-lookup"><span data-stu-id="b42a1-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="b42a1-113">In un editor di testo digitare il testo seguente:</span><span class="sxs-lookup"><span data-stu-id="b42a1-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="b42a1-114">Salvare il file come `index.htm` nella cartella `test` creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="b42a1-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span> 

## <a name="write-the-configuration"></a><span data-ttu-id="b42a1-115">Scrivere la configurazione</span><span class="sxs-lookup"><span data-stu-id="b42a1-115">Write the configuration</span></span>

<span data-ttu-id="b42a1-116">Una [configurazione DSC](configurations.md) è una funzione speciale di PowerShell che definisce come si vogliono configurare uno o più computer di destinazione (nodi).</span><span class="sxs-lookup"><span data-stu-id="b42a1-116">A [DSC configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="b42a1-117">In PowerShell ISE digitare il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="b42a1-117">In the PowerShell ISE, type the following:</span></span>

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

<span data-ttu-id="b42a1-118">Salvare il file come `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="b42a1-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="b42a1-119">Si può notare che assomiglia a una funzione di PowerShell con l'aggiunta della parola chiave **Configuration** usata prima del nome della funzione.</span><span class="sxs-lookup"><span data-stu-id="b42a1-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="b42a1-120">Il blocco **Node** specifica il nodo di destinazione da configurare, in questo caso `localhost`.</span><span class="sxs-lookup"><span data-stu-id="b42a1-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="b42a1-121">La configurazione chiama due [risorse](resources.md), [WindowsFeature](windowsFeatureResource.md) e [File](fileResource.md).</span><span class="sxs-lookup"><span data-stu-id="b42a1-121">The configuration calls two [resources](resources.md), [WindowsFeature](windowsFeatureResource.md) and [File](fileResource.md).</span></span>
<span data-ttu-id="b42a1-122">Le risorse si occupano di assicurarsi che il nodo di destinazione sia nello stato definito dalla configurazione.</span><span class="sxs-lookup"><span data-stu-id="b42a1-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="b42a1-123">Compilare la configurazione</span><span class="sxs-lookup"><span data-stu-id="b42a1-123">Compile the configuration</span></span>

<span data-ttu-id="b42a1-124">Per applicare una configurazione DSC a un nodo, è prima necessario compilarla in un file MOF.</span><span class="sxs-lookup"><span data-stu-id="b42a1-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="b42a1-125">A tale scopo, la configurazione viene eseguita come una funzione.</span><span class="sxs-lookup"><span data-stu-id="b42a1-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="b42a1-126">In una console di PowerShell passare alla stessa cartella in cui è stata salvata la configurazione ed eseguire i comandi seguenti per compilare la configurazione in un file MOF:</span><span class="sxs-lookup"><span data-stu-id="b42a1-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="b42a1-127">Verrà generato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="b42a1-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="b42a1-128">La prima riga rende la funzione di configurazione disponibile nella console.</span><span class="sxs-lookup"><span data-stu-id="b42a1-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="b42a1-129">La seconda riga esegue la configurazione.</span><span class="sxs-lookup"><span data-stu-id="b42a1-129">The second line runs the configuration.</span></span>
<span data-ttu-id="b42a1-130">Il risultato è la creazione di una nuova cartella denominata `WebsiteTest` come sottocartella della cartella corrente.</span><span class="sxs-lookup"><span data-stu-id="b42a1-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="b42a1-131">La cartella `WebsiteTest` contiene un file denominato `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="b42a1-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="b42a1-132">Si tratta del file che può quindi essere applicato al nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b42a1-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="b42a1-133">Applicare la configurazione</span><span class="sxs-lookup"><span data-stu-id="b42a1-133">Apply the configuration</span></span>

<span data-ttu-id="b42a1-134">Ora che è disponibile il file MOF compilato, è possibile applicare la configurazione al nodo di destinazione, in questo caso il computer locale, chiamando il cmdlet [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="b42a1-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span>

<span data-ttu-id="b42a1-135">Il cmdlet `Start-DscConfiguration` indica a [Gestione configurazione locale](metaConfig.md), ovvero il motore di DSC, di applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="b42a1-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="b42a1-136">Gestione configurazione locale si occupa di chiamare le risorse DSC per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="b42a1-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="b42a1-137">In una console di PowerShell passare alla stessa cartella in cui è stata salvata la configurazione ed eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="b42a1-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="b42a1-138">Verificare la configurazione</span><span class="sxs-lookup"><span data-stu-id="b42a1-138">Test the configuration</span></span>

<span data-ttu-id="b42a1-139">È possibile chiamare il cmdlet [DscConfigurationStatus Get](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) per verificare se la configurazione è stata applicata.</span><span class="sxs-lookup"><span data-stu-id="b42a1-139">You can call the [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet to see whether the configuration succeeded.</span></span> 

<span data-ttu-id="b42a1-140">È anche possibile testare i risultati direttamente, in questo caso passando a `http://localhost/` in un Web browser.</span><span class="sxs-lookup"><span data-stu-id="b42a1-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="b42a1-141">Dovrebbe essere visualizzata la pagina HTML "Hello World" creata nel primo passaggio di questo esempio.</span><span class="sxs-lookup"><span data-stu-id="b42a1-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b42a1-142">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="b42a1-142">Next steps</span></span>

- <span data-ttu-id="b42a1-143">Ulteriori informazioni sulle configurazioni DSC sono disponibili in [Configurazioni DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="b42a1-143">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="b42a1-144">Per informazioni sulle risorse DSC disponibili e su come creare risorse DSC personalizzate, vedere [Risorse DSC](resources.md).</span><span class="sxs-lookup"><span data-stu-id="b42a1-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](resources.md).</span></span>
- <span data-ttu-id="b42a1-145">Le configurazioni e le risorse DSC sono disponibili in [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="b42a1-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>



