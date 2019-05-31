---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurazioni DSC
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080176"
---
# <a name="dsc-configurations"></a><span data-ttu-id="223b8-103">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="223b8-103">DSC Configurations</span></span>

> <span data-ttu-id="223b8-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="223b8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="223b8-105">Le configurazioni DSC sono script di PowerShell che definiscono un tipo speciale di funzione.</span><span class="sxs-lookup"><span data-stu-id="223b8-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="223b8-106">Per definire una configurazione, usare la parola chiave **Configuration** di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="223b8-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

<span data-ttu-id="223b8-107">Salvare lo script come file `.ps1`.</span><span class="sxs-lookup"><span data-stu-id="223b8-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="223b8-108">Sintassi di configurazione</span><span class="sxs-lookup"><span data-stu-id="223b8-108">Configuration syntax</span></span>

<span data-ttu-id="223b8-109">Uno script di configurazione è costituito dalle parti seguenti:</span><span class="sxs-lookup"><span data-stu-id="223b8-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="223b8-110">Blocco **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="223b8-110">The **Configuration** block.</span></span> <span data-ttu-id="223b8-111">Si tratta del blocco più esterno dello script.</span><span class="sxs-lookup"><span data-stu-id="223b8-111">This is the outermost script block.</span></span> <span data-ttu-id="223b8-112">Per definirlo, usare la parola chiave **Configuration** e specificare un nome.</span><span class="sxs-lookup"><span data-stu-id="223b8-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="223b8-113">In questo caso, il nome della configurazione è "MyDscConfiguration".</span><span class="sxs-lookup"><span data-stu-id="223b8-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="223b8-114">Uno o più blocchi **Node**.</span><span class="sxs-lookup"><span data-stu-id="223b8-114">One or more **Node** blocks.</span></span> <span data-ttu-id="223b8-115">Definiscono i nodi (computer o macchine virtuali) configurati.</span><span class="sxs-lookup"><span data-stu-id="223b8-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="223b8-116">La configurazione precedente include un blocco **Node** che ha come destinazione un computer chiamato "TEST-PC1".</span><span class="sxs-lookup"><span data-stu-id="223b8-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="223b8-117">Il blocco del nodo può accettare più nomi di computer.</span><span class="sxs-lookup"><span data-stu-id="223b8-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="223b8-118">Uno o più blocchi di risorse.</span><span class="sxs-lookup"><span data-stu-id="223b8-118">One or more resource blocks.</span></span> <span data-ttu-id="223b8-119">Si tratta del punto in cui la configurazione imposta le proprietà per le risorse configurate.</span><span class="sxs-lookup"><span data-stu-id="223b8-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="223b8-120">In questo caso, sono presenti due blocchi di risorse, ognuno dei quali chiama la risorsa "WindowsFeature".</span><span class="sxs-lookup"><span data-stu-id="223b8-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="223b8-121">All'interno di un blocco **Configuration** è possibile eseguire tutte le operazioni che sono consentite anche in una funzione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="223b8-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="223b8-122">Ad esempio, se nell'esempio precedente non si vuole codificare il nome del computer di destinazione nella configurazione, è possibile aggiungere un parametro per il nome del nodo:</span><span class="sxs-lookup"><span data-stu-id="223b8-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="223b8-123">In questo esempio è necessario specificare il nome del nodo passandolo come parametro **ComputerName** quando si compila la configurazione.</span><span class="sxs-lookup"><span data-stu-id="223b8-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="223b8-124">Per impostazione predefinita, il nome è "localhost".</span><span class="sxs-lookup"><span data-stu-id="223b8-124">The name defaults to "localhost".</span></span>

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

<span data-ttu-id="223b8-125">Il blocco **Node** può accettare anche più nomi di computer.</span><span class="sxs-lookup"><span data-stu-id="223b8-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="223b8-126">Nell'esempio precedente è possibile usare il parametro `-ComputerName` o passare un elenco di computer delimitato da virgole direttamente al blocco **Node**.</span><span class="sxs-lookup"><span data-stu-id="223b8-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="223b8-127">Quando si specifica un elenco di computer per il blocco **Node** dall'interno di una configurazione, è necessario usare la notazione con matrice.</span><span class="sxs-lookup"><span data-stu-id="223b8-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a><span data-ttu-id="223b8-128">Compilazione della configurazione</span><span class="sxs-lookup"><span data-stu-id="223b8-128">Compiling the configuration</span></span>

