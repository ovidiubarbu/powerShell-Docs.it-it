---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa User DSC
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953008"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="39aa3-103">Risorsa User DSC</span><span class="sxs-lookup"><span data-stu-id="39aa3-103">DSC User Resource</span></span>

> <span data-ttu-id="39aa3-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="39aa3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="39aa3-105">La risorsa **User** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire gli account utente locali nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="39aa3-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="39aa3-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="39aa3-106">Syntax</span></span>

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="39aa3-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="39aa3-107">Properties</span></span>

|<span data-ttu-id="39aa3-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="39aa3-108">Property</span></span> |<span data-ttu-id="39aa3-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="39aa3-109">Description</span></span> |
|---|---|
|<span data-ttu-id="39aa3-110">UserName</span><span class="sxs-lookup"><span data-stu-id="39aa3-110">UserName</span></span> |<span data-ttu-id="39aa3-111">Indica il nome dell'account per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="39aa3-111">Indicates the account name for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="39aa3-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="39aa3-112">Description</span></span> |<span data-ttu-id="39aa3-113">Indica la descrizione che si vuole usare per l'account utente.</span><span class="sxs-lookup"><span data-stu-id="39aa3-113">Indicates the description you want to use for the user account.</span></span> |
|<span data-ttu-id="39aa3-114">Disabled</span><span class="sxs-lookup"><span data-stu-id="39aa3-114">Disabled</span></span> |<span data-ttu-id="39aa3-115">Indica se l'account è abilitato.</span><span class="sxs-lookup"><span data-stu-id="39aa3-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="39aa3-116">Impostare questa proprietà su `$true` per assicurarsi che l'account sia disabilitato e su `$false` per assicurarsi che sia abilitato.</span><span class="sxs-lookup"><span data-stu-id="39aa3-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="39aa3-117">FullName</span><span class="sxs-lookup"><span data-stu-id="39aa3-117">FullName</span></span> |<span data-ttu-id="39aa3-118">Rappresenta una stringa che contiene il nome completo da usare per l'account utente.</span><span class="sxs-lookup"><span data-stu-id="39aa3-118">Represents a string with the full name you want to use for the user account.</span></span> |
|<span data-ttu-id="39aa3-119">Password</span><span class="sxs-lookup"><span data-stu-id="39aa3-119">Password</span></span> |<span data-ttu-id="39aa3-120">Indica la password da usare per l'account.</span><span class="sxs-lookup"><span data-stu-id="39aa3-120">Indicates the password you want to use for this account.</span></span> |
|<span data-ttu-id="39aa3-121">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="39aa3-121">PasswordChangeNotAllowed</span></span> |<span data-ttu-id="39aa3-122">Indica se l'utente può modificare la password.</span><span class="sxs-lookup"><span data-stu-id="39aa3-122">Indicates if the user can change the password.</span></span> <span data-ttu-id="39aa3-123">Impostare questa proprietà su `$true` per assicurarsi che l'utente non possa modificare la password e su `$false` per consentire all'utente di modificare la password.</span><span class="sxs-lookup"><span data-stu-id="39aa3-123">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="39aa3-124">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="39aa3-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="39aa3-125">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="39aa3-125">PasswordChangeRequired</span></span> |<span data-ttu-id="39aa3-126">Indica se l'utente dovrà cambiare la password all'accesso successivo.</span><span class="sxs-lookup"><span data-stu-id="39aa3-126">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="39aa3-127">Impostare questa proprietà su `$true` se l'utente deve cambiare la password.</span><span class="sxs-lookup"><span data-stu-id="39aa3-127">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="39aa3-128">Il valore predefinito è `$true`.</span><span class="sxs-lookup"><span data-stu-id="39aa3-128">The default value is `$true`.</span></span> |
|<span data-ttu-id="39aa3-129">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="39aa3-129">PasswordNeverExpires</span></span> |<span data-ttu-id="39aa3-130">Indica se la password scadrà.</span><span class="sxs-lookup"><span data-stu-id="39aa3-130">Indicates if the password will expire.</span></span> <span data-ttu-id="39aa3-131">Per assicurarsi che la password per questo account non scada mai, impostare questa proprietà su `$true`.</span><span class="sxs-lookup"><span data-stu-id="39aa3-131">To ensure that the password for this account will never expire, set this property to `$true`.</span></span> <span data-ttu-id="39aa3-132">Impostarla su `$false` se la password scadrà.</span><span class="sxs-lookup"><span data-stu-id="39aa3-132">Set it to `$false` if the password will expire.</span></span> <span data-ttu-id="39aa3-133">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="39aa3-133">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="39aa3-134">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="39aa3-134">Common properties</span></span>

|<span data-ttu-id="39aa3-135">Proprietà</span><span class="sxs-lookup"><span data-stu-id="39aa3-135">Property</span></span> |<span data-ttu-id="39aa3-136">Descrizione</span><span class="sxs-lookup"><span data-stu-id="39aa3-136">Description</span></span> |
|---|---|
|<span data-ttu-id="39aa3-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="39aa3-137">DependsOn</span></span> |<span data-ttu-id="39aa3-138">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="39aa3-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="39aa3-139">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="39aa3-139">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="39aa3-140">Ensure</span><span class="sxs-lookup"><span data-stu-id="39aa3-140">Ensure</span></span> |<span data-ttu-id="39aa3-141">Indica se l'account esiste.</span><span class="sxs-lookup"><span data-stu-id="39aa3-141">Indicates if the account exists.</span></span> <span data-ttu-id="39aa3-142">Impostare questa proprietà su **Present** per assicurarsi che l'account esista e su **Absent** per specificare che non esiste.</span><span class="sxs-lookup"><span data-stu-id="39aa3-142">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> <span data-ttu-id="39aa3-143">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="39aa3-143">The default value is **Present**.</span></span> |
|<span data-ttu-id="39aa3-144">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="39aa3-144">PsDscRunAsCredential</span></span> |<span data-ttu-id="39aa3-145">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="39aa3-145">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="39aa3-146">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="39aa3-146">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="39aa3-147">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="39aa3-147">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="39aa3-148">Esempio</span><span class="sxs-lookup"><span data-stu-id="39aa3-148">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```