---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxService DSC per Linux
ms.openlocfilehash: 4273ad59f15eedd08b07888ebb6ee51d039b72b3
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="e1392-103">Risorsa nxService DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="e1392-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="e1392-104">La risorsa **nxService** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="e1392-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e1392-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e1392-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="e1392-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="e1392-106">Properties</span></span>
|  <span data-ttu-id="e1392-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="e1392-107">Property</span></span> |  <span data-ttu-id="e1392-108">Description</span><span class="sxs-lookup"><span data-stu-id="e1392-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="e1392-109">Nome</span><span class="sxs-lookup"><span data-stu-id="e1392-109">Name</span></span>| <span data-ttu-id="e1392-110">Nome del servizio/daemon da configurare.</span><span class="sxs-lookup"><span data-stu-id="e1392-110">The name of the service/daemon to configure.</span></span>| 
| <span data-ttu-id="e1392-111">Controller</span><span class="sxs-lookup"><span data-stu-id="e1392-111">Controller</span></span>| <span data-ttu-id="e1392-112">Tipo di controller del servizio da usare per la configurazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="e1392-112">The type of service controller to use when configuring the service.</span></span>| 
| <span data-ttu-id="e1392-113">Enabled</span><span class="sxs-lookup"><span data-stu-id="e1392-113">Enabled</span></span>| <span data-ttu-id="e1392-114">Indica se il servizio viene avviato all'avvio del sistema.</span><span class="sxs-lookup"><span data-stu-id="e1392-114">Indicates whether the service starts on boot.</span></span>| 
| <span data-ttu-id="e1392-115">State</span><span class="sxs-lookup"><span data-stu-id="e1392-115">State</span></span>| <span data-ttu-id="e1392-116">Indica se il servizio è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e1392-116">Indicates whether the service is running.</span></span> <span data-ttu-id="e1392-117">Impostare questa proprietà su "Stopped" per specificare che il servizio non è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e1392-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="e1392-118">Impostare la proprietà su "Running" per specificare che il servizio è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e1392-118">Set it to "Running" to ensure that the service is not running.</span></span>| 
| <span data-ttu-id="e1392-119">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e1392-119">DependsOn</span></span> | <span data-ttu-id="e1392-120">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="e1392-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e1392-121">Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e1392-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 


## <a name="additional-information"></a><span data-ttu-id="e1392-122">Informazioni aggiuntive</span><span class="sxs-lookup"><span data-stu-id="e1392-122">Additional Information</span></span>

<span data-ttu-id="e1392-123">La risorsa **nxService** non crea uno script o una definizione del servizio se il servizio non esiste.</span><span class="sxs-lookup"><span data-stu-id="e1392-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="e1392-124">È possibile usare la risorsa **nxFile** di PowerShell DSC (Desired State Configuration) per gestire l'esistenza o il contenuto dello script o del file di definizione del servizio.</span><span class="sxs-lookup"><span data-stu-id="e1392-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="e1392-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="e1392-125">Example</span></span>

<span data-ttu-id="e1392-126">L'esempio seguente mostra la configurazione del servizio "httpd" (per Apache HTTP Server), registrato con il controller del servizio **SystemD**.</span><span class="sxs-lookup"><span data-stu-id="e1392-126">The following example shows configuration of the “httpd” service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```

