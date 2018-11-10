---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Moduli per cui è richiesta l'accettazione della licenza
ms.openlocfilehash: 369e32d5278a2e1bf1d3f2ae67f670c524b9f878
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002668"
---
# <a name="modules-requiring-license-acceptance"></a>Moduli per cui è richiesta l'accettazione della licenza

## <a name="synopsis"></a>RIEPILOGO

Gli uffici legali di alcuni editori di moduli richiedono che i clienti accettino in modo esplicito la licenza prima di installare il modulo da PowerShell Gallery. Se un utente installa, aggiorna o salva un modulo con PowerShellGet, direttamente o come dipendenza per un altro pacchetto, e tale modulo richiede all'utente di accettare una licenza, l'utente deve confermare l'accettazione della licenza o l'operazione ha esito negativo.

## <a name="publish-requirements-for-modules"></a>Requisiti di pubblicazione per i moduli

I moduli che prevedono la richiesta di accettazione della licenza da parte degli utenti devono soddisfare i requisiti seguenti:

- La sezione PSData del manifesto del modulo deve includere RequireLicenseAcceptance = $True.
- Il modulo deve contenere il file license.txt nella directory radice.
- Il manifesto del modulo deve contenere l'URI della licenza.
- Il modulo deve essere pubblicato con la versione 2.0 e successive del formato PowerShellGet.

## <a name="impact-on-installsaveupdate-module"></a>Impatto sui cmdlet Install/Save/Update-Module

- I cmdlet Install/Save/Update supporteranno il nuovo parametro -AcceptLicense, che specifica un comportamento corrispondente alla presa in visione e accettazione della licenza da parte dell'utente.
- Se RequiredLicenseAcceptance è True e il parametro -AcceptLicense: non viene specificato, all'utente verrà mostrato il file license.txt e richiesto se &quot;accetta le condizioni di licenza (Yes/No/YesToAll/NoToAll)&quot;.
  - Se la licenza viene accettata
    - **Save-Module:** il modulo verrà copiato nel sistema dell'utente
    - **Install-Module:** il modulo verrà copiato nel sistema dell'utente nella cartella appropriata, in base all'ambito
    - **Update-Module:** il modulo verrà aggiornato.
  - Se la licenza non viene accettata.
    - L'operazione verrà annullata.
    - Tutti i cmdlet controlleranno se sono presenti i metadati (RequireLicenseAcceptance e versione del formato) che indicano che è richiesta l'accettazione della licenza.
    - Se la versione del formato del client è precedente alla 2.0, l'operazione avrà esito negativo e verrà richiesto all'utente di aggiornare il client.
    - Se il modulo è stato pubblicato con una versione del formato precedente alla 2.0, il flag RequireLicenseAcceptance flag verrà ignorato.

## <a name="module-dependencies"></a>Dipendenze del modulo

- Durante le operazioni Install/Save/Update, se un modulo dipendente (qualcos'altro dipende dal modulo) richiede l'accettazione della licenza, sarà richiesto il comportamento di accettazione della licenza sopra descritto.
- Se la versione del modulo è già elencata nel catalogo locale come installata nel sistema, il controllo della licenza non viene eseguito.
- Durante le operazioni Install/Save/Update, se un modulo dipendente richiede una licenza e la licenza non viene accettata, l'operazione avrà esito negativo e si seguiranno i processi normali per i casi di installazione/salvataggio/aggiornamento non riusciti per il pacchetto.

## <a name="impact-on--force"></a>Impatto su -Force

Specificare `–Force` NON è sufficiente per accettare una licenza. Per autorizzare l'installazione è richiesto il parametro `–AcceptLicense`. Se si specifica il parametro `–Force`, RequiredLicenseAcceptance è True e il parametro `–AcceptLicense` non viene specificato, l'operazione avrà esito negativo.

## <a name="examples"></a>ESEMPI

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Esempio 1: aggiornare il manifesto del modulo per richiedere l'accettazione della licenza

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

Questo comando aggiorna il file manifesto e imposta il flag RequireLicenseAcceptance su true.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Esempio 2: installare un modulo che richiede l'accettazione della licenza

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

Questo comando mostra la licenza dal file license.txt e richiede all'utente di accettare la licenza.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Esempio 3: installare un modulo che richiede l'accettazione della licenza con -AcceptLicense

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Il modulo viene installato senza visualizzare alcuna richiesta di accettazione della licenza.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Esempio 4: installare un modulo che richiede l'accettazione della licenza con -Force

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

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Esempio 5: installare un modulo con dipendenze che richiede l'accettazione della licenza

Il modulo 'ModuleWithDependency' dipende dal modulo 'ModuleRequireLicenseAcceptance'. All'utente viene richiesto di accettare la licenza.

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Esempio 6: installare un modulo con dipendenze che richiede l'accettazione della licenza e il parametro -AcceptLicense

Il modulo 'ModuleWithDependency' dipende dal modulo 'ModuleRequireLicenseAcceptance'. All'utente non viene richiesto di accettare la licenza perché viene specificato il parametro -AcceptLicense.

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Esempio 7: installare un modulo che richiede l'accettazione della licenza in un client meno recente di PSGetFormatVersion 2.0

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a>Esempio 8: salvare un modulo che richiede l'accettazione della licenza

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

Questo comando mostra la licenza dal file license.txt e richiede all'utente di accettare la licenza.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Esempio 9: salvare un modulo che richiede l'accettazione della licenza con -AcceptLicense

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

Il modulo viene salvato senza alcuna richiesta di accettazione della licenza.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Esempio 10: aggiornare un modulo che richiede l'accettazione della licenza

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

Questo comando mostra la licenza dal file license.txt e richiede all'utente di accettare la licenza.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Esempio 11: aggiornare un modulo che richiede l'accettazione della licenza con -AcceptLicense

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Il modulo viene aggiornato senza alcuna richiesta di accettazione della licenza.

## <a name="more-details"></a>Altri dettagli

[Richiedere l'accettazione della licenza per gli script](./script-license-acceptance.md)

[Richiedere il supporto dell'accettazione della licenza in PowerShell Gallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[Richiedere l'accettazione della licenza per la distribuzione in Automazione di Azure](../how-to/working-with-packages/deploy-to-azure-automation.md)
