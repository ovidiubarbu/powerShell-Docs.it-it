---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa WaitForAny DSC
ms.openlocfilehash: ba1873cc0ecfc4596cbad5b61b4a52b61ea4778a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="a8c5b-103">Risorsa WaitForAny DSC</span><span class="sxs-lookup"><span data-stu-id="a8c5b-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="a8c5b-104">Si applica a: Windows PowerShell 5.1 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="a8c5b-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="a8c5b-105">La risorsa DSC **WaitForSome** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](configurations.md) per specificare le dipendenze da configurazioni in altri nodi.</span><span class="sxs-lookup"><span data-stu-id="a8c5b-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="a8c5b-106">La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** è nello stato desiderato in qualsiasi nodo di destinazione definito nella proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="a8c5b-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="a8c5b-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a8c5b-107">Syntax</span></span>

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="a8c5b-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="a8c5b-108">Properties</span></span>

|  <span data-ttu-id="a8c5b-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="a8c5b-109">Property</span></span>  |  <span data-ttu-id="a8c5b-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="a8c5b-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="a8c5b-111">NomeRisorsa</span><span class="sxs-lookup"><span data-stu-id="a8c5b-111">ResourceName</span></span>| <span data-ttu-id="a8c5b-112">Il nome della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="a8c5b-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="a8c5b-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="a8c5b-113">NodeName</span></span>| <span data-ttu-id="a8c5b-114">I nodi di destinazione della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="a8c5b-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="a8c5b-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="a8c5b-115">RetryIntervalSec</span></span>| <span data-ttu-id="a8c5b-116">Il numero di secondi prima di riprovare.</span><span class="sxs-lookup"><span data-stu-id="a8c5b-116">The number of seconds before retrying.</span></span> <span data-ttu-id="a8c5b-117">Il valore minimo è 1.</span><span class="sxs-lookup"><span data-stu-id="a8c5b-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="a8c5b-118">RetryCount</span><span class="sxs-lookup"><span data-stu-id="a8c5b-118">RetryCount</span></span>| <span data-ttu-id="a8c5b-119">Il numero massimo di tentativi.</span><span class="sxs-lookup"><span data-stu-id="a8c5b-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="a8c5b-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="a8c5b-120">ThrottleLimit</span></span>| <span data-ttu-id="a8c5b-121">Numero di computer da connettere contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="a8c5b-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="a8c5b-122">Il valore predefinito è new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="a8c5b-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="a8c5b-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a8c5b-123">DependsOn</span></span> | <span data-ttu-id="a8c5b-124">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="a8c5b-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a8c5b-125">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a8c5b-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="a8c5b-126">Esempio</span><span class="sxs-lookup"><span data-stu-id="a8c5b-126">Example</span></span>

<span data-ttu-id="a8c5b-127">Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="a8c5b-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

