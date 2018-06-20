---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Richiedere l'accettazione della licenza per gli script
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34048366"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="d00a3-103">Richiedere l'accettazione della licenza per gli script</span><span class="sxs-lookup"><span data-stu-id="d00a3-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="d00a3-104">L'accettazione della licenza non è supportata per gli script.</span><span class="sxs-lookup"><span data-stu-id="d00a3-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="d00a3-105">Tuttavia, è supportato lo scenario in cui uno script dipende da un modulo che richiede l'accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="d00a3-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="d00a3-106">I comandi per gli script (Install-Script/Save-Script/Update-Script) supportano il nuovo parametro -AcceptLicense, che specifica un comportamento corrispondente alla presa in visione e accettazione della licenza da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="d00a3-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="d00a3-107">Se il parametro -AcceptLicense non viene specificato, all'utente verrà mostrato il file license.txt per il modulo dipendente e richiesto di accettare la licenza.</span><span class="sxs-lookup"><span data-stu-id="d00a3-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="d00a3-108">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="d00a3-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="d00a3-109">Esempio 1: installare uno script con dipendenze che richiedono l'accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="d00a3-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="d00a3-110">Lo script 'ScriptRequireLicenseAcceptance' dipende dal modulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="d00a3-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="d00a3-111">All'utente viene richiesto di accettare la licenza.</span><span class="sxs-lookup"><span data-stu-id="d00a3-111">User is prompted to Accept License.</span></span>

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="d00a3-112">Esempio 2: installare uno script con dipendenze che richiedono l'accettazione della licenza e il parametro -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="d00a3-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="d00a3-113">Lo script 'ScriptRequireLicenseAcceptance' dipende dal modulo 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="d00a3-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="d00a3-114">All'utente non viene richiesto di accettare la licenza perché viene specificato il parametro -AcceptLicense.</span><span class="sxs-lookup"><span data-stu-id="d00a3-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="d00a3-115">Altri dettagli</span><span class="sxs-lookup"><span data-stu-id="d00a3-115">More details</span></span>

- [<span data-ttu-id="d00a3-116">Richiedere il supporto dell'accettazione della licenza per i moduli</span><span class="sxs-lookup"><span data-stu-id="d00a3-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="d00a3-117">Richiedere il supporto dell'accettazione della licenza in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="d00a3-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [<span data-ttu-id="d00a3-118">Richiedere l'accettazione della licenza per la distribuzione in Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="d00a3-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)