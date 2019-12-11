---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
description: Fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione.
title: Risorsa GroupSet DSC
ms.openlocfilehash: d36274741b2c96a0852f384ccf5d187ac8d27131
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953178"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="7e2e8-104">Risorsa GroupSet DSC</span><span class="sxs-lookup"><span data-stu-id="7e2e8-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="7e2e8-105">Si applica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="7e2e8-105">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="7e2e8-106">La risorsa **GroupSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="7e2e8-107">Questa risorsa è una [risorsa composta](../../../resources/authoringResourceComposite.md) che chiama la [risorsa Group](groupResource.md) per ogni gruppo specificato nel parametro `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="7e2e8-108">Usare questa risorsa quando si vuole aggiungere e/o rimuovere lo stesso elenco di membri per più di un gruppo, rimuovere più di un gruppo o aggiungere più di un gruppo con lo stesso elenco di membri.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e2e8-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7e2e8-109">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Members = [string[]] ]
    [ Description = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="7e2e8-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="7e2e8-110">Properties</span></span>

|<span data-ttu-id="7e2e8-111">Proprietà</span><span class="sxs-lookup"><span data-stu-id="7e2e8-111">Property</span></span> |<span data-ttu-id="7e2e8-112">Description</span><span class="sxs-lookup"><span data-stu-id="7e2e8-112">Description</span></span> |
|---|---|
|<span data-ttu-id="7e2e8-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="7e2e8-113">GroupName</span></span> |<span data-ttu-id="7e2e8-114">Nomi dei gruppi per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-114">The names of the groups for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="7e2e8-115">Members</span><span class="sxs-lookup"><span data-stu-id="7e2e8-115">Members</span></span> |<span data-ttu-id="7e2e8-116">Usare questa proprietà per sostituire l'appartenenza al gruppo corrente con i membri specificati.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-116">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="7e2e8-117">Il valore di questa proprietà è una matrice di stringhe nel formato `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-117">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="7e2e8-118">Se si imposta questa proprietà in una configurazione, non usare la proprietà **MembersToExclude** o **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-118">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="7e2e8-119">In caso contrario, verrà generato un errore.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-119">Doing so will generate an error.</span></span> |
|<span data-ttu-id="7e2e8-120">Description</span><span class="sxs-lookup"><span data-stu-id="7e2e8-120">Description</span></span> |<span data-ttu-id="7e2e8-121">La descrizione dell'attività.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-121">The description of the group.</span></span> |
|<span data-ttu-id="7e2e8-122">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="7e2e8-122">MembersToInclude</span></span> |<span data-ttu-id="7e2e8-123">Usare questa proprietà per aggiungere membri all'appartenenza al gruppo esistente.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-123">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="7e2e8-124">Il valore di questa proprietà è una matrice di stringhe nel formato `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="7e2e8-125">Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="7e2e8-126">In caso contrario, verrà generato un errore.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-126">Doing so will generate an error.</span></span> |
|<span data-ttu-id="7e2e8-127">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="7e2e8-127">MembersToExclude</span></span> |<span data-ttu-id="7e2e8-128">Usare questa proprietà per rimuovere membri dall'appartenenza a gruppi esistenti.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-128">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="7e2e8-129">Il valore di questa proprietà è una matrice di stringhe nel formato `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="7e2e8-130">Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="7e2e8-131">In caso contrario, verrà generato un errore.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-131">Doing so will generate an error.</span></span> |
|<span data-ttu-id="7e2e8-132">Credential</span><span class="sxs-lookup"><span data-stu-id="7e2e8-132">Credential</span></span> |<span data-ttu-id="7e2e8-133">Le credenziali necessarie per accedere a risorse remote.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-133">The credentials required to access remote resources.</span></span> <span data-ttu-id="7e2e8-134">questo account deve avere le autorizzazioni di Active Directory appropriate per aggiungere tutti gli account non locali al gruppo. In caso contrario, si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-134">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7e2e8-135">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="7e2e8-135">Common properties</span></span>

|<span data-ttu-id="7e2e8-136">Proprietà</span><span class="sxs-lookup"><span data-stu-id="7e2e8-136">Property</span></span> |<span data-ttu-id="7e2e8-137">Description</span><span class="sxs-lookup"><span data-stu-id="7e2e8-137">Description</span></span> |
|---|---|
|<span data-ttu-id="7e2e8-138">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7e2e8-138">DependsOn</span></span> |<span data-ttu-id="7e2e8-139">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-139">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7e2e8-140">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-140">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7e2e8-141">Ensure</span><span class="sxs-lookup"><span data-stu-id="7e2e8-141">Ensure</span></span> |<span data-ttu-id="7e2e8-142">Indica se i gruppi esistono.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-142">Indicates whether the groups exist.</span></span> <span data-ttu-id="7e2e8-143">Impostare questa proprietà su **Absent** per assicurarsi che i gruppi non esistano.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-143">Set this property to **Absent** to ensure that the groups do not exist.</span></span> <span data-ttu-id="7e2e8-144">Impostando il valore su **Present** ci si assicura che i gruppi esistano.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-144">Setting it to **Present** ensures that the groups exist.</span></span> <span data-ttu-id="7e2e8-145">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-145">The default value is **Present**.</span></span> |
|<span data-ttu-id="7e2e8-146">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7e2e8-146">PsDscRunAsCredential</span></span> |<span data-ttu-id="7e2e8-147">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-147">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7e2e8-148">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-148">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7e2e8-149">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="7e2e8-149">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="7e2e8-150">Esempio 1: Verifica che i gruppi siano presenti</span><span class="sxs-lookup"><span data-stu-id="7e2e8-150">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="7e2e8-151">L'esempio seguente illustra come assicurarsi che siano presenti due gruppi denominati "myGroup" e "myOtherGroup".</span><span class="sxs-lookup"><span data-stu-id="7e2e8-151">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="7e2e8-152">In questo esempio vengono usate credenziali in testo non crittografato per maggiore semplicità.</span><span class="sxs-lookup"><span data-stu-id="7e2e8-152">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="7e2e8-153">Per informazioni sulla crittografia delle credenziali nel file MOF della configurazione, vedere [Protezione del file MOF](../../../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="7e2e8-153">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>