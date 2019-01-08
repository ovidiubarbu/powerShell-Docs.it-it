---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
description: Fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione.
title: Risorsa GroupSet DSC
ms.openlocfilehash: afe4c4d33ac5620c411481e93d76a1f90c26deb9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047712"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="70ef2-104">Risorsa GroupSet DSC</span><span class="sxs-lookup"><span data-stu-id="70ef2-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="70ef2-105">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="70ef2-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="70ef2-106">La risorsa **GroupSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="70ef2-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="70ef2-107">Questa risorsa è una [risorsa composta](../../../resources/authoringResourceComposite.md) che chiama la [risorsa Group](groupResource.md) per ogni gruppo specificato nel parametro `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="70ef2-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="70ef2-108">Usare questa risorsa quando si vuole aggiungere e/o rimuovere lo stesso elenco di membri per più di un gruppo, rimuovere più di un gruppo o aggiungere più di un gruppo con lo stesso elenco di membri.</span><span class="sxs-lookup"><span data-stu-id="70ef2-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="70ef2-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="70ef2-109">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="70ef2-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="70ef2-110">Properties</span></span>

|  <span data-ttu-id="70ef2-111">Proprietà</span><span class="sxs-lookup"><span data-stu-id="70ef2-111">Property</span></span>  |  <span data-ttu-id="70ef2-112">Description</span><span class="sxs-lookup"><span data-stu-id="70ef2-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="70ef2-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="70ef2-113">GroupName</span></span>| <span data-ttu-id="70ef2-114">Nomi dei gruppi per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="70ef2-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="70ef2-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="70ef2-115">MembersToExclude</span></span>| <span data-ttu-id="70ef2-116">Usare questa proprietà per rimuovere membri dall'appartenenza a gruppi esistenti.</span><span class="sxs-lookup"><span data-stu-id="70ef2-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="70ef2-117">Il valore di questa proprietà è una matrice di stringhe del formato *Dominio*\\*Nome utente*.</span><span class="sxs-lookup"><span data-stu-id="70ef2-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="70ef2-118">Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**.</span><span class="sxs-lookup"><span data-stu-id="70ef2-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="70ef2-119">In caso contrario, verrà generato un errore.</span><span class="sxs-lookup"><span data-stu-id="70ef2-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="70ef2-120">Credential</span><span class="sxs-lookup"><span data-stu-id="70ef2-120">Credential</span></span>| <span data-ttu-id="70ef2-121">Le credenziali necessarie per accedere a risorse remote.</span><span class="sxs-lookup"><span data-stu-id="70ef2-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="70ef2-122">**Nota**: questo account deve avere le autorizzazioni di Active Directory appropriate per aggiungere tutti gli account non locali al gruppo. In caso contrario, si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="70ef2-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="70ef2-123">Ensure</span><span class="sxs-lookup"><span data-stu-id="70ef2-123">Ensure</span></span>| <span data-ttu-id="70ef2-124">Indica se i gruppi esistono.</span><span class="sxs-lookup"><span data-stu-id="70ef2-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="70ef2-125">Impostare questa proprietà su "Absent" per specificare che i gruppi non esistono.</span><span class="sxs-lookup"><span data-stu-id="70ef2-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="70ef2-126">Se la proprietà è impostata su "Present" (valore predefinito), specifica che i gruppi esistono.</span><span class="sxs-lookup"><span data-stu-id="70ef2-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="70ef2-127">Members</span><span class="sxs-lookup"><span data-stu-id="70ef2-127">Members</span></span>| <span data-ttu-id="70ef2-128">Usare questa proprietà per sostituire l'appartenenza al gruppo corrente con i membri specificati.</span><span class="sxs-lookup"><span data-stu-id="70ef2-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="70ef2-129">Il valore di questa proprietà è una matrice di stringhe del formato *Dominio*\\*Nome utente*.</span><span class="sxs-lookup"><span data-stu-id="70ef2-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="70ef2-130">Se si imposta questa proprietà in una configurazione, non usare la proprietà **MembersToExclude** o **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="70ef2-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="70ef2-131">In caso contrario, verrà generato un errore.</span><span class="sxs-lookup"><span data-stu-id="70ef2-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="70ef2-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="70ef2-132">MembersToInclude</span></span>| <span data-ttu-id="70ef2-133">Usare questa proprietà per aggiungere membri all'appartenenza al gruppo esistente.</span><span class="sxs-lookup"><span data-stu-id="70ef2-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="70ef2-134">Il valore di questa proprietà è una matrice di stringhe del formato *Dominio*\\*Nome utente*.</span><span class="sxs-lookup"><span data-stu-id="70ef2-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="70ef2-135">Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**.</span><span class="sxs-lookup"><span data-stu-id="70ef2-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="70ef2-136">In caso contrario, verrà generato un errore.</span><span class="sxs-lookup"><span data-stu-id="70ef2-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="70ef2-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="70ef2-137">DependsOn</span></span> | <span data-ttu-id="70ef2-138">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="70ef2-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="70ef2-139">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è \`DependsOn = "[ResourceType]ResourceName"\`\`.</span><span class="sxs-lookup"><span data-stu-id="70ef2-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="70ef2-140">Esempio 1: I gruppi di garantire che siano presenti</span><span class="sxs-lookup"><span data-stu-id="70ef2-140">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="70ef2-141">L'esempio seguente illustra come assicurarsi che siano presenti due gruppi denominati "myGroup" e "myOtherGroup".</span><span class="sxs-lookup"><span data-stu-id="70ef2-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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
> <span data-ttu-id="70ef2-142">In questo esempio vengono usate credenziali in testo non crittografato per maggiore semplicità.</span><span class="sxs-lookup"><span data-stu-id="70ef2-142">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="70ef2-143">Per informazioni sulla crittografia delle credenziali nel file MOF della configurazione, vedere [Protezione del file MOF](../../../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="70ef2-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
