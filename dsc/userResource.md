---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa User DSC
ms.openlocfilehash: f2660933aec43967e3f4082a983ef328a5b93851
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
#<a name="dsc-user-resource"></a><span data-ttu-id="b2c06-103">Risorsa User DSC#</span><span class="sxs-lookup"><span data-stu-id="b2c06-103">DSC User Resource#</span></span>


><span data-ttu-id="b2c06-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b2c06-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="b2c06-105">La risorsa __User__ in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire gli account utente locali nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b2c06-105">The __User__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>


##<a name="syntax"></a><span data-ttu-id="b2c06-106">Sintassi##</span><span class="sxs-lookup"><span data-stu-id="b2c06-106">Syntax##</span></span>

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="b2c06-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="b2c06-107">Properties</span></span>
|  <span data-ttu-id="b2c06-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="b2c06-108">Property</span></span>  |  <span data-ttu-id="b2c06-109">Description</span><span class="sxs-lookup"><span data-stu-id="b2c06-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="b2c06-110">UserName</span><span class="sxs-lookup"><span data-stu-id="b2c06-110">UserName</span></span>| <span data-ttu-id="b2c06-111">Indica il nome dell'account per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="b2c06-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="b2c06-112">Description</span><span class="sxs-lookup"><span data-stu-id="b2c06-112">Description</span></span>| <span data-ttu-id="b2c06-113">Indica la descrizione che si vuole usare per l'account utente.</span><span class="sxs-lookup"><span data-stu-id="b2c06-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="b2c06-114">Disabled</span><span class="sxs-lookup"><span data-stu-id="b2c06-114">Disabled</span></span>| <span data-ttu-id="b2c06-115">Indica se l'account è abilitato.</span><span class="sxs-lookup"><span data-stu-id="b2c06-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="b2c06-116">Impostare questa proprietà su __$true__ per specificare che l'account è disabilitato e su __$false__ per specificare che è abilitato.</span><span class="sxs-lookup"><span data-stu-id="b2c06-116">Set this property to __$true__ to ensure that this account is disabled, and set it to __$false__ to ensure that it is enabled.</span></span>|
| <span data-ttu-id="b2c06-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="b2c06-117">Ensure</span></span>| <span data-ttu-id="b2c06-118">Indica se l'account esiste.</span><span class="sxs-lookup"><span data-stu-id="b2c06-118">Indicates if the account exists.</span></span> <span data-ttu-id="b2c06-119">Impostare questa proprietà su "Present" per specificare che l'account esiste e su "Absent" per specificare che non esiste.</span><span class="sxs-lookup"><span data-stu-id="b2c06-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="b2c06-120">FullName</span><span class="sxs-lookup"><span data-stu-id="b2c06-120">FullName</span></span>| <span data-ttu-id="b2c06-121">Rappresenta una stringa che contiene il nome completo da usare per l'account utente.</span><span class="sxs-lookup"><span data-stu-id="b2c06-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="b2c06-122">Password</span><span class="sxs-lookup"><span data-stu-id="b2c06-122">Password</span></span>| <span data-ttu-id="b2c06-123">Indica la password da usare per l'account.</span><span class="sxs-lookup"><span data-stu-id="b2c06-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="b2c06-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="b2c06-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="b2c06-125">Indica se l'utente può modificare la password.</span><span class="sxs-lookup"><span data-stu-id="b2c06-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="b2c06-126">Impostare questa proprietà su __$true__ per impedire all'utente di modificare la password e su __$false__ per consentire all'utente di modificare la password.</span><span class="sxs-lookup"><span data-stu-id="b2c06-126">Set this property to __$true__ to ensure that the user cannot change the password, and set it to __$false__ to allow the user to change the password.</span></span> <span data-ttu-id="b2c06-127">Il valore predefinito è __$false__.</span><span class="sxs-lookup"><span data-stu-id="b2c06-127">The default value is __$false__.</span></span>|
| <span data-ttu-id="b2c06-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="b2c06-128">PasswordChangeRequired</span></span>| <span data-ttu-id="b2c06-129">Indica se l'utente dovrà cambiare la password all'accesso successivo.</span><span class="sxs-lookup"><span data-stu-id="b2c06-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="b2c06-130">Impostare questa proprietà su __$true__ se l'utente deve cambiare la password.</span><span class="sxs-lookup"><span data-stu-id="b2c06-130">Set this property to __$true__ if the user must change the password.</span></span> <span data-ttu-id="b2c06-131">Il valore predefinito è __$true__.</span><span class="sxs-lookup"><span data-stu-id="b2c06-131">The default value is __$true__.</span></span>|
| <span data-ttu-id="b2c06-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="b2c06-132">PasswordNeverExpires</span></span>| <span data-ttu-id="b2c06-133">Indica se la password scadrà.</span><span class="sxs-lookup"><span data-stu-id="b2c06-133">Indicates if the password will expire.</span></span> <span data-ttu-id="b2c06-134">Impostare questa proprietà su __$true__ per specificare che la password per questo utente non scade mai e su __$false__ se la password scade.</span><span class="sxs-lookup"><span data-stu-id="b2c06-134">To ensure that the password for this account will never expire, set this property to __$true__, and set it to __$false__ if the password will expire.</span></span> <span data-ttu-id="b2c06-135">Il valore predefinito è __$false__.</span><span class="sxs-lookup"><span data-stu-id="b2c06-135">The default value is __$false__.</span></span>|
| <span data-ttu-id="b2c06-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b2c06-136">DependsOn</span></span> | <span data-ttu-id="b2c06-137">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="b2c06-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b2c06-138">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b2c06-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="b2c06-139">Esempio</span><span class="sxs-lookup"><span data-stu-id="b2c06-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```