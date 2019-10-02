---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Get-Test-Set
ms.openlocfilehash: 42c1df6df2fbf65cbbb8407db613cac2e5b81cfb
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323635"
---
# <a name="get-test-set"></a><span data-ttu-id="ade06-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="ade06-103">Get-Test-Set</span></span>

><span data-ttu-id="ade06-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ade06-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Ottenere, testare e impostare](../media/get-test-set.png)

<span data-ttu-id="ade06-106">La configurazione dello stato desiderato di PowerShell è costruita su un processo **Get**, **Test** e **Set**.</span><span class="sxs-lookup"><span data-stu-id="ade06-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="ade06-107">Le [risorse](resources.md) DSC contengono ciascuna i metodi per completare ognuna di queste operazioni.</span><span class="sxs-lookup"><span data-stu-id="ade06-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="ade06-108">In una [Configurazione](../configurations/configurations.md) vengono definiti blocchi di risorse in cui inserire chiavi che diventano i parametri per i metodi **Get**, **Test** e **Set** di una risorsa.</span><span class="sxs-lookup"><span data-stu-id="ade06-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="ade06-109">Questa è la sintassi per un blocco di risorse **Service**.</span><span class="sxs-lookup"><span data-stu-id="ade06-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="ade06-110">La risorsa **Service** configura i servizi di Windows.</span><span class="sxs-lookup"><span data-stu-id="ade06-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="ade06-111">I metodi **Get**, **Test** end **Set** della risorsa **Service** avranno blocchi di parametri che accettano questi valori.</span><span class="sxs-lookup"><span data-stu-id="ade06-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="ade06-112">Il linguaggio e il metodo usati per definire la risorsa determinano come definire i metodi **Get**, **Test** e **Set**.</span><span class="sxs-lookup"><span data-stu-id="ade06-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="ade06-113">Poiché la risorsa **Service** ha solo una chiave necessaria (`Name`), un blocco di risorse **Service** può essere semplice come il seguente:</span><span class="sxs-lookup"><span data-stu-id="ade06-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="ade06-114">Quando si compila la configurazione precedente, i valori specificati per una chiave vengono archiviati nel file "MOF" generato.</span><span class="sxs-lookup"><span data-stu-id="ade06-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="ade06-115">Per altre informazioni, vedere [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="ade06-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="ade06-116">Quando applicata, [Gestione configurazione locale](../managing-nodes/metaConfig.md) leggerà il valore "Spooler" dal file "MOF" e lo passerà al parametro `-Name` dei metodi **Get**, **Test** e **Set** per l'istanza "MyService" della risorsa **Service**.</span><span class="sxs-lookup"><span data-stu-id="ade06-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="ade06-117">Get</span><span class="sxs-lookup"><span data-stu-id="ade06-117">Get</span></span>

