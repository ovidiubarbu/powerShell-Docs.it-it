---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Applicare, ottenere e testare le configurazioni in un nodo
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401723"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="06792-103">Applicare, ottenere e testare le configurazioni in un nodo</span><span class="sxs-lookup"><span data-stu-id="06792-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="06792-104">Questa Guida illustrerà come lavorare con le configurazioni in una nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="06792-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="06792-105">Questa guida è suddiviso in questa procedura:</span><span class="sxs-lookup"><span data-stu-id="06792-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="06792-106">Applicare una configurazione</span><span class="sxs-lookup"><span data-stu-id="06792-106">Apply a Configuration</span></span>

<span data-ttu-id="06792-107">Per applicare e gestire una configurazione, è necessario generare un file "con estensione MOF".</span><span class="sxs-lookup"><span data-stu-id="06792-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="06792-108">Il codice seguente rappresenta una semplice configurazione che verrà usata in questa Guida.</span><span class="sxs-lookup"><span data-stu-id="06792-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

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

<span data-ttu-id="06792-109">La compilazione di questa configurazione restituirà due file "con estensione MOF".</span><span class="sxs-lookup"><span data-stu-id="06792-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="06792-110">Per applicare una configurazione, usare il [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="06792-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="06792-111">Il `-Path` parametro specifica una directory in cui si trovano i file "MOF".</span><span class="sxs-lookup"><span data-stu-id="06792-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="06792-112">Se nessun `-Computername` viene specificato `Start-DSCConfiguration` tenterà di applicare ogni configurazione per il nome del computer specificato dal nome del file 'file MOF' (\<nomecomputer\>MOF).</span><span class="sxs-lookup"><span data-stu-id="06792-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="06792-113">Specificare `-Verbose` a `Start-DSCConfiguration` per visualizzare un output più dettagliato.</span><span class="sxs-lookup"><span data-stu-id="06792-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="06792-114">Se `-Wait` non viene specificato, viene visualizzato un processo creato.</span><span class="sxs-lookup"><span data-stu-id="06792-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="06792-115">Il processo creato disporrà di uno **ChildJob** per ogni file "MOF" elaborate dal `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="06792-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="06792-116">Se una configurazione sta richiedendo molto tempo e si vuole arrestarla, è possibile usare [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) per arrestare l'applicazione nel nodo locale.</span><span class="sxs-lookup"><span data-stu-id="06792-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="06792-117">Al termine dell'operazione, è possibile visualizzare lo stato dei processi tramite l'oggetto processo restituito da [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="06792-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

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

<span data-ttu-id="06792-118">Per visualizzare il **Verbose** di output, usare i comandi seguenti per visualizzare i **Verbose** stream per ogni **ChildJob**.</span><span class="sxs-lookup"><span data-stu-id="06792-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="06792-119">Per altre informazioni sui processi di PowerShell, vedere [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="06792-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

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

<span data-ttu-id="06792-120">A partire da PowerShell 5.0, il `-UseExisting` parametro è stato aggiunto al `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="06792-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="06792-121">Specificando `-UseExisting`, è indicare al cmdlet per usare la configurazione applicata esistente invece di quella specificata per il `-Path` parametro.</span><span class="sxs-lookup"><span data-stu-id="06792-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="06792-122">Testare una configurazione</span><span class="sxs-lookup"><span data-stu-id="06792-122">Test a Configuration</span></span>

