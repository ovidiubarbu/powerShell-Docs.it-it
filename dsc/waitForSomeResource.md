---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForSome DSC
ms.openlocfilehash: 5d67a9111f6358240590b651e627ffb96abc0896
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="08398-103">Risorsa WaitForSome DSC</span><span class="sxs-lookup"><span data-stu-id="08398-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="08398-104">Si applica a: Windows PowerShell 5.0 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="08398-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="08398-105">La risorsa DSC **WaitForAny** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](configurations.md) per specificare le dipendenze da configurazioni in altri nodi.</span><span class="sxs-lookup"><span data-stu-id="08398-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="08398-106">La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="08398-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="08398-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="08398-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    NodeCount = [Uint32]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="08398-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="08398-108">Properties</span></span>

|  <span data-ttu-id="08398-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="08398-109">Property</span></span>  |  <span data-ttu-id="08398-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="08398-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="08398-111">NomeRisorsa</span><span class="sxs-lookup"><span data-stu-id="08398-111">ResourceName</span></span>| <span data-ttu-id="08398-112">Il nome della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="08398-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="08398-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="08398-113">NodeName</span></span>| <span data-ttu-id="08398-114">I nodi di destinazione della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="08398-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="08398-115">NodeCount</span><span class="sxs-lookup"><span data-stu-id="08398-115">NodeCount</span></span>| <span data-ttu-id="08398-116">Il numero minimo di nodi che devono essere nello stato desiderato perché la risorsa abbia esito positivo.</span><span class="sxs-lookup"><span data-stu-id="08398-116">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="08398-117">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="08398-117">RetryIntervalSec</span></span>| <span data-ttu-id="08398-118">Il numero di secondi prima di riprovare.</span><span class="sxs-lookup"><span data-stu-id="08398-118">The number of seconds before retrying.</span></span> <span data-ttu-id="08398-119">Il valore minimo è 1.</span><span class="sxs-lookup"><span data-stu-id="08398-119">Minimum is 1.</span></span>| 
| <span data-ttu-id="08398-120">RetryCount</span><span class="sxs-lookup"><span data-stu-id="08398-120">RetryCount</span></span>| <span data-ttu-id="08398-121">Il numero massimo di tentativi.</span><span class="sxs-lookup"><span data-stu-id="08398-121">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="08398-122">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="08398-122">ThrottleLimit</span></span>| <span data-ttu-id="08398-123">Numero di computer da connettere contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="08398-123">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="08398-124">Il valore predefinito è new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="08398-124">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="08398-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="08398-125">DependsOn</span></span> | <span data-ttu-id="08398-126">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="08398-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="08398-127">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="08398-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="08398-128">Esempio</span><span class="sxs-lookup"><span data-stu-id="08398-128">Example</span></span>

<span data-ttu-id="08398-129">Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="08398-129">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

