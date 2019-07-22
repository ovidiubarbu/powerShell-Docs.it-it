---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForAll DSC
ms.openlocfilehash: c1125b7c5b68b9b520ed052800b6a2abf4e53b85
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726869"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="0a5f9-103">Risorsa WaitForAll DSC</span><span class="sxs-lookup"><span data-stu-id="0a5f9-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="0a5f9-104">Si applica a: Windows PowerShell 5.0 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="0a5f9-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="0a5f9-105">La risorsa DSC **WaitForAll** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](../../../configurations/configurations.md) per specificare le dipendenze da configurazioni in altri nodi.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="0a5f9-106">La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** è nello stato desiderato in tutti i nodi di destinazione definiti nella proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="0a5f9-107">La risorsa **WaitForAll** usa Gestione remota Windows per controllare lo stato degli altri nodi.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="0a5f9-108">Per altre informazioni sulla porta e sui requisiti di sicurezza per Gestione remota Windows, vedere [Considerazioni sulla sicurezza della comunicazione remota di PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="0a5f9-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="0a5f9-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0a5f9-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="0a5f9-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="0a5f9-110">Properties</span></span>

|  <span data-ttu-id="0a5f9-111">Proprietà</span><span class="sxs-lookup"><span data-stu-id="0a5f9-111">Property</span></span>  |  <span data-ttu-id="0a5f9-112">Description</span><span class="sxs-lookup"><span data-stu-id="0a5f9-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="0a5f9-113">NomeRisorsa</span><span class="sxs-lookup"><span data-stu-id="0a5f9-113">ResourceName</span></span>| <span data-ttu-id="0a5f9-114">Il nome della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-114">The resource name to depend on.</span></span> <span data-ttu-id="0a5f9-115">Se questa risorsa appartiene a un'altra configurazione, il formato del nome deve essere "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="0a5f9-115">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="0a5f9-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="0a5f9-116">NodeName</span></span>| <span data-ttu-id="0a5f9-117">I nodi di destinazione della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-117">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="0a5f9-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="0a5f9-118">RetryIntervalSec</span></span>| <span data-ttu-id="0a5f9-119">Il numero di secondi prima di riprovare.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-119">The number of seconds before retrying.</span></span> <span data-ttu-id="0a5f9-120">Il valore minimo è 1.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-120">Minimum is 1.</span></span>|
| <span data-ttu-id="0a5f9-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="0a5f9-121">RetryCount</span></span>| <span data-ttu-id="0a5f9-122">Il numero massimo di tentativi.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="0a5f9-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="0a5f9-123">ThrottleLimit</span></span>| <span data-ttu-id="0a5f9-124">Numero di computer da connettere contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="0a5f9-125">Il valore predefinito è new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="0a5f9-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0a5f9-126">DependsOn</span></span> | <span data-ttu-id="0a5f9-127">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0a5f9-128">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="0a5f9-129">Esempio</span><span class="sxs-lookup"><span data-stu-id="0a5f9-129">Example</span></span>

<span data-ttu-id="0a5f9-130">Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="0a5f9-130">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
