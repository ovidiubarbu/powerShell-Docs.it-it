---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Avvio rapido - Creare un sito Web con DSC
ms.openlocfilehash: 08ca25604998ce8c913ef8112b5342f2e0216b6e
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/25/2019
ms.locfileid: "75416122"
---
# <a name="quickstart---create-a-website-with-desired-state-configuration-dsc"></a><span data-ttu-id="c109d-103">Avvio rapido - Creare un sito Web con Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="c109d-103">Quickstart - Create a website with Desired State Configuration (DSC)</span></span>

> <span data-ttu-id="c109d-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c109d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c109d-105">Questo esercizio illustra nei dettagli tutti i passaggi per creare e applicare una configurazione DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="c109d-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="c109d-106">L'esempio che verrà usato garantisce che in un server sia abilitata la funzionalità `Web-Server` (IIS) e che il contenuto di un semplice sito Web "Hello World" sia presente nella directory `inetpub\wwwroot` di tale server.</span><span class="sxs-lookup"><span data-stu-id="c109d-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `inetpub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="c109d-107">Per una panoramica di DSC e del relativo funzionamento, vedere [Panoramica di DSC (Desired State Configuration) per decision maker](../overview/decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="c109d-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c109d-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c109d-108">Requirements</span></span>

<span data-ttu-id="c109d-109">Per eseguire questo esempio, è necessario un computer che esegue Windows Server 2012 o versione successiva e PowerShell 4.0 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="c109d-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="c109d-110">Scrivere e posizionare il file index.htm</span><span class="sxs-lookup"><span data-stu-id="c109d-110">Write and place the index.htm file</span></span>

<span data-ttu-id="c109d-111">Verrà innanzitutto creato il file HTML usato come contenuto del sito Web.</span><span class="sxs-lookup"><span data-stu-id="c109d-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="c109d-112">Nella cartella radice creare una cartella denominata `test`.</span><span class="sxs-lookup"><span data-stu-id="c109d-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="c109d-113">In un editor di testo digitare il testo seguente:</span><span class="sxs-lookup"><span data-stu-id="c109d-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="c109d-114">Salvare il file come `index.htm` nella cartella `test` creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="c109d-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="c109d-115">Scrivere la configurazione</span><span class="sxs-lookup"><span data-stu-id="c109d-115">Write the configuration</span></span>

<span data-ttu-id="c109d-116">Una [configurazione DSC](../configurations/configurations.md) è una funzione speciale di PowerShell che definisce come si vogliono configurare uno o più computer di destinazione (nodi).</span><span class="sxs-lookup"><span data-stu-id="c109d-116">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="c109d-117">In PowerShell ISE digitare il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="c109d-117">In the PowerShell ISE, type the following:</span></span>

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

<span data-ttu-id="c109d-118">Salvare il file come `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="c109d-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="c109d-119">Si può notare che assomiglia a una funzione di PowerShell con l'aggiunta della parola chiave **Configuration** usata prima del nome della funzione.</span><span class="sxs-lookup"><span data-stu-id="c109d-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="c109d-120">Il blocco **Node** specifica il nodo di destinazione da configurare.</span><span class="sxs-lookup"><span data-stu-id="c109d-120">The **Node** block specifies the target node to be configured.</span></span> <span data-ttu-id="c109d-121">In questo caso, `localhost`.</span><span class="sxs-lookup"><span data-stu-id="c109d-121">In this case, `localhost`.</span></span>

<span data-ttu-id="c109d-122">La configurazione chiama due [risorse](../resources/resources.md), **WindowsFeature** e **File**.</span><span class="sxs-lookup"><span data-stu-id="c109d-122">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="c109d-123">Le risorse si occupano di assicurarsi che il nodo di destinazione sia nello stato definito dalla configurazione.</span><span class="sxs-lookup"><span data-stu-id="c109d-123">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="c109d-124">Compilare la configurazione</span><span class="sxs-lookup"><span data-stu-id="c109d-124">Compile the configuration</span></span>

