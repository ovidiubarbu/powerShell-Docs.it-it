---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 2fb2e4b0c40322b5ec78fabede22a7e3ecbbd2aa
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093763"
---
# <a name="reporting-on-jea"></a>Creazione di report per JEA

Per creare report sullo stato della configurazione JEA, è possibile usare:

1. **Get-PSSessionConfiguration** per restituire un elenco di tutti gli endpoint registrati in un determinato computer.
1. **Get-PSSessionCapability** per ottenere un report delle capacità a disposizione di ogni utente su un endpoint specifico.

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
