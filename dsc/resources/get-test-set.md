---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Get-Test-Set
ms.openlocfilehash: e46710954679bf20f4536c6efbcbd4dafd9e629e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401446"
---
# <a name="get-test-set"></a><span data-ttu-id="059fb-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="059fb-103">Get-Test-Set</span></span>

><span data-ttu-id="059fb-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="059fb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Ottenere, testare e impostare](/media/get-test-set.png)

<span data-ttu-id="059fb-106">PowerShell Desired State Configuration è costruito intorno a un **ottenere**, **Test**, e **impostare** processo.</span><span class="sxs-lookup"><span data-stu-id="059fb-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="059fb-107">DSC [risorse](resources.md) ognuno contiene metodi per completare ciascuna di queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="059fb-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="059fb-108">In un [Configuration](../configurations/configurations.md), è definire blocchi risorsa per riempire le chiavi che diventano i parametri per una risorsa **ottenere**, **Test**, e **impostata** metodi.</span><span class="sxs-lookup"><span data-stu-id="059fb-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="059fb-109">Si tratta la sintassi per un **servizio** blocco di risorse.</span><span class="sxs-lookup"><span data-stu-id="059fb-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="059fb-110">Il **servizio** risorse configura i servizi di Windows.</span><span class="sxs-lookup"><span data-stu-id="059fb-110">The **Service** resource configures Windows services.</span></span>

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="059fb-111">Il **ottenere**, **Test**, e **impostare** metodi del **servizio** risorse avranno blocchi dei parametri che accettano questi valori.</span><span class="sxs-lookup"><span data-stu-id="059fb-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> <span data-ttu-id="059fb-112">Determina la lingua e il metodo utilizzato per definire la risorsa come la **ottenere**, **Test**, e **impostare** verranno definiti i metodi.</span><span class="sxs-lookup"><span data-stu-id="059fb-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="059fb-113">Poiché il **servizio** risorsa ha solo una chiave necessaria (`Name`), una **servizio** risorsa di blocco potrebbe essere semplice come questa:</span><span class="sxs-lookup"><span data-stu-id="059fb-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

<span data-ttu-id="059fb-114">Quando si compila la configurazione precedente, i valori specificati per una chiave vengono archiviati nel file "MOF" generato.</span><span class="sxs-lookup"><span data-stu-id="059fb-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="059fb-115">Per altre informazioni, vedere [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="059fb-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

<span data-ttu-id="059fb-116">Quando applicata, la [Gestione configurazione locale](../managing-nodes/metaConfig.md) leggerà il valore "Spooler" dal file "MOF" e passarlo al `-Name` parametri del **ottenere**, **Test**, e **impostata** metodi per l'istanza "MyService" delle **servizio** risorsa.</span><span class="sxs-lookup"><span data-stu-id="059fb-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="059fb-117">Get</span><span class="sxs-lookup"><span data-stu-id="059fb-117">Get</span></span>

<span data-ttu-id="059fb-118">Il **ottenere** metodo di una risorsa, recupera lo stato della risorsa perché è configurata nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="059fb-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="059fb-119">Questo stato viene restituito come un [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="059fb-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="059fb-120">Le chiavi del **hashtable** saranno i valori configurabili, o parametri, accetta la risorsa.</span><span class="sxs-lookup"><span data-stu-id="059fb-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="059fb-121">Il **ottenere** metodo esegue il mapping direttamente alle [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="059fb-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="059fb-122">Quando si chiama `Get-DSCConfiguration`, le esecuzioni di Gestione configurazione locale le **ottenere** (metodo) di ogni risorsa nella configurazione attualmente applicata.</span><span class="sxs-lookup"><span data-stu-id="059fb-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="059fb-123">Gestione configurazione locale Usa i valori di chiave archiviati nel file "MOF" come parametri per ogni istanza di risorsa corrispondente.</span><span class="sxs-lookup"><span data-stu-id="059fb-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="059fb-124">Si tratta di output di esempio da un **servizio** risorse che consente di configurare il servizio "Spooler".</span><span class="sxs-lookup"><span data-stu-id="059fb-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won’t be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

<span data-ttu-id="059fb-125">L'output mostra le proprietà del valore corrente può essere configurato per il **servizio** risorsa.</span><span class="sxs-lookup"><span data-stu-id="059fb-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a><span data-ttu-id="059fb-126">Test</span><span class="sxs-lookup"><span data-stu-id="059fb-126">Test</span></span>