<span data-ttu-id="ade06-118">Il metodo **Get** di una risorsa recupera lo stato della risorsa così come è configurata nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ade06-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="ade06-119">Questo stato viene restituito come [TabellaHash](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="ade06-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="ade06-120">Le chiavi della **TabellaHash** saranno i valori configurabili, o parametri, accettati dalla risorsa.</span><span class="sxs-lookup"><span data-stu-id="ade06-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="ade06-121">Il metodo **Get** esegue il mapping direttamente sul cmdlet [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="ade06-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="ade06-122">Quando si richiama `Get-DSCConfiguration`, la gestione configurazione locale (LCM) esegue il metodo **Get** di ciascuna risorsa nella configurazione attualmente applicata.</span><span class="sxs-lookup"><span data-stu-id="ade06-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="ade06-123">Gestione configurazione locale (LCM) usa i valori di chiave archiviati come parametri nel file "MOF" per ogni istanza di risorsa corrispondente.</span><span class="sxs-lookup"><span data-stu-id="ade06-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="ade06-124">Questo è l'output di esempio di una risorsa **Service** che configura il servizio "Spooler".</span><span class="sxs-lookup"><span data-stu-id="ade06-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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
                       this service, you won't be able to print or see your printers.
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

<span data-ttu-id="ade06-125">L'output mostra le proprietà del valore correnti configurabili dalla risorsa **Service**.</span><span class="sxs-lookup"><span data-stu-id="ade06-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="ade06-126">Test</span><span class="sxs-lookup"><span data-stu-id="ade06-126">Test</span></span>

<span data-ttu-id="ade06-127">Il metodo **Test** di una risorsa determina se il nodo di destinazione è attualmente conforme con lo *stato desiderato* della risorsa.</span><span class="sxs-lookup"><span data-stu-id="ade06-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="ade06-128">Il metodo **Test** restituisce `$True` o `$False` solo per indicare se il nodo è conforme.</span><span class="sxs-lookup"><span data-stu-id="ade06-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="ade06-129">Quando si richiama [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) la gestione configurazione locale (LCM) richiama il metodo **Test** di tutte le risorse nella configurazione attualmente applicata.</span><span class="sxs-lookup"><span data-stu-id="ade06-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="ade06-130">Gestione configurazione locale (LCM) usa i valori di chiave archiviati come parametri nel file "MOF" per ogni istanza di risorsa corrispondente.</span><span class="sxs-lookup"><span data-stu-id="ade06-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="ade06-131">Se il risultato di qualsiasi **Test** di una singola risorsa è `$False`, `Test-DSCConfiguration` restituisce `$False` che indica che il nodo non è conforme.</span><span class="sxs-lookup"><span data-stu-id="ade06-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="ade06-132">Se tutte i metodi **Test** della risorsa restituiscono `$True`, `Test-DSCConfiguration` restituisce `$True` per indicare che il nodo è conforme.</span><span class="sxs-lookup"><span data-stu-id="ade06-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="ade06-133">A partire da PowerShell 5.0, è stato aggiunto il parametro `-Detailed`.</span><span class="sxs-lookup"><span data-stu-id="ade06-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="ade06-134">Se si specifica `-Detailed`, `Test-DSCConfiguration` restituisce un oggetto che contiene le raccolte dei risultati relativi alle risorse conformi e non conformi.</span><span class="sxs-lookup"><span data-stu-id="ade06-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="ade06-135">Per altre informazioni, vedere [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="ade06-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="ade06-136">Imposta</span><span class="sxs-lookup"><span data-stu-id="ade06-136">Set</span></span>

<span data-ttu-id="ade06-137">Il metodo **Set** di una risorsa tenta di forzare il nodo affinché diventi conforme con lo *stato desiderato* della risorsa.</span><span class="sxs-lookup"><span data-stu-id="ade06-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="ade06-138">Il metodo **Set** deve essere **idempotente**, che significa che **Set** potrebbe essere eseguito più volte e otterrà sempre lo stesso risultato senza errori.</span><span class="sxs-lookup"><span data-stu-id="ade06-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="ade06-139">Quando si esegue [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration) la gestione configurazione locale (LCM) passa da una risorsa all'altra nella configurazione attualmente applicata.</span><span class="sxs-lookup"><span data-stu-id="ade06-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="ade06-140">La gestione configurazione locale recupera i valori di chiave per l'istanza corrente delle risorse dal file "MOF" e li usa come parametri per il metodo **Test**.</span><span class="sxs-lookup"><span data-stu-id="ade06-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="ade06-141">Se il metodo **Test** restituisce `$True`, il nodo è conforme con la risorsa corrente e il metodo **Set** viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="ade06-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="ade06-142">Se **Test** restituisce `$False`, il nodo non è conforme.</span><span class="sxs-lookup"><span data-stu-id="ade06-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="ade06-143">La gestione configurazione locale (LCM) passa i valori di chiave dell'istanza della risorsa come parametri al metodo **Set** ripristinando la conformità del nodo.</span><span class="sxs-lookup"><span data-stu-id="ade06-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="ade06-144">Specificando i parametri `-Verbose` e `-Wait`, è possibile controllare lo stato di avanzamento del cmdlet `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="ade06-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="ade06-145">In questo esempio, il nodo è già conforme.</span><span class="sxs-lookup"><span data-stu-id="ade06-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="ade06-146">L'output `Verbose` indica che il metodo **Set** è stato ignorato.</span><span class="sxs-lookup"><span data-stu-id="ade06-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ade06-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ade06-147">See also</span></span>

- [<span data-ttu-id="ade06-148">Panoramica della piattaforma DSC di Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="ade06-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="ade06-149">Configurazione di un server di pull SMB</span><span class="sxs-lookup"><span data-stu-id="ade06-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="ade06-150">Configurazione di un client di pull</span><span class="sxs-lookup"><span data-stu-id="ade06-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
