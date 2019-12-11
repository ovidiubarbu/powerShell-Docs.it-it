---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Specifica delle dipendenze tra nodi
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954108"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="4aebd-103">Specifica delle dipendenze tra nodi</span><span class="sxs-lookup"><span data-stu-id="4aebd-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="4aebd-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4aebd-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4aebd-105">DSC fornisce risorse speciali quali **WaitForAll**, **WaitForAny** e **WaitForSome** che possono essere usate nelle configurazioni per specificare le dipendenze nelle configurazioni di altri nodi.</span><span class="sxs-lookup"><span data-stu-id="4aebd-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="4aebd-106">Il comportamento di queste risorse è il seguente:</span><span class="sxs-lookup"><span data-stu-id="4aebd-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="4aebd-107">**WaitForAll**: ha esito positivo se la risorsa specificata è nello stato desiderato in tutti i nodi di destinazione definiti nella proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="4aebd-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="4aebd-108">**WaitForAny**: ha esito positivo se la risorsa specificata è nello stato desiderato in almeno uno dei nodi di destinazione definiti nella proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="4aebd-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="4aebd-109">**WaitForSome**: specifica una proprietà **NodeCount** oltre alla proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="4aebd-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="4aebd-110">La risorsa ha esito positivo se si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="4aebd-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="4aebd-111">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4aebd-111">Syntax</span></span>

<span data-ttu-id="4aebd-112">Le risorse **WaitForAll** e **WaitForAny** condividono la stessa sintassi.</span><span class="sxs-lookup"><span data-stu-id="4aebd-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="4aebd-113">Sostituire \<ResourceType\> nell'esempio seguente con **WaitForAny** oppure **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="4aebd-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="4aebd-114">Come per la parola chiave **DependsOn**, sarà necessario formattare il nome come "[ResourceType]ResourceName".</span><span class="sxs-lookup"><span data-stu-id="4aebd-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="4aebd-115">Se la risorsa appartiene a un oggetto [Configuration](configurations.md) separato, includere **ConfigurationName** nella stringa formattata "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="4aebd-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="4aebd-116">**NodeName** è il computer o il nodo su cui deve restare in attesa la risorsa corrente.</span><span class="sxs-lookup"><span data-stu-id="4aebd-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

<span data-ttu-id="4aebd-117">La risorsa **WaitForSome** ha una sintassi simile all'esempio precedente, ma aggiunge la chiave **NodeCount**.</span><span class="sxs-lookup"><span data-stu-id="4aebd-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="4aebd-118">**NodeCount** indica il numero di nodi su cui deve restare in attesa la risorsa corrente.</span><span class="sxs-lookup"><span data-stu-id="4aebd-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

<span data-ttu-id="4aebd-119">Tutte le risorse **WaitForXXXX** condividono le chiavi di sintassi seguenti.</span><span class="sxs-lookup"><span data-stu-id="4aebd-119">All **WaitForXXXX** share the following syntax keys.</span></span>

|<span data-ttu-id="4aebd-120">Proprietà</span><span class="sxs-lookup"><span data-stu-id="4aebd-120">Property</span></span>|  <span data-ttu-id="4aebd-121">Description</span><span class="sxs-lookup"><span data-stu-id="4aebd-121">Description</span></span>   |
|---------|---------------------|
| <span data-ttu-id="4aebd-122">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="4aebd-122">RetryIntervalSec</span></span>| <span data-ttu-id="4aebd-123">Il numero di secondi prima di riprovare.</span><span class="sxs-lookup"><span data-stu-id="4aebd-123">The number of seconds before retrying.</span></span> <span data-ttu-id="4aebd-124">Il valore minimo è 1.</span><span class="sxs-lookup"><span data-stu-id="4aebd-124">Minimum is 1.</span></span>|
| <span data-ttu-id="4aebd-125">RetryCount</span><span class="sxs-lookup"><span data-stu-id="4aebd-125">RetryCount</span></span>| <span data-ttu-id="4aebd-126">Il numero massimo di tentativi.</span><span class="sxs-lookup"><span data-stu-id="4aebd-126">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="4aebd-127">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="4aebd-127">ThrottleLimit</span></span>| <span data-ttu-id="4aebd-128">Numero di computer da connettere contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="4aebd-128">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="4aebd-129">Il valore predefinito è `New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="4aebd-129">Default is `New-CimSession` default.</span></span>|
| <span data-ttu-id="4aebd-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4aebd-130">DependsOn</span></span> | <span data-ttu-id="4aebd-131">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="4aebd-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4aebd-132">Per altre informazioni, vedere [DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="4aebd-132">For more information, see [DependsOn](resource-depends-on.md)</span></span>|
| <span data-ttu-id="4aebd-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4aebd-133">PsDscRunAsCredential</span></span> | <span data-ttu-id="4aebd-134">Vedere [Esecuzione di DSC con le credenziali dell'utente](./runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="4aebd-134">See [Using DSC with User Credentials](./runAsUser.md)</span></span> |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="4aebd-135">Uso delle risorse WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="4aebd-135">Using WaitForXXXX resources</span></span>

<span data-ttu-id="4aebd-136">Ogni risorsa **WaitForXXXX** attende il completamento delle risorse specificate sul nodo specificato.</span><span class="sxs-lookup"><span data-stu-id="4aebd-136">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="4aebd-137">Altre risorse nella stessa configurazione possono quindi *dipendere* dalla risorsa **WaitForXXXX** tramite la chiave **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="4aebd-137">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="4aebd-138">Nella configurazione seguente, ad esempio, il nodo di destinazione è in attesa del completamento della risorsa **xADDomain** nel nodo **MyDC** con un numero massimo di 30 tentativi, a intervalli di 15 secondi, prima che il nodo di destinazione possa essere aggiunto al dominio.</span><span class="sxs-lookup"><span data-stu-id="4aebd-138">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="4aebd-139">Per impostazione predefinita, le risorse **WaitForXXX** eseguono un solo tentativo prima dell'esito negativo.</span><span class="sxs-lookup"><span data-stu-id="4aebd-139">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="4aebd-140">Sebbene non sia obbligatorio, è consigliabile specificare **RetryCount** e **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="4aebd-140">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

<span data-ttu-id="4aebd-141">Quando si compila la configurazione vengono generati due file "MOF".</span><span class="sxs-lookup"><span data-stu-id="4aebd-141">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="4aebd-142">Applicare entrambi i file "MOF" ai nodi di destinazione usando il cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)</span><span class="sxs-lookup"><span data-stu-id="4aebd-142">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="4aebd-143">Le risorse **WaitForXXX** usano Gestione remota Windows per controllare lo stato degli altri nodi.</span><span class="sxs-lookup"><span data-stu-id="4aebd-143">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="4aebd-144">Per altre informazioni sulla porta e sui requisiti di sicurezza per Gestione remota Windows, vedere [Considerazioni sulla sicurezza della comunicazione remota di PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="4aebd-144">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="see-also"></a><span data-ttu-id="4aebd-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4aebd-145">See Also</span></span>

- [<span data-ttu-id="4aebd-146">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="4aebd-146">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="4aebd-147">Usare le dipendenze delle risorse</span><span class="sxs-lookup"><span data-stu-id="4aebd-147">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="4aebd-148">Risorse DSC</span><span class="sxs-lookup"><span data-stu-id="4aebd-148">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="4aebd-149">Configurazione di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="4aebd-149">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
