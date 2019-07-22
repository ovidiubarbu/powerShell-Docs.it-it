---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa WaitForSome DSC
ms.openlocfilehash: 2260f37002171154a6f2c3996b2af1bd9120039d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726778"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="b54f7-103">Risorsa WaitForSome DSC</span><span class="sxs-lookup"><span data-stu-id="b54f7-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="b54f7-104">Si applica a: Windows PowerShell 5.0 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="b54f7-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="b54f7-105">La risorsa DSC **WaitForSome** può essere usata all'interno di un blocco del nodo in una [configurazione DSC](../../../configurations/configurations.md) per specificare le dipendenze da configurazioni in altri nodi.</span><span class="sxs-lookup"><span data-stu-id="b54f7-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="b54f7-106">La risorsa ha esito positivo se la risorsa specificata dalla proprietà **ResourceName** si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="b54f7-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="b54f7-107">La risorsa **WaitForSome** usa Gestione remota Windows per controllare lo stato degli altri nodi.</span><span class="sxs-lookup"><span data-stu-id="b54f7-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="b54f7-108">Per altre informazioni sulla porta e sui requisiti di sicurezza per Gestione remota Windows, vedere [Considerazioni sulla sicurezza della comunicazione remota di PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="b54f7-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="b54f7-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b54f7-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="b54f7-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="b54f7-110">Properties</span></span>

|  <span data-ttu-id="b54f7-111">Proprietà</span><span class="sxs-lookup"><span data-stu-id="b54f7-111">Property</span></span>  |  <span data-ttu-id="b54f7-112">Description</span><span class="sxs-lookup"><span data-stu-id="b54f7-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="b54f7-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="b54f7-113">NodeCount</span></span>| <span data-ttu-id="b54f7-114">Il numero minimo di nodi che devono essere nello stato desiderato perché la risorsa abbia esito positivo.</span><span class="sxs-lookup"><span data-stu-id="b54f7-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="b54f7-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="b54f7-115">NodeName</span></span>| <span data-ttu-id="b54f7-116">I nodi di destinazione della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="b54f7-116">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="b54f7-117">NomeRisorsa</span><span class="sxs-lookup"><span data-stu-id="b54f7-117">ResourceName</span></span>| <span data-ttu-id="b54f7-118">Il nome della risorsa da cui dipendere.</span><span class="sxs-lookup"><span data-stu-id="b54f7-118">The resource name to depend on.</span></span> <span data-ttu-id="b54f7-119">Se questa risorsa appartiene a un'altra configurazione, il formato del nome deve essere "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="b54f7-119">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="b54f7-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="b54f7-120">RetryIntervalSec</span></span>| <span data-ttu-id="b54f7-121">Il numero di secondi prima di riprovare.</span><span class="sxs-lookup"><span data-stu-id="b54f7-121">The number of seconds before retrying.</span></span> <span data-ttu-id="b54f7-122">Il valore minimo è 1.</span><span class="sxs-lookup"><span data-stu-id="b54f7-122">Minimum is 1.</span></span>|
| <span data-ttu-id="b54f7-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="b54f7-123">RetryCount</span></span>| <span data-ttu-id="b54f7-124">Il numero massimo di tentativi.</span><span class="sxs-lookup"><span data-stu-id="b54f7-124">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="b54f7-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b54f7-125">ThrottleLimit</span></span>| <span data-ttu-id="b54f7-126">Numero di computer da connettere contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="b54f7-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="b54f7-127">Il valore predefinito è new-cimsession.</span><span class="sxs-lookup"><span data-stu-id="b54f7-127">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="b54f7-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b54f7-128">DependsOn</span></span> | <span data-ttu-id="b54f7-129">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="b54f7-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b54f7-130">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b54f7-130">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="b54f7-131">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b54f7-131">PsDscRunAsCredential</span></span> | <span data-ttu-id="b54f7-132">Vedere [Esecuzione di DSC con le credenziali dell'utente](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="b54f7-132">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="b54f7-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="b54f7-133">Example</span></span>

<span data-ttu-id="b54f7-134">Per un esempio di come usare questa risorsa, vedere [Specifica delle dipendenze tra nodi](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="b54f7-134">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
