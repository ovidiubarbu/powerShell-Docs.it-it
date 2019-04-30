---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Applicare, ottenere e testare le configurazioni in un nodo
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079711"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="b661a-103">Applicare, ottenere e testare le configurazioni in un nodo</span><span class="sxs-lookup"><span data-stu-id="b661a-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="b661a-104">Questa Guida illustrerà come usare le configurazioni in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b661a-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="b661a-105">Questa guida è suddivisa nei seguenti passaggi:</span><span class="sxs-lookup"><span data-stu-id="b661a-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="b661a-106">Applicare una configurazione</span><span class="sxs-lookup"><span data-stu-id="b661a-106">Apply a Configuration</span></span>

<span data-ttu-id="b661a-107">Per applicare e gestire una configurazione, è necessario generare un file "MOF".</span><span class="sxs-lookup"><span data-stu-id="b661a-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="b661a-108">Il codice seguente rappresenta una configurazione semplice che verrà usata in questa guida.</span><span class="sxs-lookup"><span data-stu-id="b661a-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

<span data-ttu-id="b661a-109">La compilazione di questa configurazione restituirà due file "MOF".</span><span class="sxs-lookup"><span data-stu-id="b661a-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="b661a-110">Per applicare una configurazione usare il cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="b661a-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="b661a-111">Il parametro `-Path` specifica una directory in cui risiedono i file "MOF".</span><span class="sxs-lookup"><span data-stu-id="b661a-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="b661a-112">Se non è specificato `-Computername`, `Start-DSCConfiguration` tenterà di applicare ogni configurazione al nome del computer specificato dal nome del file 'MOF' (\<computername\>.mof).</span><span class="sxs-lookup"><span data-stu-id="b661a-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="b661a-113">Specificare `-Verbose` per `Start-DSCConfiguration` per visualizzare un output più dettagliato.</span><span class="sxs-lookup"><span data-stu-id="b661a-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="b661a-114">Se `-Wait` non è specificato, viene visualizzato un processo creato.</span><span class="sxs-lookup"><span data-stu-id="b661a-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="b661a-115">Il processo creato disporrà di un **ChildJob** per ogni file "MOF" elaborato da `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="b661a-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="b661a-116">Se una configurazione sta richiedendo molto tempo e si vuole arrestarla, è possibile usare [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) per arrestare l'applicazione nel nodo locale.</span><span class="sxs-lookup"><span data-stu-id="b661a-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="b661a-117">Al termine dell'operazione, è possibile visualizzare lo stato dei processi tramite l'oggetto processo restituito da [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="b661a-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="b661a-118">Per visualizzare l'output **dettagliato**, usare i seguenti comandi per visualizzare il flusso **dettagliato** per ogni **ChildJob**.</span><span class="sxs-lookup"><span data-stu-id="b661a-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="b661a-119">Per altre informazioni sui processi di PowerShell, vedere le [informazioni sui processi](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="b661a-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="b661a-120">A partire da PowerShell 5.0, il parametro `-UseExisting` è stato aggiunto a `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="b661a-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="b661a-121">Specificando `-UseExisting`, si indica al cmdlet di usare la configurazione esistente applicata invece di quella specificata dal parametro `-Path`.</span><span class="sxs-lookup"><span data-stu-id="b661a-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="b661a-122">Test di una configurazione</span><span class="sxs-lookup"><span data-stu-id="b661a-122">Test a Configuration</span></span>

