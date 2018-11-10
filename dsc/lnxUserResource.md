---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxUser DSC per Linux
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226033"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="81eb6-103">Risorsa nxUser DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="81eb6-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="81eb6-104">La risorsa **nxUser** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire gli utenti locali in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="81eb6-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="81eb6-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="81eb6-105">Syntax</span></span>

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="81eb6-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="81eb6-106">Properties</span></span>

|  <span data-ttu-id="81eb6-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="81eb6-107">Property</span></span> |  <span data-ttu-id="81eb6-108">Indica il nome dell'account per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="81eb6-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="81eb6-109">UserName</span><span class="sxs-lookup"><span data-stu-id="81eb6-109">UserName</span></span>| <span data-ttu-id="81eb6-110">Indica il percorso in cui si vuole specificare lo stato di un file o una directory.</span><span class="sxs-lookup"><span data-stu-id="81eb6-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="81eb6-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="81eb6-111">Ensure</span></span>| <span data-ttu-id="81eb6-112">Specifica se l'account esiste.</span><span class="sxs-lookup"><span data-stu-id="81eb6-112">Specifies whether the account exists.</span></span> <span data-ttu-id="81eb6-113">Impostare questa proprietà su "Present" per specificare che l'account esiste e su "Absent" per specificare che non esiste.</span><span class="sxs-lookup"><span data-stu-id="81eb6-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="81eb6-114">FullName</span><span class="sxs-lookup"><span data-stu-id="81eb6-114">FullName</span></span>| <span data-ttu-id="81eb6-115">Stringa che contiene il nome completo da usare per l'account utente.</span><span class="sxs-lookup"><span data-stu-id="81eb6-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="81eb6-116">Description</span><span class="sxs-lookup"><span data-stu-id="81eb6-116">Description</span></span>| <span data-ttu-id="81eb6-117">Descrizione dell'account utente.</span><span class="sxs-lookup"><span data-stu-id="81eb6-117">The description for the user account.</span></span>|
| <span data-ttu-id="81eb6-118">Password</span><span class="sxs-lookup"><span data-stu-id="81eb6-118">Password</span></span>| <span data-ttu-id="81eb6-119">Hash della password dell'utente nel formato appropriato per il computer Linux.</span><span class="sxs-lookup"><span data-stu-id="81eb6-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="81eb6-120">In genere, è un hash salt SHA-256 o SHA-512.</span><span class="sxs-lookup"><span data-stu-id="81eb6-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="81eb6-121">In Debian e Ubuntu Linux, questo valore può essere generato con il comando mkpasswd.</span><span class="sxs-lookup"><span data-stu-id="81eb6-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="81eb6-122">Per altre distribuzioni Linux, è possibile usare il metodo di crittografia della libreria Crypt di Python per generare l'hash.</span><span class="sxs-lookup"><span data-stu-id="81eb6-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="81eb6-123">Disabled</span><span class="sxs-lookup"><span data-stu-id="81eb6-123">Disabled</span></span>| <span data-ttu-id="81eb6-124">Indica se l'account è abilitato.</span><span class="sxs-lookup"><span data-stu-id="81eb6-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="81eb6-125">Impostare questa proprietà su **$true** per specificare che l'account è disabilitato e su **$false** per specificare che è abilitato.</span><span class="sxs-lookup"><span data-stu-id="81eb6-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="81eb6-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="81eb6-126">PasswordChangeRequired</span></span>| <span data-ttu-id="81eb6-127">Indica se l'utente può modificare la password.</span><span class="sxs-lookup"><span data-stu-id="81eb6-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="81eb6-128">Impostare questa proprietà su **$true** per impedire all'utente di modificare la password e su **$false** per consentire all'utente di modificare la password.</span><span class="sxs-lookup"><span data-stu-id="81eb6-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="81eb6-129">Il valore predefinito è **$false**.</span><span class="sxs-lookup"><span data-stu-id="81eb6-129">The default value is **$false**.</span></span> <span data-ttu-id="81eb6-130">Questa proprietà viene valutata solo se l'account utente non esisteva in precedenza e viene creato ora.</span><span class="sxs-lookup"><span data-stu-id="81eb6-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="81eb6-131">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="81eb6-131">HomeDirectory</span></span>| <span data-ttu-id="81eb6-132">Home directory per l'utente.</span><span class="sxs-lookup"><span data-stu-id="81eb6-132">The home directory for the user.</span></span>|
| <span data-ttu-id="81eb6-133">GroupID</span><span class="sxs-lookup"><span data-stu-id="81eb6-133">GroupID</span></span>| <span data-ttu-id="81eb6-134">ID gruppo primario per l'utente.</span><span class="sxs-lookup"><span data-stu-id="81eb6-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="81eb6-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="81eb6-135">DependsOn</span></span> | <span data-ttu-id="81eb6-136">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="81eb6-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="81eb6-137">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è "ResourceName" e il tipo è "ResourceType", la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="81eb6-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="81eb6-138">Esempio</span><span class="sxs-lookup"><span data-stu-id="81eb6-138">Example</span></span>

<span data-ttu-id="81eb6-139">L'esempio seguente specifica che l'utente "monuser" esiste ed è un membro del gruppo "DBusers".</span><span class="sxs-lookup"><span data-stu-id="81eb6-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}

nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"
}
}
```