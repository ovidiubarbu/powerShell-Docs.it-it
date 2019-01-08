---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Specifica delle dipendenze tra nodi
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401164"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="a9a60-103">Specifica delle dipendenze tra nodi</span><span class="sxs-lookup"><span data-stu-id="a9a60-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="a9a60-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a9a60-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a9a60-105">DSC fornisce risorse speciali quali **WaitForAll**, **WaitForAny** e **WaitForSome** che possono essere usate nelle configurazioni per specificare le dipendenze nelle configurazioni di altri nodi.</span><span class="sxs-lookup"><span data-stu-id="a9a60-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="a9a60-106">Il comportamento di queste risorse è il seguente:</span><span class="sxs-lookup"><span data-stu-id="a9a60-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="a9a60-107">**WaitForAll**: Ha esito positivo se la risorsa specificata è nello stato desiderato in tutti i nodi di destinazione definito nel **NodeName** proprietà.</span><span class="sxs-lookup"><span data-stu-id="a9a60-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="a9a60-108">**WaitForAny**: Ha esito positivo se la risorsa specificata è nello stato desiderato in almeno uno dei nodi di destinazione definiti nel **NodeName** proprietà.</span><span class="sxs-lookup"><span data-stu-id="a9a60-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="a9a60-109">**WaitForSome**: Specifica un **NodeCount** oltre alla proprietà un **NodeName** proprietà.</span><span class="sxs-lookup"><span data-stu-id="a9a60-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="a9a60-110">La risorsa ha esito positivo se si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="a9a60-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="a9a60-111">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a9a60-111">Syntax</span></span>

<span data-ttu-id="a9a60-112">Il **WaitForAll** e **WaitForAny** risorse che condividono la stessa sintassi.</span><span class="sxs-lookup"><span data-stu-id="a9a60-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="a9a60-113">Sostituire \<ResourceType\> nell'esempio seguente con uno **WaitForAny** oppure **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="a9a60-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="a9a60-114">Ad esempio la **DependsOn** (parola chiave), è necessario formattare il nome come "[ResourceType] ResourceName".</span><span class="sxs-lookup"><span data-stu-id="a9a60-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="a9a60-115">Se la risorsa appartiene a un oggetto separato [Configuration](configurations.md), includono il **ConfigurationName** nella stringa di formato "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="a9a60-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="a9a60-116">Il **NodeName** è il computer o un nodo, in cui deve attendere la risorsa corrente.</span><span class="sxs-lookup"><span data-stu-id="a9a60-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="a9a60-117">Il **WaitForSome** risorsa presenta una sintassi simile all'esempio precedente, ma aggiunge le **NodeCount** chiave.</span><span class="sxs-lookup"><span data-stu-id="a9a60-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="a9a60-118">Il **NodeCount** indica il numero di nodi dovrebbe attendere la risorsa corrente.</span><span class="sxs-lookup"><span data-stu-id="a9a60-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="a9a60-119">Tutti i **WaitForXXXX** condividere le chiavi di sintassi seguenti.</span><span class="sxs-lookup"><span data-stu-id="a9a60-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="a9a60-120">|  Proprietà |  Descrizione | | RetryIntervalSec | Il numero di secondi prima di riprovare.</span><span class="sxs-lookup"><span data-stu-id="a9a60-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="a9a60-121">Valore minimo è 1. | | RetryCount | Il numero massimo di tentativi. | | ThrottleLimit | Numero di computer da connettere contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="a9a60-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="a9a60-122">Il valore predefinito è `New-CimSession` predefinito. | | DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="a9a60-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a9a60-123">Per altre informazioni, vedere [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | Vedere [uso di DSC con le credenziali dell'utente](./runAsUser.md) |</span><span class="sxs-lookup"><span data-stu-id="a9a60-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="a9a60-124">Uso delle risorse WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="a9a60-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="a9a60-125">Ciascuna **WaitForXXXX** attese risorse per le risorse specificate per il completamento nel nodo specificato.</span><span class="sxs-lookup"><span data-stu-id="a9a60-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="a9a60-126">Altre risorse nella stessa configurazione possono quindi *dipendono* le **WaitForXXXX** risorse usando il **DependsOn** chiave.</span><span class="sxs-lookup"><span data-stu-id="a9a60-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="a9a60-127">Nella configurazione seguente, ad esempio, il nodo di destinazione è in attesa del completamento della risorsa **xADDomain** nel nodo **MyDC** con un numero massimo di 30 tentativi, a intervalli di 15 secondi, prima che il nodo di destinazione possa essere aggiunto al dominio.</span><span class="sxs-lookup"><span data-stu-id="a9a60-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

<span data-ttu-id="a9a60-128">Quando si compila la configurazione, vengono generati due file di "MOF".</span><span class="sxs-lookup"><span data-stu-id="a9a60-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="a9a60-129">Applicare entrambi i file "MOF" ai nodi di destinazione usando il [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span><span class="sxs-lookup"><span data-stu-id="a9a60-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="a9a60-130">**Nota:** Per impostazione predefinita il WaitForXXX risorse prova una sola volta e quindi esito negativo.</span><span class="sxs-lookup"><span data-stu-id="a9a60-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="a9a60-131">Sebbene non sia obbligatorio, si sarà in genere consigliabile specificare una **RetryCount** e **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="a9a60-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9a60-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a9a60-132">See Also</span></span>

- [<span data-ttu-id="a9a60-133">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="a9a60-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="a9a60-134">Usare le dipendenze delle risorse</span><span class="sxs-lookup"><span data-stu-id="a9a60-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="a9a60-135">Risorse DSC</span><span class="sxs-lookup"><span data-stu-id="a9a60-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="a9a60-136">Configurazione di Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="a9a60-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
