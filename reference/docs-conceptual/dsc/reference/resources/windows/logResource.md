---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Log DSC
ms.openlocfilehash: a1b7bf44fbaf36a3adaf0666e9f0a754fa3f6ee1
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954668"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="3fc11-103">Risorsa Log DSC</span><span class="sxs-lookup"><span data-stu-id="3fc11-103">DSC Log Resource</span></span>

> <span data-ttu-id="3fc11-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="3fc11-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="3fc11-105">La risorsa **Log** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per scrivere messaggi nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="3fc11-105">The **Log** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

## <a name="syntax"></a><span data-ttu-id="3fc11-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3fc11-106">Syntax</span></span>

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="3fc11-107">Per impostazione predefinita sono abilitati solo i log operativi per DSC.</span><span class="sxs-lookup"><span data-stu-id="3fc11-107">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="3fc11-108">Per rendere disponibile o visibile il log analitico, è necessario abilitarlo.</span><span class="sxs-lookup"><span data-stu-id="3fc11-108">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="3fc11-109">Per altre informazioni, vedere [Dove sono i registri eventi DSC?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="3fc11-109">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="3fc11-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="3fc11-110">Properties</span></span>

|<span data-ttu-id="3fc11-111">Proprietà</span><span class="sxs-lookup"><span data-stu-id="3fc11-111">Property</span></span> |<span data-ttu-id="3fc11-112">Description</span><span class="sxs-lookup"><span data-stu-id="3fc11-112">Description</span></span> |
|---|---|
|<span data-ttu-id="3fc11-113">Message</span><span class="sxs-lookup"><span data-stu-id="3fc11-113">Message</span></span> |<span data-ttu-id="3fc11-114">Indica il messaggio che si vuole scrivere nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="3fc11-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="3fc11-115">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="3fc11-115">Common properties</span></span>

|<span data-ttu-id="3fc11-116">Proprietà</span><span class="sxs-lookup"><span data-stu-id="3fc11-116">Property</span></span> |<span data-ttu-id="3fc11-117">Description</span><span class="sxs-lookup"><span data-stu-id="3fc11-117">Description</span></span> |
|---|---|
|<span data-ttu-id="3fc11-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3fc11-118">DependsOn</span></span> |<span data-ttu-id="3fc11-119">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="3fc11-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3fc11-120">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3fc11-120">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="3fc11-121">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="3fc11-121">PsDscRunAsCredential</span></span> |<span data-ttu-id="3fc11-122">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="3fc11-122">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="3fc11-123">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="3fc11-123">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="3fc11-124">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="3fc11-124">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="3fc11-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="3fc11-125">Example</span></span>

<span data-ttu-id="3fc11-126">L'esempio seguente mostra come includere un messaggio nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="3fc11-126">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="3fc11-127">Se si esegue [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) con questa risorsa configurata, il cmdlet restituisce sempre **$false**.</span><span class="sxs-lookup"><span data-stu-id="3fc11-127">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```