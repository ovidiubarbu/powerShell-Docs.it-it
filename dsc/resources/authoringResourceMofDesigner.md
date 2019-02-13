---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Uso dello strumento di progettazione risorse
ms.openlocfilehash: 3fd2f06cf46602ee30dd34f8e7bd77d3c92b808f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681432"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="7e08e-103">Uso dello strumento di progettazione risorse</span><span class="sxs-lookup"><span data-stu-id="7e08e-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="7e08e-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7e08e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7e08e-105">Lo strumento di progettazione risorse è un set di cmdlet esposti dal modulo **xDscResourceDesigner** che semplifica la creazione di risorse Windows PowerShell DSC (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="7e08e-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="7e08e-106">I cmdlet in questa risorsa offrono supporto per creare lo schema MOF, il modulo di script e la struttura di directory per la nuova risorsa.</span><span class="sxs-lookup"><span data-stu-id="7e08e-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="7e08e-107">Per altre informazioni sulle risorse DSC, vedere [Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="7e08e-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="7e08e-108">In questo argomento verrà creata una risorsa DSC che gestisce gli utenti di Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7e08e-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="7e08e-109">Usare il cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) per installare il modulo **xDscResourceDesigner**.</span><span class="sxs-lookup"><span data-stu-id="7e08e-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="7e08e-110">**Nota**: il cmdlet **Install-Module** è incluso nel modulo **PowerShellGet**, disponibile in PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="7e08e-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="7e08e-111">È possibile scaricare il modulo **PowerShellGet** per PowerShell 3.0 e 4.0 dalla pagina dell'[anteprima dei moduli PackageManagement di PowerShell](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="7e08e-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="7e08e-112">Creazione delle proprietà della risorsa</span><span class="sxs-lookup"><span data-stu-id="7e08e-112">Creating resource properties</span></span>
<span data-ttu-id="7e08e-113">La prima cosa da fare è stabilire le proprietà che la risorsa dovrà esporre.</span><span class="sxs-lookup"><span data-stu-id="7e08e-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="7e08e-114">In questo esempio verrà definito un utente di Active Directory con le proprietà seguenti.</span><span class="sxs-lookup"><span data-stu-id="7e08e-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="7e08e-115">Nome parametro e descrizione</span><span class="sxs-lookup"><span data-stu-id="7e08e-115">Parameter name  Description</span></span>
* <span data-ttu-id="7e08e-116">**UserName**: proprietà chiave che identifica in modo univoco un utente.</span><span class="sxs-lookup"><span data-stu-id="7e08e-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="7e08e-117">**Ensure**: specifica se l'account utente deve essere presente o assente.</span><span class="sxs-lookup"><span data-stu-id="7e08e-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="7e08e-118">Questo parametro avrà solo due valori possibili.</span><span class="sxs-lookup"><span data-stu-id="7e08e-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="7e08e-119">**DomainCredential**: password di dominio per l'utente.</span><span class="sxs-lookup"><span data-stu-id="7e08e-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="7e08e-120">**Password**: password desiderata per l'utente in modo da consentire a una configurazione di modificare la password utente, se necessario.</span><span class="sxs-lookup"><span data-stu-id="7e08e-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="7e08e-121">Per creare le proprietà, viene usato il cmdlet **New-xDscResourceProperty**.</span><span class="sxs-lookup"><span data-stu-id="7e08e-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="7e08e-122">I comandi di PowerShell seguenti creano le proprietà descritte in precedenza.</span><span class="sxs-lookup"><span data-stu-id="7e08e-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="7e08e-123">Creazione della risorsa</span><span class="sxs-lookup"><span data-stu-id="7e08e-123">Create the resource</span></span>

<span data-ttu-id="7e08e-124">Dopo aver creato le proprietà della risorsa, è possibile chiamare il cmdlet **New-xDscResource** per creare la risorsa.</span><span class="sxs-lookup"><span data-stu-id="7e08e-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="7e08e-125">Il cmdlet **New-xDscResource** accetta l'elenco di proprietà come parametri.</span><span class="sxs-lookup"><span data-stu-id="7e08e-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="7e08e-126">Accetta anche il percorso in cui deve essere creato il modulo, il nome della nuova risorsa e il nome del modulo in cui è contenuta.</span><span class="sxs-lookup"><span data-stu-id="7e08e-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="7e08e-127">Il comando di PowerShell seguente consente di creare la risorsa.</span><span class="sxs-lookup"><span data-stu-id="7e08e-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

<span data-ttu-id="7e08e-128">Il cmdlet **New-xDscResource** crea lo schema MOF, uno script di risorsa di base, la struttura di directory necessaria per la nuova risorsa e un manifesto per il modulo che espone la nuova risorsa.</span><span class="sxs-lookup"><span data-stu-id="7e08e-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="7e08e-129">Il file di schema MOF si trova in **C:\Programmi\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof** e il suo contenuto è il seguente.</span><span class="sxs-lookup"><span data-stu-id="7e08e-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

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

<span data-ttu-id="7e08e-130">Lo script di risorsa si trova in **C:\Programmi\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span><span class="sxs-lookup"><span data-stu-id="7e08e-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="7e08e-131">Non include la logica effettiva per implementare la risorsa, che è necessario aggiungere manualmente.</span><span class="sxs-lookup"><span data-stu-id="7e08e-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="7e08e-132">Il contenuto dello script di base è il seguente.</span><span class="sxs-lookup"><span data-stu-id="7e08e-132">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="7e08e-133">Aggiornamento della risorsa</span><span class="sxs-lookup"><span data-stu-id="7e08e-133">Updating the resource</span></span>

<span data-ttu-id="7e08e-134">Se è necessario aggiungere o modificare l'elenco di parametri della risorsa, è possibile chiamare il cmdlet **Update-xDscResource**.</span><span class="sxs-lookup"><span data-stu-id="7e08e-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="7e08e-135">Il cmdlet aggiorna la risorsa con un nuovo elenco di parametri.</span><span class="sxs-lookup"><span data-stu-id="7e08e-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="7e08e-136">Se la logica è già stata aggiunta allo script di risorsa, non viene apportata alcuna modifica.</span><span class="sxs-lookup"><span data-stu-id="7e08e-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="7e08e-137">Si supponga, ad esempio, di voler includere l'ora dell'ultimo accesso per l'utente alla risorsa.</span><span class="sxs-lookup"><span data-stu-id="7e08e-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="7e08e-138">Invece che scrivere di nuovo la risorsa completamente, è possibile chiamare **New-xDscResourceProperty** per creare la nuova proprietà e quindi chiamare **Update-xDscResource** e aggiungere la nuova proprietà all'elenco di proprietà.</span><span class="sxs-lookup"><span data-stu-id="7e08e-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="7e08e-139">Test di uno schema di risorse</span><span class="sxs-lookup"><span data-stu-id="7e08e-139">Testing a resource schema</span></span>

<span data-ttu-id="7e08e-140">Lo strumento di progettazione risorse espone un altro cmdlet che è possibile usare per testare la validità di uno schema MOF scritto manualmente.</span><span class="sxs-lookup"><span data-stu-id="7e08e-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="7e08e-141">Chiamare il cmdlet **Test-xDscSchema**, passando il percorso di uno schema di risorsa MOF come parametro.</span><span class="sxs-lookup"><span data-stu-id="7e08e-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="7e08e-142">L'output del cmdlet conterrà eventuali errori presenti nello schema.</span><span class="sxs-lookup"><span data-stu-id="7e08e-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="7e08e-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7e08e-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="7e08e-144">Concetti</span><span class="sxs-lookup"><span data-stu-id="7e08e-144">Concepts</span></span>
[<span data-ttu-id="7e08e-145">Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate</span><span class="sxs-lookup"><span data-stu-id="7e08e-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="7e08e-146">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="7e08e-146">Other Resources</span></span>
[<span data-ttu-id="7e08e-147">Modulo xDscResourceDesigner</span><span class="sxs-lookup"><span data-stu-id="7e08e-147">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
