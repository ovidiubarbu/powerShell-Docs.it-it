---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa User DSC
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682039"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="070d4-103">Risorsa User DSC</span><span class="sxs-lookup"><span data-stu-id="070d4-103">DSC User Resource</span></span>

<span data-ttu-id="070d4-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="070d4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="070d4-105">La risorsa **User** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire gli account utente locali nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="070d4-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="070d4-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="070d4-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="070d4-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="070d4-107">Properties</span></span>

|  <span data-ttu-id="070d4-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="070d4-108">Property</span></span>  |  <span data-ttu-id="070d4-109">Description</span><span class="sxs-lookup"><span data-stu-id="070d4-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="070d4-110">UserName</span><span class="sxs-lookup"><span data-stu-id="070d4-110">UserName</span></span>| <span data-ttu-id="070d4-111">Indica il nome dell'account per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="070d4-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="070d4-112">Description</span><span class="sxs-lookup"><span data-stu-id="070d4-112">Description</span></span>| <span data-ttu-id="070d4-113">Indica la descrizione che si vuole usare per l'account utente.</span><span class="sxs-lookup"><span data-stu-id="070d4-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="070d4-114">Disabled</span><span class="sxs-lookup"><span data-stu-id="070d4-114">Disabled</span></span>| <span data-ttu-id="070d4-115">Indica se l'account è abilitato.</span><span class="sxs-lookup"><span data-stu-id="070d4-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="070d4-116">Impostare questa proprietà su `$true` per assicurarsi che l'account sia disabilitato e su `$false` per assicurarsi che sia abilitato.</span><span class="sxs-lookup"><span data-stu-id="070d4-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span>|
| <span data-ttu-id="070d4-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="070d4-117">Ensure</span></span>| <span data-ttu-id="070d4-118">Indica se l'account esiste.</span><span class="sxs-lookup"><span data-stu-id="070d4-118">Indicates if the account exists.</span></span> <span data-ttu-id="070d4-119">Impostare questa proprietà su "Present" per specificare che l'account esiste e su "Absent" per specificare che non esiste.</span><span class="sxs-lookup"><span data-stu-id="070d4-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="070d4-120">FullName</span><span class="sxs-lookup"><span data-stu-id="070d4-120">FullName</span></span>| <span data-ttu-id="070d4-121">Rappresenta una stringa che contiene il nome completo da usare per l'account utente.</span><span class="sxs-lookup"><span data-stu-id="070d4-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="070d4-122">Password</span><span class="sxs-lookup"><span data-stu-id="070d4-122">Password</span></span>| <span data-ttu-id="070d4-123">Indica la password da usare per l'account.</span><span class="sxs-lookup"><span data-stu-id="070d4-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="070d4-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="070d4-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="070d4-125">Indica se l'utente può modificare la password.</span><span class="sxs-lookup"><span data-stu-id="070d4-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="070d4-126">Impostare questa proprietà su `$true` per assicurarsi che l'utente non possa modificare la password e su `$false` per consentire all'utente di modificare la password.</span><span class="sxs-lookup"><span data-stu-id="070d4-126">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="070d4-127">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="070d4-127">The default value is `$false`.</span></span>|
| <span data-ttu-id="070d4-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="070d4-128">PasswordChangeRequired</span></span>| <span data-ttu-id="070d4-129">Indica se l'utente dovrà cambiare la password all'accesso successivo.</span><span class="sxs-lookup"><span data-stu-id="070d4-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="070d4-130">Impostare questa proprietà su `$true` se l'utente deve cambiare la password.</span><span class="sxs-lookup"><span data-stu-id="070d4-130">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="070d4-131">Il valore predefinito è `$true`.</span><span class="sxs-lookup"><span data-stu-id="070d4-131">The default value is `$true`.</span></span>|
| <span data-ttu-id="070d4-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="070d4-132">PasswordNeverExpires</span></span>| <span data-ttu-id="070d4-133">Indica se la password scadrà.</span><span class="sxs-lookup"><span data-stu-id="070d4-133">Indicates if the password will expire.</span></span> <span data-ttu-id="070d4-134">Impostare questa proprietà su `$true` per assicurarsi che la password per questo utente non scada mai e su `$false` se la password scade.</span><span class="sxs-lookup"><span data-stu-id="070d4-134">To ensure that the password for this account will never expire, set this property to `$true`, and set it to `$false` if the password will expire.</span></span> <span data-ttu-id="070d4-135">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="070d4-135">The default value is `$false`.</span></span>|
| <span data-ttu-id="070d4-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="070d4-136">DependsOn</span></span> | <span data-ttu-id="070d4-137">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="070d4-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="070d4-138">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="070d4-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="070d4-139">Esempio</span><span class="sxs-lookup"><span data-stu-id="070d4-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```