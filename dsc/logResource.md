---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Log DSC
ms.openlocfilehash: fade94efd8133ae0172737e4bb1aed89fc0f97d9
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093477"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="fefea-103">Risorsa Log DSC</span><span class="sxs-lookup"><span data-stu-id="fefea-103">DSC Log Resource</span></span>

> <span data-ttu-id="fefea-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fefea-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="fefea-105">La risorsa __Log__ in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per scrivere messaggi nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="fefea-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="fefea-106">Per impostazione predefinita sono abilitati solo i log operativi per DSC.</span><span class="sxs-lookup"><span data-stu-id="fefea-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="fefea-107">Per rendere disponibile o visibile il log analitico, è necessario abilitarlo.</span><span class="sxs-lookup"><span data-stu-id="fefea-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="fefea-108">Per altre informazioni, vedere [Dove sono i registri eventi DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="fefea-108">For more information, see [Where are DSC Event Logs?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="fefea-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="fefea-109">Properties</span></span>

|  <span data-ttu-id="fefea-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="fefea-110">Property</span></span>  |  <span data-ttu-id="fefea-111">Description</span><span class="sxs-lookup"><span data-stu-id="fefea-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="fefea-112">Message</span><span class="sxs-lookup"><span data-stu-id="fefea-112">Message</span></span>| <span data-ttu-id="fefea-113">Indica il messaggio che si vuole scrivere nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="fefea-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="fefea-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fefea-114">DependsOn</span></span> | <span data-ttu-id="fefea-115">Indica che prima di poter scrivere questo messaggio del registro è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="fefea-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="fefea-116">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="fefea-116">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="fefea-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="fefea-117">Example</span></span>

<span data-ttu-id="fefea-118">L'esempio seguente mostra come includere un messaggio nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="fefea-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="fefea-119">Se si esegue [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) con questa risorsa configurata, il cmdlet restituisce sempre **$false**.</span><span class="sxs-lookup"><span data-stu-id="fefea-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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