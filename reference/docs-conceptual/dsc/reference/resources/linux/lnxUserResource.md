---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxUser DSC per Linux
ms.openlocfilehash: 6d7b52809741813af7fa80b1c6372b267aff4777
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954798"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="90ee6-103">Risorsa nxUser DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="90ee6-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="90ee6-104">La risorsa **nxUser** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire gli utenti locali in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="90ee6-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="90ee6-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="90ee6-105">Syntax</span></span>

```Syntax
nxUser <string> #ResourceName
{
    UserName = <string>
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="90ee6-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="90ee6-106">Properties</span></span>

|<span data-ttu-id="90ee6-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="90ee6-107">Property</span></span> |<span data-ttu-id="90ee6-108">Indica il nome dell'account per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="90ee6-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
|<span data-ttu-id="90ee6-109">UserName</span><span class="sxs-lookup"><span data-stu-id="90ee6-109">UserName</span></span> |<span data-ttu-id="90ee6-110">Indica il percorso in cui si vuole specificare lo stato di un file o una directory.</span><span class="sxs-lookup"><span data-stu-id="90ee6-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="90ee6-111">FullName</span><span class="sxs-lookup"><span data-stu-id="90ee6-111">FullName</span></span> |<span data-ttu-id="90ee6-112">Stringa che contiene il nome completo da usare per l'account utente.</span><span class="sxs-lookup"><span data-stu-id="90ee6-112">A string that contains the full name to use for the user account.</span></span> |
|<span data-ttu-id="90ee6-113">Description</span><span class="sxs-lookup"><span data-stu-id="90ee6-113">Description</span></span> |<span data-ttu-id="90ee6-114">Descrizione dell'account utente.</span><span class="sxs-lookup"><span data-stu-id="90ee6-114">The description for the user account.</span></span> |
|<span data-ttu-id="90ee6-115">Password</span><span class="sxs-lookup"><span data-stu-id="90ee6-115">Password</span></span> |<span data-ttu-id="90ee6-116">Hash della password dell'utente nel formato appropriato per il computer Linux.</span><span class="sxs-lookup"><span data-stu-id="90ee6-116">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="90ee6-117">In genere, è un hash salt SHA-256 o SHA-512.</span><span class="sxs-lookup"><span data-stu-id="90ee6-117">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="90ee6-118">In Debian e Ubuntu Linux, questo valore può essere generato con il comando `mkpasswd`.</span><span class="sxs-lookup"><span data-stu-id="90ee6-118">On Debian and Ubuntu Linux, this value can be generated with the `mkpasswd` command.</span></span> <span data-ttu-id="90ee6-119">Per altre distribuzioni Linux, è possibile usare il metodo di crittografia della libreria Crypt di Python per generare l'hash.</span><span class="sxs-lookup"><span data-stu-id="90ee6-119">For other Linux distros, the crypt method of Python's Crypt library can be used to generate the hash.</span></span> |
|<span data-ttu-id="90ee6-120">Disabled</span><span class="sxs-lookup"><span data-stu-id="90ee6-120">Disabled</span></span> |<span data-ttu-id="90ee6-121">Indica se l'account è abilitato.</span><span class="sxs-lookup"><span data-stu-id="90ee6-121">Indicates whether the account is enabled.</span></span> <span data-ttu-id="90ee6-122">Impostare questa proprietà su `$true` per assicurarsi che l'account sia disabilitato e su `$false` per assicurarsi che sia abilitato.</span><span class="sxs-lookup"><span data-stu-id="90ee6-122">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="90ee6-123">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="90ee6-123">PasswordChangeRequired</span></span> |<span data-ttu-id="90ee6-124">Indica se l'utente può modificare la password.</span><span class="sxs-lookup"><span data-stu-id="90ee6-124">Indicates whether the user can change the password.</span></span> <span data-ttu-id="90ee6-125">Impostare questa proprietà su `$true` per assicurarsi che l'utente non possa modificare la password e su `$false` per consentire all'utente di modificare la password.</span><span class="sxs-lookup"><span data-stu-id="90ee6-125">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="90ee6-126">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="90ee6-126">The default value is `$false`.</span></span> <span data-ttu-id="90ee6-127">Questa proprietà viene valutata solo se l'account utente non esisteva in precedenza e viene creato ora.</span><span class="sxs-lookup"><span data-stu-id="90ee6-127">This property is only evaluated if the user account did not exist previously and is being created.</span></span> |
|<span data-ttu-id="90ee6-128">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="90ee6-128">HomeDirectory</span></span> |<span data-ttu-id="90ee6-129">Home directory per l'utente.</span><span class="sxs-lookup"><span data-stu-id="90ee6-129">The home directory for the user.</span></span> |
|<span data-ttu-id="90ee6-130">GroupID</span><span class="sxs-lookup"><span data-stu-id="90ee6-130">GroupID</span></span> |<span data-ttu-id="90ee6-131">ID gruppo primario per l'utente.</span><span class="sxs-lookup"><span data-stu-id="90ee6-131">The primary group ID for the user.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="90ee6-132">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="90ee6-132">Common properties</span></span>

|<span data-ttu-id="90ee6-133">Proprietà</span><span class="sxs-lookup"><span data-stu-id="90ee6-133">Property</span></span> |<span data-ttu-id="90ee6-134">Description</span><span class="sxs-lookup"><span data-stu-id="90ee6-134">Description</span></span> |
|---|---|
|<span data-ttu-id="90ee6-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="90ee6-135">DependsOn</span></span> |<span data-ttu-id="90ee6-136">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="90ee6-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="90ee6-137">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="90ee6-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="90ee6-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="90ee6-138">Ensure</span></span> |<span data-ttu-id="90ee6-139">Specifica se l'account esiste.</span><span class="sxs-lookup"><span data-stu-id="90ee6-139">Specifies whether the account exists.</span></span> <span data-ttu-id="90ee6-140">Impostare questa proprietà su **Present** per assicurarsi che l'account esista e su **Absent** per specificare che non esiste.</span><span class="sxs-lookup"><span data-stu-id="90ee6-140">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> |

## <a name="example"></a><span data-ttu-id="90ee6-141">Esempio</span><span class="sxs-lookup"><span data-stu-id="90ee6-141">Example</span></span>

<span data-ttu-id="90ee6-142">L'esempio seguente specifica che l'utente "monuser" esiste ed è un membro del gruppo "DBusers".</span><span class="sxs-lookup"><span data-stu-id="90ee6-142">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
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