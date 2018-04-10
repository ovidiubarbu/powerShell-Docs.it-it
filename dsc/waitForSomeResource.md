---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForSome DSC
ms.openlocfilehash: 8132b584fad350530f6fc80175980881a399ac2e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="9b951-103">Risorsa WaitForSome DSC</span><span class="sxs-lookup"><span data-stu-id="9b951-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="9b951-104">Si applica a: Windows PowerShell 5.0 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="9b951-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="9b951-105">La risorsa DSC **WaitForAny** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](configurations.md) per specificare le dipendenze da configurazioni in altri nodi.</span><span class="sxs-lookup"><span data-stu-id="9b951-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="9b951-106">La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="9b951-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="9b951-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9b951-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="9b951-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9b951-108">Properties</span></span>

|  <span data-ttu-id="9b951-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="9b951-109">Property</span></span>  |  <span data-ttu-id="9b951-110">Description</span><span class="sxs-lookup"><span data-stu-id="9b951-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="9b951-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="9b951-111">NodeCount</span></span>| <span data-ttu-id="9b951-112">Il numero minimo di nodi che devono essere nello stato desiderato perché la risorsa abbia esito positivo.</span><span class="sxs-lookup"><span data-stu-id="9b951-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="9b951-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="9b951-113">NodeName</span></span>| <span data-ttu-id="9b951-114">I nodi di destinazione della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="9b951-114">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="9b951-115">NomeRisorsa</span><span class="sxs-lookup"><span data-stu-id="9b951-115">ResourceName</span></span>| <span data-ttu-id="9b951-116">Il nome della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="9b951-116">The resource name to depend on.</span></span> <span data-ttu-id="9b951-117">Se questa risorsa appartiene a un'altra configurazione, il formato del nome deve essere "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="9b951-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="9b951-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="9b951-118">RetryIntervalSec</span></span>| <span data-ttu-id="9b951-119">Il numero di secondi prima di riprovare.</span><span class="sxs-lookup"><span data-stu-id="9b951-119">The number of seconds before retrying.</span></span> <span data-ttu-id="9b951-120">Il valore minimo è 1.</span><span class="sxs-lookup"><span data-stu-id="9b951-120">Minimum is 1.</span></span>|
| <span data-ttu-id="9b951-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="9b951-121">RetryCount</span></span>| <span data-ttu-id="9b951-122">Il numero massimo di tentativi.</span><span class="sxs-lookup"><span data-stu-id="9b951-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="9b951-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="9b951-123">ThrottleLimit</span></span>| <span data-ttu-id="9b951-124">Numero di computer da connettere contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="9b951-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="9b951-125">Il valore predefinito è new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="9b951-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="9b951-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9b951-126">DependsOn</span></span> | <span data-ttu-id="9b951-127">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="9b951-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9b951-128">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="9b951-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="9b951-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="9b951-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="9b951-130">Vedere [Esecuzione di DSC con le credenziali dell'utente](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="9b951-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="9b951-131">Esempio</span><span class="sxs-lookup"><span data-stu-id="9b951-131">Example</span></span>

<span data-ttu-id="9b951-132">Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="9b951-132">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>