---
ms.date: 03/28/2019
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Moduli con versioni di PowerShell compatibili
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328502"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="64c75-103">Moduli con versioni di PowerShell compatibili</span><span class="sxs-lookup"><span data-stu-id="64c75-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="64c75-104">A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="64c75-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="64c75-105">**Desktop Edition:** basata su .NET Framework, si applica a Windows PowerShell versione 4.0 e precedenti, nonché a Windows PowerShell 5.1 in Windows Desktop, Windows Server, Windows Server Core e la maggior parte delle altre edizioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="64c75-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="64c75-106">**Core Edition:** basata su .NET Core, si applica a PowerShell Core versione 6.0 e successive, nonché a Windows PowerShell 5.1 nelle edizioni di Windows con footprint ridotto, come Windows IoT e Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="64c75-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="64c75-107">Per altre informazioni sulle edizioni di PowerShell, vedere [about_PowerShell_Editions][].</span><span class="sxs-lookup"><span data-stu-id="64c75-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="64c75-108">Dichiarazione delle edizioni compatibili</span><span class="sxs-lookup"><span data-stu-id="64c75-108">Declaring compatible editions</span></span>

<span data-ttu-id="64c75-109">Gli autori di moduli possono dichiarare i propri moduli compatibili con una o più edizioni di PowerShell usando la chiave manifesto del modulo CompatiblePSEditions.</span><span class="sxs-lookup"><span data-stu-id="64c75-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="64c75-110">Questa chiave è supportata solo in PowerShell 5.1 o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="64c75-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="64c75-111">Quando un manifesto del modulo viene specificato con la chiave CompatiblePSEditions, non può più essere importato in PowerShell versione 4 o precedenti.</span><span class="sxs-lookup"><span data-stu-id="64c75-111">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on PowerShell versions 4 and below.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

<span data-ttu-id="64c75-112">Quando si recupera un elenco dei moduli disponibili, è possibile filtrarlo in base all'edizione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64c75-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

## <a name="targeting-multiple-editions"></a><span data-ttu-id="64c75-113">Selezionare più edizioni di destinazione</span><span class="sxs-lookup"><span data-stu-id="64c75-113">Targeting multiple editions</span></span>

<span data-ttu-id="64c75-114">Gli autori dei moduli possono pubblicare un singolo modulo destinato a una o entrambe le edizioni di PowerShell (Desktop e Core).</span><span class="sxs-lookup"><span data-stu-id="64c75-114">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="64c75-115">Un modulo singolo può essere usato sia nell'edizione Desktop che nell'edizione Core purché l'autore vi aggiunga la logica necessaria in RootModule o nel manifesto del modulo usando la variabile $PSEdition.</span><span class="sxs-lookup"><span data-stu-id="64c75-115">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span> <span data-ttu-id="64c75-116">I moduli possono avere due set di DLL compilate con destinazione a CoreCLR e FullCLR.</span><span class="sxs-lookup"><span data-stu-id="64c75-116">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span> <span data-ttu-id="64c75-117">Di seguito sono riportate le due opzioni per creare il pacchetto del modulo con la logica per il caricamento delle DLL appropriate.</span><span class="sxs-lookup"><span data-stu-id="64c75-117">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="64c75-118">Opzione 1: creazione di un modulo destinabile a più versioni e più edizioni di PowerShell</span><span class="sxs-lookup"><span data-stu-id="64c75-118">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="64c75-119">Contenuto della cartella del modulo</span><span class="sxs-lookup"><span data-stu-id="64c75-119">Module folder contents</span></span>

