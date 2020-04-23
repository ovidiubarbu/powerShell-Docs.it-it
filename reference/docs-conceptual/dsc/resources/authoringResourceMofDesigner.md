---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Uso dello strumento di progettazione risorse
ms.openlocfilehash: 36eed0fc888380a03a3279e834748708f578d973
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500638"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="51208-103">Uso dello strumento di progettazione risorse</span><span class="sxs-lookup"><span data-stu-id="51208-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="51208-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="51208-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="51208-105">Lo strumento di progettazione risorse è un set di cmdlet esposti dal modulo **xDscResourceDesigner** che semplifica la creazione di risorse Windows PowerShell DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="51208-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="51208-106">I cmdlet in questa risorsa offrono supporto per creare lo schema MOF, il modulo di script e la struttura di directory per la nuova risorsa.</span><span class="sxs-lookup"><span data-stu-id="51208-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="51208-107">Per altre informazioni sulle risorse DSC, vedere [Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="51208-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span> <span data-ttu-id="51208-108">In questo argomento verrà creata una risorsa DSC che gestisce gli utenti di Active Directory.</span><span class="sxs-lookup"><span data-stu-id="51208-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span> <span data-ttu-id="51208-109">Usare il cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) per installare il modulo **xDscResourceDesigner**.</span><span class="sxs-lookup"><span data-stu-id="51208-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="51208-110">Creazione delle proprietà della risorsa</span><span class="sxs-lookup"><span data-stu-id="51208-110">Creating resource properties</span></span>
<span data-ttu-id="51208-111">La prima cosa da fare è stabilire le proprietà che la risorsa dovrà esporre.</span><span class="sxs-lookup"><span data-stu-id="51208-111">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="51208-112">In questo esempio verrà definito un utente di Active Directory con le proprietà seguenti.</span><span class="sxs-lookup"><span data-stu-id="51208-112">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="51208-113">Nome parametro e descrizione</span><span class="sxs-lookup"><span data-stu-id="51208-113">Parameter name  Description</span></span>
* <span data-ttu-id="51208-114">**UserName**: proprietà chiave che identifica in modo univoco un utente.</span><span class="sxs-lookup"><span data-stu-id="51208-114">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="51208-115">**Ensure**: specifica se l'account utente deve essere presente o assente.</span><span class="sxs-lookup"><span data-stu-id="51208-115">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="51208-116">Questo parametro avrà solo due valori possibili.</span><span class="sxs-lookup"><span data-stu-id="51208-116">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="51208-117">**DomainCredential**: password di dominio per l'utente.</span><span class="sxs-lookup"><span data-stu-id="51208-117">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="51208-118">**Password**: password desiderata per l'utente in modo da consentire a una configurazione di modificare la password utente, se necessario.</span><span class="sxs-lookup"><span data-stu-id="51208-118">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="51208-119">Per creare le proprietà, viene usato il cmdlet **New-xDscResourceProperty**.</span><span class="sxs-lookup"><span data-stu-id="51208-119">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="51208-120">I comandi di PowerShell seguenti creano le proprietà descritte in precedenza.</span><span class="sxs-lookup"><span data-stu-id="51208-120">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="51208-121">Creare la risorsa</span><span class="sxs-lookup"><span data-stu-id="51208-121">Create the resource</span></span>

<span data-ttu-id="51208-122">Dopo aver creato le proprietà della risorsa, è possibile chiamare il cmdlet **New-xDscResource** per creare la risorsa.</span><span class="sxs-lookup"><span data-stu-id="51208-122">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="51208-123">Il cmdlet **New-xDscResource** accetta l'elenco di proprietà come parametri.</span><span class="sxs-lookup"><span data-stu-id="51208-123">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="51208-124">Accetta anche il percorso in cui deve essere creato il modulo, il nome della nuova risorsa e il nome del modulo in cui è contenuta.</span><span class="sxs-lookup"><span data-stu-id="51208-124">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="51208-125">Il comando di PowerShell seguente consente di creare la risorsa.</span><span class="sxs-lookup"><span data-stu-id="51208-125">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

