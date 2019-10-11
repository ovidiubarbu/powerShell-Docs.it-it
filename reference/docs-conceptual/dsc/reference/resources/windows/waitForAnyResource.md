---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForAny DSC
ms.openlocfilehash: 61fee456d2652e08ed9bdbe64457627ff5b2e145
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952998"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="6ebb1-103">Risorsa WaitForAny DSC</span><span class="sxs-lookup"><span data-stu-id="6ebb1-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="6ebb1-104">Si applica a: Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="6ebb1-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="6ebb1-105">La risorsa DSC **WaitForAny** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](../../../configurations/configurations.md) per specificare le dipendenze da configurazioni in altri nodi.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="6ebb1-106">La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** è nello stato desiderato in tutti i nodi di destinazione definiti nella proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="6ebb1-107">La risorsa **WaitForAny** usa Gestione remota Windows per controllare lo stato degli altri nodi.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-107">**WaitForAny** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="6ebb1-108">Per altre informazioni sulla porta e sui requisiti di sicurezza per Gestione remota Windows, vedere [Considerazioni sulla sicurezza della comunicazione remota di PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="6ebb1-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="6ebb1-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6ebb1-109">Syntax</span></span>

```Syntax
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string[]]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="6ebb1-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6ebb1-110">Properties</span></span>

|<span data-ttu-id="6ebb1-111">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6ebb1-111">Property</span></span> |<span data-ttu-id="6ebb1-112">Description</span><span class="sxs-lookup"><span data-stu-id="6ebb1-112">Description</span></span> |
|---|---|
|<span data-ttu-id="6ebb1-113">NomeRisorsa</span><span class="sxs-lookup"><span data-stu-id="6ebb1-113">ResourceName</span></span> |<span data-ttu-id="6ebb1-114">Il nome della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-114">The resource name to depend on.</span></span> <span data-ttu-id="6ebb1-115">Se questa risorsa appartiene a una configurazione diversa, formattare il nome come `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-115">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="6ebb1-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="6ebb1-116">NodeName</span></span> |<span data-ttu-id="6ebb1-117">I nodi di destinazione della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-117">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="6ebb1-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="6ebb1-118">RetryIntervalSec</span></span> |<span data-ttu-id="6ebb1-119">Il numero di secondi prima di riprovare.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-119">The number of seconds before retrying.</span></span> <span data-ttu-id="6ebb1-120">Il valore minimo è 1.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-120">Minimum is 1.</span></span> |
|<span data-ttu-id="6ebb1-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="6ebb1-121">RetryCount</span></span> |<span data-ttu-id="6ebb1-122">Il numero massimo di tentativi.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-122">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="6ebb1-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6ebb1-123">ThrottleLimit</span></span> |<span data-ttu-id="6ebb1-124">Numero di computer da connettere contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="6ebb1-125">Il valore predefinito è `New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-125">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="6ebb1-126">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="6ebb1-126">Common properties</span></span>

|<span data-ttu-id="6ebb1-127">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6ebb1-127">Property</span></span> |<span data-ttu-id="6ebb1-128">Description</span><span class="sxs-lookup"><span data-stu-id="6ebb1-128">Description</span></span> |
|---|---|
|<span data-ttu-id="6ebb1-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6ebb1-129">DependsOn</span></span> |<span data-ttu-id="6ebb1-130">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6ebb1-131">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="6ebb1-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="6ebb1-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="6ebb1-133">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="6ebb1-134">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="6ebb1-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="6ebb1-135">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="6ebb1-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="6ebb1-136">Esempio</span><span class="sxs-lookup"><span data-stu-id="6ebb1-136">Example</span></span>

<span data-ttu-id="6ebb1-137">Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="6ebb1-137">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>