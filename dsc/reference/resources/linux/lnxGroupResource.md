---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxGroup DSC per Linux
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077860"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="6df6b-103">Risorsa nxGroup DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="6df6b-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="6df6b-104">La risorsa **nxGroup** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="6df6b-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="6df6b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6df6b-105">Syntax</span></span>

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="6df6b-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6df6b-106">Properties</span></span>

|  <span data-ttu-id="6df6b-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6df6b-107">Property</span></span> |  <span data-ttu-id="6df6b-108">Description</span><span class="sxs-lookup"><span data-stu-id="6df6b-108">Description</span></span> |
|---|---|
| <span data-ttu-id="6df6b-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="6df6b-109">GroupName</span></span>| <span data-ttu-id="6df6b-110">Indica il nome del gruppo per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="6df6b-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="6df6b-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="6df6b-111">Ensure</span></span>| <span data-ttu-id="6df6b-112">Determina se verificare l'esistenza del gruppo.</span><span class="sxs-lookup"><span data-stu-id="6df6b-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="6df6b-113">Impostare questa proprietà su "Present" per specificare che il gruppo esiste.</span><span class="sxs-lookup"><span data-stu-id="6df6b-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="6df6b-114">Impostarla su "Absent" per specificare che il gruppo non esiste.</span><span class="sxs-lookup"><span data-stu-id="6df6b-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="6df6b-115">Il valore predefinito è "Present".</span><span class="sxs-lookup"><span data-stu-id="6df6b-115">The default value is "Present".</span></span>|
| <span data-ttu-id="6df6b-116">Members</span><span class="sxs-lookup"><span data-stu-id="6df6b-116">Members</span></span>| <span data-ttu-id="6df6b-117">Specifica i membri che formano il gruppo.</span><span class="sxs-lookup"><span data-stu-id="6df6b-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="6df6b-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="6df6b-118">MembersToInclude</span></span>| <span data-ttu-id="6df6b-119">Indica gli utenti da specificare come membri del gruppo.</span><span class="sxs-lookup"><span data-stu-id="6df6b-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="6df6b-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="6df6b-120">MembersToExclude</span></span>| <span data-ttu-id="6df6b-121">Indica gli utenti da specificare come non membri del gruppo.</span><span class="sxs-lookup"><span data-stu-id="6df6b-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="6df6b-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="6df6b-122">PreferredGroupID</span></span>| <span data-ttu-id="6df6b-123">Imposta l'ID gruppo sul valore specificato, se possibile.</span><span class="sxs-lookup"><span data-stu-id="6df6b-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="6df6b-124">Se l'ID gruppo è attualmente in uso, viene usato il successivo ID gruppo disponibile.</span><span class="sxs-lookup"><span data-stu-id="6df6b-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="6df6b-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6df6b-125">DependsOn</span></span> | <span data-ttu-id="6df6b-126">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="6df6b-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6df6b-127">Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="6df6b-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="6df6b-128">Esempio</span><span class="sxs-lookup"><span data-stu-id="6df6b-128">Example</span></span>

<span data-ttu-id="6df6b-129">L'esempio seguente specifica che l'utente 'monuser' esiste ed è un membro del gruppo 'DBusers'.</span><span class="sxs-lookup"><span data-stu-id="6df6b-129">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
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