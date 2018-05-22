---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForAll DSC
ms.openlocfilehash: 4413220bb0b5eeef5fd1599f794cd551f15a2925
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="24624-103">Risorsa WaitForAll DSC</span><span class="sxs-lookup"><span data-stu-id="24624-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="24624-104">Si applica a: Windows PowerShell 5.0 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="24624-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="24624-105">La risorsa DSC **WaitForAll** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](configurations.md) per specificare le dipendenze da configurazioni in altri nodi.</span><span class="sxs-lookup"><span data-stu-id="24624-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="24624-106">La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** è nello stato desiderato in tutti i nodi di destinazione definiti nella proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="24624-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="24624-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="24624-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="24624-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="24624-108">Properties</span></span>

|  <span data-ttu-id="24624-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="24624-109">Property</span></span>  |  <span data-ttu-id="24624-110">Description</span><span class="sxs-lookup"><span data-stu-id="24624-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="24624-111">NomeRisorsa</span><span class="sxs-lookup"><span data-stu-id="24624-111">ResourceName</span></span>| <span data-ttu-id="24624-112">Il nome della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="24624-112">The resource name to depend on.</span></span> <span data-ttu-id="24624-113">Se questa risorsa appartiene a un'altra configurazione, il formato del nome deve essere "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="24624-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="24624-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="24624-114">NodeName</span></span>| <span data-ttu-id="24624-115">I nodi di destinazione della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="24624-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="24624-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="24624-116">RetryIntervalSec</span></span>| <span data-ttu-id="24624-117">Il numero di secondi prima di riprovare.</span><span class="sxs-lookup"><span data-stu-id="24624-117">The number of seconds before retrying.</span></span> <span data-ttu-id="24624-118">Il valore minimo è 1.</span><span class="sxs-lookup"><span data-stu-id="24624-118">Minimum is 1.</span></span>|
| <span data-ttu-id="24624-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="24624-119">RetryCount</span></span>| <span data-ttu-id="24624-120">Il numero massimo di tentativi.</span><span class="sxs-lookup"><span data-stu-id="24624-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="24624-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="24624-121">ThrottleLimit</span></span>| <span data-ttu-id="24624-122">Numero di computer da connettere contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="24624-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="24624-123">Il valore predefinito è new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="24624-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="24624-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="24624-124">DependsOn</span></span> | <span data-ttu-id="24624-125">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="24624-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="24624-126">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="24624-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="24624-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="24624-127">Example</span></span>

<span data-ttu-id="24624-128">Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="24624-128">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>