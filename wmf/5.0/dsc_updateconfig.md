---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 410fa4b6c6d3e2708da78414cbb9b80dd3ca1387
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="on-demand-pull-of-dsc-configurations" class="xliff"></a>
# PULL su richiesta delle configurazioni DSC

Il nuovo cmdlet Update-DscConfiguration attiva un'operazione di pull dai server di pull definiti nella metaconfigurazione. Questo comportamento è spesso indicato anche come 'pull immediato'. 


Una volta attivato, il pull funziona esattamente come nell'ambito della normale frequenza:

1. Il checksum per la configurazione corrente viene confrontato con il checksum per la configurazione nel server di pull. 
2. Se sono uguali, l'operazione viene completata correttamente senza applicare la configurazione. 
3. In presenza di differenze, viene effettuato il pull della configurazione dal server di pull e poi la configurazione viene applicata.

**Nota:** se RefreshMode = 'Push' per la metaconfigurazione, il cmdlet restituisce un errore in modo che questo cmdlet non esegua mai alcuna operazione quando un nodo di destinazione è in modalità 'Push'.

```PowerShell
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