<span data-ttu-id="51208-126">Il cmdlet **New-xDscResource** crea lo schema MOF, uno script di risorsa di base, la struttura di directory necessaria per la nuova risorsa e un manifesto per il modulo che espone la nuova risorsa.</span><span class="sxs-lookup"><span data-stu-id="51208-126">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="51208-127">Il file di schema MOF si trova in **C:\Programmi\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof** e il suo contenuto è il seguente.</span><span class="sxs-lookup"><span data-stu-id="51208-127">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
  [Key] string UserName;
  [Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
  [Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
  [Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

<span data-ttu-id="51208-128">Lo script di risorsa si trova in **C:\Programmi\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span><span class="sxs-lookup"><span data-stu-id="51208-128">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span>
<span data-ttu-id="51208-129">Non include la logica effettiva per implementare la risorsa, che è necessario aggiungere manualmente.</span><span class="sxs-lookup"><span data-stu-id="51208-129">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="51208-130">Il contenuto dello script di base è il seguente.</span><span class="sxs-lookup"><span data-stu-id="51208-130">The contents of the skeleton script are as follows.</span></span>

```powershell
function Get-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Collections.Hashtable])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $returnValue = @{
  UserName = [System.String]
  Ensure = [System.String]
  DomainAdminCredential = [System.Management.Automation.PSCredential]
  Password = [System.Management.Automation.PSCredential]
  }

  $returnValue
  #>
}


function Set-TargetResource
{
  [CmdletBinding()]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  #Include this line if the resource requires a system reboot.
  #$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Boolean])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $result = [System.Boolean]

  $result
  #>
}


Export-ModuleMember -Function *-TargetResource
```

## <a name="updating-the-resource"></a><span data-ttu-id="51208-131">Aggiornamento della risorsa</span><span class="sxs-lookup"><span data-stu-id="51208-131">Updating the resource</span></span>

<span data-ttu-id="51208-132">Se è necessario aggiungere o modificare l'elenco di parametri della risorsa, è possibile chiamare il cmdlet **Update-xDscResource**.</span><span class="sxs-lookup"><span data-stu-id="51208-132">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="51208-133">Il cmdlet aggiorna la risorsa con un nuovo elenco di parametri.</span><span class="sxs-lookup"><span data-stu-id="51208-133">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="51208-134">Se la logica è già stata aggiunta allo script di risorsa, non viene apportata alcuna modifica.</span><span class="sxs-lookup"><span data-stu-id="51208-134">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="51208-135">Si supponga, ad esempio, di voler includere l'ora dell'ultimo accesso per l'utente alla risorsa.</span><span class="sxs-lookup"><span data-stu-id="51208-135">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="51208-136">Invece che scrivere di nuovo la risorsa completamente, è possibile chiamare **New-xDscResourceProperty** per creare la nuova proprietà e quindi chiamare **Update-xDscResource** e aggiungere la nuova proprietà all'elenco di proprietà.</span><span class="sxs-lookup"><span data-stu-id="51208-136">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="51208-137">Test di uno schema di risorse</span><span class="sxs-lookup"><span data-stu-id="51208-137">Testing a resource schema</span></span>

<span data-ttu-id="51208-138">Lo strumento di progettazione risorse espone un altro cmdlet che è possibile usare per testare la validità di uno schema MOF scritto manualmente.</span><span class="sxs-lookup"><span data-stu-id="51208-138">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="51208-139">Chiamare il cmdlet **Test-xDscSchema**, passando il percorso di uno schema di risorsa MOF come parametro.</span><span class="sxs-lookup"><span data-stu-id="51208-139">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="51208-140">L'output del cmdlet conterrà eventuali errori presenti nello schema.</span><span class="sxs-lookup"><span data-stu-id="51208-140">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="51208-141">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="51208-141">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="51208-142">Concetti</span><span class="sxs-lookup"><span data-stu-id="51208-142">Concepts</span></span>
[<span data-ttu-id="51208-143">Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate</span><span class="sxs-lookup"><span data-stu-id="51208-143">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="51208-144">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="51208-144">Other Resources</span></span>
[<span data-ttu-id="51208-145">Modulo xDscResourceDesigner</span><span class="sxs-lookup"><span data-stu-id="51208-145">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
