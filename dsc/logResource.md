---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Log DSC
ms.openlocfilehash: f1a528767508d4a0e7f0ea2e58fd27a6a4d7ec75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-log-resource"></a><span data-ttu-id="e63ef-103">Risorsa Log DSC</span><span class="sxs-lookup"><span data-stu-id="e63ef-103">DSC Log Resource</span></span>

> <span data-ttu-id="e63ef-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e63ef-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e63ef-105">La risorsa __Log__ in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per scrivere messaggi nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="e63ef-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="e63ef-106">NOTA: per impostazione predefinita sono abilitati solo i log operativi per DSC.</span><span class="sxs-lookup"><span data-stu-id="e63ef-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="e63ef-107">Per rendere disponibile o visibile il log analitico, è necessario abilitarlo.</span><span class="sxs-lookup"><span data-stu-id="e63ef-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="e63ef-108">Vedere l'articolo seguente.</span><span class="sxs-lookup"><span data-stu-id="e63ef-108">See the following article.</span></span>

[<span data-ttu-id="e63ef-109">Dove sono i registri eventi DSC?</span><span class="sxs-lookup"><span data-stu-id="e63ef-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="e63ef-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="e63ef-110">Properties</span></span>
|  <span data-ttu-id="e63ef-111">Proprietà</span><span class="sxs-lookup"><span data-stu-id="e63ef-111">Property</span></span>  |  <span data-ttu-id="e63ef-112">Description</span><span class="sxs-lookup"><span data-stu-id="e63ef-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="e63ef-113">Message</span><span class="sxs-lookup"><span data-stu-id="e63ef-113">Message</span></span>| <span data-ttu-id="e63ef-114">Indica il messaggio che si vuole scrivere nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="e63ef-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="e63ef-115">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e63ef-115">DependsOn</span></span> | <span data-ttu-id="e63ef-116">Indica che prima di poter scrivere questo messaggio del registro è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="e63ef-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="e63ef-117">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e63ef-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="e63ef-118">Esempio</span><span class="sxs-lookup"><span data-stu-id="e63ef-118">Example</span></span>

<span data-ttu-id="e63ef-119">L'esempio seguente mostra come includere un messaggio nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="e63ef-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="e63ef-120">**Nota**: se si esegue [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) con questa risorsa configurata, il cmdlet restituisce sempre **$false**.</span><span class="sxs-lookup"><span data-stu-id="e63ef-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```