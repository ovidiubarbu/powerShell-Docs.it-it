---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Moduli per cui è richiesta l'accettazione della licenza
ms.openlocfilehash: a2f7ed72aae8579a6723f65b86dd0993f1a22afd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "80082822"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="4b168-103">Moduli per cui è richiesta l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="4b168-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="4b168-104">RIEPILOGO</span><span class="sxs-lookup"><span data-stu-id="4b168-104">SYNOPSIS</span></span>

<span data-ttu-id="4b168-105">Gli uffici legali di alcuni editori di moduli richiedono che i clienti accettino in modo esplicito la licenza prima di installare il modulo da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="4b168-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="4b168-106">Se un utente installa, aggiorna o salva un modulo con PowerShellGet, direttamente o come dipendenza per un altro pacchetto, e tale modulo richiede all'utente di accettare una licenza, l'utente deve confermare l'accettazione della licenza o l'operazione ha esito negativo.</span><span class="sxs-lookup"><span data-stu-id="4b168-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another package, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="4b168-107">Requisiti di pubblicazione per i moduli</span><span class="sxs-lookup"><span data-stu-id="4b168-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="4b168-108">I moduli che prevedono la richiesta di accettazione della licenza da parte degli utenti devono soddisfare i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="4b168-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="4b168-109">La sezione PSData del manifesto del modulo deve includere RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="4b168-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="4b168-110">Il modulo deve contenere il file license.txt nella directory radice.</span><span class="sxs-lookup"><span data-stu-id="4b168-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="4b168-111">Il manifesto del modulo deve contenere l'URI della licenza.</span><span class="sxs-lookup"><span data-stu-id="4b168-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="4b168-112">Il modulo deve essere pubblicato con la versione 2.0 e successive del formato PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="4b168-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="4b168-113">Impatto sui cmdlet Install/Save/Update-Module</span><span class="sxs-lookup"><span data-stu-id="4b168-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="4b168-114">I cmdlet Install/Save/Update supportano il nuovo parametro **AcceptLicense** che specifica un comportamento corrispondente alla presa in visione e accettazione della licenza da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="4b168-114">Install/Save/Update cmdlets support a new parameter **AcceptLicense** that behaves as though the user saw the license.</span></span>
- <span data-ttu-id="4b168-115">Se **RequiredLicenseAcceptance** è True e il parametro **AcceptLicense** non viene specificato, l'utente visualizza `license.txt` e il messaggio `Do you accept these license terms
  (Yes/No/YesToAll/NoToAll)`.</span><span class="sxs-lookup"><span data-stu-id="4b168-115">If **RequiredLicenseAcceptance** is True and **AcceptLicense** is not specified, the user is shown the `license.txt`, and prompted with: `Do you accept these license terms
  (Yes/No/YesToAll/NoToAll)`.</span></span>
  - <span data-ttu-id="4b168-116">Se la licenza viene accettata</span><span class="sxs-lookup"><span data-stu-id="4b168-116">If the license is accepted</span></span>
    - <span data-ttu-id="4b168-117">**Save-Module:** il modulo viene copiato nel sistema dell'utente</span><span class="sxs-lookup"><span data-stu-id="4b168-117">**Save-Module:** the module is copied to the user's system</span></span>
    - <span data-ttu-id="4b168-118">**Install-Module:** il modulo viene copiato nel sistema dell'utente nella cartella appropriata, in base all'ambito</span><span class="sxs-lookup"><span data-stu-id="4b168-118">**Install-Module:** the module is copied to the user's system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="4b168-119">**Update-Module:** il modulo viene aggiornato.</span><span class="sxs-lookup"><span data-stu-id="4b168-119">**Update-Module:** the module is updated.</span></span>
  - <span data-ttu-id="4b168-120">Se la licenza non viene accettata.</span><span class="sxs-lookup"><span data-stu-id="4b168-120">If the license is declined.</span></span>
    - <span data-ttu-id="4b168-121">L'operazione viene annullata.</span><span class="sxs-lookup"><span data-stu-id="4b168-121">Operation is canceled.</span></span>
    - <span data-ttu-id="4b168-122">Tutti i cmdlet controllano se sono presenti i metadati (**requireLicenseAcceptance** e versione del formato) a indicare che è richiesta l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="4b168-122">All cmdlets check for the metadata (**requireLicenseAcceptance** and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="4b168-123">Se la versione del formato del client è precedente alla 2.0, l'operazione ha esito negativo e viene richiesto all'utente di aggiornare il client.</span><span class="sxs-lookup"><span data-stu-id="4b168-123">If format version of client is older than 2.0, operation fails and asks the user to update the client.</span></span>
    - <span data-ttu-id="4b168-124">Se il modulo è stato pubblicato con una versione del formato precedente alla 2.0, il flag requireLicenseAcceptance viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="4b168-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag is ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="4b168-125">Dipendenze del modulo</span><span class="sxs-lookup"><span data-stu-id="4b168-125">Module Dependencies</span></span>

- <span data-ttu-id="4b168-126">Durante le operazioni Install/Save/Update, se un modulo dipendente (qualcos'altro dipende dal modulo) richiede l'accettazione della licenza, è richiesto il comportamento di accettazione della licenza sopra descritto.</span><span class="sxs-lookup"><span data-stu-id="4b168-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) is required.</span></span>
- <span data-ttu-id="4b168-127">Se la versione del modulo è già elencata nel catalogo locale come installata nel sistema, il controllo della licenza non viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="4b168-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="4b168-128">Durante le operazioni Install/Save/Update, se un modulo dipendente richiede una licenza e la licenza non viene accettata, l'operazione ha esito negativo e si seguono i processi normali per i casi di installazione/salvataggio/aggiornamento non riusciti per il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="4b168-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation fails and follows normal processes for the package failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="4b168-129">Impatto su -Force</span><span class="sxs-lookup"><span data-stu-id="4b168-129">Impact on -Force</span></span>

<span data-ttu-id="4b168-130">Specificare `–Force` NON è sufficiente per accettare una licenza.</span><span class="sxs-lookup"><span data-stu-id="4b168-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="4b168-131">Per autorizzare l'installazione è richiesto il parametro `–AcceptLicense`.</span><span class="sxs-lookup"><span data-stu-id="4b168-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="4b168-132">Se si specifica il parametro `–Force`, RequiredLicenseAcceptance è True e il parametro `–AcceptLicense` NON viene specificato, l'operazione ha esito negativo.</span><span class="sxs-lookup"><span data-stu-id="4b168-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation fails.</span></span>

## <a name="examples"></a><span data-ttu-id="4b168-133">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="4b168-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="4b168-134">Esempio 1: aggiornare il manifesto del modulo per richiedere l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="4b168-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="4b168-135">Questo comando aggiorna il file manifesto e imposta il flag RequireLicenseAcceptance su true.</span><span class="sxs-lookup"><span data-stu-id="4b168-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="4b168-136">Esempio 2: installare un modulo che richiede l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="4b168-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
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

<span data-ttu-id="4b168-137">Questo comando visualizza la licenza dal file `license.txt` e richiede all'utente di accettare la licenza.</span><span class="sxs-lookup"><span data-stu-id="4b168-137">This command shows the license from `license.txt` file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="4b168-138">Esempio 3: installare un modulo che richiede l'accettazione della licenza con -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="4b168-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="4b168-139">Il modulo viene installato senza visualizzare alcuna richiesta di accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="4b168-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="4b168-140">Esempio 4: installare un modulo che richiede l'accettazione della licenza con -Force</span><span class="sxs-lookup"><span data-stu-id="4b168-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```Output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="4b168-141">Esempio 5: installare un modulo con dipendenze che richiede l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="4b168-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="4b168-142">Il modulo **ModuleWithDependency** dipende dal modulo **ModuleRequireLicenseAcceptance**.</span><span class="sxs-lookup"><span data-stu-id="4b168-142">Module **ModuleWithDependency** depends on module **ModuleRequireLicenseAcceptance**.</span></span> <span data-ttu-id="4b168-143">All'utente viene richiesto di accettare la licenza.</span><span class="sxs-lookup"><span data-stu-id="4b168-143">User is prompted to accept license.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```Output
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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="4b168-144">Esempio 6: installare un modulo con dipendenze che richiede l'accettazione della licenza e il parametro -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="4b168-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="4b168-145">Il modulo **ModuleWithDependency** dipende dal modulo **ModuleRequireLicenseAcceptance**.</span><span class="sxs-lookup"><span data-stu-id="4b168-145">Module **ModuleWithDependency** depends on module **ModuleRequireLicenseAcceptance**.</span></span> <span data-ttu-id="4b168-146">All'utente non viene richiesto di accettare la licenza perché è specificato il parametro **AcceptLicense**.</span><span class="sxs-lookup"><span data-stu-id="4b168-146">User is not prompted to accept license as **AcceptLicense** is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="4b168-147">Esempio 7: installare un modulo che richiede l'accettazione della licenza in un client meno recente di PSGetFormatVersion 2.0</span><span class="sxs-lookup"><span data-stu-id="4b168-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion
'2.0' is not supported by the current version of PowerShellGet. Get the latest version of the
PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="4b168-148">Esempio 8: salvare un modulo che richiede l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="4b168-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```Output
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