<span data-ttu-id="06792-123">È possibile testare una configurazione attualmente applicata mediante [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="06792-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="06792-124">`Test-DSCConfiguration` restituirà `True` se il nodo è conforme, e `False` in caso contrario.</span><span class="sxs-lookup"><span data-stu-id="06792-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="06792-125">A partire da PowerShell 5.0, il `-Detailed` parametro è stato aggiunto che restituisce un oggetto con le raccolte per **ResourcesInDesiredState** e **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="06792-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="06792-126">A partire da PowerShell 5.0 è possibile testare una configurazione senza applicarlo.</span><span class="sxs-lookup"><span data-stu-id="06792-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="06792-127">Il `-ReferenceConfiguration` parametro accetta il percorso di un file "MOF" per eseguire il test di nodo rispetto.</span><span class="sxs-lookup"><span data-stu-id="06792-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="06792-128">No **impostare** azioni vengono eseguite nel nodo.</span><span class="sxs-lookup"><span data-stu-id="06792-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="06792-129">In PowerShell 4.0, sono disponibili soluzioni alternative per testare una configurazione senza applicarlo, ma non vengano descritti di seguito.</span><span class="sxs-lookup"><span data-stu-id="06792-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="06792-130">Ottenere i valori di configurazione</span><span class="sxs-lookup"><span data-stu-id="06792-130">Get Configuration Values</span></span>

<span data-ttu-id="06792-131">Il [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet restituisce i valori correnti per qualsiasi risorsa configurata nella configurazione attualmente applicata.</span><span class="sxs-lookup"><span data-stu-id="06792-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="06792-132">Output di esempio configurazione avrebbe un aspetto simile al seguente se è stata applicata.</span><span class="sxs-lookup"><span data-stu-id="06792-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

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

## <a name="get-configuration-status"></a><span data-ttu-id="06792-133">Ottenere lo stato di configurazione</span><span class="sxs-lookup"><span data-stu-id="06792-133">Get Configuration Status</span></span>

<span data-ttu-id="06792-134">A partire da PowerShell 5.0 il [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet consente di visualizzare la cronologia delle configurazioni applicate al nodo.</span><span class="sxs-lookup"><span data-stu-id="06792-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="06792-135">PowerShell DSC tiene traccia delle ultime configurazioni di {{N}} applicate in **Push** oppure **Pull** modalità.</span><span class="sxs-lookup"><span data-stu-id="06792-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="06792-136">Ciò include eventuali *coerenza* controlli eseguiti da Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="06792-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="06792-137">Per impostazione predefinita, `Get-DSCConfigurationStatus` Mostra solo l'ultima voce di cronologia.</span><span class="sxs-lookup"><span data-stu-id="06792-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="06792-138">Usare il `-All` parametro per visualizzare tutta la cronologia dello stato di configurazione.</span><span class="sxs-lookup"><span data-stu-id="06792-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="06792-139">Output viene troncato per brevità.</span><span class="sxs-lookup"><span data-stu-id="06792-139">Output is truncated for brevity.</span></span>

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

## <a name="manage-configuration-documents"></a><span data-ttu-id="06792-140">Gestire i documenti di configurazione</span><span class="sxs-lookup"><span data-stu-id="06792-140">Manage Configuration Documents</span></span>

<span data-ttu-id="06792-141">Gestione configurazione locale gestisce la configurazione del nodo consultando **documenti di configurazione**.</span><span class="sxs-lookup"><span data-stu-id="06792-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="06792-142">Questi file "MOF" si trovano nella directory "C:\Windows\System32\Configuration".</span><span class="sxs-lookup"><span data-stu-id="06792-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="06792-143">A partire da PowerShell 5.0 il [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) consente di rimuovere i file "MOF" per interrompere verifiche di coerenza futura o rimuovere una configurazione con errori quando vengono applicate.</span><span class="sxs-lookup"><span data-stu-id="06792-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="06792-144">Il `-Stage` parametro consente di specificare quali file "MOF" che si desidera rimuovere.</span><span class="sxs-lookup"><span data-stu-id="06792-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="06792-145">In PowerShell 4.0, è comunque possibile rimuovere questi file "MOF" direttamente usando [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="06792-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="06792-146">Pubblicare le configurazioni</span><span class="sxs-lookup"><span data-stu-id="06792-146">Publish Configurations</span></span>

<span data-ttu-id="06792-147">A partire da PowerShell 5.0, il [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) è stato aggiunto il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="06792-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="06792-148">Questo cmdlet consente di pubblicare un file "con estensione MOF" a computer remoti, senza applicarlo.</span><span class="sxs-lookup"><span data-stu-id="06792-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="06792-149">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="06792-149">See also</span></span>

- [<span data-ttu-id="06792-150">Ottenere, testare e impostare</span><span class="sxs-lookup"><span data-stu-id="06792-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
