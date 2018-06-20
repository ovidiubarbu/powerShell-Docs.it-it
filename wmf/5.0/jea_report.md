---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 7982acc111e95b4167f948314f176d53f39d3620
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218723"
---
# <a name="reporting-on-jea"></a>Creazione di report per JEA
Per creare report sullo stato della configurazione JEA, è possibile usare:
1.  **Get-PSSessionConfiguration** per restituire un elenco di tutti gli endpoint registrati in un determinato computer.
2.  **Get-PSSessionCapability** per ottenere un report delle capacità a disposizione di ogni utente su un endpoint specifico.

Ecco un esempio di **Get-PSSessionCapability**:
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           clear -> Clear-Host
Alias           cls -> Clear-Host
Alias           exsn -> Exit-PSSession
Alias           gcm -> Get-Command
Alias           measure -> Measure-Object
Alias           select -> Select-Object
Function        Clear-Host
Function        Exit-PSSession
Function        Get-Command
Function        Get-FormatData
Function        Get-Help
Function        Get-UserInfo
Function        Measure-Object
Function        Out-Default
Function        Select-Object
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

Per creare un report delle _azioni_ eseguite dagli utenti durante una sessione JEA, è possibile:
1. Abilitare le trascrizioni "Over The Shoulder" per l'endpoint JEA e vedere la directory delle trascrizioni per un log completo delle azioni di ogni utente
2. Attivare la registrazione per i moduli di PowerShell ed esaminare i registri eventi di PowerShell.
