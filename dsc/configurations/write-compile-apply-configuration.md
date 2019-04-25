---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,servizio,impostazione
title: Scrivere, compilare e applicare una configurazione
ms.openlocfilehash: 947308efa165543571801c88a922daf44fa88be0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080017"
---
> <span data-ttu-id="c9c24-103">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c9c24-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="c9c24-104">Scrivere, compilare e applicare una configurazione</span><span class="sxs-lookup"><span data-stu-id="c9c24-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="c9c24-105">Questo esercizio illustra nei dettagli tutti i passaggi per creare e applicare una configurazione DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="c9c24-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="c9c24-106">Nell'esempio seguente si apprenderà come scrivere e applicare una configurazione molto semplice.</span><span class="sxs-lookup"><span data-stu-id="c9c24-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="c9c24-107">La configurazione garantirà la presenza di un file "HelloWorld.txt" nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="c9c24-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="c9c24-108">Se si elimina il file, DSC lo crea nuovamente al successivo aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="c9c24-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="c9c24-109">Per una panoramica di DSC e del relativo funzionamento, vedere [Panoramica di DSC (Desired State Configuration) per sviluppatori](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="c9c24-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c9c24-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c9c24-110">Requirements</span></span>

<span data-ttu-id="c9c24-111">Per eseguire questo esempio, è necessario un computer che esegue PowerShell 4.0 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="c9c24-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="c9c24-112">Scrivere la configurazione</span><span class="sxs-lookup"><span data-stu-id="c9c24-112">Write the configuration</span></span>

<span data-ttu-id="c9c24-113">Una [configurazione](configurations.md) DSC è una funzione speciale di PowerShell che definisce come si vogliono configurare uno o più computer di destinazione (nodi).</span><span class="sxs-lookup"><span data-stu-id="c9c24-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="c9c24-114">In PowerShell ISE o altri editor di PowerShell digitare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="c9c24-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

<span data-ttu-id="c9c24-115">Salvare il file con nome "HelloWorld.ps1".</span><span class="sxs-lookup"><span data-stu-id="c9c24-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="c9c24-116">La definizione di una configurazione è simile a definizione di una funzione.</span><span class="sxs-lookup"><span data-stu-id="c9c24-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="c9c24-117">Il blocco **Node** specifica il nodo di destinazione da configurare, in questo caso `localhost`.</span><span class="sxs-lookup"><span data-stu-id="c9c24-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="c9c24-118">La configurazione chiama un'unica [risorsa](../resources/resources.md), la risorsa `File`.</span><span class="sxs-lookup"><span data-stu-id="c9c24-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="c9c24-119">Le risorse si occupano di assicurarsi che il nodo di destinazione sia nello stato definito dalla configurazione.</span><span class="sxs-lookup"><span data-stu-id="c9c24-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="c9c24-120">Compilare la configurazione</span><span class="sxs-lookup"><span data-stu-id="c9c24-120">Compile the configuration</span></span>

<span data-ttu-id="c9c24-121">Per applicare una configurazione DSC a un nodo, è prima necessario compilarla in un file MOF.</span><span class="sxs-lookup"><span data-stu-id="c9c24-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="c9c24-122">L'esecuzione della configurazione, come una funzione, compila un unico file con estensione "mof" per ogni nodo definito dal blocco `Node`.</span><span class="sxs-lookup"><span data-stu-id="c9c24-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="c9c24-123">Per eseguire la configurazione, è necessario *eseguire tramite l'operatore '.'* lo script "HelloWorld.ps1" nell'ambito corrente.</span><span class="sxs-lookup"><span data-stu-id="c9c24-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="c9c24-124">Per altre informazioni, vedere [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="c9c24-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="c9c24-125">*Usare il dotsourcing* per lo script "HelloWorld.ps1" digitando il percorso in cui è archiviato dopo `. ` (punto, spazio).</span><span class="sxs-lookup"><span data-stu-id="c9c24-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="c9c24-126">È quindi possibile eseguire la configurazione chiamandola come una funzione.</span><span class="sxs-lookup"><span data-stu-id="c9c24-126">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="c9c24-127">Verrà generato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="c9c24-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="c9c24-128">Applicare la configurazione</span><span class="sxs-lookup"><span data-stu-id="c9c24-128">Apply the configuration</span></span>