<span data-ttu-id="4b168-149">Questo comando visualizza la licenza dal file `license.txt` e richiede all'utente di accettare la licenza.</span><span class="sxs-lookup"><span data-stu-id="4b168-149">This command shows the license from `license.txt` file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="4b168-150">Esempio 9: salvare un modulo che richiede l'accettazione della licenza con -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="4b168-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="4b168-151">Il modulo viene salvato senza alcuna richiesta di accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="4b168-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="4b168-152">Esempio 10: aggiornare un modulo che richiede l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="4b168-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```Output
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

<span data-ttu-id="4b168-153">Questo comando visualizza la licenza dal file `license.txt` e richiede all'utente di accettare la licenza.</span><span class="sxs-lookup"><span data-stu-id="4b168-153">This command shows the license from `license.txt` file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="4b168-154">Esempio 11: aggiornare un modulo che richiede l'accettazione della licenza con -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="4b168-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="4b168-155">Il modulo viene aggiornato senza alcuna richiesta di accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="4b168-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="4b168-156">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="4b168-156">More details</span></span>

[<span data-ttu-id="4b168-157">Richiedere l'accettazione della licenza per gli script</span><span class="sxs-lookup"><span data-stu-id="4b168-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="4b168-158">Richiedere il supporto dell'accettazione della licenza in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="4b168-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[<span data-ttu-id="4b168-159">Richiedere l'accettazione della licenza per la distribuzione in Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="4b168-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
