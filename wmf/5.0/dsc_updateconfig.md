---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 6d37fbc5091d69925d60349f3acbdecc92da1b95
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220343"
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
