---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Configurazioni DSC
ms.openlocfilehash: 2c2f8183ef586ff9371e4af7ea83db3e04fa68a4
ms.sourcegitcommit: 378c7ed4e8c8c1c5fe71417b9ba672a4c990630b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="dsc-configurations"></a><span data-ttu-id="c54e1-103">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="c54e1-103">DSC Configurations</span></span>

><span data-ttu-id="c54e1-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c54e1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c54e1-105">Le configurazioni DSC sono script di PowerShell che definiscono un tipo speciale di funzione.</span><span class="sxs-lookup"><span data-stu-id="c54e1-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span> <span data-ttu-id="c54e1-106">Per definire una configurazione, usare la parola chiave **Configuration** di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c54e1-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

<span data-ttu-id="c54e1-107">Salvare lo script come file PS1.</span><span class="sxs-lookup"><span data-stu-id="c54e1-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="c54e1-108">Sintassi di configurazione</span><span class="sxs-lookup"><span data-stu-id="c54e1-108">Configuration syntax</span></span>

<span data-ttu-id="c54e1-109">Uno script di configurazione è costituito dalle parti seguenti:</span><span class="sxs-lookup"><span data-stu-id="c54e1-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="c54e1-110">Blocco **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="c54e1-110">The **Configuration** block.</span></span> <span data-ttu-id="c54e1-111">Si tratta del blocco più esterno dello script.</span><span class="sxs-lookup"><span data-stu-id="c54e1-111">This is the outermost script block.</span></span> <span data-ttu-id="c54e1-112">Per definirlo, usare la parola chiave **Configuration** e specificare un nome.</span><span class="sxs-lookup"><span data-stu-id="c54e1-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="c54e1-113">In questo caso, il nome della configurazione è "MyDscConfiguration".</span><span class="sxs-lookup"><span data-stu-id="c54e1-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="c54e1-114">Uno o più blocchi **Node**.</span><span class="sxs-lookup"><span data-stu-id="c54e1-114">One or more **Node** blocks.</span></span> <span data-ttu-id="c54e1-115">Definiscono i nodi (computer o macchine virtuali) configurati.</span><span class="sxs-lookup"><span data-stu-id="c54e1-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="c54e1-116">La configurazione precedente include un blocco **Node** che ha come destinazione un computer chiamato "TEST-PC1".</span><span class="sxs-lookup"><span data-stu-id="c54e1-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="c54e1-117">Uno o più blocchi di risorse.</span><span class="sxs-lookup"><span data-stu-id="c54e1-117">One or more resource blocks.</span></span> <span data-ttu-id="c54e1-118">Si tratta del punto in cui la configurazione imposta le proprietà per le risorse configurate.</span><span class="sxs-lookup"><span data-stu-id="c54e1-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="c54e1-119">In questo caso, sono presenti due blocchi di risorse, ognuno dei quali chiama la risorsa "WindowsFeature".</span><span class="sxs-lookup"><span data-stu-id="c54e1-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="c54e1-120">All'interno di un blocco **Configuration** è possibile eseguire tutte le operazioni che sono consentite anche in una funzione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c54e1-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="c54e1-121">Ad esempio, se nell'esempio precedente non si vuole codificare il nome del computer di destinazione nella configurazione, è possibile aggiungere un parametro per il nome del nodo:</span><span class="sxs-lookup"><span data-stu-id="c54e1-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration -ComputerName <MyComputer>