<span data-ttu-id="059fb-127">Il **Test** metodo di una risorsa determina se il nodo di destinazione è attualmente compatibile con la risorsa *stato desiderato*.</span><span class="sxs-lookup"><span data-stu-id="059fb-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="059fb-128">Il **Test** metodo restituisce `$True` o `$False` solo per indicare se il nodo è conforme.</span><span class="sxs-lookup"><span data-stu-id="059fb-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="059fb-129">Quando si chiama [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), le chiamate di Gestione configurazione locale le **Test** (metodo) di ogni risorsa nella configurazione attualmente applicata.</span><span class="sxs-lookup"><span data-stu-id="059fb-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="059fb-130">Gestione configurazione locale Usa i valori di chiave archiviati nel file "MOF" come parametri per ogni istanza di risorsa corrispondente.</span><span class="sxs-lookup"><span data-stu-id="059fb-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="059fb-131">Se il risultato di qualsiasi risorsa singole **Test** viene `$False`, `Test-DSCConfiguration` restituisce `$False` che indica che il nodo non è conforme.</span><span class="sxs-lookup"><span data-stu-id="059fb-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="059fb-132">Se tutte le risorse **Test** metodi restituiscono `$True`, `Test-DSCConfiguration` restituisce `$True` per indicare che il nodo è conforme.</span><span class="sxs-lookup"><span data-stu-id="059fb-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="059fb-133">A partire da PowerShell 5.0, il `-Detailed` è stato aggiunto il parametro.</span><span class="sxs-lookup"><span data-stu-id="059fb-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="059fb-134">Che specifica `-Detailed` provoca `Test-DSCConfiguration` per restituire un oggetto che contiene le raccolte di risultati per le risorse conformi e non conformi.</span><span class="sxs-lookup"><span data-stu-id="059fb-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="059fb-135">Per altre informazioni, vedere [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="059fb-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="059fb-136">Imposta</span><span class="sxs-lookup"><span data-stu-id="059fb-136">Set</span></span>

<span data-ttu-id="059fb-137">Il **impostata** metodo di una risorsa tenta di forzare il nodo per diventare conformi con la risorsa *stato desiderato*.</span><span class="sxs-lookup"><span data-stu-id="059fb-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="059fb-138">Il **impostata** metodo deve essere **idempotente**, che significa che **impostare** potrebbe essere eseguito più volte e otterrà sempre lo stesso risultato senza errori.</span><span class="sxs-lookup"><span data-stu-id="059fb-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="059fb-139">Quando si esegue [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), i cicli di Gestione configurazione locale tramite ogni risorsa nella configurazione attualmente applicata.</span><span class="sxs-lookup"><span data-stu-id="059fb-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="059fb-140">Gestione configurazione locale recupera i valori di chiave per l'istanza corrente di risorse dal file "MOF" e li usa come parametri per il **Test** (metodo).</span><span class="sxs-lookup"><span data-stu-id="059fb-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="059fb-141">Se il **Test** metodo restituisce `$True`, il nodo è conforme con la risorsa corrente e il **impostare** metodo è stato ignorato.</span><span class="sxs-lookup"><span data-stu-id="059fb-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="059fb-142">Se il **Test** restituisce `$False`, il nodo è non conforme.</span><span class="sxs-lookup"><span data-stu-id="059fb-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="059fb-143">Gestione configurazione locale passa la risorsa di valori di chiave dell'istanza come parametri per la risorsa **impostare** metodo, il ripristino del nodo per la conformità.</span><span class="sxs-lookup"><span data-stu-id="059fb-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="059fb-144">Specificando il `-Verbose` e `-Wait` i parametri, è possibile controllare lo stato di avanzamento del `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="059fb-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="059fb-145">In questo esempio, il nodo è già conforme.</span><span class="sxs-lookup"><span data-stu-id="059fb-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="059fb-146">Il `Verbose` output indica che il **impostare** metodo è stato ignorato.</span><span class="sxs-lookup"><span data-stu-id="059fb-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a><span data-ttu-id="059fb-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="059fb-147">See also</span></span>

- [<span data-ttu-id="059fb-148">Panoramica della piattaforma DSC di Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="059fb-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="059fb-149">Configurazione di un server di pull SMB</span><span class="sxs-lookup"><span data-stu-id="059fb-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="059fb-150">Configurazione di un client di pull</span><span class="sxs-lookup"><span data-stu-id="059fb-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