<span data-ttu-id="c109d-125">Per applicare una configurazione DSC a un nodo, è prima necessario compilarla in un file MOF.</span><span class="sxs-lookup"><span data-stu-id="c109d-125">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="c109d-126">A tale scopo, la configurazione viene eseguita come una funzione.</span><span class="sxs-lookup"><span data-stu-id="c109d-126">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="c109d-127">In una console di PowerShell passare alla stessa cartella in cui è stata salvata la configurazione ed eseguire i comandi seguenti per compilare la configurazione in un file MOF:</span><span class="sxs-lookup"><span data-stu-id="c109d-127">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="c109d-128">Verrà generato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="c109d-128">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="c109d-129">La prima riga rende la funzione di configurazione disponibile nella console.</span><span class="sxs-lookup"><span data-stu-id="c109d-129">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="c109d-130">La seconda riga esegue la configurazione.</span><span class="sxs-lookup"><span data-stu-id="c109d-130">The second line runs the configuration.</span></span>
<span data-ttu-id="c109d-131">Il risultato è la creazione di una nuova cartella denominata `WebsiteTest` come sottocartella della cartella corrente.</span><span class="sxs-lookup"><span data-stu-id="c109d-131">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="c109d-132">La cartella `WebsiteTest` contiene un file denominato `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="c109d-132">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="c109d-133">Si tratta del file che può quindi essere applicato al nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="c109d-133">This is the file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="c109d-134">Applicare la configurazione</span><span class="sxs-lookup"><span data-stu-id="c109d-134">Apply the configuration</span></span>

<span data-ttu-id="c109d-135">Ora che è disponibile il file MOF compilato, è possibile applicare la configurazione al nodo di destinazione, in questo caso il computer locale, chiamando il cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="c109d-135">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="c109d-136">Il cmdlet `Start-DscConfiguration` indica a [Gestione configurazione locale](../managing-nodes/metaConfig.md), ovvero il motore di DSC, di applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="c109d-136">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="c109d-137">Gestione configurazione locale si occupa di chiamare le risorse DSC per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="c109d-137">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="c109d-138">Per consentire l'esecuzione di DSC, è necessario configurare Windows per la ricezione di comandi remoti di PowerShell, anche quando si esegue una configurazione `localhost`.</span><span class="sxs-lookup"><span data-stu-id="c109d-138">To allow DSC to run, Windows needs to be configured to receive PowerShell remote commands, even when you're running a `localhost` configuration.</span></span> <span data-ttu-id="c109d-139">Per configurare correttamente l'ambiente, è sufficiente eseguire `Set-WsManQuickConfig -Force` in un terminale di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="c109d-139">To easily configure your environment correctly, just run `Set-WsManQuickConfig -Force` in an elevated PowerShell Terminal.</span></span>

<span data-ttu-id="c109d-140">In una console di PowerShell passare alla stessa cartella in cui è stata salvata la configurazione ed eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="c109d-140">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="c109d-141">Testare la configurazione</span><span class="sxs-lookup"><span data-stu-id="c109d-141">Test the configuration</span></span>

<span data-ttu-id="c109d-142">È possibile chiamare il cmdlet [DscConfigurationStatus Get](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) per verificare se la configurazione è stata applicata.</span><span class="sxs-lookup"><span data-stu-id="c109d-142">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="c109d-143">È anche possibile testare i risultati direttamente, in questo caso passando a `http://localhost/` in un Web browser.</span><span class="sxs-lookup"><span data-stu-id="c109d-143">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="c109d-144">Dovrebbe essere visualizzata la pagina HTML "Hello World" creata nel primo passaggio di questo esempio.</span><span class="sxs-lookup"><span data-stu-id="c109d-144">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c109d-145">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="c109d-145">Next steps</span></span>

- <span data-ttu-id="c109d-146">Ulteriori informazioni sulle configurazioni DSC sono disponibili in [Configurazioni DSC](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c109d-146">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="c109d-147">Per informazioni sulle risorse DSC disponibili e su come creare risorse DSC personalizzate, vedere [Risorse DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="c109d-147">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="c109d-148">Le configurazioni e le risorse DSC sono disponibili in [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="c109d-148">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
