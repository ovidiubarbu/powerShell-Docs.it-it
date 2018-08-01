---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: cd3338ae305896e282056a871974e5f899ef6ff5
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268579"
---
# <a name="reporting-on-jea"></a><span data-ttu-id="5b9b0-102">Creazione di report per JEA</span><span class="sxs-lookup"><span data-stu-id="5b9b0-102">Reporting on JEA</span></span>

<span data-ttu-id="5b9b0-103">Per creare report sullo stato della configurazione JEA, è possibile usare:</span><span class="sxs-lookup"><span data-stu-id="5b9b0-103">In order to report on the state of your JEA configuration, you can use:</span></span>

1. <span data-ttu-id="5b9b0-104">**Get-PSSessionConfiguration** per restituire un elenco di tutti gli endpoint registrati in un determinato computer.</span><span class="sxs-lookup"><span data-stu-id="5b9b0-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2. <span data-ttu-id="5b9b0-105">**Get-PSSessionCapability** per ottenere un report delle capacità a disposizione di ogni utente su un endpoint specifico.</span><span class="sxs-lookup"><span data-stu-id="5b9b0-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="5b9b0-106">Ecco un esempio di **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="5b9b0-106">Here's an example of **Get-PSSessionCapability**:</span></span>

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

<span data-ttu-id="5b9b0-107">Per creare un report delle _azioni_ eseguite dagli utenti durante una sessione JEA, è possibile:</span><span class="sxs-lookup"><span data-stu-id="5b9b0-107">To report on the _actions_ users took during a JEA session, you can:</span></span>

1. <span data-ttu-id="5b9b0-108">Abilitare le trascrizioni "Over The Shoulder" per l'endpoint JEA e vedere la directory delle trascrizioni per un log completo delle azioni di ogni utente</span><span class="sxs-lookup"><span data-stu-id="5b9b0-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="5b9b0-109">Attivare la registrazione per i moduli di PowerShell ed esaminare i registri eventi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5b9b0-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>