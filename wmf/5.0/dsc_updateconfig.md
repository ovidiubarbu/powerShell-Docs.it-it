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
# <a name="on-demand-pull-of-dsc-configurations"></a>PULL su richiesta delle configurazioni DSC

Il nuovo cmdlet Update-DscConfiguration attiva un'operazione di pull dai server di pull definiti nella metaconfigurazione. Questo comportamento è spesso indicato anche come 'pull immediato'.


Una volta attivato, il pull funziona esattamente come nell'ambito della normale frequenza:

1. Il checksum per la configurazione corrente viene confrontato con il checksum per la configurazione nel server di pull.
2. Se sono uguali, l'operazione viene completata correttamente senza applicare la configurazione.
3. In presenza di differenze, viene effettuato il pull della configurazione dal server di pull e poi la configurazione viene applicata.

**Nota:** se RefreshMode = 'Push' per la metaconfigurazione, il cmdlet restituisce un errore in modo che questo cmdlet non esegua mai alcuna operazione quando un nodo di destinazione è in modalità 'Push'.

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