<span data-ttu-id="c9c24-129">Ora che è disponibile il file MOF compilato, è possibile applicare la configurazione al nodo di destinazione, in questo caso il computer locale, chiamando il cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="c9c24-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="c9c24-130">Il cmdlet `Start-DscConfiguration` indica a [Gestione configurazione locale](../managing-nodes/metaConfig.md), il motore di DSC, di applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="c9c24-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="c9c24-131">Gestione configurazione locale si occupa di chiamare le risorse DSC per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="c9c24-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="c9c24-132">Usare il codice seguente per eseguire il cmdlet `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="c9c24-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="c9c24-133">Specificare il percorso della directory in cui è archiviato il file "localhost.mof" nel parametro `-Path`.</span><span class="sxs-lookup"><span data-stu-id="c9c24-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="c9c24-134">Il cmdlet `Start-DSCConfiguration` ricerca nella directory specificata i file "\<nomecomputer\>.mof".</span><span class="sxs-lookup"><span data-stu-id="c9c24-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="c9c24-135">Il cmdlet `Start-DSCConfiguration` tenta di applicare ogni file con estensione "mof" trovato al nome computer specificato dal nome file ("hostlocale", "server01", "dc-02" e così via).</span><span class="sxs-lookup"><span data-stu-id="c9c24-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="c9c24-136">Se il parametro `-Wait` non è specificato, `Start-DSCConfiguration` crea un processo in background per eseguire l'operazione.</span><span class="sxs-lookup"><span data-stu-id="c9c24-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="c9c24-137">La specifica del parametro `-Verbose` consente di controllare l'output **dettagliato** dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="c9c24-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="c9c24-138">`-Wait` e `-Verbose` sono entrambi parametri facoltativi.</span><span class="sxs-lookup"><span data-stu-id="c9c24-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="c9c24-139">Verificare la configurazione</span><span class="sxs-lookup"><span data-stu-id="c9c24-139">Test the configuration</span></span>

<span data-ttu-id="c9c24-140">Al termine del cmdlet `Start-DSCConfiguration`, viene visualizzato un file "HelloWorld.txt" nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="c9c24-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="c9c24-141">È possibile verificare il contenuto con il cmdlet [Get-Content](/powershell/module/microsoft.powershell.management/get-content).</span><span class="sxs-lookup"><span data-stu-id="c9c24-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="c9c24-142">È anche possibile *testare* lo stato corrente usando [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="c9c24-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="c9c24-143">L'output sarà "True" se il nodo è attualmente compatibile con la configurazione applicata.</span><span class="sxs-lookup"><span data-stu-id="c9c24-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="c9c24-144">Riapplicazione della configurazione</span><span class="sxs-lookup"><span data-stu-id="c9c24-144">Re-applying the configuration</span></span>

<span data-ttu-id="c9c24-145">Per applicare nuovamente la configurazione, è possibile rimuovere il file di testo creato dalla configurazione.</span><span class="sxs-lookup"><span data-stu-id="c9c24-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="c9c24-146">Quindi usare il cmdlet `Start-DSCConfiguration` con il parametro `-UseExisting`.</span><span class="sxs-lookup"><span data-stu-id="c9c24-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="c9c24-147">Il parametro `-UseExisting` indica a `Start-DSCConfiguration` di riapplicare il file "current.mof" che rappresenta l'ultima configurazione applicata correttamente.</span><span class="sxs-lookup"><span data-stu-id="c9c24-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="c9c24-148">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="c9c24-148">Next steps</span></span>

- <span data-ttu-id="c9c24-149">Ulteriori informazioni sulle configurazioni DSC sono disponibili in [Configurazioni DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c9c24-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="c9c24-150">Per informazioni sulle risorse DSC disponibili e su come creare risorse DSC personalizzate, vedere [Risorse DSC](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="c9c24-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="c9c24-151">Le configurazioni e le risorse DSC sono disponibili in [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="c9c24-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
