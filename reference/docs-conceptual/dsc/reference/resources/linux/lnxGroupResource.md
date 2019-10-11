---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxGroup DSC per Linux
ms.openlocfilehash: 098ae2e8ab183934ec3c185c0fd237731b1353dc
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953208"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="c846c-103">Risorsa nxGroup DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="c846c-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="c846c-104">La risorsa **nxGroup** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="c846c-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c846c-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c846c-105">Syntax</span></span>

```Syntax
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ PreferredGroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present } ]
}
```

## <a name="properties"></a><span data-ttu-id="c846c-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="c846c-106">Properties</span></span>

|<span data-ttu-id="c846c-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="c846c-107">Property</span></span> |<span data-ttu-id="c846c-108">Description</span><span class="sxs-lookup"><span data-stu-id="c846c-108">Description</span></span> |
|---|---|
|<span data-ttu-id="c846c-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="c846c-109">GroupName</span></span> |<span data-ttu-id="c846c-110">Indica il nome del gruppo per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="c846c-110">Specifies the name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="c846c-111">Members</span><span class="sxs-lookup"><span data-stu-id="c846c-111">Members</span></span> |<span data-ttu-id="c846c-112">Specifica i membri che formano il gruppo.</span><span class="sxs-lookup"><span data-stu-id="c846c-112">Specifies the members that form the group.</span></span> |
|<span data-ttu-id="c846c-113">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="c846c-113">MembersToInclude</span></span> |<span data-ttu-id="c846c-114">Indica gli utenti da specificare come membri del gruppo.</span><span class="sxs-lookup"><span data-stu-id="c846c-114">Specifies the users who you want to ensure are members of the group.</span></span> |
|<span data-ttu-id="c846c-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="c846c-115">MembersToExclude</span></span> |<span data-ttu-id="c846c-116">Indica gli utenti da specificare come non membri del gruppo.</span><span class="sxs-lookup"><span data-stu-id="c846c-116">Specifies the users who you want to ensure are not members of the group.</span></span> |
|<span data-ttu-id="c846c-117">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="c846c-117">PreferredGroupID</span></span> |<span data-ttu-id="c846c-118">Imposta l'ID gruppo sul valore specificato, se possibile.</span><span class="sxs-lookup"><span data-stu-id="c846c-118">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="c846c-119">Se l'ID gruppo è attualmente in uso, viene usato il successivo ID gruppo disponibile.</span><span class="sxs-lookup"><span data-stu-id="c846c-119">If the group id is currently in use, the next available group id is used.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c846c-120">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="c846c-120">Common properties</span></span>

|<span data-ttu-id="c846c-121">Proprietà</span><span class="sxs-lookup"><span data-stu-id="c846c-121">Property</span></span> |<span data-ttu-id="c846c-122">Description</span><span class="sxs-lookup"><span data-stu-id="c846c-122">Description</span></span> |
|---|---|
|<span data-ttu-id="c846c-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c846c-123">DependsOn</span></span> |<span data-ttu-id="c846c-124">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="c846c-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c846c-125">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c846c-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c846c-126">Ensure</span><span class="sxs-lookup"><span data-stu-id="c846c-126">Ensure</span></span> |<span data-ttu-id="c846c-127">Determina se verificare l'esistenza del gruppo.</span><span class="sxs-lookup"><span data-stu-id="c846c-127">Determines whether to check if the group exists.</span></span> <span data-ttu-id="c846c-128">Impostare questa proprietà su **Present** per assicurarsi che il gruppo esista.</span><span class="sxs-lookup"><span data-stu-id="c846c-128">Set this property to **Present** to ensure the group exists.</span></span> <span data-ttu-id="c846c-129">Impostarla su **Absent** per assicurarsi che il gruppo non esista.</span><span class="sxs-lookup"><span data-stu-id="c846c-129">Set it to **Absent** to ensure the group does not exist.</span></span> <span data-ttu-id="c846c-130">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="c846c-130">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="c846c-131">Esempio</span><span class="sxs-lookup"><span data-stu-id="c846c-131">Example</span></span>

<span data-ttu-id="c846c-132">L'esempio seguente specifica che l'utente 'monuser' esiste ed è un membro del gruppo 'DBusers'.</span><span class="sxs-lookup"><span data-stu-id="c846c-132">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```