- <span data-ttu-id="64c75-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="64c75-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="64c75-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="64c75-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="64c75-122">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="64c75-122">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="64c75-123">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="64c75-123">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="64c75-124">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="64c75-124">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="64c75-125">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="64c75-125">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="64c75-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="64c75-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="64c75-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="64c75-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="64c75-128">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="64c75-128">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="64c75-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="64c75-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="64c75-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="64c75-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="64c75-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="64c75-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="64c75-132">Impostazioni\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="64c75-132">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="64c75-133">Impostazioni\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="64c75-133">Settings\DSC.psd1</span></span>
- <span data-ttu-id="64c75-134">Impostazioni\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="64c75-134">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="64c75-135">Impostazioni\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="64c75-135">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="64c75-136">Impostazioni\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="64c75-136">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="64c75-137">Contenuto del file PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="64c75-137">Contents of PSScriptAnalyzer.psd1 file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

<span data-ttu-id="64c75-138">La logica riportata qui sotto carica gli assembly necessari in base all'edizione o alla versione corrente.</span><span class="sxs-lookup"><span data-stu-id="64c75-138">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="64c75-139">Contenuto del file PSScriptAnalyzer.psm1:</span><span class="sxs-lookup"><span data-stu-id="64c75-139">Contents of PSScriptAnalyzer.psm1 file:</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="64c75-140">Opzione 2: uso della variabile $PSEdition nel file PSD1 per caricare le DLL appropriate e moduli nidificati/richiesti</span><span class="sxs-lookup"><span data-stu-id="64c75-140">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="64c75-141">Nella versione PS 5.1 o successiva la variabile globale $PSEdition è consentita nel file manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="64c75-141">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="64c75-142">Usando questa variabile l'autore del modulo può specificare i valori condizionali nel file manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="64c75-142">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="64c75-143">È possibile fare riferimento alla variabile $PSEdition in modalità linguaggio con restrizioni o in una sezione di dati.</span><span class="sxs-lookup"><span data-stu-id="64c75-143">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="64c75-144">Quando un manifesto del modulo viene specificato con la chiave CompatiblePSEditions oppure usa la variabile `$PSEdition`, non può più essere importato in versioni di PowerShell precedenti.</span><span class="sxs-lookup"><span data-stu-id="64c75-144">Once a module manifest is specified with the CompatiblePSEditions key or uses `$PSEdition` variable, it can not be imported on lower versions of PowerShell.</span></span>

<span data-ttu-id="64c75-145">Esempio di file manifesto del modulo con la chiave CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="64c75-145">Sample module manifest file with CompatiblePSEditions key</span></span>

```powershell
@{
    # Script module or binary module file associated with this manifest.
    RootModule = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrRM.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrRM.dll'
    }

    # Supported PSEditions
    CompatiblePSEditions = 'Desktop', 'Core'

    # Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
    NestedModules = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrNM1.dll',
        'coreclr\MyCoreClrNM2.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrNM1.dll',
        'clr\MyFullClrNM2.dll'
    }
}
```

### <a name="module-contents"></a><span data-ttu-id="64c75-146">Contenuto del modulo</span><span class="sxs-lookup"><span data-stu-id="64c75-146">Module contents</span></span>

```powershell
dir -Recurse
```

```Output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

<span data-ttu-id="64c75-147">Gli utenti di PowerShell Gallery possono visualizzare l'elenco dei moduli supportati in un'edizione specifica di PowerShell usando i tag PSEdition_Desktop e PSEditon_Core.</span><span class="sxs-lookup"><span data-stu-id="64c75-147">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="64c75-148">I moduli senza tag PSEdition_Desktop e PSEditon_Core sono considerati idonei per le edizioni Desktop di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="64c75-148">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="64c75-149">Altri dettagli</span><span class="sxs-lookup"><span data-stu-id="64c75-149">More details</span></span>

[<span data-ttu-id="64c75-150">Script con PSEditions</span><span class="sxs-lookup"><span data-stu-id="64c75-150">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="64c75-151">Supporto di PSEditions nella raccolta di PowerShell</span><span class="sxs-lookup"><span data-stu-id="64c75-151">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="64c75-152">Aggiornare il manifesto del modulo</span><span class="sxs-lookup"><span data-stu-id="64c75-152">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="64c75-153">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="64c75-153">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
