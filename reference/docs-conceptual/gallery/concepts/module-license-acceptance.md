---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Moduli per cui è richiesta l'accettazione della licenza
ms.openlocfilehash: 369e32d5278a2e1bf1d3f2ae67f670c524b9f878
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328522"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="6c98e-103">Moduli per cui è richiesta l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="6c98e-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="6c98e-104">RIEPILOGO</span><span class="sxs-lookup"><span data-stu-id="6c98e-104">SYNOPSIS</span></span>

<span data-ttu-id="6c98e-105">Gli uffici legali di alcuni editori di moduli richiedono che i clienti accettino in modo esplicito la licenza prima di installare il modulo da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="6c98e-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="6c98e-106">Se un utente installa, aggiorna o salva un modulo con PowerShellGet, direttamente o come dipendenza per un altro pacchetto, e tale modulo richiede all'utente di accettare una licenza, l'utente deve confermare l'accettazione della licenza o l'operazione ha esito negativo.</span><span class="sxs-lookup"><span data-stu-id="6c98e-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another package, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="6c98e-107">Requisiti di pubblicazione per i moduli</span><span class="sxs-lookup"><span data-stu-id="6c98e-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="6c98e-108">I moduli che prevedono la richiesta di accettazione della licenza da parte degli utenti devono soddisfare i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="6c98e-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="6c98e-109">La sezione PSData del manifesto del modulo deve includere RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="6c98e-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="6c98e-110">Il modulo deve contenere il file license.txt nella directory radice.</span><span class="sxs-lookup"><span data-stu-id="6c98e-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="6c98e-111">Il manifesto del modulo deve contenere l'URI della licenza.</span><span class="sxs-lookup"><span data-stu-id="6c98e-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="6c98e-112">Il modulo deve essere pubblicato con la versione 2.0 e successive del formato PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="6c98e-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="6c98e-113">Impatto sui cmdlet Install/Save/Update-Module</span><span class="sxs-lookup"><span data-stu-id="6c98e-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="6c98e-114">I cmdlet Install/Save/Update supporteranno il nuovo parametro -AcceptLicense, che specifica un comportamento corrispondente alla presa in visione e accettazione della licenza da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6c98e-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="6c98e-115">Se RequiredLicenseAcceptance è True e il parametro -AcceptLicense: non viene specificato, all'utente verrà mostrato il file license.txt e la richiesta: &quot;Si accettano le condizioni di licenza (Yes/No/YesToAll/NoToAll)&quot;.</span><span class="sxs-lookup"><span data-stu-id="6c98e-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="6c98e-116">Se la licenza viene accettata</span><span class="sxs-lookup"><span data-stu-id="6c98e-116">If the license is accepted</span></span>
    - <span data-ttu-id="6c98e-117">**Save-Module:** il modulo verrà copiato nel sistema dell'utente</span><span class="sxs-lookup"><span data-stu-id="6c98e-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="6c98e-118">**Install-Module:** il modulo verrà copiato nel sistema dell'utente nella cartella appropriata, in base all'ambito</span><span class="sxs-lookup"><span data-stu-id="6c98e-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="6c98e-119">**Update-Module:** il modulo verrà aggiornato.</span><span class="sxs-lookup"><span data-stu-id="6c98e-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="6c98e-120">Se la licenza non viene accettata.</span><span class="sxs-lookup"><span data-stu-id="6c98e-120">If the license is declined.</span></span>
    - <span data-ttu-id="6c98e-121">L'operazione verrà annullata.</span><span class="sxs-lookup"><span data-stu-id="6c98e-121">Operation will be cancelled.</span></span>
    - <span data-ttu-id="6c98e-122">Tutti i cmdlet controlleranno se sono presenti i metadati (RequireLicenseAcceptance e versione del formato) che indicano che è richiesta l'accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="6c98e-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="6c98e-123">Se la versione del formato del client è precedente alla 2.0, l'operazione avrà esito negativo e verrà richiesto all'utente di aggiornare il client.</span><span class="sxs-lookup"><span data-stu-id="6c98e-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
    - <span data-ttu-id="6c98e-124">Se il modulo è stato pubblicato con una versione del formato precedente alla 2.0, il flag RequireLicenseAcceptance flag verrà ignorato.</span><span class="sxs-lookup"><span data-stu-id="6c98e-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="6c98e-125">Dipendenze del modulo</span><span class="sxs-lookup"><span data-stu-id="6c98e-125">Module Dependencies</span></span>