<span data-ttu-id="223b8-129">Prima di poter applicare una configurazione, è necessario compilarla in un documento MOF.</span><span class="sxs-lookup"><span data-stu-id="223b8-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="223b8-130">A questo scopo, è necessario chiamare la configurazione allo stesso modo in cui si chiama una funzione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="223b8-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="223b8-131">L'ultima riga dell'esempio contenente solo il nome della configurazione, chiama la configurazione.</span><span class="sxs-lookup"><span data-stu-id="223b8-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="223b8-132">Per chiamare una configurazione, la funzione deve essere nell'ambito globale (come per qualsiasi funzione di PowerShell).</span><span class="sxs-lookup"><span data-stu-id="223b8-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="223b8-133">A questo scopo, è possibile effettuare il "dot-sourcing" dello script oppure eseguire lo script di configurazione premendo F5 o facendo clic sul pulsante **Esegui script** in ISE.</span><span class="sxs-lookup"><span data-stu-id="223b8-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="223b8-134">Per effettuare il dot-sourcing dello script, eseguire il comando `. .\myConfig.ps1`, dove `myConfig.ps1` è il nome del file di script che contiene la configurazione.</span><span class="sxs-lookup"><span data-stu-id="223b8-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="223b8-135">Quando si chiama la configurazione, si verificano gli scenari seguenti:</span><span class="sxs-lookup"><span data-stu-id="223b8-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="223b8-136">Risoluzione di tutte le variabili</span><span class="sxs-lookup"><span data-stu-id="223b8-136">Resolves all variables</span></span>
- <span data-ttu-id="223b8-137">Creazione di una cartella nella directory corrente con lo stesso nome della configurazione.</span><span class="sxs-lookup"><span data-stu-id="223b8-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="223b8-138">Creazione di un file denominato _NomeNodo_.mof nella nuova directory, dove _NomeNodo_ è il nome del nodo di destinazione della configurazione.</span><span class="sxs-lookup"><span data-stu-id="223b8-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="223b8-139">In presenza di più nodi, verrà creato un file MOF per ognuno.</span><span class="sxs-lookup"><span data-stu-id="223b8-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="223b8-140">Il file MOF contiene tutte le informazioni di configurazione per il nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="223b8-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="223b8-141">Per questo motivo, è importante garantirne la sicurezza.</span><span class="sxs-lookup"><span data-stu-id="223b8-141">Because of this, it’s important to keep it secure.</span></span>
> <span data-ttu-id="223b8-142">Per altre informazioni, vedere [Protezione del file MOF](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="223b8-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="223b8-143">La compilazione della prima configurazione sopra produce la struttura di cartelle seguente:</span><span class="sxs-lookup"><span data-stu-id="223b8-143">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

<span data-ttu-id="223b8-144">Se la configurazione accetta un parametro, come nel secondo esempio, il parametro deve essere specificato in fase di compilazione.</span><span class="sxs-lookup"><span data-stu-id="223b8-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="223b8-145">La configurazione avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="223b8-145">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="223b8-146">Uso di nuove risorse nella configurazione</span><span class="sxs-lookup"><span data-stu-id="223b8-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="223b8-147">Eseguendo gli esempi precedenti, si ricevere un avviso che informa che è stata usata una risorsa senza importarla in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="223b8-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="223b8-148">Oggi DSC include 12 risorse come parte del modulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="223b8-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="223b8-149">È possibile usare il cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) per determinare le risorse installate nel sistema e disponibili per l'uso da parte di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="223b8-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="223b8-150">Dopo che i moduli vengono inseriti in `$env:PSModulePath` e sono riconosciuti correttamente da [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), devono comunque essere caricati nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="223b8-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="223b8-151">**Import-DscResource** è una parola chiave dinamica che può essere riconosciuta solo all'interno di un blocco **Configuration** e non è un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="223b8-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="223b8-152">**Import-DscResource** supporta due parametri:</span><span class="sxs-lookup"><span data-stu-id="223b8-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="223b8-153">**ModuleName** corrisponde al modo consigliato di usare **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="223b8-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="223b8-154">Questo parametro accetta il nome del modulo che contiene le risorse da importare, nonché una matrice di stringhe di nomi di modulo.</span><span class="sxs-lookup"><span data-stu-id="223b8-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="223b8-155">**Name** è il nome della risorsa da importare.</span><span class="sxs-lookup"><span data-stu-id="223b8-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="223b8-156">Non si tratta del nome descrittivo restituito come "Name" da [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), ma del nome di classe usato per definire lo schema della risorsa (restituito come **ResourceType** da [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span><span class="sxs-lookup"><span data-stu-id="223b8-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="223b8-157">Per altre informazioni sull'uso di `Import-DSCResource`, vedere [Uso di Import-DSCResource](import-dscresource.md)</span><span class="sxs-lookup"><span data-stu-id="223b8-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="223b8-158">Differenze tra PowerShell v4 e v5</span><span class="sxs-lookup"><span data-stu-id="223b8-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="223b8-159">Esistono alcune differenze per la posizione di archiviazione delle risorse DSC in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="223b8-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="223b8-160">Per altre informazioni, vedere [Posizione delle risorse](import-dscresource.md#resource-location).</span><span class="sxs-lookup"><span data-stu-id="223b8-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="223b8-161">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="223b8-161">See Also</span></span>

- <span data-ttu-id="223b8-162">[Panoramica di Windows PowerShell DSC (Desired State Configuration)](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="223b8-162">[Windows PowerShell Desired State Configuration Overview](../overview/overview.md)</span></span>
- [<span data-ttu-id="223b8-163">Risorse DSC</span><span class="sxs-lookup"><span data-stu-id="223b8-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="223b8-164">Configurazione di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="223b8-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
