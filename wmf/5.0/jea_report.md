---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: cd3338ae305896e282056a871974e5f899ef6ff5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085258"
---
# <a name="reporting-on-jea"></a><span data-ttu-id="b1fbc-102">Creazione di report per JEA</span><span class="sxs-lookup"><span data-stu-id="b1fbc-102">Reporting on JEA</span></span>

<span data-ttu-id="b1fbc-103">Per creare report sullo stato della configurazione JEA, è possibile usare:</span><span class="sxs-lookup"><span data-stu-id="b1fbc-103">In order to report on the state of your JEA configuration, you can use:</span></span>

1. <span data-ttu-id="b1fbc-104">**Get-PSSessionConfiguration** per restituire un elenco di tutti gli endpoint registrati in un determinato computer.</span><span class="sxs-lookup"><span data-stu-id="b1fbc-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2. <span data-ttu-id="b1fbc-105">**Get-PSSessionCapability** per ottenere un report delle capacità a disposizione di ogni utente su un endpoint specifico.</span><span class="sxs-lookup"><span data-stu-id="b1fbc-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="b1fbc-106">Ecco un esempio di **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="b1fbc-106">Here's an example of **Get-PSSessionCapability**:</span></span>

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

<span data-ttu-id="b1fbc-107">Per creare un report delle _azioni_ eseguite dagli utenti durante una sessione JEA, è possibile:</span><span class="sxs-lookup"><span data-stu-id="b1fbc-107">To report on the _actions_ users took during a JEA session, you can:</span></span>

1. <span data-ttu-id="b1fbc-108">Abilitare le trascrizioni "Over The Shoulder" per l'endpoint JEA e vedere la directory delle trascrizioni per un log completo delle azioni di ogni utente</span><span class="sxs-lookup"><span data-stu-id="b1fbc-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="b1fbc-109">Attivare la registrazione per i moduli di PowerShell ed esaminare i registri eventi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1fbc-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>