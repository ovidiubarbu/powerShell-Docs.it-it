---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxService DSC per Linux
ms.openlocfilehash: 6bb58796c4deff1153f932f61c328d84f8c4d2ca
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954838"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="194cf-103">Risorsa nxService DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="194cf-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="194cf-104">La risorsa **nxService** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="194cf-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="194cf-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="194cf-105">Syntax</span></span>

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="194cf-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="194cf-106">Properties</span></span>

|<span data-ttu-id="194cf-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="194cf-107">Property</span></span> |<span data-ttu-id="194cf-108">Description</span><span class="sxs-lookup"><span data-stu-id="194cf-108">Description</span></span> |
|---|---|
|<span data-ttu-id="194cf-109">Nome</span><span class="sxs-lookup"><span data-stu-id="194cf-109">Name</span></span> |<span data-ttu-id="194cf-110">Nome del servizio/daemon da configurare.</span><span class="sxs-lookup"><span data-stu-id="194cf-110">The name of the service/daemon to configure.</span></span> |
|<span data-ttu-id="194cf-111">Controller</span><span class="sxs-lookup"><span data-stu-id="194cf-111">Controller</span></span> |<span data-ttu-id="194cf-112">Tipo di controller del servizio da usare per la configurazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="194cf-112">The type of service controller to use when configuring the service.</span></span> |
|<span data-ttu-id="194cf-113">Enabled</span><span class="sxs-lookup"><span data-stu-id="194cf-113">Enabled</span></span> |<span data-ttu-id="194cf-114">Indica se il servizio viene avviato all'avvio del sistema.</span><span class="sxs-lookup"><span data-stu-id="194cf-114">Indicates whether the service starts on boot.</span></span> |
|<span data-ttu-id="194cf-115">State</span><span class="sxs-lookup"><span data-stu-id="194cf-115">State</span></span> |<span data-ttu-id="194cf-116">Indica se il servizio è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="194cf-116">Indicates whether the service is running.</span></span> <span data-ttu-id="194cf-117">Impostare questa proprietà su **Stopped** per assicurarsi che il servizio non sia in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="194cf-117">Set this property to **Stopped** to ensure that the service is not running.</span></span> <span data-ttu-id="194cf-118">Impostare la proprietà su **Running** per assicurarsi che il servizio sia in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="194cf-118">Set it to **Running** to ensure that the service is running.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="194cf-119">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="194cf-119">Common properties</span></span>

|<span data-ttu-id="194cf-120">Proprietà</span><span class="sxs-lookup"><span data-stu-id="194cf-120">Property</span></span> |<span data-ttu-id="194cf-121">Description</span><span class="sxs-lookup"><span data-stu-id="194cf-121">Description</span></span> |
|---|---|
|<span data-ttu-id="194cf-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="194cf-122">DependsOn</span></span> |<span data-ttu-id="194cf-123">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="194cf-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="194cf-124">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="194cf-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="194cf-125">Informazioni aggiuntive</span><span class="sxs-lookup"><span data-stu-id="194cf-125">Additional Information</span></span>

<span data-ttu-id="194cf-126">La risorsa **nxService** non crea uno script o una definizione del servizio se il servizio non esiste.</span><span class="sxs-lookup"><span data-stu-id="194cf-126">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="194cf-127">È possibile usare la risorsa **nxFile** di PowerShell DSC (Desired State Configuration) per gestire l'esistenza o il contenuto dello script o del file di definizione del servizio.</span><span class="sxs-lookup"><span data-stu-id="194cf-127">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="194cf-128">Esempio</span><span class="sxs-lookup"><span data-stu-id="194cf-128">Example</span></span>

<span data-ttu-id="194cf-129">L'esempio seguente mostra la configurazione del servizio 'httpd' (per Apache HTTP Server), registrato con il controller del servizio **SystemD**.</span><span class="sxs-lookup"><span data-stu-id="194cf-129">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```