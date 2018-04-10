---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 27f8fab6a72e7f3a3f510f5a9e503bbfb8a8f618
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="8debc-102">PULL su richiesta delle configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="8debc-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="8debc-103">Il nuovo cmdlet Update-DscConfiguration attiva un'operazione di pull dai server di pull definiti nella metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="8debc-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="8debc-104">Questo comportamento è spesso indicato anche come 'pull immediato'.</span><span class="sxs-lookup"><span data-stu-id="8debc-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="8debc-105">Una volta attivato, il pull funziona esattamente come nell'ambito della normale frequenza:</span><span class="sxs-lookup"><span data-stu-id="8debc-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="8debc-106">Il checksum per la configurazione corrente viene confrontato con il checksum per la configurazione nel server di pull.</span><span class="sxs-lookup"><span data-stu-id="8debc-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="8debc-107">Se sono uguali, l'operazione viene completata correttamente senza applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="8debc-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="8debc-108">In presenza di differenze, viene effettuato il pull della configurazione dal server di pull e poi la configurazione viene applicata.</span><span class="sxs-lookup"><span data-stu-id="8debc-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="8debc-109">**Nota:** se RefreshMode = 'Push' per la metaconfigurazione, il cmdlet restituisce un errore in modo che questo cmdlet non esegua mai alcuna operazione quando un nodo di destinazione è in modalità 'Push'.</span><span class="sxs-lookup"><span data-stu-id="8debc-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```