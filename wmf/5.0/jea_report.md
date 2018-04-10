---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 2af56be1915c148809f52cd9040c45da160ae0a2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
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