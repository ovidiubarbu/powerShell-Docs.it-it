---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa Group DSC
ms.openlocfilehash: 6fb6c5f9593687d7204ff31fddd9bca978ed2707
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-group-resource"></a><span data-ttu-id="aefa2-103">Risorsa Group DSC</span><span class="sxs-lookup"><span data-stu-id="aefa2-103">DSC Group Resource</span></span>

> <span data-ttu-id="aefa2-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="aefa2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="aefa2-105">La risorsa Group in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="aefa2-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="aefa2-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="aefa2-106">Syntax</span></span>
```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="aefa2-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="aefa2-107">Properties</span></span>

|  <span data-ttu-id="aefa2-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="aefa2-108">Property</span></span>  |  <span data-ttu-id="aefa2-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="aefa2-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="aefa2-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="aefa2-110">GroupName</span></span>| <span data-ttu-id="aefa2-111">Il nome del gruppo per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="aefa2-111">The name of the group for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="aefa2-112">Credential</span><span class="sxs-lookup"><span data-stu-id="aefa2-112">Credential</span></span>| <span data-ttu-id="aefa2-113">Le credenziali necessarie per accedere a risorse remote.</span><span class="sxs-lookup"><span data-stu-id="aefa2-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="aefa2-114">**Nota**: per aggiungere tutti gli account non locali al gruppo, questo account deve avere le autorizzazioni di Active Directory appropriate. In caso contrario, quando la configurazione viene eseguita nel nodo di destinazione, si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="aefa2-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>  
| <span data-ttu-id="aefa2-115">Descrizione</span><span class="sxs-lookup"><span data-stu-id="aefa2-115">Description</span></span>| <span data-ttu-id="aefa2-116">La descrizione dell'attività.</span><span class="sxs-lookup"><span data-stu-id="aefa2-116">The description of the group.</span></span>| 
| <span data-ttu-id="aefa2-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="aefa2-117">Ensure</span></span>| <span data-ttu-id="aefa2-118">Indica se il gruppo esiste.</span><span class="sxs-lookup"><span data-stu-id="aefa2-118">Indicates if the group exists.</span></span> <span data-ttu-id="aefa2-119">Impostare questa proprietà su "Absent" per specificare che il gruppo non esiste.</span><span class="sxs-lookup"><span data-stu-id="aefa2-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="aefa2-120">Se la proprietà è impostata su "Present" (valore predefinito), specifica che il gruppo esiste.</span><span class="sxs-lookup"><span data-stu-id="aefa2-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>| 
| <span data-ttu-id="aefa2-121">Membri</span><span class="sxs-lookup"><span data-stu-id="aefa2-121">Members</span></span>| <span data-ttu-id="aefa2-122">Usare questa proprietà per sostituire l'appartenenza al gruppo corrente con i membri specificati.</span><span class="sxs-lookup"><span data-stu-id="aefa2-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="aefa2-123">Il valore di questa proprietà è una matrice di stringhe del formato *Dominio*\\*Nome utente*.</span><span class="sxs-lookup"><span data-stu-id="aefa2-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="aefa2-124">Se si imposta questa proprietà in una configurazione, non usare la proprietà **MembersToExclude** o **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="aefa2-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="aefa2-125">Questa operazione genera un errore.</span><span class="sxs-lookup"><span data-stu-id="aefa2-125">Doing so generates an error.</span></span>| 
| <span data-ttu-id="aefa2-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="aefa2-126">MembersToExclude</span></span>| <span data-ttu-id="aefa2-127">Usare questa proprietà per rimuovere membri dall'appartenenza al gruppo esistente.</span><span class="sxs-lookup"><span data-stu-id="aefa2-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="aefa2-128">Il valore di questa proprietà è una matrice di stringhe del formato *Dominio*\\*Nome utente*.</span><span class="sxs-lookup"><span data-stu-id="aefa2-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="aefa2-129">Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**.</span><span class="sxs-lookup"><span data-stu-id="aefa2-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="aefa2-130">Questa operazione genera un errore.</span><span class="sxs-lookup"><span data-stu-id="aefa2-130">Doing so generates an error.</span></span>| 
| <span data-ttu-id="aefa2-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="aefa2-131">MembersToInclude</span></span>| <span data-ttu-id="aefa2-132">Usare questa proprietà per aggiungere membri all'appartenenza al gruppo esistente.</span><span class="sxs-lookup"><span data-stu-id="aefa2-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="aefa2-133">Il valore di questa proprietà è una matrice di stringhe del formato *Dominio*\\*Nome utente*.</span><span class="sxs-lookup"><span data-stu-id="aefa2-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="aefa2-134">Se si imposta questa proprietà in una configurazione, non usare la proprietà **Members**.</span><span class="sxs-lookup"><span data-stu-id="aefa2-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="aefa2-135">In caso contrario, verrà generato un errore.</span><span class="sxs-lookup"><span data-stu-id="aefa2-135">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="aefa2-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="aefa2-136">DependsOn</span></span> | <span data-ttu-id="aefa2-137">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="aefa2-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="aefa2-138">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`\`.</span><span class="sxs-lookup"><span data-stu-id="aefa2-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example-1"></a><span data-ttu-id="aefa2-139">Esempio 1</span><span class="sxs-lookup"><span data-stu-id="aefa2-139">Example 1</span></span>

<span data-ttu-id="aefa2-140">L'esempio seguente illustra come specificare che un gruppo denominato "TestGroup" sia assente.</span><span class="sxs-lookup"><span data-stu-id="aefa2-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span> 

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
## <a name="example-2"></a><span data-ttu-id="aefa2-141">Esempio 2</span><span class="sxs-lookup"><span data-stu-id="aefa2-141">Example 2</span></span>
<span data-ttu-id="aefa2-142">L'esempio seguente illustra come aggiungere un utente Active Directory al gruppo Administrators locale come parte della compilazione di un ambiente con più computer in cui è già in uso un PSCredential per l'account amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="aefa2-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span> <span data-ttu-id="aefa2-143">Questo utente viene anche usato per l'account amministratore di dominio (dopo l'innalzamento di livello di un dominio). A questo punto è necessario convertire il PSCredential esistente in credenziali descrittive del dominio per consentire l'aggiunta di un utente di dominio al gruppo Administrators locale del server membro.</span><span class="sxs-lookup"><span data-stu-id="aefa2-143">As this is also used for the Domain Admin Account (after Domain promotion) we then need to convert this existing PSCredential to a Domain Friendly credential to enable us to add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```

## <a name="example-3"></a><span data-ttu-id="aefa2-144">Esempio 3</span><span class="sxs-lookup"><span data-stu-id="aefa2-144">Example 3</span></span>
<span data-ttu-id="aefa2-145">L'esempio seguente illustra come garantire che un gruppo locale, TigerTeamAdmins, nel server TigerTeamSource.Contoso.Com non contenga un account di dominio specifico, Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="aefa2-145">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>  

```powershell

Configuration SecureTigerTeamSrouce 
{
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'
  
  Node TigerTeamSource.Contoso.Com {
  Group TigerTeamAdmins
    {
       GroupName        = 'TigerTeamAdmins'   
       Ensure           = 'Absent'             
       MembersToInclude = "Contoso\JerryG"
    }
  }
}
```