```

<span data-ttu-id="c54e1-122">In questo esempio è necessario specificare il nome del nodo passandolo come parametro **ComputerName** quando si compila la configurazione.</span><span class="sxs-lookup"><span data-stu-id="c54e1-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="c54e1-123">Per impostazione predefinita, il nome è "localhost".</span><span class="sxs-lookup"><span data-stu-id="c54e1-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="c54e1-124">Compilazione della configurazione</span><span class="sxs-lookup"><span data-stu-id="c54e1-124">Compiling the configuration</span></span>

<span data-ttu-id="c54e1-125">Prima di poter applicare una configurazione, è necessario compilarla in un documento MOF.</span><span class="sxs-lookup"><span data-stu-id="c54e1-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span> <span data-ttu-id="c54e1-126">A questo scopo, è necessario chiamare la configurazione allo stesso modo in cui si chiama una funzione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c54e1-126">You do this by calling the configuration like you would a PowerShell function.</span></span>  
<span data-ttu-id="c54e1-127">L'ultima riga dell'esempio contenente solo il nome della configurazione, chiama la configurazione.</span><span class="sxs-lookup"><span data-stu-id="c54e1-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

><span data-ttu-id="c54e1-128">**Nota:** per chiamare una configurazione, la funzione deve essere nell'ambito globale (come per qualsiasi funzione di PowerShell).</span><span class="sxs-lookup"><span data-stu-id="c54e1-128">**Note:** To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span> 
><span data-ttu-id="c54e1-129">A questo scopo, è possibile effettuare il "dot-sourcing" dello script oppure eseguire lo script di configurazione premendo F5 o facendo clic sul pulsante **Esegui script** in ISE.</span><span class="sxs-lookup"><span data-stu-id="c54e1-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span> 
><span data-ttu-id="c54e1-130">Per effettuare il dot-sourcing dello script, eseguire il comando `. .\myConfig.ps1`, dove `myConfig.ps1` è il nome del file di script che contiene la configurazione.</span><span class="sxs-lookup"><span data-stu-id="c54e1-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="c54e1-131">Quando si chiama la configurazione, si verificano gli scenari seguenti:</span><span class="sxs-lookup"><span data-stu-id="c54e1-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="c54e1-132">Risoluzione di tutte le variabili</span><span class="sxs-lookup"><span data-stu-id="c54e1-132">Resolves all variables</span></span> 
- <span data-ttu-id="c54e1-133">Creazione di una cartella nella directory corrente con lo stesso nome della configurazione.</span><span class="sxs-lookup"><span data-stu-id="c54e1-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="c54e1-134">Creazione di un file denominato _NomeNodo_.mof nella nuova directory, dove _NomeNodo_ è il nome del nodo di destinazione della configurazione.</span><span class="sxs-lookup"><span data-stu-id="c54e1-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span> 
    <span data-ttu-id="c54e1-135">In presenza di più nodi, viene creato un file MOF per ognuno.</span><span class="sxs-lookup"><span data-stu-id="c54e1-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

><span data-ttu-id="c54e1-136">**Nota**: il file MOF contiene tutte le informazioni di configurazione per il nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="c54e1-136">**Note**: The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="c54e1-137">Per questo motivo, è importante garantirne la sicurezza.</span><span class="sxs-lookup"><span data-stu-id="c54e1-137">Because of this, it’s important to keep it secure.</span></span> 
><span data-ttu-id="c54e1-138">Per altre informazioni, vedere [Protezione del file MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="c54e1-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="c54e1-139">La compilazione della prima configurazione sopra produce la struttura di cartelle seguente:</span><span class="sxs-lookup"><span data-stu-id="c54e1-139">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="c54e1-140">Se la configurazione accetta un parametro, come nel secondo esempio, il parametro deve essere specificato in fase di compilazione.</span><span class="sxs-lookup"><span data-stu-id="c54e1-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="c54e1-141">La configurazione avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="c54e1-141">Here's how that would look:</span></span>

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

## <a name="using-dependson"></a><span data-ttu-id="c54e1-142">Uso di DependsOn</span><span class="sxs-lookup"><span data-stu-id="c54e1-142">Using DependsOn</span></span>

<span data-ttu-id="c54e1-143">Un'utile parola chiave di DSC è **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="c54e1-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="c54e1-144">In genere, anche se non necessariamente sempre, DSC applica le risorse nell'ordine in cui sono visualizzate all'interno della configurazione.</span><span class="sxs-lookup"><span data-stu-id="c54e1-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span> <span data-ttu-id="c54e1-145">Tuttavia, **DependsOn** specifica le dipendenze tra le risorse e Gestione configurazione locale garantisce che le risorse vengano applicate nell'ordine corretto, indipendentemente da quello in cui sono definite le rispettive istanze.</span><span class="sxs-lookup"><span data-stu-id="c54e1-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span> <span data-ttu-id="c54e1-146">Ad esempio, una configurazione può specificare che un'istanza della risorsa **User** dipende dalla presenza di un'istanza di **Group**:</span><span class="sxs-lookup"><span data-stu-id="c54e1-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="c54e1-147">Uso di nuove risorse nella configurazione</span><span class="sxs-lookup"><span data-stu-id="c54e1-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="c54e1-148">Eseguendo gli esempi precedenti, si ricevere un avviso che informa che è stata usata una risorsa senza importarla in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="c54e1-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="c54e1-149">Oggi DSC include 12 risorse come parte del modulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="c54e1-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span> <span data-ttu-id="c54e1-150">Le altre risorse nei moduli esterni devono essere inserite in `$env:PSModulePath` nell'ordine perché Gestione configurazione locale sia in grado di riconoscerle.</span><span class="sxs-lookup"><span data-stu-id="c54e1-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span> <span data-ttu-id="c54e1-151">È possibile usare un nuovo cmdlet, [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), per determinare le risorse installate nel sistema e disponibili per l'uso da parte di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="c54e1-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span> <span data-ttu-id="c54e1-152">Dopo che i moduli vengono inseriti in `$env:PSModulePath` e sono riconosciuti correttamente da [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), devono comunque essere caricati nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="c54e1-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span> 
<span data-ttu-id="c54e1-153">**Import-DscResource** è una parola chiave dinamica che può essere riconosciuta solo all'interno di un blocco **Configuration**, ovvero non è un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c54e1-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span> 
<span data-ttu-id="c54e1-154">**Import-DscResource** supporta due parametri:</span><span class="sxs-lookup"><span data-stu-id="c54e1-154">**Import-DscResource** supports two parameters:</span></span>
- <span data-ttu-id="c54e1-155">**ModuleName** corrisponde al modo consigliato di usare **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="c54e1-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="c54e1-156">Questo parametro accetta il nome del modulo che contiene le risorse da importare, nonché una matrice di stringhe di nomi di modulo.</span><span class="sxs-lookup"><span data-stu-id="c54e1-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span> 
- <span data-ttu-id="c54e1-157">**Name** è il nome della risorsa da importare.</span><span class="sxs-lookup"><span data-stu-id="c54e1-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="c54e1-158">Non si tratta del nome descrittivo restituito come "Name" da [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), ma del nome di classe usato per definire lo schema della risorsa (restituito come **ResourceType** da [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)).</span><span class="sxs-lookup"><span data-stu-id="c54e1-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)).</span></span> 

## <a name="see-also"></a><span data-ttu-id="c54e1-159">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c54e1-159">See Also</span></span>
* <span data-ttu-id="c54e1-160">[Panoramica di Windows PowerShell DSC (Desired State Configuration)](overview.md).</span><span class="sxs-lookup"><span data-stu-id="c54e1-160">[Windows PowerShell Desired State Configuration Overview](overview.md)</span></span>
* [<span data-ttu-id="c54e1-161">Risorse DSC</span><span class="sxs-lookup"><span data-stu-id="c54e1-161">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="c54e1-162">Configurazione di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="c54e1-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

