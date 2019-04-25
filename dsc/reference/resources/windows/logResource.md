---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Log DSC
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077229"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="7079f-103">Risorsa Log DSC</span><span class="sxs-lookup"><span data-stu-id="7079f-103">DSC Log Resource</span></span>

> <span data-ttu-id="7079f-104">_Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="7079f-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="7079f-105">La risorsa __Log__ in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per scrivere messaggi nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="7079f-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="7079f-106">Per impostazione predefinita sono abilitati solo i log operativi per DSC.</span><span class="sxs-lookup"><span data-stu-id="7079f-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="7079f-107">Per rendere disponibile o visibile il log analitico, è necessario abilitarlo.</span><span class="sxs-lookup"><span data-stu-id="7079f-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="7079f-108">Per altre informazioni, vedere [Dove sono i registri eventi DSC?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="7079f-108">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="7079f-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="7079f-109">Properties</span></span>

| <span data-ttu-id="7079f-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="7079f-110">Property</span></span> | <span data-ttu-id="7079f-111">Description</span><span class="sxs-lookup"><span data-stu-id="7079f-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="7079f-112">Message</span><span class="sxs-lookup"><span data-stu-id="7079f-112">Message</span></span>| <span data-ttu-id="7079f-113">Indica il messaggio che si vuole scrivere nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="7079f-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="7079f-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7079f-114">DependsOn</span></span> | <span data-ttu-id="7079f-115">Indica che prima di poter scrivere questo messaggio del registro è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="7079f-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="7079f-116">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="7079f-116">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="7079f-117">Esempio</span><span class="sxs-lookup"><span data-stu-id="7079f-117">Example</span></span>

<span data-ttu-id="7079f-118">L'esempio seguente mostra come includere un messaggio nel registro eventi Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="7079f-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="7079f-119">Se si esegue [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) con questa risorsa configurata, il cmdlet restituisce sempre **$false**.</span><span class="sxs-lookup"><span data-stu-id="7079f-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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