- <span data-ttu-id="6c98e-126">Durante le operazioni Install/Save/Update, se un modulo dipendente (qualcos'altro dipende dal modulo) richiede l'accettazione della licenza, sarà richiesto il comportamento di accettazione della licenza sopra descritto.</span><span class="sxs-lookup"><span data-stu-id="6c98e-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="6c98e-127">Se la versione del modulo è già elencata nel catalogo locale come installata nel sistema, il controllo della licenza non viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="6c98e-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="6c98e-128">Durante le operazioni Install/Save/Update, se un modulo dipendente richiede una licenza e la licenza non viene accettata, l'operazione avrà esito negativo e si seguiranno i processi normali per i casi di installazione/salvataggio/aggiornamento non riusciti per il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="6c98e-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the package failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="6c98e-129">Impatto su -Force</span><span class="sxs-lookup"><span data-stu-id="6c98e-129">Impact on -Force</span></span>

<span data-ttu-id="6c98e-130">Specificare `–Force` NON è sufficiente per accettare una licenza.</span><span class="sxs-lookup"><span data-stu-id="6c98e-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="6c98e-131">Per autorizzare l'installazione è richiesto il parametro `–AcceptLicense`.</span><span class="sxs-lookup"><span data-stu-id="6c98e-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="6c98e-132">Se si specifica il parametro `–Force`, RequiredLicenseAcceptance è True e il parametro `–AcceptLicense` non viene specificato, l'operazione avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="6c98e-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="6c98e-133">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="6c98e-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="6c98e-134">Esempio 1: aggiornare il manifesto del modulo per richiedere l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="6c98e-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="6c98e-135">Questo comando aggiorna il file manifesto e imposta il flag RequireLicenseAcceptance su true.</span><span class="sxs-lookup"><span data-stu-id="6c98e-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="6c98e-136">Esempio 2: installare un modulo che richiede l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="6c98e-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="6c98e-137">Questo comando mostra la licenza dal file license.txt e richiede all'utente di accettare la licenza.</span><span class="sxs-lookup"><span data-stu-id="6c98e-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="6c98e-138">Esempio 3: installare un modulo che richiede l'accettazione della licenza con -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="6c98e-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="6c98e-139">Il modulo viene installato senza visualizzare alcuna richiesta di accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="6c98e-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="6c98e-140">Esempio 4: installare un modulo che richiede l'accettazione della licenza con -Force</span><span class="sxs-lookup"><span data-stu-id="6c98e-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="6c98e-141">Esempio 5: installare un modulo con dipendenze che richiede l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="6c98e-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="6c98e-142">Il modulo 'ModuleWithDependency' dipende dal modulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="6c98e-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="6c98e-143">All'utente viene richiesto di accettare la licenza.</span><span class="sxs-lookup"><span data-stu-id="6c98e-143">User is prompted to Accept License.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```output
License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="6c98e-144">Esempio 6: installare un modulo con dipendenze che richiede l'accettazione della licenza e il parametro -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="6c98e-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="6c98e-145">Il modulo 'ModuleWithDependency' dipende dal modulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="6c98e-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="6c98e-146">All'utente non viene richiesto di accettare la licenza perché viene specificato il parametro -AcceptLicense.</span><span class="sxs-lookup"><span data-stu-id="6c98e-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="6c98e-147">Esempio 7: installare un modulo che richiede l'accettazione della licenza in un client meno recente di PSGetFormatVersion 2.0</span><span class="sxs-lookup"><span data-stu-id="6c98e-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="6c98e-148">Esempio 8: salvare un modulo che richiede l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="6c98e-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="6c98e-149">Questo comando mostra la licenza dal file license.txt e richiede all'utente di accettare la licenza.</span><span class="sxs-lookup"><span data-stu-id="6c98e-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="6c98e-150">Esempio 9: salvare un modulo che richiede l'accettazione della licenza con -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="6c98e-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="6c98e-151">Il modulo viene salvato senza alcuna richiesta di accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="6c98e-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="6c98e-152">Esempio 10: aggiornare un modulo che richiede l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="6c98e-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="6c98e-153">Questo comando mostra la licenza dal file license.txt e richiede all'utente di accettare la licenza.</span><span class="sxs-lookup"><span data-stu-id="6c98e-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="6c98e-154">Esempio 11: aggiornare un modulo che richiede l'accettazione della licenza con -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="6c98e-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="6c98e-155">Il modulo viene aggiornato senza alcuna richiesta di accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="6c98e-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="6c98e-156">Altri dettagli</span><span class="sxs-lookup"><span data-stu-id="6c98e-156">More details</span></span>

[<span data-ttu-id="6c98e-157">Richiedere l'accettazione della licenza per gli script</span><span class="sxs-lookup"><span data-stu-id="6c98e-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="6c98e-158">Richiedere il supporto dell'accettazione della licenza in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="6c98e-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[<span data-ttu-id="6c98e-159">Richiedere l'accettazione della licenza per la distribuzione in Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="6c98e-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)