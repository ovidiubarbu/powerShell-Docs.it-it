---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Group DSC
ms.openlocfilehash: 695a914683c6daff44dd2a6c94b6353acf881030
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954658"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="ad068-103">Risorsa Group DSC</span><span class="sxs-lookup"><span data-stu-id="ad068-103">DSC Group Resource</span></span>

> <span data-ttu-id="ad068-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="ad068-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="ad068-105">La risorsa **Group** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ad068-105">The **Group** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ad068-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ad068-106">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="ad068-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="ad068-107">Properties</span></span>

|<span data-ttu-id="ad068-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="ad068-108">Property</span></span> |<span data-ttu-id="ad068-109">Description</span><span class="sxs-lookup"><span data-stu-id="ad068-109">Description</span></span> |
|---|---|
|<span data-ttu-id="ad068-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="ad068-110">GroupName</span></span> |<span data-ttu-id="ad068-111">Il nome del gruppo per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="ad068-111">The name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="ad068-112">Credential</span><span class="sxs-lookup"><span data-stu-id="ad068-112">Credential</span></span> |<span data-ttu-id="ad068-113">Le credenziali necessarie per accedere a risorse remote.</span><span class="sxs-lookup"><span data-stu-id="ad068-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="ad068-114">per aggiungere tutti gli account non locali al gruppo, questo account deve avere le autorizzazioni di Active Directory appropriate. In caso contrario, quando la configurazione viene eseguita nel nodo di destinazione, si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="ad068-114">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
|<span data-ttu-id="ad068-115">Description</span><span class="sxs-lookup"><span data-stu-id="ad068-115">Description</span></span> |<span data-ttu-id="ad068-116">La descrizione dell'attività.</span><span class="sxs-lookup"><span data-stu-id="ad068-116">The description of the group.</span></span> |
|<span data-ttu-id="ad068-117">Members</span><span class="sxs-lookup"><span data-stu-id="ad068-117">Members</span></span> |<span data-ttu-id="ad068-118">Usare questa proprietà per sostituire l'appartenenza al gruppo corrente con i membri specificati.</span><span class="sxs-lookup"><span data-stu-id="ad068-118">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="ad068-119">Il valore di questa proprietà è una matrice di stringhe nel formato `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="ad068-119">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="ad068-120">Se si imposta questa proprietà in una configurazione, non usare la proprietà **MembersToExclude** o **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="ad068-120">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="ad068-121">Questa operazione genera un errore.</span><span class="sxs-lookup"><span data-stu-id="ad068-121">Doing so generates an error.</span></span> |
|<span data-ttu-id="ad068-122">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="ad068-122">MembersToExclude</span></span> |<span data-ttu-id="ad068-123">Usare questa proprietà per rimuovere membri dall'appartenenza al gruppo esistente.</span><span class="sxs-lookup"><span data-stu-id="ad068-123">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="ad068-124">Il valore di questa proprietà è una matrice di stringhe nel formato `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="ad068-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="ad068-125">Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**.</span><span class="sxs-lookup"><span data-stu-id="ad068-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="ad068-126">Questa operazione genera un errore.</span><span class="sxs-lookup"><span data-stu-id="ad068-126">Doing so generates an error.</span></span> |
|<span data-ttu-id="ad068-127">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="ad068-127">MembersToInclude</span></span> |<span data-ttu-id="ad068-128">Usare questa proprietà per aggiungere membri all'appartenenza al gruppo esistente.</span><span class="sxs-lookup"><span data-stu-id="ad068-128">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="ad068-129">Il valore di questa proprietà è una matrice di stringhe nel formato `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="ad068-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="ad068-130">Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**.</span><span class="sxs-lookup"><span data-stu-id="ad068-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="ad068-131">In caso contrario, verrà generato un errore.</span><span class="sxs-lookup"><span data-stu-id="ad068-131">Doing so will generate an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ad068-132">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="ad068-132">Common properties</span></span>

|<span data-ttu-id="ad068-133">Proprietà</span><span class="sxs-lookup"><span data-stu-id="ad068-133">Property</span></span> |<span data-ttu-id="ad068-134">Description</span><span class="sxs-lookup"><span data-stu-id="ad068-134">Description</span></span> |
|---|---|
|<span data-ttu-id="ad068-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ad068-135">DependsOn</span></span> |<span data-ttu-id="ad068-136">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="ad068-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ad068-137">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ad068-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="ad068-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="ad068-138">Ensure</span></span> |<span data-ttu-id="ad068-139">Indica se il gruppo esiste.</span><span class="sxs-lookup"><span data-stu-id="ad068-139">Indicates if the group exists.</span></span> <span data-ttu-id="ad068-140">Impostare questa proprietà su **Absent** per assicurarsi che il gruppo non esista.</span><span class="sxs-lookup"><span data-stu-id="ad068-140">Set this property to **Absent** to ensure that the group does not exist.</span></span> <span data-ttu-id="ad068-141">Impostando il valore su **Present** ci si assicura che il gruppo esista.</span><span class="sxs-lookup"><span data-stu-id="ad068-141">Setting it to **Present** ensures that the group exists.</span></span> <span data-ttu-id="ad068-142">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="ad068-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="ad068-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ad068-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="ad068-144">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="ad068-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="ad068-145">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="ad068-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="ad068-146">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="ad068-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensure-group-is-not-present"></a><span data-ttu-id="ad068-147">Esempio 1: Assicurarsi che il gruppo non sia presente</span><span class="sxs-lookup"><span data-stu-id="ad068-147">Example 1: Ensure group is not present</span></span>

<span data-ttu-id="ad068-148">L'esempio seguente illustra come specificare che un gruppo denominato "TestGroup" sia assente.</span><span class="sxs-lookup"><span data-stu-id="ad068-148">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a><span data-ttu-id="ad068-149">Esempio 2: Aggiungere un utente di dominio al gruppo locale</span><span class="sxs-lookup"><span data-stu-id="ad068-149">Example 2: Add domain user to local group</span></span>

<span data-ttu-id="ad068-150">L'esempio seguente illustra come aggiungere un utente Active Directory al gruppo Administrators locale come parte della compilazione di un ambiente con più computer in cui è già in uso un PSCredential per l'account Amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="ad068-150">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Administrator account.</span></span> <span data-ttu-id="ad068-151">Questo utente viene anche usato per l'account amministratore di dominio (dopo l'innalzamento di livello di un dominio). A questo punto è necessario convertire il PSCredential esistente in credenziali descrittive del dominio.</span><span class="sxs-lookup"><span data-stu-id="ad068-151">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span> <span data-ttu-id="ad068-152">Ciò consente l'aggiunta di un utente di dominio al gruppo Administrators locale del server membro.</span><span class="sxs-lookup"><span data-stu-id="ad068-152">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="ad068-153">Esempio 3</span><span class="sxs-lookup"><span data-stu-id="ad068-153">Example 3</span></span>

<span data-ttu-id="ad068-154">L'esempio seguente illustra come garantire che un gruppo locale, TigerTeamAdmins, nel server TigerTeamSource.Contoso.Com non contenga un account di dominio specifico, Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="ad068-154">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```