<span data-ttu-id="b661a-123">È possibile testare una configurazione attualmente applicata mediante [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="b661a-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="b661a-124">`Test-DSCConfiguration` restituirà `True` se il nodo è conforme e `False` in caso contrario.</span><span class="sxs-lookup"><span data-stu-id="b661a-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="b661a-125">A partire da PowerShell 5.0, è stato aggiunto il parametro `-Detailed` che restituisce un oggetto con le raccolte per **ResourcesInDesiredState** e **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="b661a-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="b661a-126">A partire da PowerShell 5.0 è possibile testare una configurazione senza applicarla.</span><span class="sxs-lookup"><span data-stu-id="b661a-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="b661a-127">Il parametro `-ReferenceConfiguration` accetta il percorso di un file "MOF" per eseguire il test del nodo.</span><span class="sxs-lookup"><span data-stu-id="b661a-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="b661a-128">Non vengono intraprese azioni **Set** sul nodo.</span><span class="sxs-lookup"><span data-stu-id="b661a-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="b661a-129">In PowerShell 4.0, sono disponibili soluzioni alternative per testare una configurazione senza applicarla, ma non sono descritte qui.</span><span class="sxs-lookup"><span data-stu-id="b661a-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="b661a-130">Recuperare i valori della configurazione</span><span class="sxs-lookup"><span data-stu-id="b661a-130">Get Configuration Values</span></span>

<span data-ttu-id="b661a-131">Il cmdlet [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) restituisce i valori correnti per qualsiasi risorsa configurata nella configurazione attualmente applicata.</span><span class="sxs-lookup"><span data-stu-id="b661a-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="b661a-132">L'output della configurazione di esempio ha un aspetto simile al seguente se la configurazione è stata applicata correttamente.</span><span class="sxs-lookup"><span data-stu-id="b661a-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a><span data-ttu-id="b661a-133">Ottenere lo stato della configurazione</span><span class="sxs-lookup"><span data-stu-id="b661a-133">Get Configuration Status</span></span>

<span data-ttu-id="b661a-134">A partire da PowerShell 5.0 il cmdlet [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) consente di visualizzare la cronologia delle configurazioni applicate al nodo.</span><span class="sxs-lookup"><span data-stu-id="b661a-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="b661a-135">PowerShell DSC tiene traccia delle ultime configurazioni applicate {{N}} in modalità **Push** o **Pull**.</span><span class="sxs-lookup"><span data-stu-id="b661a-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="b661a-136">Ciò include eventuali verifiche di *coerenza* eseguite da Gestione configurazione locale (LCM).</span><span class="sxs-lookup"><span data-stu-id="b661a-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="b661a-137">Per impostazione predefinita, `Get-DSCConfigurationStatus` mostra solo l'ultima voce di cronologia.</span><span class="sxs-lookup"><span data-stu-id="b661a-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="b661a-138">Usare il parametro `-All` per visualizzare tutta la cronologia dello stato di configurazione.</span><span class="sxs-lookup"><span data-stu-id="b661a-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="b661a-139">L'output viene troncato per brevità.</span><span class="sxs-lookup"><span data-stu-id="b661a-139">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a><span data-ttu-id="b661a-140">Gestire i documenti di configurazione</span><span class="sxs-lookup"><span data-stu-id="b661a-140">Manage Configuration Documents</span></span>

<span data-ttu-id="b661a-141">Gestione configurazione locale (LCM) gestisce la configurazione del nodo usando i **documenti di configurazione**.</span><span class="sxs-lookup"><span data-stu-id="b661a-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="b661a-142">Questi file "MOF" si trovano nella directory "C:\Windows\System32\Configuration".</span><span class="sxs-lookup"><span data-stu-id="b661a-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="b661a-143">A partire da PowerShell 5.0 [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) consente di rimuovere i file "MOF" per interrompere verifiche coerenza future o per rimuovere una configurazione che restituisce errori quando applicata.</span><span class="sxs-lookup"><span data-stu-id="b661a-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="b661a-144">Il parametro `-Stage` consente di specificare quale file "MOF" si desidera rimuovere.</span><span class="sxs-lookup"><span data-stu-id="b661a-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="b661a-145">In PowerShell 4.0 è comunque possibile rimuovere i file "MOF" direttamente usando [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="b661a-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="b661a-146">Pubblicare le configurazioni</span><span class="sxs-lookup"><span data-stu-id="b661a-146">Publish Configurations</span></span>

<span data-ttu-id="b661a-147">A partire da PowerShell 5.0 è stato aggiunto il cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="b661a-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="b661a-148">Questo cmdlet consente di pubblicare un file "MOF" in computer remoti, senza applicarlo.</span><span class="sxs-lookup"><span data-stu-id="b661a-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="b661a-149">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b661a-149">See also</span></span>

- [<span data-ttu-id="b661a-150">Ottenere, testare e impostare</span><span class="sxs-lookup"><span data-stu-id="b661a-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
