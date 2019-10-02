---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Richiedere l'accettazione della licenza per gli script
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328082"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Richiedere l'accettazione della licenza per gli script

L'accettazione della licenza non è supportata per gli script. Tuttavia, è supportato lo scenario in cui uno script dipende da un modulo che richiede l'accettazione della licenza.

I comandi per gli script (Install-Script/Save-Script/Update-Script) supportano il nuovo parametro -AcceptLicense, che specifica un comportamento corrispondente alla presa in visione e accettazione della licenza da parte dell'utente. Se il parametro -AcceptLicense non viene specificato, all'utente verrà mostrato il file license.txt per il modulo dipendente e richiesto di accettare la licenza.

## <a name="examples"></a>ESEMPI

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Esempio 1: installare uno script con dipendenze che richiedono l'accettazione della licenza

Lo script 'ScriptRequireLicenseAcceptance' dipende dal modulo 'ModuleRequireLicenseAcceptance'. All'utente viene richiesto di accettare la licenza.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Esempio 2: installare uno script con dipendenze che richiedono l'accettazione della licenza e il parametro -AcceptLicense

Lo script 'ScriptRequireLicenseAcceptance' dipende dal modulo 'ModuleRequireLicenseAcceptance'. All'utente non viene richiesto di accettare la licenza perché viene specificato il parametro -AcceptLicense.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Altri dettagli

- [Richiedere il supporto dell'accettazione della licenza per i moduli](module-license-acceptance.md)
- [Richiedere il supporto dell'accettazione della licenza in PowerShell Gallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Richiedere l'accettazione della licenza per la distribuzione in Automazione di Azure](../how-to/working-with-packages/deploy-to-azure-automation.md)
