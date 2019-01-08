---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForAny DSC
ms.openlocfilehash: 39e90f0df3459b8891ed46e02ae82c45a285e7f5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047655"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="48ff5-103">Risorsa WaitForAny DSC</span><span class="sxs-lookup"><span data-stu-id="48ff5-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="48ff5-104">Si applica a: Windows PowerShell 5.1 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="48ff5-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="48ff5-105">La risorsa DSC **WaitForSome** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](../../../configurations/configurations.md) per specificare le dipendenze da configurazioni in altri nodi.</span><span class="sxs-lookup"><span data-stu-id="48ff5-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="48ff5-106">La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** è nello stato desiderato in tutti i nodi di destinazione definiti nella proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="48ff5-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="48ff5-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="48ff5-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="48ff5-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="48ff5-108">Properties</span></span>

|  <span data-ttu-id="48ff5-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="48ff5-109">Property</span></span>  |  <span data-ttu-id="48ff5-110">Description</span><span class="sxs-lookup"><span data-stu-id="48ff5-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="48ff5-111">NomeRisorsa</span><span class="sxs-lookup"><span data-stu-id="48ff5-111">ResourceName</span></span>| <span data-ttu-id="48ff5-112">Il nome della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="48ff5-112">The resource name to depend on.</span></span> <span data-ttu-id="48ff5-113">Se questa risorsa appartiene a un'altra configurazione, il formato del nome deve essere "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="48ff5-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="48ff5-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="48ff5-114">NodeName</span></span>| <span data-ttu-id="48ff5-115">I nodi di destinazione della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="48ff5-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="48ff5-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="48ff5-116">RetryIntervalSec</span></span>| <span data-ttu-id="48ff5-117">Il numero di secondi prima di riprovare.</span><span class="sxs-lookup"><span data-stu-id="48ff5-117">The number of seconds before retrying.</span></span> <span data-ttu-id="48ff5-118">Il valore minimo è 1.</span><span class="sxs-lookup"><span data-stu-id="48ff5-118">Minimum is 1.</span></span>|
| <span data-ttu-id="48ff5-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="48ff5-119">RetryCount</span></span>| <span data-ttu-id="48ff5-120">Il numero massimo di tentativi.</span><span class="sxs-lookup"><span data-stu-id="48ff5-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="48ff5-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="48ff5-121">ThrottleLimit</span></span>| <span data-ttu-id="48ff5-122">Numero di computer da connettere contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="48ff5-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="48ff5-123">Il valore predefinito è new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="48ff5-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="48ff5-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="48ff5-124">DependsOn</span></span> | <span data-ttu-id="48ff5-125">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="48ff5-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="48ff5-126">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="48ff5-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="48ff5-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="48ff5-127">Example</span></span>

<span data-ttu-id="48ff5-128">Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="48ff5-128">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
