---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForSome DSC
ms.openlocfilehash: 91589c84518a2bd0f4816d11aa011dec1d5305e1
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952978"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="9d640-103">Risorsa WaitForSome DSC</span><span class="sxs-lookup"><span data-stu-id="9d640-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="9d640-104">Si applica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="9d640-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="9d640-105">La risorsa DSC **WaitForSome** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](../../../configurations/configurations.md) per specificare le dipendenze da configurazioni in altri nodi.</span><span class="sxs-lookup"><span data-stu-id="9d640-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="9d640-106">La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="9d640-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="9d640-107">La risorsa **WaitForSome** usa Gestione remota Windows per controllare lo stato degli altri nodi.</span><span class="sxs-lookup"><span data-stu-id="9d640-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="9d640-108">Per altre informazioni sulla porta e sui requisiti di sicurezza per Gestione remota Windows, vedere [Considerazioni sulla sicurezza della comunicazione remota di PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="9d640-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="9d640-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9d640-109">Syntax</span></span>

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="9d640-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9d640-110">Properties</span></span>

|<span data-ttu-id="9d640-111">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9d640-111">Property</span></span> |<span data-ttu-id="9d640-112">Description</span><span class="sxs-lookup"><span data-stu-id="9d640-112">Description</span></span> |
|---|---|
|<span data-ttu-id="9d640-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="9d640-113">NodeCount</span></span> |<span data-ttu-id="9d640-114">Il numero minimo di nodi che devono essere nello stato desiderato perché la risorsa abbia esito positivo.</span><span class="sxs-lookup"><span data-stu-id="9d640-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span> |
|<span data-ttu-id="9d640-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="9d640-115">NodeName</span></span> |<span data-ttu-id="9d640-116">I nodi di destinazione della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="9d640-116">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="9d640-117">NomeRisorsa</span><span class="sxs-lookup"><span data-stu-id="9d640-117">ResourceName</span></span> |<span data-ttu-id="9d640-118">Il nome della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="9d640-118">The resource name to depend on.</span></span> <span data-ttu-id="9d640-119">Se questa risorsa appartiene a una configurazione diversa, formattare il nome come `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span><span class="sxs-lookup"><span data-stu-id="9d640-119">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="9d640-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="9d640-120">RetryIntervalSec</span></span> |<span data-ttu-id="9d640-121">Il numero di secondi prima di riprovare.</span><span class="sxs-lookup"><span data-stu-id="9d640-121">The number of seconds before retrying.</span></span> <span data-ttu-id="9d640-122">Il valore minimo è 1.</span><span class="sxs-lookup"><span data-stu-id="9d640-122">Minimum is 1.</span></span> |
|<span data-ttu-id="9d640-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="9d640-123">RetryCount</span></span> |<span data-ttu-id="9d640-124">Il numero massimo di tentativi.</span><span class="sxs-lookup"><span data-stu-id="9d640-124">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="9d640-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="9d640-125">ThrottleLimit</span></span> |<span data-ttu-id="9d640-126">Numero di computer da connettere contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="9d640-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="9d640-127">Il valore predefinito è `New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="9d640-127">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="9d640-128">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="9d640-128">Common properties</span></span>

|<span data-ttu-id="9d640-129">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9d640-129">Property</span></span> |<span data-ttu-id="9d640-130">Description</span><span class="sxs-lookup"><span data-stu-id="9d640-130">Description</span></span> |
|---|---|
|<span data-ttu-id="9d640-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9d640-131">DependsOn</span></span> |<span data-ttu-id="9d640-132">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="9d640-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9d640-133">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="9d640-133">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="9d640-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="9d640-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="9d640-135">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="9d640-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="9d640-136">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="9d640-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="9d640-137">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="9d640-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="9d640-138">Esempio</span><span class="sxs-lookup"><span data-stu-id="9d640-138">Example</span></span>

<span data-ttu-id="9d640-139">Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="9d640-139">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>