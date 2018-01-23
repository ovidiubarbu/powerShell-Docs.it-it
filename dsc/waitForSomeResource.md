---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForSome DSC
ms.openlocfilehash: cbe16c543f0eeb62dbe1fb439af2f9147f1bc210
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="d40aa-103">Risorsa WaitForSome DSC</span><span class="sxs-lookup"><span data-stu-id="d40aa-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="d40aa-104">Si applica a: Windows PowerShell 5.0 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="d40aa-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="d40aa-105">La risorsa DSC **WaitForAny** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](configurations.md) per specificare le dipendenze da configurazioni in altri nodi.</span><span class="sxs-lookup"><span data-stu-id="d40aa-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="d40aa-106">La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="d40aa-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="d40aa-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d40aa-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="d40aa-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d40aa-108">Properties</span></span>

|  <span data-ttu-id="d40aa-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d40aa-109">Property</span></span>  |  <span data-ttu-id="d40aa-110">Description</span><span class="sxs-lookup"><span data-stu-id="d40aa-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="d40aa-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="d40aa-111">NodeCount</span></span>| <span data-ttu-id="d40aa-112">Il numero minimo di nodi che devono essere nello stato desiderato perché la risorsa abbia esito positivo.</span><span class="sxs-lookup"><span data-stu-id="d40aa-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="d40aa-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="d40aa-113">NodeName</span></span>| <span data-ttu-id="d40aa-114">I nodi di destinazione della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="d40aa-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="d40aa-115">NomeRisorsa</span><span class="sxs-lookup"><span data-stu-id="d40aa-115">ResourceName</span></span>| <span data-ttu-id="d40aa-116">Il nome della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="d40aa-116">The resource name to depend on.</span></span>| 
| <span data-ttu-id="d40aa-117">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="d40aa-117">RetryIntervalSec</span></span>| <span data-ttu-id="d40aa-118">Il numero di secondi prima di riprovare.</span><span class="sxs-lookup"><span data-stu-id="d40aa-118">The number of seconds before retrying.</span></span> <span data-ttu-id="d40aa-119">Il valore minimo è 1.</span><span class="sxs-lookup"><span data-stu-id="d40aa-119">Minimum is 1.</span></span>| 
| <span data-ttu-id="d40aa-120">RetryCount</span><span class="sxs-lookup"><span data-stu-id="d40aa-120">RetryCount</span></span>| <span data-ttu-id="d40aa-121">Il numero massimo di tentativi.</span><span class="sxs-lookup"><span data-stu-id="d40aa-121">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="d40aa-122">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="d40aa-122">ThrottleLimit</span></span>| <span data-ttu-id="d40aa-123">Numero di computer da connettere contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="d40aa-123">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="d40aa-124">Il valore predefinito è new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="d40aa-124">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="d40aa-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d40aa-125">DependsOn</span></span> | <span data-ttu-id="d40aa-126">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="d40aa-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d40aa-127">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d40aa-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="d40aa-128">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d40aa-128">PsDscRunAsCredential</span></span> | <span data-ttu-id="d40aa-129">Vedere [Esecuzione di DSC con le credenziali dell'utente](https://docs.microsoft.com/en-us/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="d40aa-129">See [Using DSC with User Credentials](https://docs.microsoft.com/en-us/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="d40aa-130">Esempio</span><span class="sxs-lookup"><span data-stu-id="d40aa-130">Example</span></span>

<span data-ttu-id="d40aa-131">Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="d40aa-131">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

